# Uptime Kuma — mini-guía
**Stack 1 de 3 de la muestra gratuita de «Home Lab Express»**

## Qué hace
Uptime Kuma es un monitor de servicios autoalojado: comprueba cada X segundos que tus webs, contenedores o puertos responden, guarda el historial y **te avisa por Telegram (u otro canal) cuando algo se cae o se recupera**. Es el "vigilante nocturno" de tu home lab.

## Requisitos
- Raspberry Pi 4/5 (o cualquier equipo) con Docker y Docker Compose instalados.
- Puerto **3001** libre en el equipo.
- ~200 MB de RAM libres.

## Cómo levantarlo
```bash
cd 01-uptime-kuma
sudo docker compose up -d
```

## Cómo verificar que funciona
1. Abre en tu navegador `http://IP-DE-TU-PI:3001` (sustituye `IP-DE-TU-PI` por la IP local de tu Raspberry, p. ej. `http://192.168.1.10:3001`).
2. La primera vez te pedirá crear la cuenta de administrador: elige usuario y contraseña y guárdalos bien.
3. Comprueba que el contenedor está sano:
```bash
sudo docker compose ps
sudo docker compose logs --tail=20 uptime-kuma
```

## Primeros pasos (5 minutos)
1. **Añade tu primer monitor:** Dashboard → "Añadir nuevo monitor" → tipo HTTP(s) → URL de un servicio tuyo (p. ej. tu Homepage) → intervalo 60 segundos → Guardar.
2. **Configura las alertas de Telegram:** habla con `@BotFather` en Telegram, crea un bot y copia el token. En Kuma: Ajustes → Notificaciones → "Configurar notificación" → Telegram → pega el token y tu chat ID (lo obtienes hablando con `@userinfobot`). Marca "Activado por defecto" y prueba con "Probar".
3. **Simula una caída** (opcional pero instructivo): para un contenedor unos segundos y comprueba que te llega el aviso.

## Los 3 errores típicos
1. **No abre la página:** el puerto 3001 está ocupado por otro servicio. Cambia `"3001:3001"` por `"3002:3001"` en el compose y repite `sudo docker compose up -d`.
2. **No llegan las alertas de Telegram:** el chat ID más fiable es el que da `@userinfobot` escribiéndole directamente; el de un grupo requiere añadir el bot como administrador.
3. **Tras recrear el contenedor perdí los monitores:** el volumen `uptime-kuma-data` no se montó (revisa que el compose no se editó mal). Con el volumen en su sitio, los datos sobreviven a recreaciones y actualizaciones.

## Cómo actualizarlo sin romperlo
```bash
cd 01-uptime-kuma
# 1. Edita docker-compose.yml y cambia la versión de la imagen por la nueva
#    (consulta la última estable en https://github.com/louislam/uptime-kuma/releases)
# 2. Recrea con la imagen nueva:
sudo docker compose pull
sudo docker compose up -d
# 3. Verifica que la web responde y que tus monitores siguen ahí.
```
Los datos viven en el volumen, así que la actualización no borra nada. Aun así, antes de actualizar versiones mayores conviene respaldar el volumen.

## Cómo desinstalarlo (sin dejar rastro)
```bash
cd 01-uptime-kuma
sudo docker compose down -v   # -v borra también el volumen con los datos
```

---
*Parte de la muestra gratuita de «Home Lab Express». Versiones de imagen verificadas en sep-2026.*
