# 02 — Lyriikat & Rakenne

**Työkalu:** Claude (lyriikat) + ElevenLabs Music -konvention mukainen rakenne

## Tehtävät
- [x] Biisin rakenne (intro / verse / chorus / bridge / outro)
- [x] Säkeistöjen lyriikat kirjoitettu
- [x] Kertosäkeen koukku viilattu
- [x] Lopullinen lyriikkaversio hyväksytty

## Tuotokset tähän kansioon
- `lyriikat_final.md` — lukittu, laulettava versio (max 200 ch/rivi, ei stage directioneita)
- `composition_plan.json` — ElevenLabs Music API:n composition plan: global + per-section style-tagit englanniksi, lyriikat suomeksi
- `luonnokset/` — historiaversiot (v1, v2, …) tuotantomuistiinpanoineen

## ElevenLabs-konventio (tärkeä!)

**Music-malli** ei käytä inline `[emotion]`-tageja lyriikoissa. Virallinen sääntö:

> *"The `lines` field must contain only singable or speakable content.
> Performance directions, vocal styles, and stage directions go in
> `positive_local_styles`, not in lyrics."*
> — [ElevenLabs Music · Composition Plans](https://elevenlabs.io/docs/eleven-api/guides/how-to/music/composition-plans)

| Mihin tag menee?               | Music (meidän)            | v3 TTS (ei käytössä) |
|--------------------------------|---------------------------|----------------------|
| Emootio / tyyli / instrumentti | `composition_plan.json`   | `[bracket]` tekstissä|
| Laulettava sisältö             | `lyriikat_final.md`       | sama tekstirivi      |
| Foneettiset äänet (ulvonta)    | lyriikoihin OK            | `[whispers]` ym.     |
| Kieli                          | lyriikat fi · tagit en    | molemmat samaa kieltä|

**Lisärajat (Music API):**
- max 30 sectionia / biisi
- max 30 riviä / section
- max 200 merkkiä / rivi
- section duration 3–120 s, total 3 s – 10 min
- style-tagit englanniksi, lyriikat millä tahansa kielellä

## Mitä menee seuraavaan vaiheeseen (03_audio)

1. Avaa ElevenLabs Music API tai Studio-UI
2. Syötä `composition_plan.json` Composition Plan -kenttään (tai POST `/v1/music/compose`)
3. Voice: katso `composition_plan.json` → global styles ("male Finnish vocalist, rough textured…")
4. Render → tallenna master `03_audio/master/`-kansioon
