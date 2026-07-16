# Guía de Instalación — Stremio / Nuvio

Instrucciones paso a paso para dejar el setup completo desde cero. El orden
importa: instala primero la app, después metadatos, luego fuentes de
streams, y al final las cosas "extra" (subtítulos, badges, sync).

Los campos que dicen `[tu API key aquí]` o `[tu login]` los completas tú con
tus propios datos — no se guardan en este documento.

---

## 1. Instalar la app

Elige una o ambas:

- **Stremio** (PC/móvil/TV) — https://www.stremio.com/
- **Nuvio** (alternativa con más opciones de personalización) — https://nuvio.tv/

Crea una cuenta con tu correo. Usa la **misma cuenta** en ambas si vas a usar
las dos, para que compartan biblioteca/perfil vía Trakt más adelante (ver
paso 7).

---

## 2. (Opcional) Auto-configuración rápida

Si no quieres configurar addon por addon manualmente, hay wizards que arman
todo de una vez:

- Auto-setup de Nuvio: https://latinokodi.site/nuvio-autosetup/
  - Entrega catalogo, addon de torrentio y pluggins   
- Wizard genérico Stremio/Nuvio: https://numb3rs.stream/wizard/
- Despues para catálogo: https://xperience-app.com/

Si usas uno de estos, puedes saltarte los pasos 3-5 y pasar directo al 6.

---

## 3. Addon de metadatos (instalar PRIMERO, antes que los de streams)

Los addons de metadatos le dan a Stremio/Nuvio la info de películas/series
(posters, sinopsis, calificaciones). Otros addons y colecciones dependen de
que esto ya esté instalado.

- **AIOMetadata** — configurar en https://aiometadata.elfhosted.com/configure/
  - Guía en video (instalación completa): https://www.youtube.com/watch?v=bDgtJMQ8be8
  - Necesitarás tus propias API keys de (opcional, mejora resultados):
    - MDBLIST (regístrate en mdblist.com para obtener la tuya)
    - TMDB (developer.themoviedb.org)
    - TheTVDB (thetvdb.com/api-information)
    - Fanart.tv (fanart.tv/get-an-api-key)
  - Al terminar te da una URL de manifest única — instálala en Stremio/Nuvio

---

## 4. Addons de streams (fuentes de contenido)

Instala en este orden — generales primero, luego los específicos de Latino:

### Generales
- **Torrentio** (configurable con filtro de idioma/calidad):
  https://torrentio.strem.fun/configure
- **Pengu** — https://pengu.uk/
- **Anime** — https://pigamer37.alwaysdata.net/configure

### Específicos Latino/LATAM
- LatinoKodi - Latinuvio V2:
  `https://raw.githubusercontent.com/latinokodi/latinuvio-V2/main/manifest.json`
- LatinoKodi - Nuvio Custom Latino Providers:
  `https://raw.githubusercontent.com/latinokodi/nuvio-custom-latino-providers/main/manifest.json`
- Nuvio Providers Latino (KennethJYS):
  `https://raw.githubusercontent.com/KennethJYS/Nuvio-Providers-Latino/refs/heads/main/manifest.json`
- Plugin Latino (Adrianjael):
  `https://raw.githubusercontent.com/adrianjael/pluggin-latino/refs/heads/main/manifest.json`
- Plugin Anime
  `https://pigamer37.alwaysdata.net/configure`

### Aggregador con debrid (recomendado si vas a usar TorBox/RealDebrid)
- **AIOStreams** (Stremio, con catálogo) — genera tu propia instancia en el
  sitio de tu hoster preferido; guarda la URL de manifest generada, no la
  compartas (funciona como llave de acceso a tu configuración)
- **AIOStreams** (Nuvio, sin catálogo) — misma idea, instancia separada
- **Meteor** — hoster de catálogo alternativo, mismo patrón que AIOStreams

---

## 5. Servicio Debrid (para streaming instantáneo)

- **TorBox** — https://torbox.app/dashboard (de pago, revisa planes en el sitio)
  - CDN Selection: déjalo en "Auto" salvo que tengas problemas de velocidad
- Conecta tu cuenta de TorBox dentro de AIOStreams (paso 4) y dentro de
  Nuvio (Settings → Integrations → Connected Services)

### Addon debrid adicional
- **HDHub** — configurable con tu propia key de TorBox y calidades
  preferidas desde su página de configuración

---

## 6. Subtítulos

- **Subsense** — configurar en https://subsense.nepiraw.com/configure
  - Al terminar te da un link de manifest único para instalar
  - Mejora resultados con tus propias API keys (opcionales):
    - SubSource (subsource.net → developer/API)
    - SubDL (subdl.com → API)
    - Wyzie Subs

---

## 7. Sincronización (Trakt) — hazlo con UNA sola cuenta

**Importante:** usa la misma cuenta de Trakt en todos los servicios de abajo.
Si tienes más de una cuenta de Trakt guardada en el navegador, cierra sesión
de las demás antes de continuar, para evitar conflictos de sincronización.

1. Crea/inicia sesión en Trakt: https://app.trakt.tv/
2. Conecta Trakt dentro de Nuvio: Settings → Integrations → Trakt
3. Conecta Trakt dentro de Stremio: Settings → Trakt Scrobbling → Authenticate
4. (Opcional, si el sync oficial falla) usa un addon community de sync tipo
   MyTrakt Sync — genera tu propia instancia con tu cuenta de Trakt, instala
   el addon resultante, guarda la URL de tu instancia en privado

---

## 8. Colecciones / Catálogos (opcional, cosmético)

- Streaming Catalogs (estilo Netflix) — colección community, instalar desde
  Beamup con tu propia configuración
- Ultimate Horror Collection: https://nuvio.tv/community-collections/ultimate-horror-collection
- Production Studios: https://nuvio.tv/community-collections/production-studios-2

---

## 9. Badges (decorar los resultados de streams)

- Crear tu propio set de badges: https://nintle.github.io/Badger/
- Fuentes/presets ya armados: https://latinokodi.site/badges3/
- Pegar la URL resultante en: Nuvio → Settings → Integrations → Connected

<img width="1722" height="247" alt="image" src="https://github.com/user-attachments/assets/43902326-2f00-45d2-932c-bb136bdb50b2" />


### Posters con rating (opcional)
- RatingPosterDB — regístrate en ratingposterdb.com para tu propia API key
- OMDB — regístrate en omdbapi.com para tu propia API key

---

## 10. Extras / mantenimiento

- **Ordenar addons de Stremio** (reordenar prioridad visualmente):
  https://stremio-addon-manager.vercel.app/
- **M3U / TV en vivo** — addon genérico donde pegas tu propia URL de lista
  M3U (ej. una pública como iptv-org) y opcionalmente un EPG
  https://stiptv.ddns.me/eyJwcm92aWRlciI6ImRpcmVjdCIsIm0zdVVybCI6Imh0dHBzOi8vaXB0di1vcmcuZ2l0aHViLmlvL2lwdHYvaW5kZXgubTN1IiwiZW5hYmxlRXBnIjpmYWxzZSwicHJlc2NhbiI6eyJlbnRyaWVzIjoxMDg2MiwiYXBwcm94VHYiOjEwNzUxLCJhcHByb3hNb3ZpZXMiOjExMSwiZXBnUHJvZ3JhbW1lcyI6MCwiZXBnQ2hhbm5lbHMiOjB9LCJpbnN0YW5jZUlkIjoiOGFmZDM0NTQtNjYyOS00YmE3LWE3ZWMtMDc3ZWY3OWUzNTBjIn0/configure
  
- **CloudStream** (alternativa Android nativa, no depende de Stremio):
  - Guía: https://www.youtube.com/watch?v=bplbtMECbMg
  - Repositorios: https://cloudstreamrepo.com/
- **Anime directo (sitios web, no addon)**:
  - itachi.tv
  - streamxtv (anime)

---

