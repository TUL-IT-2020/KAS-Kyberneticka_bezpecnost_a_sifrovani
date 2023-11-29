---
tags:
  - slide
theme: gaia
paginate: true
marp: true
---
# Semestrální práce:
## Kontrolní součty (MD5 a jiné) a jejich použití

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
- [[Rivest-MD5_rfc1321.pdf]]
- [[Kontrolní součty a jejich výpočty v C.pdf]]
- [Hashing Algorithms and Security - Computerphile](https://www.youtube.com/watch?v=b4b8ktEV4Bg)
- [kontrolni soucet checksum - Lukas Hron](https://www.lukashron.cz/kontrolni-soucet-checksum.html)
- Obrázky: [DALL-E](https://labs.openai.com)
