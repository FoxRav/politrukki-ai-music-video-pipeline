<div align="center">

# Politrukki — Lapua Jonne!

### AI-musiikkivideoputki ideasta YouTube-julkaisuun · 9 vaihetta · 1 biisi · 24 klippiä

[![Status](https://img.shields.io/badge/status-released-39ff8a)]()
[![Stack](https://img.shields.io/badge/stack-Claude%20·%20ElevenLabs%20·%20FocalML%20·%20DaVinci-00e5ff)]()
[![AI Content](https://img.shields.io/badge/AI%20generated-disclosed-ff2bd6)]()
[![Made in](https://img.shields.io/badge/made%20in-Lapua%2C%20Finland-ffb627)]()
[![License: CC BY-NC 4.0](https://img.shields.io/badge/license-CC%20BY--NC%204.0-lightgrey)](LICENSE)
[![Live build on Kick](https://img.shields.io/badge/live%20build-kick.com%2Fpolitrukki-53fc18)](https://kick.com/politrukki)

![Pipeline Checklist](html/checklist.png)

</div>

---

## Mistä on kyse

**Lapua Jonne!** on roots reggae -biisi 17-vuotiaasta jonnesta, joka huudattaa viritettyä 80cc PV-Suzukiaan Lapuan VR-parkilla vanhan patruunatehtaan kupeessa. Sama Etelä-Pohjanmaan henki kuin 1800-luvun puukkojunkkareilla — vain kaasukahva on vaihtanut puukon paikan.

Tämä repo dokumentoi koko tuotannon: **ideasta → lyriikoista → audiosta → storyboardista → videoklipistä → editoinnista → julkaisuun**. Tavoitteena näyttää konkreettisesti miten yksi nykyaikainen AI-musiikkivideo rakennetaan alusta loppuun, mitkä työkalut toimivat mihinkin, ja mitä promptit oikeasti sisältävät.

> Yksittäinen tarina, avoin tuotantokansio.

---

## Kuuntele & katso

<div align="center">

[![Katso YouTubessa — Politrukki: Lapua Jonne!](https://img.youtube.com/vi/dnFbXpW00kM/maxresdefault.jpg)](https://www.youtube.com/watch?v=dnFbXpW00kM)

**▶ [Katso YouTubessa](https://www.youtube.com/watch?v=dnFbXpW00kM)**

</div>

| | |
| --- | --- |
| YouTube | [youtube.com/watch?v=dnFbXpW00kM](https://www.youtube.com/watch?v=dnFbXpW00kM) |
| Live-rakennus *(katso miten tämä syntyi)* | [kick.com/politrukki](https://kick.com/politrukki) |
| Lyriikat | [`02_lyriikat/lyriikat_final.md`](02_lyriikat/lyriikat_final.md) |
| YouTube-metadata (otsikko/kuvaus/tagit) | [`09_julkaisu/metadata.md`](09_julkaisu/metadata.md) |
| Live-progress-dashboard (avaa selaimessa) | [`html/checklist.html`](html/checklist.html) |

> **Live-rakennuksesta:** Koko putki vaiheista 01–07 ja 09 on rakennettu livenä [kick.com/politrukki](https://kick.com/politrukki) -kanavalla. **Poikkeus:** vaihe **08 (DaVinci Resolve)** tehdään offlinena — Resolven 4K-aikajana yhdessä OBS-streamin kanssa ei mahdu tämän koneen suorituskykybudjettiin. Editointivaihe näkyy lopputuloksessa, ei prosessina.

---

## Pipeline — 9 vaihetta

| # | Vaihe | Työkalu | Kansio |
| --- | --- | --- | --- |
| 01 | Ideointi & konsepti | Claude / Brainstorm | [`01_konsepti/`](01_konsepti/) |
| 02 | Lyriikat & rakenne | Claude | [`02_lyriikat/`](02_lyriikat/) |
| 03 | Audio & laulu | ElevenLabs Music | [`03_audio/`](03_audio/) |
| 04 | Visuaalinen käsikirjoitus | Claude / Storyboard | [`04_storyboard/`](04_storyboard/) |
| 05 | Videoklippien generointi | FocalML Seedance 2.0 | [`05_video_klipit/`](05_video_klipit/) |
| 06 | Decode & konversio | FFmpeg (DNxHR / ProRes) | [`06_decode/`](06_decode/) |
| 07 | Stem separation | Audacity · OpenVINO (Demucs v4) | [`07_stems/`](07_stems/) |
| 08 | **Editointi, mixaus, color, mastering & deliverables** — *kaikki säädöt täällä* | **DaVinci Resolve** (Edit · Fairlight · Color · Fusion · Deliver) | [`08_editointi/`](08_editointi/) |
| 09 | Julkaisu | YouTube · *Politrukki Live* | [`09_julkaisu/`](09_julkaisu/) |

Jokaisessa vaihekansiossa on oma `README.md`, jossa on tehtävälista ja ohje juuri sen vaiheen suoritukseen.

---

## Tech stack

| Rooli | Työkalu |
| --- | --- |
| Käsikirjoitus & promptit | `Claude` |
| Referenssikuvat | `ChatGPT` (image generation) |
| Musiikin generointi | `ElevenLabs Music` |
| Video (image-to-video) | `FocalML Seedance 2.0` |
| Stem-erottelu | `Audacity` + `OpenVINO` (Demucs v4) |
| Codec-konversio Resolveen | `FFmpeg` (DNxHR / ProRes) |
| **Editointi · audio-mix · color · master · deliverables** | **`DaVinci Resolve` — koko paketin kasaaja** |
| Julkaisu | `YouTube Studio` · `TikTok` · `Instagram Reels` |

---

## DaVinci Resolve — koko tuotannon kasaaja

Resolve ei ole vain editori vaan koko paketin **viimeistelijä**: kaikki AI-syötteet (24 video­klippiä, 1 master-audio, 4 stemmiä, Whisper-transkriptiot) tuodaan yhdelle aikajanalle ja säädetään sekuntilleen kohdalleen.

### Mitä Resolvessa tehdään

| Sivu (Page) | Mitä siellä säädetään |
| --- | --- |
| **Media / Cut** | Koko AI-materiaalin importti: 24 × Seedance-klippiä, ElevenLabs master-audio, 4 stem-raitaa (vocals/drums/bass/other), referenssikuvat tarvittaessa |
| **Edit** | Klippien leikkaus tahtiin (markers 85 BPM), section-rakenne (intro → 3 säettä → 3 kertosäettä → bridge → outro), siirtymät, b-rollin sijoittelu |
| **Fairlight** | Multi-stem audio-mix: vocals erilleen, drum bus, bass bus, FX-kerros; volume-automaatio per säe vs. kertosäe; sidechain-ducking puhe-VO:ille; EQ + kompressointi; LUFS-master normalisointi (-14 LUFS YouTubelle, -16 LUFS TikTokille) |
| **Color** | Per-klippi color grading: yhtenäinen teal/orange-look, sepia-poikkeus puukkojunkkari-flashbackeissa, vignette, film grain |
| **Fusion** | Tekstitykset (lyriikat), lopputekstit, logo-bumper alkuun/loppuun, motion graphics |
| **Deliver** | Render eri formaatteihin |

### Deliverables — yksi projekti, monta exportia

Resolven `Deliver`-sivulla tehdään render-jonosta useita versioita samasta master-projektista:

| Alusta | Resoluutio | Aspect | FPS | Codec | LUFS | Kesto |
| --- | --- | --- | --- | --- | --- | --- |
| **YouTube** (master) | 3840 × 2160 / 1920 × 1080 | 16:9 | 25 | H.264 / H.265 | -14 | 3:55 |
| **TikTok / Reels / Shorts** | 1080 × 1920 | 9:16 | 30 | H.264 | -16 | 0:30 – 0:60 leikkaus |
| **Instagram Feed** | 1080 × 1080 / 1080 × 1350 | 1:1 / 4:5 | 30 | H.264 | -14 | 0:60 |
| **Subtitlet** | SRT / TTML | — | — | — | — | Whisper-transkriptiosta |

### Mitä tämä tarkoittaa käytännössä

> AI generoi raaka-aineen — Resolve tekee siitä **valmiin tuotteen**. Sama master-projekti syöttää videoita kaikille alustoille, ja jokainen video on tarkalleen kyseisen alustan algoritmin haluamissa speksissä (kuvasuhde, kesto, audio-loudness).

Katso tarkemmin: [`08_editointi/README.md`](08_editointi/README.md)

---

## Mitä reposta löytyy

| Mitä | Missä |
| --- | --- |
| Biisin briefi ja referenssikuva | [`01_konsepti/referenssit/`](01_konsepti/referenssit/) |
| Lyriikat (final) | [`02_lyriikat/lyriikat_final.md`](02_lyriikat/lyriikat_final.md) |
| ElevenLabs Music composition plan (JSON) | [`02_lyriikat/composition_plan.json`](02_lyriikat/composition_plan.json) |
| ElevenLabs valmis tekstiprompti | [`02_lyriikat/elevenlabs_prompt.txt`](02_lyriikat/elevenlabs_prompt.txt) |
| Storyboard (shot list 24 klippiä) | [`04_storyboard/shot_list.md`](04_storyboard/shot_list.md) |
| Visuaalinen tyyliopas (character / location / camera) | [`04_storyboard/style_guide.md`](04_storyboard/style_guide.md) |
| GPT + Seedance promptit (12 tiedostoa, numerojärjestyksessä) | [`04_storyboard/promptit/`](04_storyboard/promptit/) |
| YouTube otsikko + kuvaus + tagit + chapters | [`09_julkaisu/metadata.md`](09_julkaisu/metadata.md) |
| Live progress-dashboard (offline HTML, localStorage) | [`html/checklist.html`](html/checklist.html) |

---

## Repo-rakenne

```
Biisi1/
├── 01_konsepti/        Brief, mood-board, referenssikuvat
├── 02_lyriikat/        Sanoitukset + ElevenLabs Music config
├── 03_audio/           Audio-master (binäärit lokaalisti)
├── 04_storyboard/      Shot list + 24 klipin GPT/Seedance promptit
├── 05_video_klipit/    Video raw + approved (binäärit lokaalisti)
├── 06_decode/          FFmpeg-skriptit DaVinciin
├── 07_stems/           Demucs-erotellut raidat (lokaalisti)
├── 08_editointi/       DaVinci Resolve -projekti — KOKO PAKETIN KASAAJA (lokaalisti)
├── 09_julkaisu/        YouTube + TikTok julkaisutekstit
└── html/               Live progress dashboard + checklist-kuva
```

Repo sisältää koko tuotantoprosessin **tekstipohjaisen ytimen** (lyriikat, promptit, käsikirjoitus, julkaisutekstit). Raskaat mediatiedostot (audio-mastersit, video-klipit, DaVinci-projekti) säilytetään paikallisesti ja niihin viitataan vain dokumentaatiossa.

---

## Käyttö

1. **Avaa [`html/checklist.html`](html/checklist.html)** selaimessa — näet livenä missä vaiheessa tuotanto on.
2. **Etene numerojärjestyksessä** vaiheesta `01_konsepti/` vaiheeseen `09_julkaisu/`.
3. **Lue vaihekansion `README.md`** ennen aloitusta — siellä on kyseisen vaiheen tehtävälista ja työkaluohje.
4. **Kopioi promptit suoraan** valmiina ChatGPT:hen, ElevenLabsiin tai FocalML Seedanceen — tiedostoissa on `copy-paste`-blokit.

---

## Lopputulos lukuina

| | |
| --- | --- |
| Biisin pituus | 3 min 55 s |
| Genre | Roots reggae · 85 BPM · D-mol |
| Lyriikat | Suomeksi, Etelä-Pohjanmaan murreviittauksin |
| Videoklippejä | 24 kpl, 7–11 s / klippi |
| GPT-referenssikuvia | 24 kpl |
| Seedance-renderöintejä | 24 kpl |
| Tuotantoaika ideasta julkaisuun | ~5 päivää |

---

## AI Disclosure

Musiikki tuotettu **ElevenLabs Music** -mallilla. Video **FocalML Seedance 2.0** -mallilla (image-to-video). Referenssikuvat **ChatGPT** -kuvageneroinnilla. Lyriikat ja käsikirjoitus käsikirjoitettu yhteistyössä **Claude**-mallin kanssa. Stems erotettu paikallisesti **OpenVINO + Demucs v4** -mallilla.

YouTube-julkaisussa video on merkitty *Altered content* -lipulla YouTuben käytäntöjen mukaisesti.

---

## Lisenssi

Tämä **järjestelmä** (repon rakenne, dokumentaatio, lyriikat-templaatit, promptit, käsikirjoitukset, skriptit, putki) on lisensoitu **[Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)](LICENSE)** -lisenssillä.

### Saat ✅

- **Käyttää** järjestelmää itse — opiskeluun, harrastukseen, omiin biiseihin
- **Muokata** ja rakentaa omat versiosi
- **Jakaa** muokattua tai muokkaamatonta versiota eteenpäin
- **Forkata** GitHubissa ja julkaista oman variaatiosi

### Et saa ❌

- **Myydä** järjestelmää tai sen osia (sellaisenaan, paketoituna, "AI-kurssina", asiakastyönä jne.)
- **Käyttää järjestelmää kaupallisesti** ilman erillistä kirjallista lupaa tekijältä

### Vaaditaan 📌

Kun jaat tai julkaiset jotain mikä perustuu tähän järjestelmään, **mainitse credits-osiossa**:

```
Built with the "Politrukki — Lapua Jonne!" AI Music Video Pipeline
by Politrukki Live · https://github.com/FoxRav/politrukki-ai-music-video-pipeline
Licensed under CC BY-NC 4.0
```

> **Käytännössä:** Forkkaa, opi, rakenna oma biisi tällä putkella, mainitse alkuperä — kaikki kunnossa. Pyydä lupa jos haluat käyttää kaupallisesti.

**Huom.** Lisenssi kattaa **järjestelmän** (rakenne, työkalut, dokumentaatio). Julkaistu **musiikkikappale, video ja kuvat** (`Lapua Jonne!` -teos kokonaisuutena) on erillinen taiteellinen teos, johon sovelletaan normaalia tekijänoikeutta — kaikki oikeudet pidätetään. Pipeline on jaettu, teos ei.

Kaupalliseen lisensointiin: ota yhteyttä tekijään.

© 2026 **Politrukki Live** · Lapua, Finland
