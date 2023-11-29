# Kybernetická bezpečnost a šifrování

## Vyučující
Otto Severýn
CO2OO7 - Budova C druhé patro

## Semestrální práce
[[TUL-navazující_studium/1. semestr/KAS-Kyberneticka_bezpecnost_a_sifrovani/Semestrální práce|Semestrální práce]]

Do 4.12. rozpis prezentujících. 
Obhajoby 5. a 12.12. v čase cvičení E114. 10 minut na člověka 5 minut na prezentaci. 

### Zápočet
Téma ve 4. týdnu.
Vypracování a prezentace semestrální práce. Prezentace koncem semestru, 11-12 týden. 10 minut na prezentaci.

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
Výklad významu jedniček a nul.
#### Kódování jednoho znaku:
Zobrazení $K : A \to B^*$
- $A$ - zdrojová abeceda, př: $A = \{a,b,...,z\}$ 
- $B$ - kódová abeceda, př: $B = \{0,1\}$
- $^*$ - iterace množiny, př: $B^* = \{ \varnothing,0,1,00,01,10,11,...\}$
Kódová slova: Prvky z $B^*$, kterým je přiřazeno nějaké $a \in A$.
$b = K(a)$

#### Kódování zprávy:
Zpráva: $M = a_1, a_2, a_3, ..., a_n \; a \in A$
Zakódovaná zpráva: $K(M) = K(a_1), K(a_2), K(a_3), ..., K(a_n)$

Příklad:
$A = \{a,b,c\}$
$B = \{0,1\}$

|     | $K_1$ | $K_2$ | $K_3$ | $K_4$ | $K_5$ |
| --- | ----- | ----- | ----- | ----- | ----- |
| a   | 0     | 0     | 00    | 01    | 0     |
| b   | 0     | 1     | 01    | 001   | 10    |
| c   | 1     | 01    | 10    | 0001  | 110   |
| d   | 11    | 11    | 11    | 00001 | 111   |

- $K_1$ - Singulární kód - není prostý
- $K_2$ - není jednoznačně dekódovatelný
- $K_3$ - blokový, stejně dlouhá bloková slova
- $K_4$ - různě dlouhá bloková slova, (jedničky slouží jako oddělovače)

$K_3,K_4,K_5$ - jsou instantní kódy (okamžité), lze je dekódovat jak postupně kódy přichází.

#### Instantní kódy
![[Instantní kódy]]
#### Bezztrátová komprese dat
![[Bezztrátová komprese dat]]
### Šifrování
![[Úvod do šifrování]]
## Cvičení

