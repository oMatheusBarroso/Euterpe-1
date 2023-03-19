# EuterpeOne
   
   A code to read songs transposed (within standards) from scores and run them on an Arduino Uno with a buzzer.
   
   Um código para ler músicas transpostas (dentro dos padrões) de partituras e executar elas em um Arduino Uno com buzzer.
   
---

## Padronização para Transposição de Partituras

### ESCALA MAIOR NATURAL

   Todas as TAGS DE NOTAS precisam vir acompanhadas por parêntesis.

> Ex.: `C()` ou `Gsus()`

   A exceção é a pausa, que deve ser usada sem os parêntesis.

> Ex.:
> - `pausa`     ---   correto
> - `pausa()`   ---   INCORRETO
        
#### LISTA DE TAGS

TAG       | Nota             | Frequência
:-------: | :--------------- | :--------:
pausa     | Pausa / Silêncio | 0 Hz
--- |  | 
C         | Dó               | 264 Hz
Csus      | Dó sustenido     | 280 Hz
Db        | Ré bemol         |  idem
--- |  | 
D         | Ré               | 297 Hz
Dsus      | Ré sustenido     | 313 Hz
Eb        | Mi bemol         |  idem
--- |  | 
E         | Mi               | 330 Hz
--- |  | 
F         | Fá               | 352 Hz
Fsus      | Fá sustenido     | 374 Hz
Gb        | Sol bemol        |  idem
--- |  | 
G         | Sol              | 396 Hz
Gsus      | Sol sustenido    | 418 Hz
Ab        | Lá bemol         |  idem
--- |  | 
A         | Lá               | 440 Hz
Asus      | Lá sustenido     | 467 Hz
Bb        | Si bemol         |  idem
--- |  | 
B         | Si               | 495 Hz 

---

### OITAVAS

   O código suporta 4 oitavas acima e 3 oitavas abaixo das notas naturais. 
   
   Para utilizar as oitavas, basta colocar sua representação entre os parêntesis das notas: 
   
> Ex.: `nota(oitava)`

#### Representação das oitavas

Representação | Oitava
:-----------: | :-
<vazio>       | natural
n             | natural
<vazio>       |
I             | 1 oitava acima
II            | 2 oitavas acima
III           | 3 oitavas acima
IV            | 4 oitavas acima
<vazio>       |
i             | 1 oitava abaixo
ii            | 2 oitavas abaixo
iii           | 3 oitavas abaixo

##### Exemplos:
   
Nota  | Código
:--- | :----:
Dó natural | `C()`
Sol natural | `G(n)`
Dó, 1 oitava acima | `C(I)`
Fá sustenido, 1 oitava acima | `Fsus(I)`
Si bemol, 2 oitavas acima | `Bb(II)`
Lá bemol, 1 oitava abaixo | `Ab(i)`

---
   
### Figuras e Tempos

   É necessário inserir o ritmo/passo da música em BPM (batidas por minuto) no início do código para que o tempo das figuras seja calculado.

   Por padrão o ritmo será 120 BPM.
   

#### LISTA DE TAGS
TAG       | Nota          | Duração
:-------: | :------------ | :-----:
sbre      | Semibreve     | 1
<vazio>   |   |
mini      | Mínima        | 1/2
smini     | Semínima      | 1/4
<vazio>   |   |
col       | Colcheia      | 1/8
scol      | Semicolcheia  | 1/16
<vazio>   |   |
fusa      | Fusa          | 1/32
sfusa     | Semifusa      | 1/64

   Assim como as notas, as *TAGS DE FIGURA* devem ser acompanhadas por parêntesis.

   Ex.: `sbre()` ou `mini()`
 
---

### Pontos de aumento e diminuição da duração
 
   Para alterar a duração das notas, basta colocar sua representação entre os parêntesis das figuras.

>Ex.: `figura(duração)`

#### Representação dos pontos duração

Representação | Duração
:-----------: | :------
<vazio>       | natural
n             | natural
p             | ponto de aumento
s             | staccato (ponto de diminuição)

##### Exemplos:

Nota | Duração | Código
:--- | :-----: | :----:
Semibreve | natural | `sbre()`
Mínima | natural | `mini(n)`
Colcheia | aumentada | `col(p)`
Mínima | diminuida |  `mini(s)`
