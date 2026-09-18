# Homepage — mini-guía
**Stack 2 de 3 de la muestra gratuita de «Home Lab Express»**

## Qué hace
Homepage es un panel de inicio para tu home lab: una página rápida y bonita con accesos directos a todos tus servicios (Pi-hole, Uptime Kuma, Jellyfin…), widgets de estado y barra de búsqueda. La "puerta principal": en vez de recordar diez puertos, abres una sola página.

## Requisitos
- Raspberry Pi 4/5 (o cualquier equipo) con Docker y Docker Compose instalados.
- Puerto **3000** libre en el equipo.
- ~150 MB de RAM libres.

## Cómo levantarlo
```bash
cd 02-homepage
sudo docker compose up -d
```

## Cómo verificar que funciona
1. Abre `http://IP-DE-TU-PI:3000` en tu navegador.
2. Deberías ver el panel "Mi Home Lab" con los grupos de ejemplo (Monitorización, Red).
3. Edita `config/services.yaml`, cambia `192.168.1.10` por la IP real de tu Pi, guarda, y recarga la página: los cambios aparecen sin reiniciar nada.
```bash
sudo docker compose ps
sudo docker compose logs --tail=20 homepage
```

## Primeros pasos (10 minutos)
1. **Pon tu IP real** en `config/services.yaml` (busca `192.168.1.10` y sustitúyelo).
2. **Añade tus servicios:** copia un bloque existente, cambia nombre, `href` e `icon`. Los iconos disponibles están en https://gethomepage.dev/configs/services
3. **Ajusta el aspecto** en `config/settings.yaml`: título, idioma (`es`), tema (`dark`/`light`).
4. **Widget de Docker** (opcional): añade a un servicio un bloque `widget:` tipo `docker` para ver tus contenedores en el panel. Requiere el montaje de `docker.sock` que ya viene en el compose (solo lectura).

## Los 3 errores típicos
1. **Página en blanco o error 500:** algún fichero YAML tiene un error de indentación. Comprueba con `sudo docker compose logs homepage` y revisa espacios (YAML no admite tabuladores).
2. **Los cambios en services.yaml no aparecen:** Homepage tarda unos segundos en recargar; si no, revisa que editaste el fichero dentro de `./config`, no una copia en otro sitio.
3. **Permission denied en /app/config:** el PUID/PGID del compose no coincide con tu usuario. Averigua tu UID con `id -u` y ajusta las variables `PUID`/`PGID`.

## Cómo actualizarlo sin romperlo
```bash
cd 02-homepage
# 1. Cambia la versión de la imagen en docker-compose.yml por la nueva estable
#    (https://github.com/gethomepage/homepage/releases)
sudo docker compose pull
sudo docker compose up -d
```
Tu configuración vive en `./config` (carpeta del equipo), así que sobrevive a las actualizaciones. Guarda una copia de `config/` antes de saltos de versión mayor.

## Cómo desinstalarlo (sin dejar rastro)
```bash
cd 02-homepage
sudo docker compose down
# La carpeta config/ con tus ajustes queda en el equipo; bórrala si no la quieres.
```

---
*Parte de la muestra gratuita de «Home Lab Express». Versiones de imagen verificadas en sep-2026.*
