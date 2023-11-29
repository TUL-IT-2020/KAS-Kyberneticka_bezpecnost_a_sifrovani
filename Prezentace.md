---
tags:
  - slide
theme: gaia
paginate: true
marp: true
---
# Semestrální práce:
## Kontrolní součty (MD5 a jiné) a jejich použití

Předmět: KAS - Kybernetická bezpečnost a šifrování
Datum: 29. 11. 2023
Autor: Jaroslav Körner

---
## Kontrolní součty

---
## Hash
- Královnina zpráva:
1. "Jsem těhotná, asi s kočím z Mostu. Královna"
2. "Jsem těhotná asi skočím z mostu. Královna"
- MD5 otisky:
1. `3c723007c372b83ea3e28161f174dbdf`
2. `04005f28f6f6bed78a8a316df66a07f7`

![bg right:50% 80%](assets/Queen.png)

---
## Použití:
- autenticita souborů při internetové komunikaci
- ochrana proti chybě přenosu:
	- nespolehlivým médiem (kontrolní součet)
	- úmyslné záměně souborů (otisk hashovací funkce)

- ukládání hesel (kryptografické hashovací funkce)
- asociativní vyhledávání v datech

---
## Zdroje:
- [Miroslav Němeček - Kontrolní součty a jejich výpočty v C](http://www.breatharian.eu/sw/crc/index.html)
- [Lukas Hron - kontrolni soucet checksum](https://www.lukashron.cz/kontrolni-soucet-checksum.html)
- [Computerphile: Hashing Algorithms and Security](https://www.youtube.com/watch?v=b4b8ktEV4Bg)
- [googlesource: crc32](https://fuchsia.googlesource.com/third_party/wuffs/+/HEAD/std/crc32/README.md)
- [EAN13Barcode](https://www.technoriversoft.com/EAN13Barcode.html)
- [rfc: Rivest-MD5](https://datatracker.ietf.org/doc/html/rfc1321)
- [rfc: ISBN](https://datatracker.ietf.org/doc/html/rfc3187)
- [rfc: Computing the Internet Checksum](https://datatracker.ietf.org/doc/html/rfc1071)

---
## Otázky
- [DALL-E](https://labs.openai.com)

---
## Děkuji za pozornost