# Style Guide — Lapua-Jonnet

Visuaalisen jatkuvuuden raamatto. **Jokainen GPT-prompt sisältää alla olevat anchor-stringit muuttumattomina**, jotta hahmo, paikka ja look pysyvät samana 24 klipin yli.

---

## 1. Character Anchor — JONNE (kopioitava jokaiseen GPT-promptiin)

```
A 17-year-old Finnish teenage boy, slim athletic build, average height, pale Nordic skin with faint freckles, light brown short hair partly hidden under a plain black baseball cap worn slightly sideways, oversized black hoodie with the hood pulled up over the cap, faded dark blue jeans with frayed cuffs, scuffed black low-top sneakers, sullen blank expression with eyes half-hidden in shadow, occasional black scarf pulled down around the neck.
```

**Vehkeet:**
```
He rides a tuned 80cc two-stroke moped: glossy cherry-red lacquer fuel tank with no visible logos, chrome modified longer exhaust pipe with a curved tip, knobby tires, slightly raised handlebars.
```

---

## 2. Location Anchor — VR-PARKKI / VANHA PAUKKU (kopioitava jokaiseen parkkikuvaan)

```
Location: large empty asphalt parking lot in Lapua Finland on a calm summer evening. Background features four tall pale concrete factory silos and red brick industrial buildings of the historic Vanha Paukku cartridge factory, single railway track visible at the far edge, sparse birch trees on the perimeter, tall slim street lamps with warm sodium light, faded white crosswalk lines on cracked asphalt, low concrete curbs.
```

**Lapuanjoki (bridge-osio):**
```
Location: bend of the Lapuanjoki river in late summer twilight, calm dark water reflecting the sky, low grassy banks, scattered birch and pine trees on the opposite bank, distant silhouette of old wooden barns and factory chimneys in the background.
```

---

## 3. Style Anchor (kopioitava jokaiseen GPT-promptiin)

```
Cinematic photograph, anamorphic 2.39:1 framing inside a 16:9 frame with mild letterbox, shallow depth of field, light 35mm film grain, teal and orange color grading, warm key light from low angle, soft atmospheric haze, photorealistic, no text or watermarks.
```

> Sub-bridge poikkeus (s15, sepia): vaihda style anchor muotoon `Vintage 1880s sepia archival photograph aesthetic, heavy film grain, scratched emulsion, slight motion blur, faded brown tones, 16:9 framing.`

---

## 4. Color Palette

| Aikajakso       | Pääväri      | Aksenttiväri      | Käyttö                          |
|-----------------|--------------|-------------------|---------------------------------|
| **Golden hour** | Amber/orange | Magenta horizon   | Intro, V1, V2 alku              |
| **Twilight**    | Teal/cyan    | Sodium orange     | Pre-Chorus, Chorus 1–2          |
| **Night**       | Deep navy    | Headlight white   | Bridge, V3, Pre-Chorus 3        |
| **Chaos peak**  | Hot orange   | Smoke gray        | Chorus Final                    |
| **Pre-dawn**    | Cold gray    | Pink horizon line | Outro                           |

---

## 5. Camera Language

| Section type           | Kamera                                        | Pacing              |
|------------------------|-----------------------------------------------|---------------------|
| Intro                  | Slow drone push-in                            | Long hold (11s)     |
| Verses (storytelling)  | Dolly, tracking, locked-off mids              | 8–11s clips         |
| Pre-Chorus (tension)   | Slow zoom-in, handheld breathing              | 11s clips           |
| Chorus (energy)        | Handheld, low-angle, whip pans, rapid cuts    | 4–8s clips          |
| Bridge (historical)    | Locked-off, contemplative, sepia archival cut | 11s clips           |
| Chorus Final (climax)  | Aerial + ground mix, fast cuts                | 4–9s clips          |
| Outro (resolution)     | Static wide, slow fade                        | 11s                 |

**Yleissääntö Seedancelle:** *yksi (1) kameraliike per klippi.* Älä koskaan pyydä useita liikkeitä peräkkäin.

---

## 6. Hahmon kasvojen näkyvyys

- **Verse 1 & 2:** Kasvot pidetään puolivarjossa, lippiksen alle. Identiteetti hahmottuu, mutta ei suoraa katsekontaktia ennen Verse 2:n loppua.
- **Chorus:** Kaaos, kasvoja näkyy vain välähdyksinä — keskitytään käsiin, kaasukahvaan, äänenvaimentimeen, savuun, renkaaseen.
- **Bridge:** Ensimmäistä kertaa pidempi katsekontakti — historiallinen paino.
- **Chorus Final:** Ohimennen virneitä, kasvot säilyvät anonyymeinä (mikä tahansa nuori voisi olla "jonne").
- **Outro:** Kaukainen siluetti — hahmo katoaa.

---

## 7. Toistuvat motiivit (visuaaliset koukut)

1. **Kaasukahva** kääntyy → toistuu jokaisessa kertosäkeessä
2. **Äänenvaimennin** lähikuvana, lämpöväreilyä ilmassa
3. **Vanhan Paukun piiput** taustalla (joka 3.–4. klippi vähintään)
4. **Renkaan jälki asvaltissa** — kumipalo kuviona
5. **Kuu / tähdet** Lapuanjoen yllä — vain Bridge ja Pre-Chorus 3:ssa
6. **Äidin keittiöikkuna** — Verse 3:n loppussa, hiljainen vastapooli

---

## 8. Negative constraint -lista (kopioitava jokaiseen Seedance-promptiin)

```
no morphing faces, no extra limbs, no warped license plates, no text or watermarks, no slow-motion unless specified, no abrupt cuts mid-clip, no camera shake unless specified
```

Per-clip-spesifit kiellot lisätään tämän jälkeen (esim. *"no daytime"*, *"no other people in shot"*).

---

## 9. Tekninen output

| Parametri        | Arvo                                  |
|------------------|---------------------------------------|
| Aspect ratio     | **16:9**                              |
| Resolution       | 1920×1080 (lopullinen)                |
| Klippi-pituus    | **MAX 15 s** (Seedance-raja)         |
| Frame rate       | 24 fps (cinematic) — tarkista Focal-asetuksista |
| Workflow         | GPT image → Seedance image-to-video   |
| Klippejä         | 24 kpl                                |
| Yhteiskesto      | ~235 s = 3:55                         |

---

## 10. Workflow per klippi

1. Avaa kyseisen sectionin promptit-tiedosto (esim. `promptit/chorus_1.md`)
2. Kopioi **GPT image prompt** → ChatGPT → tallenna saatu kuva nimellä `sXX_<name>.png` kansioon `05_video_klipit/raw/_refs/`
3. Avaa Focal / Seedance 2.0, lataa kuva referenssiksi (image-to-video)
4. Kopioi **Seedance prompt** → liimaa motion-kenttään
5. Aseta kesto klipin pituuden mukaan (clip-headerissä)
6. Generoi → tallenna `05_video_klipit/raw/<clip_id>_takeNN.mp4`
7. Kun hyväksytty: siirrä `05_video_klipit/approved/`

> *(Vaihe 06 → ajetaan decode-skripti DaVinci-yhteensopivaan codeciin)*
