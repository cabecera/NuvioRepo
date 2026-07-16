# AIOStreams — 10 Variantes de Formatter

Mismo contenido y orden en todas (Título → Idiomas → Subtítulos → Calidad →
Tamaño → Video → Audio → Seeders/Tracker → Duración → Servicio), solo cambia
el estilo visual. Cada plantilla incluye cómo se vería con el ejemplo de
**Avatar (2009)**.

---

## 1. Etiquetas claras (la más legible, sin ambigüedad)

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
```

**Se ve así:**
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

---

## 2. Emoji temático

```
🎬 {stream.title::exists["{stream.title}"||"{stream.filename}"]}{stream.year::exists[" ({stream.year})"||""]}
🌎 {stream.languages::exists["{stream.languages::join(' • ')}"||"—"]}
💬 {stream.subtitles::exists["{stream.subtitles::join(' • ')}"||"No incluye"]}
📀 {stream.resolution} • {stream.quality::exists["{stream.quality}"||""]}{stream.encode::exists[" {stream.encode}"||""]}
📦 {stream.size::bytes}
🎨 {stream.visualTags::exists["{stream.visualTags::join(' • ')}"||"Estándar"]}
🔊 {stream.audioTags::exists["{stream.audioTags::join(' • ')}"||"—"]}{stream.audioChannels::exists[" • {stream.audioChannels::join('/')}"||""]}
👥 {stream.seeders::>0["{stream.seeders}"||"—"]} · 🔍 {stream.indexer::exists["{stream.indexer}"||"—"]}
⏱️ {stream.duration::>0["{stream.duration::time}"||"—"]}
🛰️ {service.name::exists["{service.name}"||"P2P"]}{service.cached::istrue[" ⚡"||""]}{service.cached::isfalse[" ⏳"||""]}
```

**Se ve así:**
```
🎬 Avatar (2009)
🌎 RUS • UKR • ENG
💬 ENG • ESP
📀 2160p • BluRay REMUX
📦 85.23 GB
🎨 HDR • DV
🔊 Atmos • TrueHD • 7.1
👥 125 · 🔍 RARBG
⏱️ 2h 42m
🛰️ TorBox ⚡
```

---

## 3. Minimalista con guiones

```
─ {stream.title::exists["{stream.title}"||"{stream.filename}"]}{stream.year::exists[" ({stream.year})"||""]}
─ {stream.languages::exists["{stream.languages::join(' • ')}"||"—"]}
─ {stream.subtitles::exists["{stream.subtitles::join(' • ')}"||"No incluye"]}
─ {stream.resolution} • {stream.quality::exists["{stream.quality}"||""]}
─ {stream.size::bytes}
─ {stream.visualTags::exists["{stream.visualTags::join(' • ')}"||"Estándar"]}
─ {stream.audioTags::exists["{stream.audioTags::join(' • ')}"||"—"]}{stream.audioChannels::exists[" • {stream.audioChannels::join('/')}"||""]}
─ {stream.seeders::>0["{stream.seeders}"||"—"]} / {stream.indexer::exists["{stream.indexer}"||"—"]}
─ {stream.duration::>0["{stream.duration::time}"||"—"]}
─ {service.name::exists["{service.name}"||"P2P"]}{service.cached::istrue[" ⚡"||""]}{service.cached::isfalse[" ⏳"||""]}
```

**Se ve así:**
```
─ Avatar (2009)
─ RUS • UKR • ENG
─ ENG • ESP
─ 2160p • BluRay REMUX
─ 85.23 GB
─ HDR • DV
─ Atmos • TrueHD • 7.1
─ 125 / RARBG
─ 2h 42m
─ TorBox ⚡
```

---

## 4. Compacto en 3 líneas

*(Versión original descartada por quedar demasiado apretada y difícil de leer
de un vistazo — la reemplazo por una de 4 líneas más ordenada, agrupando por
tema en vez de meter todo junto.)*

```
🎬 {stream.title::exists["{stream.title}"||"{stream.filename}"]}{stream.year::exists[" ({stream.year})"||""]}  •  🌎 {stream.languages::exists["{stream.languages::join('/')}"||"—"]}  •  💬 {stream.subtitles::exists["{stream.subtitles::join('/')}"||"No"]}
📀 {stream.resolution} {stream.quality::exists["{stream.quality}"||""]}  •  📦 {stream.size::bytes}
🎨 {stream.visualTags::exists["{stream.visualTags::join(' ')}"||"SDR"]}  •  🔊 {stream.audioTags::exists["{stream.audioTags::join(' ')}"||"—"]}{stream.audioChannels::exists[" {stream.audioChannels::join('/')}"||""]}
👥 {stream.seeders::>0["{stream.seeders}"||"—"]}  •  ⏱️ {stream.duration::>0["{stream.duration::time}"||"—"]}  •  {service.name::exists["{service.name}"||"P2P"]}{service.cached::istrue[" ⚡"||""]}
```

**Se ve así:**
```
🎬 Avatar (2009)  •  🌎 RUS/UKR/ENG  •  💬 ENG/ESP
📀 2160p BluRay REMUX  •  📦 85.23 GB
🎨 HDR DV  •  🔊 Atmos TrueHD 7.1
👥 125  •  ⏱️ 2h 42m  •  TorBox ⚡
```

---

## 5. Estilo "terminal/log"

```
[TÍTULO] {stream.title::exists["{stream.title}"||"{stream.filename}"]}{stream.year::exists[" ({stream.year})"||""]}
[IDIOMA] {stream.languages::exists["{stream.languages::join(' • ')}"||"—"]}
[SUBS]   {stream.subtitles::exists["{stream.subtitles::join(' • ')}"||"No incluye"]}
[CALID]  {stream.resolution} • {stream.quality::exists["{stream.quality}"||""]}
[PESO]   {stream.size::bytes}
[VIDEO]  {stream.visualTags::exists["{stream.visualTags::join(' • ')}"||"Estándar"]}
[AUDIO]  {stream.audioTags::exists["{stream.audioTags::join(' • ')}"||"—"]}{stream.audioChannels::exists[" • {stream.audioChannels::join('/')}"||""]}
[SEEDS]  {stream.seeders::>0["{stream.seeders}"||"—"]} @ {stream.indexer::exists["{stream.indexer}"||"—"]}
[TIEMPO] {stream.duration::>0["{stream.duration::time}"||"—"]}
[FUENTE] {service.name::exists["{service.name}"||"P2P"]}{service.cached::istrue[" [READY]"||""]}{service.cached::isfalse[" [WAIT]"||""]}
```

**Se ve así:**
```
[TÍTULO] Avatar (2009)
[IDIOMA] RUS • UKR • ENG
[SUBS]   ENG • ESP
[CALID]  2160p • BluRay REMUX
[PESO]   85.23 GB
[VIDEO]  HDR • DV
[AUDIO]  Atmos • TrueHD • 7.1
[SEEDS]  125 @ RARBG
[TIEMPO] 2h 42m
[FUENTE] TorBox [READY]
```

---

## 6. Iconos geométricos por categoría

```
◆ {stream.title::exists["{stream.title}"||"{stream.filename}"]}{stream.year::exists[" ({stream.year})"||""]}
◇ {stream.languages::exists["{stream.languages::join(' • ')}"||"—"]}
◇ {stream.subtitles::exists["{stream.subtitles::join(' • ')}"||"No incluye"]}
▲ {stream.resolution} • {stream.quality::exists["{stream.quality}"||""]}
▲ {stream.size::bytes}
△ {stream.visualTags::exists["{stream.visualTags::join(' • ')}"||"Estándar"]}
△ {stream.audioTags::exists["{stream.audioTags::join(' • ')}"||"—"]}{stream.audioChannels::exists[" • {stream.audioChannels::join('/')}"||""]}
■ {stream.seeders::>0["{stream.seeders}"||"—"]} · {stream.indexer::exists["{stream.indexer}"||"—"]}
□ {stream.duration::>0["{stream.duration::time}"||"—"]}
● {service.name::exists["{service.name}"||"P2P"]}{service.cached::istrue[" ⚡"||""]}
```

**Se ve así:**
```
◆ Avatar (2009)
◇ RUS • UKR • ENG
◇ ENG • ESP
▲ 2160p • BluRay REMUX
▲ 85.23 GB
△ HDR • DV
△ Atmos • TrueHD • 7.1
■ 125 · RARBG
□ 2h 42m
● TorBox ⚡
```

---

## 7. Con separadores visuales entre bloques

```
🎬 {stream.title::exists["{stream.title}"||"{stream.filename}"]}{stream.year::exists[" ({stream.year})"||""]}
━━━━━━━━━━━━━━━
🌎 {stream.languages::exists["{stream.languages::join(' • ')}"||"—"]}  |  💬 {stream.subtitles::exists["{stream.subtitles::join(' • ')}"||"No"]}
📀 {stream.resolution} {stream.quality::exists["{stream.quality}"||""]}  |  📦 {stream.size::bytes}
🎨 {stream.visualTags::exists["{stream.visualTags::join(' • ')}"||"SDR"]}  |  🔊 {stream.audioTags::exists["{stream.audioTags::join(' • ')}"||"—"]}{stream.audioChannels::exists[" {stream.audioChannels::join('/')}"||""]}
━━━━━━━━━━━━━━━
👥 {stream.seeders::>0["{stream.seeders}"||"—"]}  ⏱ {stream.duration::>0["{stream.duration::time}"||"—"]}  🛰 {service.name::exists["{service.name}"||"P2P"]}{service.cached::istrue[" ⚡"||""]}
```

**Se ve así:**
```
🎬 Avatar (2009)
━━━━━━━━━━━━━━━
🌎 RUS • UKR • ENG  |  💬 ENG • ESP
📀 2160p BluRay REMUX  |  📦 85.23 GB
🎨 HDR • DV  |  🔊 Atmos • TrueHD 7.1
━━━━━━━━━━━━━━━
👥 125  ⏱ 2h 42m  🛰 TorBox ⚡
```

---

## 8. Ficha técnica numerada

```
1. Título: {stream.title::exists["{stream.title}"||"{stream.filename}"]}{stream.year::exists[" ({stream.year})"||""]}
2. Idiomas: {stream.languages::exists["{stream.languages::join(' • ')}"||"—"]}
3. Subtítulos: {stream.subtitles::exists["{stream.subtitles::join(' • ')}"||"No incluye"]}
4. Calidad: {stream.resolution} • {stream.quality::exists["{stream.quality}"||""]}
5. Tamaño: {stream.size::bytes}
6. Video: {stream.visualTags::exists["{stream.visualTags::join(' • ')}"||"Estándar"]}
7. Audio: {stream.audioTags::exists["{stream.audioTags::join(' • ')}"||"—"]}{stream.audioChannels::exists[" • {stream.audioChannels::join('/')}"||""]}
8. Seeders: {stream.seeders::>0["{stream.seeders}"||"—"]} ({stream.indexer::exists["{stream.indexer}"||"—"]})
9. Duración: {stream.duration::>0["{stream.duration::time}"||"—"]}
10. Servicio: {service.name::exists["{service.name}"||"P2P"]}{service.cached::istrue[" ⚡"||""]}{service.cached::isfalse[" ⏳"||""]}
```

**Se ve así:**
```
1. Título: Avatar (2009)
2. Idiomas: RUS • UKR • ENG
3. Subtítulos: ENG • ESP
4. Calidad: 2160p • BluRay REMUX
5. Tamaño: 85.23 GB
6. Video: HDR • DV
7. Audio: Atmos • TrueHD • 7.1
8. Seeders: 125 (RARBG)
9. Duración: 2h 42m
10. Servicio: TorBox ⚡
```

---

## 9. Iconos minimalistas de línea fina

```
▸ {stream.title::exists["{stream.title}"||"{stream.filename}"]}{stream.year::exists[" ({stream.year})"||""]}
▹ {stream.languages::exists["{stream.languages::join(' • ')}"||"—"]}
▹ {stream.subtitles::exists["{stream.subtitles::join(' • ')}"||"No incluye"]}
▸ {stream.resolution} • {stream.quality::exists["{stream.quality}"||""]}
▹ {stream.size::bytes}
▹ {stream.visualTags::exists["{stream.visualTags::join(' • ')}"||"Estándar"]}
▹ {stream.audioTags::exists["{stream.audioTags::join(' • ')}"||"—"]}{stream.audioChannels::exists[" • {stream.audioChannels::join('/')}"||""]}
▸ {stream.seeders::>0["{stream.seeders}"||"—"]} · {stream.indexer::exists["{stream.indexer}"||"—"]}
▹ {stream.duration::>0["{stream.duration::time}"||"—"]}
▸ {service.name::exists["{service.name}"||"P2P"]}{service.cached::istrue[" ⚡"||""]}
```

**Se ve así:**
```
▸ Avatar (2009)
▹ RUS • UKR • ENG
▹ ENG • ESP
▸ 2160p • BluRay REMUX
▹ 85.23 GB
▹ HDR • DV
▹ Atmos • TrueHD • 7.1
▸ 125 · RARBG
▹ 2h 42m
▸ TorBox ⚡
```

---

## 10. Formato "ficha" con barra lateral

*(La versión original con `|` al inicio de cada línea se veía como una tabla
rota sin serlo — la cambio por una barra lateral `▐` que da la misma idea de
"ficha" pero se ve intencional, no como un error de formato.)*

```
▐ {stream.title::exists["{stream.title}"||"{stream.filename}"]}{stream.year::exists[" ({stream.year})"||""]}
▐ Idioma: {stream.languages::exists["{stream.languages::join(' • ')}"||"—"]} • Subs: {stream.subtitles::exists["{stream.subtitles::join(' • ')}"||"No"]}
▐ Calidad: {stream.resolution} {stream.quality::exists["{stream.quality}"||""]} • {stream.size::bytes}
▐ Video: {stream.visualTags::exists["{stream.visualTags::join(' • ')}"||"SDR"]} • Audio: {stream.audioTags::exists["{stream.audioTags::join(' • ')}"||"—"]}{stream.audioChannels::exists[" {stream.audioChannels::join('/')}"||""]}
▐ {stream.seeders::>0["{stream.seeders} seeders"||"—"]} • {stream.duration::>0["{stream.duration::time}"||"—"]} • {service.name::exists["{service.name}"||"P2P"]}{service.cached::istrue[" ⚡"||""]}
```

**Se ve así:**
```
▐ Avatar (2009)
▐ Idioma: RUS • UKR • ENG • Subs: ENG • ESP
▐ Calidad: 2160p BluRay REMUX • 85.23 GB
▐ Video: HDR • DV • Audio: Atmos • TrueHD • 7.1
▐ 125 seeders • 2h 42m • TorBox ⚡
```

---

## Resumen rápido — ¿cuál elegir?

| # | Estilo | Mejor para... |
|---|--------|----------------|
| 1 | Etiquetas claras | Máxima legibilidad, cero ambigüedad |
| 2 | Emoji temático | Balance entre visual y claro |
| 3 | Guiones minimalistas | Look limpio sin sobrecargar |
| 4 | Compacto 4 líneas | Pantallas chicas / listas largas |
| 5 | Terminal/log | Estética "técnica" |
| 6 | Geométrico | Distinguir categorías sin texto |
| 7 | Con separadores | Resaltar el título del resto |
| 8 | Numerado | Referencia tipo checklist |
| 9 | Línea fina | Minimalista pero con jerarquía visual |
| 10 | Barra lateral | Look de "ficha" sin usar tabla real |
