# Bezpečnostní kódy

Chyby přenosu po komunikačním kanále. 

Detekce (oprava) chyby při přenosu informace. 

``` mermaid
flowchart LR
	Z["Zdroj in formace"] 
	V["Vysílání"] 
	p["přijímac"]
	P["Přijemce"] 
	Š["Zdroj šumu"]
	
	
	Z ---> V
	V -- komunikační kanál --> p
	p ---> P
	Š ---> p	
```

Nezávislé chyby - bílý šum

``` mermaid
flowchart LR
	subgraph Vstup
		I
		O
	end
	subgraph Výstup
		i
		o
	end
	O -- "(1-p)" --> o
	O -- p --> i
	I -- "(1-p)" --> i
	I -- p --> o
``` 
$p = \frac{1}{2}$

Reálně p cca $10^{-5}$ a méně

Pdp chyby na 1 bitu P
Délka zprávy ... n bitů
Pdp zprávy bez chyby = $(1-p)^n$

$(1 - \frac{1}{n})^n -> \frac{1}{e}$

## Parita
Ke každé n-tici bitů zprávy přidá bit tak, aby výsledný počet 1 (nebo 0) ve slově o n+1 bitech byl sudý (lichý).

Odesilatel:
110110(0) 111001(0) 000100(1)

Příjemce:

| Data      | vyhodnocení parity | validnost zprávy |
| --------- | ------------------ | ---------------- |
| 110110(0) | OK                 | OK               |
| 101001(0) | NOK                | NOK              |
|   100100(0)        |         OK           |      NOK            |


Detekuje lichý počet chyb ve slově. Pouze detekuje, neopravuje. 

## Volební kódy
Každý bit vysíláme nx-krát.
Příklad - kód (3,1)
Ztrojení bitů. 
Zpráva: 0110
Vyšleme: 000 111 111 000
Příjemce:

| Data | Vyhodnocení | opravení | dekódováno | Validnost zprávy |
| ---- | ----------- | -------- | ---------- | ---------------- |
| 000  | OK          |          | 0          | OK               |
| 110  | NOK         | 1        | 1          | OK               |
| 010  | NOK         | 0        | 0          | NOK              |
| 000  | OK          |          | 0          | OK               | 

Jedničky přehlasovali nulu a zpráva byla opravena na $111$.

Opravuje jednu chybu, nebo detekuje až dvojitou chybu!

## "Sloupcová parita"
Ochrana před shluky chyb. Průměrná délka shluku 6bitů.

| data   | řádková parita |
| ------ | -------------- |
| 101100 |   1             |
| 111001 |    0            |
| 110001 |     1           |
| 001001 |      0          |
| --     |        --        |
| 101101 |       0         |

Na posledním řádku je takzvaná sloupcová parita. 