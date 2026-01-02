### Slovnik

- **abeceda** `∑` - neprazdna mnozina znaku
- **slovo** - libovolna konecna posloupnost symbolu z dane abecedy
- **jazyk** - `L` v abecede `∑` je nejaka libovolna podmnozina mnoziny ∑<sup>*</sup>
  ***
- **w** - delka slova
- **w<sup>0</sup>** slovo delky 0 znacime `ε`
- **∑<sup>*</sup>** - mnozina vsech slov vcetne `ε` (slovo delky 0)
- **∑<sup>+</sup>** - mnozina bez `ε`
- **a<sup>2</sup>b<sup>3</sup>** - aabbb
- **(ab)<sup>3</sup>** - ababab

#### Jazyky
- {00,01001,1101} je jazyk v abecede {0,1}
- L<sub>1</sub> = {ab, bb,bc} L<sub>2</sub> = {aa,bb,cc}
  - **L<sub>1</sub> u  L<sub>2</sub>** = {ab, bb, bc, aa, cc} = L<sub>2</sub> ∩ L<sub>1</sub>
  - **L<sub>1</sub> ∩ L<sub>2</sub>** = {bb} =  L<sub>2</sub> ∩ L<sub>1</sub>
  - **L<sub>1</sub>.L<sub>1</sub>** = {bcaa, bbbb, abcc, ...} (rzetezeni jazyku)

#### Gramatika
- je ctverice `G=(V,T,S,P)` V∩T=∅
  - V - konecna mnozina entit (promenne {A,B,C}
  - T - mnozina terminalnich symbolu {a,b}
  - S - pocatecni promenna {S}
  - P - konecna mnozina {obsahuje pravidla}
- zapisuji se pomoci odvozovaciho pravidla `x→y`

- **zkraceny zapis pravidel** (pokud existuje vice pravidel se stejnou pravou stranou)
  - S → aAb
  - A → Ac|ε
- **ekvivalentni gramatika** pokud L(G1)=L(G2)
= **linearni gramatika** obsahuuje na prave strane nejvysse jedno promennou a nezalezi na miste vyskytu teto promenne

- **kontextova gramatika**
  - pravidla maji tvar xAy → xvy   
```
w=uxv
x→y
z=uyv (z bylo odvozeno z w, w=>z)
```
lze prepisovat vicekrat w<sub>3</sub>=>w<sub>3</sub>=>w<sub>3</sub>...w<sub>n</sub>

#### Regularni vyrazy

- popisuji jazyky nad abecedou `∑`
- `∅` prazdny jazyk
- `ε` oznacuje jazyk {ε}
- operatoru `+,.,*`
- `a` oznacuje jazyk {a}

  pokud mame abecedu L = {0,1}, lze chapat nasledovne (0+1) bude nula nebo jedna, 0* bude nula vubec nebo vicekrat, ab* bude {a, ab, abb, abbb, ...}

### Priklady ke zkousce

#### Napište regulární výraz r, pro který platí L(r)={(ab) n01 : n>=1}
```
L = {ab01, abab01, ababab01, ...}

ab(ab)*01
```

#### Stanovte gramatiku pro jazyk L(r), r=c(a+b)*
```
L = {c, ca, cb, cab, cba, caa, cbb, ...}
S → cA
A → aA|bA|ε
```

#### Nakreslete přechodový graf deterministického akceptoru, který přijímá jazyk L(r), r=c(a+b)(0+1)*
```
L = {ca, cb, ca0011001, cb011110, ...}
```
```

```
#### Nakreslete přechodový graf dfa M s abecedou {0, 1}, který přijímá slova obsahující sudý počet jedniček a lichý počet nul a stanovte gramatiku L(M).
mame 4 mozne stavy, ktere muzou nastat
```
q0: so, s1
q1: s0, l1
q2: l0, s1 (akceptujeme)
q3: l0, l1
```


| | 1 | 0 | 
|------|-----|----|
| q0 | q1 | q2 | 
| q1 | q0 | q3 | 
| q2 | q3 | q0 | 
| q3 | q2 | q1 | 
