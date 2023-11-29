# Semestrální práce
Autor: Jaroslav Körner
# Kontrolní součty (MD5 a jiné) a jejich použití.

## Kontrolní součty
Kontrolní součet z anglického: **checksum = check + sum**, které vzniklo spojením dvou slov *kontrola* a *suma*. Kontrolní součty slouží pro detekci chyby v datech. Dle webového IT slovníku, pak definice tohoto pojmu zní:

> **Checksum** (Kontrolní součet) - číslo, které slouží k kontrole integrity dat. Je vypočteno nějakým speciálním algoritmem. Kontrolní součet je přenášen společně s nějakou informací. Pokud vypočtený kontrolní součet nesouhlasí s tím přeneseným, nastala pravděpodobně při přenosu chyba.  
> - [IT slovník](https://it-slovnik.cz)
### Jak by ale takový kontrolní součet mohl vypadat? 
Pro představu můžeme uvažovat velmi jednoduchý algoritmus, který bude na data aplikovat funkci $sum() \; mod(32)$ nad 32bitovými slovy. Když chceme odeslat zprávu po nespolehlivém kanálu, tak je potřeba ověřit na straně příjemce zda obdržel správná data. Odesilatel pak bude postupovat následovně:
1) Rozdělí zprávu na $n * 32b$ úseků (poslední doplní nulami na příslušnou délku).
2) Dále začne tyto bloky postupně číst a odesílat kanálem. Zároveň je však bude sčítat "$sum()$" s akumulátorem (ten zde inicializujeme na hodnotu $0$), pokud něco přeteče přes $32bitovou$ přesnost, tak se tyto bity jednoduše zahodí "$mod(32)$".
3) Když odesilatel odešle poslední slovo zprávy, tak přichází na řadu náš akumulátor. U něj se nejdříve určí jeho **dvojkový doplněk** (inverzní prvek pro sčítání), tím se docílí že příjemce po přičtení všech přijatých slov získá $0$.
Příjemce postupně jednotlivá slova k sobě sčítá obdobně jako odesilatel, ale mohou zde nastat dvě výsledné situace:
1) V akumulátoru mu zůstane po přijetí zprávy $0$. Hurá! Zpráva je v pořádku.
2) V akumulátoru není $0$. Něco se cestou pokazilo a my žádáme o znovu zaslání zprávy.  

Takovýto algoritmus je velice triviální a praxi se nepoužívá. Vrátil by nám naprosto stejný výsledek například když by jsme proházeli jednotlivá slova zprávy, ta tak nabyde naprosto jiného významu a její kontrolní součet bude naprosto shodný.

### CRC - Cyclic Redundancy Check 

- CRC-16 (IBM, Modbus)
- CRC-32

- DNP
- CRC-8 Dallas
- CRC-16 XOR
Sum:
- CRC-8 Sum
- CRC-16 Sum
- CRC-32 Sum

## Hashovací funkce
Hashovací funkce musí splňovat do určité míry několik vlastností:
- nesmí být příliš rychlá na výpočet (ochrana proti brute-force),
- běžně v ní nenastávají kolize (dva různé vzory mají stejný obraz),
- neexistuje k ní inverzní funkce (nelze z otisku určit původní soubor).

Dále také mývají tu vlastnosti že otisky dvou "podobných" souborů (například záměna jednoho písmene ve zprávě) si vůbec podobné nejsou.

Příklad takové zprávy:
Královna posílá zpráva po vládním poslovi:
1. "Jsem těhotná, asi s kočím z Mostu. Královna"
2. "Jsem těhotná asi skočím z mostu. Královna"
MD5 otisky:
1. `3c723007c372b83ea3e28161f174dbdf`
2. `04005f28f6f6bed78a8a316df66a07f7`

Jak si můžete všimnout, stačí jen malá záměna zprávy vzniklá například tím že se královský posel přeslechne a král se dozví naprosto odlišnou informaci. Kdyby královna součástí zprávy poslovi předala i otisk MD5, nemohli by již dojít k záměně. 

Při ověření souborů zaslaných po internetu neklademe zas takový důraz na to aby výpočet hashe byl časově náročný jako tomu je například u ukládání hesel.  

### Co je to ten Hash?
Jedná se o digitální otisk souboru, který se vygeneruje kryptografickou hashovací funkcí. Mezi příklady standardních hashovacích algoritmů patří:
- MD5, 
- SHA1, 
- RMD160, 
- SHA256, 
- SHA384, 
- SHA512, 
- SHA224.

Z nich jsou nejčastěji používány algoritmy SHA-1, SHA-256 a MD5, který však je dnes považován za "deprecated" tedy zastaralý a neměl by se používat pro nic důležitého. SHA je anglická zkratka slovního spojení: Secure Hashing Algorithm, tedy bezpečný hashovací algoritmus.

Postup práce s těmito otisky pak spočívá v porovnání kontrolního součtu získaného otisknutím staženého souboru s původním kontrolním součtem od jeho tvůrce. Ukázka kontrolního součtu získaného při použití kryptografické hashovací funkce SHA-256 může vypadat následovně:

`79caae92ee6a3ef8f639b31b6b516100449502c07df722ce5a68c407129a0f6d`

Tato metodika slouží jako kontrolní mechanismus při předávání souborů k ověření zda nedošlo k poškození předávaných dat, zda nedošlo k infiltrování dat škodlivým kódem a nebo zda nedošlo k jakémukoliv zásahu do dat během procesu předávání třetí stranou.
### MD5 blíže
MD5 je akronym pro Message-Digest algorithm 5. Jedná se o rozšířený šifrovací algoritmus. Ze vstupních dat vzniká výstup označovaný jako tzv. Hash nebo "otisk MD5". Počítače mají dnes dostatečný výkon na to, že MD5 nesplňuje požadavek na to aby, nebyl příliš rychlý na výpočet. 
- duhové slovníky

## K čemu slouží hashování a kontrolní součty?

Slouží zejména k ověření autenticity souborů při internetové komunikaci. Poskytují ochrana jak proti chybě přenosu způsobené nespolehlivým médiem (kontrolní součet), tak i proti úmyslné záměně souborů (otisk hashovací funkce). 
Mezí další využití hashovacích funkcí patří ukládání hesel (kryptografické hashovací funkce), nebo například asociativní vyhledávání v datech. U vyhledávání klademe trochu jiné nároky na hashovací funkce. Například je výhodou, když data s podobnou vnitřní strukturou získají ve výsledku stejný nebo podobný hash, na čemž je pak postavené samotné vyhledávání či porovnávání souborů.
## Zdroje:
- [[Rivest-MD5_rfc1321.pdf]]
- [[Kontrolní součty a jejich výpočty v C.pdf]]
- https://it-slovnik.cz
- [Hashing Algorithms and Security - Computerphile](https://www.youtube.com/watch?v=b4b8ktEV4Bg)
- [kontrolni soucet checksum - Lukas Hron](https://www.lukashron.cz/kontrolni-soucet-checksum.html)