# 04 — Visuaalinen käsikirjoitus

**Työkalu:** Claude / Storyboard
**Output:** GPT (kuva) + FocalML Seedance 2.0 (image-to-video)

## Tehtävät
- [x] Shot list biisin rakenteen mukaan
- [x] Promptit per klippi kirjoitettu
- [x] Visuaalinen tyyli ja jatkuvuus määritelty
- [x] Käsikirjoitus lukittu tuotantoon

## Tuotokset tähän kansioon

| Tiedosto              | Sisältö                                                                                      |
|-----------------------|----------------------------------------------------------------------------------------------|
| `shot_list.md`        | Yleiskatsaus + 24 klipin taulukko timecodein                                                |
| `style_guide.md`      | **Character/location/style anchor -stringit** + paletti + kamera-kielioppi + workflow       |
| `promptit/*.md`       | 12 tiedostoa, **per section** — sisältää valmiit GPT- ja Seedance-promptit jokaiselle klipille |

## Promptit-kansion sisältö (numerojärjestyksessä, toistojärjestyksessä)

| #  | Tiedosto                | Klippejä | Aika           |
|----|-------------------------|----------|----------------|
| 00 | `00_intro.md`           | 1        | 0:00 – 0:11    |
| 01 | `01_verse_1.md`         | 2        | 0:11 – 0:33    |
| 02 | `02_pre_chorus_1.md`    | 1        | 0:33 – 0:44    |
| 03 | `03_chorus_1.md`        | 3        | 0:44 – 1:07    |
| 04 | `04_verse_2.md`         | 2        | 1:07 – 1:29    |
| 05 | `05_pre_chorus_2.md`    | 1        | 1:29 – 1:40    |
| 06 | `06_chorus_2.md`        | 3        | 1:40 – 2:03    |
| 07 | `07_bridge.md`          | 2        | 2:03 – 2:25 (sis. sepia-archival -poikkeus) |
| 08 | `08_verse_3.md`         | 2        | 2:25 – 2:48    |
| 09 | `09_pre_chorus_3.md`    | 1        | 2:48 – 2:59    |
| 10 | `10_chorus_final.md`    | 5        | 2:59 – 3:44 (climax) |
| 11 | `11_outro.md`           | 1        | 3:44 – 3:55    |

**Yhteensä:** 24 klippiä · 235 s (3:55) · max 15 s/klippi (Seedance-raja)

## Workflow

1. Lue `style_guide.md` (kerran)
2. Avaa sectionin promptit-tiedosto (esim. `promptit/03_chorus_1.md`)
3. **Kopioi "GPT image prompt"** → ChatGPT (image generation) → tallenna kuva `05_video_klipit/raw/_refs/sXX_<name>.png`
4. Avaa Focal / Seedance 2.0, lataa kuva referenssiksi
5. **Kopioi "Seedance 2.0 prompt"** → liimaa motion-kenttään
6. Aseta kesto klipin headerin mukaan (7–11 s)
7. Generoi → tallenna `05_video_klipit/raw/sXX_<name>_takeNN.mp4`
8. Hyväksytyt klipit → `05_video_klipit/approved/`

> **Huom:** Konvention "yksi tiedosto per klippi" sijaan käytetään "yksi tiedosto per section" — pienempi tiedostomäärä, mutta jokainen klippi silti omana copy-paste -lohkonaan.
