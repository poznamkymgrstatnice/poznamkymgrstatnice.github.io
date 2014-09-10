---
layout: post
title: Složitost
---

- Jenom pro jistotu.
- Vyčíslitelnost znamená v normální řeči vypočítatelnost, tj. computability
- spočetnost znamená, že to můžu označit N - tj. enumeration


rozděl a panuj
---
- Co k tomu říct....
- rozdělí se problém na menší problémy
- je docela problém pak počítat složitost
    - je na to jakýsi Master Theorem a ten je nad moje matematické schopnosti

dynamické programování
---
- to mi nikdy nebylo 100pro jasné
- "optimizace" backtrackingu
- v podstatě je to rekurze, kdy řešíme menší a menší problémy, a někde si pamatujeme výsledky těch posledních funkcí
-  If a problem can be solved by combining optimal solutions to non-overlapping subproblems, the strategy is called "divide and conquer" instead.

hladový algoritmus
---
- v každém kroku uděláme jenom lokální optimum
- může nás to dovést to globálního optima, ale nemusí
- každopádně je to aspoň nějaká heuristika

Amortizovaná složitost
---
- Amortized complexity is the total expense per operation, evaluated over a sequence of operations
- accounting method
    - dolar je nejmenší časová jednotka
    - každá operace bude mít cenu v dolarech
    - má jakousi amortizovanou a skutečnou cenu - amortizovaná je, kolik to "stojí", a skutečná je skutečná
    - aha, začíná mi to docházet
    - počítáme si v bance, kolik zrovna máme

Úplné problémy pro třídu NP
---
- oh boy
- redukce
    - Y je redukovatelné v p. čase na X (Y<=X)
    - když instance Y může být vyřešena polynomiálním počtem regulárních kroků PLUS polynomiální počet volání black-boxu co řeší X
    - můj problém s notací: Y je redukovatelné na X, tj. Y je ta menší
        - člověk má pocit, že když A redukujeme na B, tak B je menší, ale je to naopak
        - každý jednoduchý úkol můžeme redukovat na něco složitého, viz dál
    - když Y<=X a X je P, tak Y je P
- P - polynomiální problémy - mají polynomiální složitost
- NP - můžu v pol. čase zkontrolovat, jestli je řešení pravda
    - existují problémy, co nejsou NP - halting problem např, nebo TQBF
    - frmálně přes certifikáty
- NP úplnost- Y je NP up, když
    - Y musí být v NP
    - pro X z NP, X<=Y
        - pro konkrétní problémy je to poměrně těžké dokázat z téhle definice(ale je to ve skriptech)
    - SAT, 3SAT, vertex cover/ind. set
    - pokud NP-complete jsem schopný převést na jiný v NP, tak ten je taky np-complete
    - takže to skutečně stačí z definice dokázat jenom u jednoho z nich a pak je to easy
- kdyby existovalo P řešení NP-c problému, tak P=NP, a to je divný 
- ještě jednou - buď všechny NP-c jsou P, nebo žádné
- Teoreticky:
    - pokud P != NP, tak existují problémy, co nejsou ani P ani NP-c
    - ve skutečnosti jsme ale takové nenašli - buď jsou P, nebo NP-c, a ten důkaz o existenci není konstruktivní ale nějaký čistě matematický
- NP těžké
    - stejná definice jako NP-c, ale není potřeba, aby byl z NP
    - moc jich teda neni, co nejsou NPc a zároveň jsou rozhodnutelné
- jaké jsou konkrétně NP complete problémy?
    - salesman
    - SAT
    - nezávislá množina / pokrytí vrcholové
    - klika (úplný podgraf)
    - isomorfní podgraf
    - 3barevnost
    - batoh
    - stačí

Cook-Levinova věta
---
- SAT je NP-c
- to je vše
- proof se musí dělat přes konstrukci T. stroje jako SATu a to jako nebudu dělat

Pseudopolynomiální algoritmy, silná NP úplnost
---
- well.... je to algoritmus, co je pol vzhledem k číselné hodnotě, ale exp. k počtu číslic
    - např. primality
    - musim zkoušet do odmocniny, ale sqrt(n) je sublinearni, což by bylo fajn
    - ale vzhledem k počtu číslic je to hrozně 
- pokud existuje PP algoritmus, tak je to "slabě NP úplné"
- to znamená, že pro dostatečně malá čísla je to téměř polynomiální
    - pokud čísla omezíme zvrchu, tak je to skutečně ponynomiální
- pokud není slabě NP úplný, pak je silně úplný
- knapsack je slabě NP úplný

Aproximační algoritmy a schémata
---
- algoritmus
    - takový, co vrátí výsledek jenom o něco horší než by měl
- příklad: bin packing
    - hladový algoritmus, je max. 2x horší
- polynomiální aproximační schéma
    - algoritmus, co mi umí říct pro každé epsilon algoritmus, co je max. (1+epsilon) jiné od optima
    - a je polynomiální vzhledem ke vstupu - 1/epsilon se ale smí objevit v exponentu
- úplné polynomiální aproximační schéma
    - totéž, ale je polynomiální vzhledem k 1/epsilon

Algoritmicky vyčíslitelné funkce
---
- asi je lepší začít Turingovým strojem
    - (Q, Sigma, d, q0, F)
    - Q jsou stavy
    - Sigma je abeceda na pásce
    - d je fce QxSigma->Q x Sigma x (RNL) + KONEC
    - q0 je počáteční stav
    - F jsou finální stavy
- částečná funkce je turingovsky vyčíslitelná, pokud exustuje TSm co 
    - f(x)=,y => (TS dostane na vstupu x => skončí a dá na výstupu po skončení y)
    - f(x) není def => TS nemusí končit nebo tam není legální zápis čísla
- moc nevim, co sem psát dál

jejich vlastnosti
---
- jde o formalizovanou ideu algoritmu
- Church Turingova teze
    - taková neformální věc (proto jenom "teze" a ne "věta", asi)
    - pokud je funkce spočítatelná něčím, co má následující vlastnosti, tak je vyčíslitelná
        - procedura musí fungovat pro libovolně velká čísla
        - musí skončit po konečném počtu kroků
        - má nekonečně místa
    - eh, nějak nechápu, jestli je to definice, nebo popis, nebo co přesně
    - prostě cca co jde udělat algoritmem jde popsat i turingovým strojem
    - nebo tak něco

ekvivalence jejich různých matematických definic.
---
- já znám jenom ČRF a Turinga, další definice neznám
- důkaz ekvivalence se učit nebudu

Částečně rekurzivní funkce.
---
- ve skutečnosti stejná množina jako turvyč
- nejdřív primitivně rekurzivní funkce
    - konstantní nulová funkce
    - následník
    - projekce
    - operátor: substituce (volání podprogramu) - h(x) = f(g1(x), g2(x)...gn(x))
    - operátor: primitivní rekurze - jakoby for cyklus od 0 - h(x,y)= f(y) když x=0, g(x-1,h(x-1,y),y) když neni 
- ČRF přidá minimalizaci
    - operátor: minimalizace - h(x) = minimální y, že f(x,y) skončí a je 0, a všechny menší skončí
        - nemusí skončit, proto Č
        - ale druhá část podmínky je nutná (jinak by nedef - 0 nikdy nebylo nalezitelné)
- ORF je ČRF, která je definovaná všude
    - badass

Rekurzivní a rekurzivně spočetné množiny
---
- AAAAAAA
- množina je rekurzivně spočetná, je-li definičním oborem ČRF.
- množina je rekurzivní, je-li její charakteristická funkce ORF.
    - to je ale strašné. Nejde to vysvětlit nějak líp?
- osobní vysvětlení
    - rekurzivnost - znamená vlastně jenom to, že jde o rek. funkce, a tedy turstroj
    - rekurzivní - dokáže mi rekurzivní funkce - tj. algoritmus - říct, jestli tam prvek je, nebo neni, a doběhne to vždycky
    - rekurzivně spočetná - dokážu udělat rekurzivní funkci, co mi to spočítá - to není definice nahoře, ale je to s ní i ekvivalentní

Algoritmicky nerozhodnutelné problémy (halting problem). Riceova věta.
---
- halting problém
    - chceme o TS a vstupu říct, jestli se tam zastaví
    - to samozřejmě nemůžeme
- Riceova věta
    - "většina otázek, co si o algoritmech můžeme položit, není řešitelná"
    - anglicky "for any non-trivial property of partial functions, there is no general and effective method to decide whether an algorithm computes a partial function with that property"
    - důkaz se samozřejmě neučim


Věta o rekurzi
---
- uff
- máme ORF funkci f (můžeme si představit, že modifikuje algoritmy)
- pak existuje pevný bod n té funkce, že phi_n = phi_f(n), tedy: existuje algoritmus, co dává stejné výsledky
    - tohle platí, ať je f jakákoliv, pokud je ORF
    - ty algoritmy nemusí být ORF, musí být ČRF, tj. občas stačí "nikdy neskončí pro žádný vstup" - což není až tak zajímavé, ale stačí to
- dokonce existuje prostá PRF, co najde pevný bod (wat)
- každá ORF má nekonečně pevných bodů (WAT!!!)

