# Validación — Home Lab Express
**Estado:** lista para publicar · **Fecha:** 17-sep-2026 · **Gasto:** $0

## Qué hay aquí
Fase de validación del producto digital (concepto aprobado por el 17-sep-2026).
El pack completo **NO** está escrito: primero se mide si hay demanda real.

- `stacks/01-uptime-kuma/` — monitorización con alertas a Telegram (`louislam/uptime-kuma:2.5.3`)
- `stacks/02-homepage/` — panel de entrada al lab (`ghcr.io/gethomepage/homepage:v2.1.0`)
- `stacks/03-pihole-unbound/` — bloqueador de anuncios + DNS privado (`pihole/pihole:2026.07.2` + `l33tlamer/unbound-recursive:1.25.1`)
- Cada stack: `docker-compose.yml` (sin `version:`, versiones fijadas, comentarios en español) + `README.md` con mini-guía.
- `index.html` — página de aterrizaje (estilo coherente con el sitio de afiliados): ofrece los 3 stacks gratis, botón "Me interesa el pack completo" (`mailto:[EMAIL_CONTACTO]`), y plan de medición público con umbrales propuestos.
- `style.css` — copia del estilo del sitio de afiliados (la carpeta es autocontenida).

## Qué falta (en orden)
1. **Crear el repositorio GitHub** (gratis) y subir los 3 stacks. Sustituir `[USUARIO]` en los enlaces de `index.html` por el usuario real. Publicar los stacks como *releases* para tener contador de descargas público.
2. **Sustituir `[EMAIL_CONTACTO]`** en `index.html` por el correo real de contacto/avisos.
3. **Publicar la landing**: opción $0 → GitHub Pages en el mismo repo; opción con dominio → subcarpeta/subdominio del sitio de afiliados cuando exista.
4. **Difundir sin spam** (2–4 semanas): 2–3 piezas de contenido SEO en español («cómo montar X en Raspberry Pi»), presencia útil en comunidades hispanas (r/selfhosted, foros, grupos), enlazando a los stacks gratuitos.
5. **Medir** según el plan de `index.html` (descargas, visitas, correos de interés, señal en comunidades).
6. **Decisión con datos:** solo si se alcanza algún umbral de señal se escribe el pack completo (índice en `../indice-producto-recomendado.md`). Si no hay señal: pivotar al Concepto 2 o cambiar el ángulo, y decirlo en la landing.

## Reglas que siguen vigentes
- El pack completo SOLO se escribe si hay señal. Sin excepciones.
- $0 de gasto hasta aprobación expresa (el único gasto autorizado del objetivo es el dominio ~$12/año).
- Nada publicado ni desplegado sin el OK correspondiente donde aplique (repo GitHub a su nombre si quiere, o el que se decida).
- Sin testimonios ni cifras de ventas inventadas: los umbrales de la landing son criterios propuestos, no resultados.
- Todo en español; sin datos personales  en ningún fichero.

## Verificación hecha (17-sep-2026)
- Versiones de imagen Docker confirmadas vía web para ARM64 (sep-2026).
- Composes sin campo `version:`, sin tags `latest`, comentarios en español.
- Landing sin datos personales; placeholders `[USUARIO]` y `[EMAIL_CONTACTO]` documentados aquí.
