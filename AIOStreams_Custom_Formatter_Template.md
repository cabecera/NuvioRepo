# AIOStreams — Custom Formatter Template

Plantilla personalizada para el Formatter de AIOStreams, pensada para que cada
campo se entienda claramente (sin jerga de release-scene) y ordenada por
prioridad: Título → Idiomas → Subtítulos → Calidad → Tamaño → Video → Audio →
Seeders/Tracker → Duración → Servicio.

## Name Template

```
{stream.resolution}
```

## Description Template

```
Título: {stream.title::exists["{stream.title}"||"{stream.filename}"]}{stream.year::exists[" ({stream.year})"||""]}{stream.season::exists[" S{stream.season}"||""]}{stream.episode::exists["E{stream.episode}"||""]}
Idiomas: {stream.languages::exists["{stream.languages::join(' • ')}"||"—"]}
Subtítulos: {stream.subtitles::exists["{stream.subtitles::join(' • ')}"||"No incluye"]}
Calidad: {stream.resolution} • {stream.quality::exists["{stream.quality}"||""]}{stream.encode::exists[" {stream.encode}"||""]}
Tamaño: {stream.size::bytes}{stream.folderSize::>0[" / {stream.folderSize::bytes}"||""]}
Video: {stream.visualTags::exists["{stream.visualTags::join(' • ')}"||"Estándar (sin HDR/DV)"]}
Audio: {stream.audioTags::exists["{stream.audioTags::join(' • ')}"||"—"]}{stream.audioChannels::exists[" • {stream.audioChannels::join('/')}"||""]}
Seeders: {stream.seeders::>0["{stream.seeders}"||"—"]} | Tracker: {stream.indexer::exists["{stream.indexer}"||"—"]}
Duración: {stream.duration::>0["{stream.duration::time}"||"—"]}
Servicio: {service.name::exists["{service.name}"||"P2P (sin debrid)"]}{service.cached::istrue[" — Listo al instante ⚡"||""]}{service.cached::isfalse[" — Requiere descarga ⏳"||""]}
{stream.message::exists["Nota: {stream.message}"||""]}
```

## Ejemplo de salida (Avatar, 2009)

```
Título: Avatar (2009)
Idiomas: RUS • UKR • ENG
Subtítulos: ENG • ESP
Calidad: 2160p • BluRay REMUX
Tamaño: 85.23 GB
Video: HDR • DV
Audio: Atmos • TrueHD • 7.1
Seeders: 125 | Tracker: RARBG
Duración: 2h 42m
Servicio: TorBox — Listo al instante ⚡
```

## Ejemplo de salida (serie, sin cache)

```
Título: Breaking Bad (2008) S1E1
Idiomas: ENG
Subtítulos: No incluye
Calidad: 1080p • WEB-DL
Tamaño: 2.1 GB
Video: Estándar (sin HDR/DV)
Audio: DD • 5.1
Seeders: 40 | Tracker: DMM
Duración: 47m
Servicio: RealDebrid — Requiere descarga ⏳
```

## Notas

- `stream.season` / `stream.episode` solo aparecen si el resultado es un
  episodio de serie; en películas esa parte del título simplemente no se
  muestra.
- `service.name` y `service.cached` solo se llenan si el resultado viene
  servido por un debrid; en resultados P2P puro, la línea de Servicio cae al
  fallback `"P2P (sin debrid)"`.
- `stream.languages` puede salir vacío en algunos addons (p. ej. Comet) que
  solo parsean el nombre del archivo y no hacen sondeo real del audio — no es
  un bug de la plantilla, es una limitación de la fuente.
