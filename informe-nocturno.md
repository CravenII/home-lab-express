# Informe nocturno — preparación (17-sep-2026)

Trabajo nocturno autorizado ("dale, todo lo que puedas"). **$0 gastados, nada publicado, ninguna cuenta abierta, nadie contactado.**

## Estado general

| Bloque | Estado |
|---|---|
| 1. Verificación de MP4 del catálogo de Vera | ✅ Completado — 9/9 archivos OK |
| 2. Opciones de dominio para el sitio de afiliados | ✅ Completado — 5 candidatos verificados, comparativa de precios lista |
| 3. Plan de difusión de los stacks gratuitos | ✅ Completado — plan de 4 semanas redactado |

---

## Bloque 1 — Verificación de MP4 del catálogo de Vera

**Motivo:** el episodio 13 dio error de reproducción en Facebook ("Tenemos problemas para reproducir este video"). Había que cazar cualquier otro MP4 roto ANTES de subirlo a YouTube.

**Método:** `ffprobe` (contenedor, streams, duración) + decodificación completa con `ffmpeg` a null (detecta corrupción que el simple listado no ve).

**Resultado — 9/9 OK:**

| Archivo | Duración | Video | Audio | Decodificación | Veredicto |
|---|---|---|---|---|---|
| episodio-01.mp4 | 40.0 s | h264 1080×1920 @30fps | AAC | sin errores | ✅ OK |
| episodio-02.mp4 | 41.0 s | h264 1080×1920 @30fps | AAC | sin errores | ✅ OK |
| episodio-03.mp4 | 41.0 s | h264 1080×1920 @30fps | AAC | sin errores | ✅ OK |
| episodio-04.mp4 | 41.0 s | h264 1080×1920 @30fps | AAC | sin errores | ✅ OK |
| episodio-05.mp4 | 41.0 s | h264 1080×1920 @30fps | AAC | sin errores | ✅ OK |
| episodio-06.mp4 | 40.0 s | h264 1080×1920 @30fps | AAC | sin errores | ✅ OK |
| episodio-07.mp4 | 42.0 s | h264 1080×1920 @30fps | AAC | sin errores | ✅ OK |
| episodio-11-final.mp4 | 42.0 s | h264 1080×1920 @30fps | AAC | sin errores | ✅ OK |
| episodio-12-final.mp4 | 42.0 s | h264 1080×1920 @30fps | AAC | sin errores | ✅ OK |

**Conclusión:** el error del episodio 13 fue un caso aislado — ningún otro MP4 del catálogo presenta corrupción. Los 9 archivos del calendario de subidas de YouTube (18–26 sep) son seguros para subir. Siguen vigentes las reglas: el episodio 13 NO se republica sin autorización, y los episodios 08/09/10 no tienen MP4 final y no se publican.

---

## Bloque 2 — Opciones de dominio para el sitio de afiliados

**Verificado:** 17-sep-2026. Disponibilidad comprobada en vivo vía RDAP contra el registro .com de Verisign (fuente autoritativa). Precios confirmados a nivel de TLD en fuentes oficiales/actualizadas.

### Precios base .com

| Registrador | Registro 1 año .com | Notas |
|---|---|---|
| **Porkbun** | **$11.08** | registro = renovación, sin sorpresas; incluye privacidad WHOIS, SSL, reenvío de email y DNS gratis |
| **Cloudflare Registrar** | **~$10.46** | precio al costo, sin margen; exige cuenta de Cloudflare y usar sus DNS |

⚠️ **Aviso:** Verisign sube el mayorista .com de $10.26 a **$10.97 el 1-nov-2026**. Ambos registradores reflejarán la subida. Si se decide, conviene registrar antes de noviembre.

### Candidatos (todos disponibles, todos dentro del presupuesto de ~$12/año en ambos registradores)

| Candidato | Caracteres | Porkbun 1 año | Cloudflare 1 año | Notas |
|---|---|---|---|---|
| **labencasa.com** | 9 | $11.08 | ~$10.46 | "El lab en casa": abarca TODO el sitio (Pi, NAS, WiFi, Jellyfin, Pi-hole, Nextcloud). Fácil de decir y deletrear |
| **misnube.com** | 7 | $11.08 | ~$10.46 | El más corto y brandeable; sesga un poco a nube/NAS |
| **nubeencasa.com** | 10 | $11.08 | ~$10.46 | Claro y temático (nube personal/autoalojada) |
| **datoshogar.com** | 11 | $11.08 | ~$10.46 | Bueno para ángulo NAS/almacenamiento; menos "lab/tech" |
| **servidorcasa.com** | 12 | $11.08 | ~$10.46 | Descriptivo pero el más largo y menos pegadizo |

Descartados por estar ya registrados: mihomelab.com, cacharreo.com, tecnohogar.com, hogardigital.com, trasteando.com, tecnocasa.com, miservidor.com, hogarlab.com, labhogar.com, labcasero.com. Ningún candidato usa marcas registradas.

### Recomendación

**#1 — labencasa.com**: el mejor equilibrio. Corto, 100% en español, memorable, y el único que abarca el concepto completo del sitio (no solo nube ni solo servidores). Funciona como marca y para SEO en español.

**#2 (alternativa) — misnube.com**: el más corto (7 caracteres), suena a marca. Matiz: "nube" orienta la percepción a almacenamiento, aunque como marca serviría para todo.

**Caveats:** los dominios libres pueden registrarse por terceros en cualquier momento — no demorar mucho una vez elegido. El precio exacto por dominio individual debe confirmarse en pantalla antes de pagar (son nombres inventados, no premium de diccionario, así que el precio estándar aplica casi con seguridad). **NADA comprado.**

---

## Bloque 3 — Plan de difusión de los stacks gratuitos (Home Lab Express)

**Objetivo:** publicar los 3 stacks gratuitos durante 2–4 semanas y medir interés. Umbrales de "señal" (definidos en la landing): **200+ descargas, o 25+ correos de interés, o 300+ visitas con ≥8% de clics** en "me interesa". Regla dura: el pack completo SOLO se escribe si hay señal.

### Principios

- **Transparencia total desde el primer post:** "Son 3 stacks gratuitos y libres, sin trampa. Estoy validando si hay interés real en un pack de pago (~30 stacks, $29); si no hay señal, el pack no se escribe. Los 3 stacks quedan gratis pase lo que pase."
- **Valor antes que enlace:** el cuerpo del post funciona por sí solo; el enlace es el "por si quieres el archivo listo".
- **Anti-spam:** máximo una comunidad por día, nunca el mismo texto el mismo día en dos sitios, responder a TODOS los comentarios.
- **Licencia MIT** en el repo público de GitHub (sin licencia clara, varias comunidades penalizan).

### Los 7 lugares, priorizados

1. **r/selfhosted** (inglés, prioridad 1) — la más grande y receptiva a FOSS autoalojable. Reglas: divulgar autoría ("I made this"), flair de self-promotion si existe, proporción sana de participación no promocional (~10:1), no cross-post el mismo día. Formato: text-post largo con decisiones técnicas concretas + enlace al final. NO pedir estrellas en GitHub ni publicar sin haber comentado antes en el sub.
2. **dev.to** (español, tag #spanish, prioridad 2) — artículos técnicos largos con enlaces propios si aportan valor real. Reglas: el artículo debe funcionar como tutorial completo por sí solo; nada de link farming. Formato: tutorial paso a paso del stack Pi-hole + Unbound con el compose explicado bloque por bloque.
3. **r/raspberry_pi** (inglés, prioridad 3) — audiencia exacta pero moderación estricta contra self-promotion. Enmarcarlo como proyecto/tutorial con el contenido dentro del post + capturas. NO enlazar la landing como cuerpo del post.
4. **r/homelab** (inglés, prioridad 4) — menos tolerante que r/selfhosted (regla 3: nada de publicidad de bajo esfuerzo). UN solo post presentando los 3 stacks como "mi tríada base para la Pi 5", tono de compañero de hobby. Flair `Projects`.
5. **Foros oficiales de Raspberry Pi — sección en español** (prioridad 5) — público hispano cualificado. Reglas: "be kind, be civil, don't spam"; los posts generados por IA están prohibidos (redactar con voz propia). UN hilo tutorial + participar antes en hilos existentes.
6. **Grupos de Telegram / servidores de Discord de self-hosting en español** (prioridad 6) — conversación real, poco volumen. Reglas: presentarse y participar antes; usar solo canales #showcase/#proyectos o pedir permiso al moderador; un solo mensaje por grupo en todo el periodo.
7. **Hashnode + Mastodon/Fediverso** (refuerzo, prioridad 7) — coste cero, cero riesgo de baneo. Hashnode: republicar el tutorial adaptado. Mastodon (p. ej. fosstodon.org): un hilo corto por stack con #selfhosting #raspberrypi #docker, máximo uno por semana.

### Textos propuestos

**A. dev.to / Hashnode / Foro Pi español (español) — tutorial**
Título: `Pi-hole + Unbound en Raspberry Pi 5 con Docker Compose: bloquea anuncios en toda tu red y sin depender de DNS ajenos`
Cuerpo: presentación honesta ("llevo años con una Pi 5 como servidor de casa"), tutorial completo del stack, y cierre con la frase de transparencia: los 3 stacks son gratis para siempre (MIT); el pack mayor (~30 stacks, $29) solo se escribirá si hay señal real; formulario en la landing si quieres que te avise.

**B. r/selfhosted (inglés)**
Title: `[Project] 3 production-ready Docker Compose stacks for Raspberry Pi 5 — Uptime Kuma, Homepage, Pi-hole + Unbound (free, MIT)`
Body: qué resuelve cada stack, decisiones técnicas (sin `version:`, sin tags `latest`, imágenes pineadas), enlace al repo, y el párrafo de honestidad sobre la validación del pack de pago.

**C. r/raspberry_pi (inglés)** — versión más personal y visual de B: el caso propio ("my Pi 5 runs 24/7"), 2–3 capturas del Homepage y Uptime Kuma, cierre con la misma transparencia.

**D. r/homelab (inglés)** — UN solo post, tono de colega ("reinstalé mi Pi tres veces hasta estandarizar esto"), decisiones técnicas concretas, enlace al final + transparencia. Flair `Projects`.

**E. Telegram/Discord (español, corto)** — "Soy aficionado al self-hosting. Llevo años con una Raspberry Pi 5 como servidor de casa y he publicado gratis 3 stacks Docker Compose que uso a diario... Son gratis para siempre; estoy validando si hay interés en un pack mayor de pago antes de escribirlo. Si alguien los prueba y le da guerra la instalación, respondo dudas por aquí."

**F. Mastodon (hilo corto)** — 3 stacks gratis que uso a diario en mi home lab, uno por post del hilo, cierre con repo + transparencia. Hashtags #selfhosting #raspberrypi #docker.

### Métricas y lectura de la señal

Todos los enlaces con UTM (`?utm_source=reddit_selfhosted&utm_medium=post&utm_campaign=homelabexpress`). Descargas medidas gratis con GitHub Releases: cada stack como release v1.0.0 con `.zip` descargable — el contador de descargas por asset es público, y la API `GET /repos/<usuario>/<repo>/releases` devuelve `download_count` sin autenticación. Complemento: *Insights → Traffic* del repo (visitas/clones, solo visible para el dueño).

- **Hay señal:** se cumple cualquiera de los 3 umbrales al cerrar la semana 4 (o antes si se disparan).
- **No hay señal:** a las 4 semanas ningún umbral se acerca (<50 descargas, <5 correos, <100 visitas) → se archiva el pack sin escribirlo, como promete la regla dura.
- **Zona gris** (p. ej. 120 descargas pero 3 correos): no basta para escribir 30 stacks; extender 2 semanas con un segundo tutorial o darlo por no validado. No mover el umbral a posteriori.

### Calendario semana a semana

- **Semana 0 — preparación (19–21 sep):** repo público GitHub con los 3 stacks + READMEs en español, licencia MIT, 3 releases con `.zip`; landing con formulario y enlaces UTM; crear/activar cuentas y **empezar a comentar** en r/selfhosted y r/homelab (el historial previo evita marcas de spam); probar los 3 stacks de cero en la Pi.
- **Semana 1 (22–28 sep):** lun 22 → tutorial Pi-hole + Unbound en **dev.to** (español, cero riesgo de baneo, SEO duradero); mié 24 → compartirlo en **Mastodon**; resto de la semana: participar en Reddit sin publicar nada propio; responder 1–2 hilos en el foro Pi español.
- **Semana 2 (29 sep–5 oct):** mar 30 (9–11 AM EDT) → post en **r/selfhosted** (texto B), quedarse 2–3h respondiendo; jue 2 oct → **r/raspberry_pi** (texto C) solo si el anterior fue bien recibido; vie 3 oct → hilo tutorial en el **foro Pi español**.
- **Semana 3 (6–12 oct):** mar 7 → post único en **r/homelab** (texto D); jue 9 → republicar tutorial adaptado en **Hashnode**; vie 10 → mensaje en 2–3 grupos de Telegram/Discord en español (texto E), uno por día como máximo.
- **Semana 4 (13–19 oct):** no publicar nada nuevo; responder comentarios pendientes; **dom 18 → corte de métricas** y decisión (¿algún umbral cumplido? → luz verde al pack; si no → post breve de cierre transparente en los hilos con más tracción: "no hubo señal suficiente, los 3 stacks siguen gratis").

**Salvaguardas anti-spam:** nunca dos publicaciones de lanzamiento el mismo día ni el mismo texto en dos sitios; si un post es eliminado: no republicar, leer el motivo, ajustar, esperar ≥7 días; si recibe downvotes fuertes en la primera hora (<−5 en 30 min): valorar borrarlo y no insistir en ese venue.

---

## Pendientes que requieren decisión (nada hecho sin él)

1. **Dominio:** elegir entre los candidatos (recomendado: labencasa.com) — la compra se hace con el precio exacto en pantalla.
2. **Repo GitHub:** crear el repo público con los stacks (semana 0 del plan de difusión) — requiere su cuenta.
3. **Prueba de humo:** los 3 stacks están verificados en sintaxis pero no probados en hardware real — conviene probarlos en su Pi 5 antes de publicar.
4. **YouTube:** el calendario de subidas sigue su curso (episodio 01 el 18-sep a las 7:00 PM EDT).
