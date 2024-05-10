# Kybernetická bezpečnost a šifrování

## Vyučující
Otto Severýn
CO2OO7 - Budova C druhé patro

## Semestrální práce
- [[TUL-navazující_studium/1. semestr/KAS-Kyberneticka_bezpecnost_a_sifrovani/Semestrální práce|Semestrální práce]]
	- [[KAS-Checksum_Semestrální_práce.pdf]]
- [[Prezentace]]
	- [[KAS-Checksum_prezentace.pdf]]

Do 4.12. rozpis prezentujících. 
Obhajoby 5. a 12.12. v čase cvičení E114. 10 minut na člověka 5 minut na prezentaci. 

### Zápočet
Téma ve 4. týdnu.
Vypracování a prezentace semestrální práce. Prezentace koncem semestru, 11-12 týden. 10 minut na prezentaci.

## Zkouška
Otázky:  
1,2 - kódování  
3,4 - šifrování  

Ústní část:  
Doplňující otázka + otázka na semestrální práci

Písemná část: 
1) Huffman 
	   a) vyřešit příklad 
	   b) je u toho příkladu jednoznačná délka slov? 
	   c) průměrná délka 
2) systemické systémy 
	   a) co to je 
	   b) výhody a nevýhody 
	   c) použití 
	   d) příklady 
 3) certifikáty 
    a) co to je 
    b) k čemu to je 
    c) kdo je vydává 

Stačilo to napsat poměrně vágně, samozřejmě krom příkladů.
## Přednášky
účast nepovinná

### Literatura
- Matoušek - Metody kódování, VUT 2006
- NIC.CZ - Kolouch - [[cybersecurity.pdf|Cybersecurity]], [[cybercrime.pdf|Cybercrime]]
- [[Kryptografie_okolo_nas.pdf|Burda - Kryptografie okolo nás]]
- [[bajecny_svet_elektronickeho_podpisu_cznic.pdf|Peterka - Báječný svět elektronického podpisu]]
- [[Applied Cryptography.pdf|Bruce Schneier - Applied Cryptography]]
- [[Neal_stephenson-cryptonomicon.pdf|Neal Stephenson - Cryptonomicon]] (beletrie)

## Výklad

``` mermaid
sequenceDiagram
    actor Odesilatel
    actor Příjemnce
    Odesilatel->>Příjemnce: Komunikační kanál
```

Zpráva 
- libovolná informace

Kanál 
- omezené znaky pro přenos informace
- mezená kapacita (využití kompresních kódů)
- rušení na kanálu (bezpečnostní kódy)
- Odposlech kanálu (šifry, kryptografické kódy)

Postup přípravy na odeslání zprávy
1) Zkomprimovat
2) Zašifrovat
3) Zabezpečit

### Kódování
[[Kódování]]
### Šifrování
[[Úvod do šifrování]]

[[Poznámky k bezpečnosti]]
## Cvičení

![[TUL-navazující_studium/1. semestr/KAS-Kyberneticka_bezpecnost_a_sifrovani/Příklady]]