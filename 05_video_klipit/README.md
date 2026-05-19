# 05 — Videoklippien generointi

**Työkalu:** FocalML

## Tehtävät
- [ ] Kaikki promptit syötetty FocalML:ään
- [ ] Klipit generoitu
- [ ] Heikot klipit regeneroitu
- [ ] Hyväksytyt klipit ladattu paikalliseen kansioon

## Alikansiot
| Kansio       | Sisältö                                                       |
|--------------|---------------------------------------------------------------|
| `raw/`       | Kaikki FocalML:stä ladatut klipit (ml. hylätyt versiot)       |
| `approved/`  | Lopullinen hyväksytty setti → menee vaiheeseen 06 (decode)    |

## Nimeämiskäytäntö
`<shot_id>_<take>.mp4`  esim. `s01_verse1_a_take03.mp4`

## Huom.
Videotiedostot ovat oletuksena `.gitignore`d.
