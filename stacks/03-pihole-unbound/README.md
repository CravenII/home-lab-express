# Pi-hole + Unbound — mini-guía
**Stack 3 de 3 de la muestra gratuita de «Home Lab Express»**

## Qué hace
**Pi-hole** es un filtro DNS para toda tu red: bloquea publicidad, rastreadores y dominios maliciosos antes de que lleguen a tus dispositivos. Funciona en el móvil, la Smart TV y el portátil **sin instalar nada en cada uno**: basta con que usen tu Pi como DNS.
**Unbound** resuelve las consultas DNS de forma recursiva y privada, con DNSSEC: ni tu proveedor de internet ni un DNS público ven el conjunto de tus consultas.

## Requisitos
- Raspberry Pi 4/5 (o cualquier equipo) con Docker y Docker Compose instalados.
- Puertos **53 TCP/UDP** y **8080** libres en el equipo.
- Poder cambiar el servidor DNS en tu router (o, en su defecto, en cada dispositivo). **Sin este paso, Pi-hole no filtra nada.**

## Cómo levantarlo
```bash
cd 03-pihole-unbound
export FTL_WEBPASSWORD='elige-una-clave-segura'
sudo -E docker compose up -d
```
(`-E` es importante: pasa tu variable de entorno al comando con sudo.)

## Cómo verificar que funciona
1. Panel web: `http://IP-DE-TU-PI:8080/admin` → entra con la clave que definiste.
2. Prueba DNS desde tu PC apuntando a la Pi:
```bash
nslookup google.com IP-DE-TU-PI
```
3. **Actívalo en tu red:** entra a tu router y cambia el DNS primario por la IP de tu Pi (guarda el DNS anterior por si quieres revertirlo). Ojo: si tu router no lo permite, cambia el DNS en cada dispositivo.
4. Visita una web con anuncios desde el móvil: deberías verlos bloqueados, y el contador del panel de Pi-hole subiendo.

## Primeros pasos (15 minutos)
1. **Añade listas de bloqueo** (el pack base ya filtra, pero puedes ampliar): en el panel, *Adlists* → añade listas conocidas de la comunidad (p. ej. las recomendadas en https://firebog.net) → *Tools → Update Gravity*.
2. **Lista blanca si algo se rompe:** alguna web legítima puede fallar por un falso positivo. En *Query Log* busca la consulta bloqueada y añádela a la allowlist.
3. **IP fija para la Pi:** si la IP de tu Pi cambia, toda tu red se queda sin DNS. Asigna una IP fija por DHCP en tu router (recomendado) o configúrala en el equipo.

## Los 3 errores típicos
1. **El puerto 53 está ocupado:** en Raspberry Pi OS, `systemd-resolved` a veces lo usa. Comprueba con `sudo ss -tulpn | grep ':53 '`. Si es `systemd-resolved` escuchando solo en `127.0.0.53`, no hay conflicto (Docker puede bindear el 53 en las demás interfaces). Si otro proceso ocupa el 53 en todas las interfaces, tendrás que liberarlo.
2. **Sin internet tras cambiar el DNS del router:** la Pi no resuelve. Entra al panel: si Pi-hole está caído, revierte el DNS del router al anterior y revisa `sudo docker compose logs pihole`. Unbound tarda ~30 segundos en arrancar la primera vez.
3. **`FTL_WEBPASSWORD` no definida:** el compose se niega a arrancar con un mensaje claro. Define la variable y repite el comando con `sudo -E`.

## Cómo actualizarlo sin romperlo
```bash
cd 03-pihole-unbound
export FTL_WEBPASSWORD='tu-clave-actual'
# 1. Cambia las versiones de imagen en docker-compose.yml por las nuevas estables
#    (Pi-hole: https://github.com/pi-hole/pi-hole/releases)
sudo -E docker compose pull
sudo -E docker compose up -d
```
Tus listas, consultas y ajustes viven en `./pihole`, así que sobreviven. Antes de saltos de versión mayor, haz copia de la carpeta `pihole/`.

## Cómo desinstalarlo (sin dejar rastro)
```bash
cd 03-pihole-unbound
sudo docker compose down
# ¡IMPORTANTE! Antes de apagarlo, devuelve el DNS original en tu router o
# tus dispositivos: si no, te quedas sin internet al parar Pi-hole.
# La carpeta pihole/ con tus datos queda en el equipo; bórrala si no la quieres.
```

## Aviso honesto
Pi-hole se convierte en un punto crítico de tu red: si la Pi se apaga, nadie navega. Para un uso serio, ponle una IP fija y considera una segunda instancia o un DNS secundario. Este stack de muestra es el punto de partida; el pack completo cubre alta disponibilidad y copias de seguridad.

---
*Parte de la muestra gratuita de «Home Lab Express». Versiones de imagen verificadas en sep-2026.*
