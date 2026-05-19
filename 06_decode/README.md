# 06 — Decode & konversio

**Työkalu:** Oma repo / FFmpeg

## Tehtävät
- [ ] Decode-skripti ajettu (DaVinci-yhteensopiva codec)
- [ ] Tiedostonimet ja kansiorakenne järjestetty
- [ ] Klipit verifioitu DaVinci-importtiin

## Alikansiot
| Kansio           | Sisältö                                                 |
|------------------|---------------------------------------------------------|
| `scripts/`       | FFmpeg / Python -skriptit konversioon (committoidaan)   |
| `davinci_ready/` | Konvertoidut klipit (DNxHR / ProRes) DaVinci-importtiin |

## Tyypillinen FFmpeg-komento (DNxHR HQ, 1080p)
```bash
ffmpeg -i input.mp4 -c:v dnxhd -profile:v dnxhr_hq -pix_fmt yuv422p \
       -c:a pcm_s16le output.mov
```

Tallenna toimivat versiot `scripts/`-kansioon (esim. `decode_dnxhr.ps1`, `decode_prores.sh`).
