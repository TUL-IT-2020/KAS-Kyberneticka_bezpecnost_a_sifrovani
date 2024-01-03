# Příklady 
## Samostatné cvičení 3. týden

### Příklad 1.

Je dána zdrojová abeceda A,B,C,D. Pravděpodobnosti výskytu jednotlivých znaků jsou: p(A) = 0.4, p(B) = 0.3, p(C) = 0.2 a p(D) = 0.1.  
Zakódujte zprávu ADCB aritmetickým kódováním.  
Jaká je minimální a maximální délka zprávy než bude dosaženo strojové přesnosti typu float (IEE754, 32-bit)?

### Příklad 2.

Je dána zdrojová abeceda A,B,C,D,E. Pravděpodobnosti výskytu jednotlivých znaků jsou: p(A) =  p(B) = p(C) = p(D) = p(E) = 0.2. Aritmetickým kódováním byla zakódována zpráva o délce čtyři znaky. Zpráva po zakódování je číslo 0.385.  
Jaká je nezakódovaná zpráva.

### Příklad 3.

Aplikujte algoritmus LZW na zprávu nad abecedou A,B. Zpráva je BABAABBAAAB. První dvě položky slovníku budou A = 1, B = 2. Jak bude vypadat komprimovaná zpráva (v číslech položek slovníku)? Jak bude vypadat slovník na konci?

### Příklad 4.

Na zprávu nad abecedou A,B,C byl aplikován algoritmus LZW. Komprimovaná zpráva - v číslech slovníkových položek je: 31124253. Počáteční položky slovníku jsou A = 1, B = 2, C = 3. Jaká je nekomprimovaná zpráva? Jak bude vypadat slovník na konci?

## Řešení příkladů

### Příklad 1:

Interval (0.3912, 0.3936)  
Minimální délka 7 znaků (samá 'D') - dosáhneme délky intervalů okolo 10^-7, což je strojová přesnost 32-bitového float-u.  
Maximální délka 17 znaků (samá 'A') - 0.4^17 = 1.72*10^-7

### Příklad 2

BEDA

### Příklad 3

Zpráva po komprimaci: 213454   
Slovník na konci: A=1,B=2,BA=3,AB=4,BAA=5,ABB=6,BAAA=7

### Příklad 4

Původní zpráva: CAABCABAAC  
Slovník na konci: A=1,B=2,C=3,CA=4,AA=5,AB=6,BC=7,CAB=8,BA=9,AAC=10