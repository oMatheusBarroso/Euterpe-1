# EuterpeOne
   
   A program to read songs transcribed from sheet to code, following a pattern, and run them on an Arduino Uno with a buzzer. Project named after the Greek Muse of Music, Euterpe. ***< Text in portuguese >***.
   
   Um programa para ler músicas transcritas da partitura para o código, seguindo um padrão, e executá-las em um Arduino Uno com buzzer. Projeto nomeado em referência à Musa Grega da Música, Euterpe.
   
---

## Pontos de Atenção

### Linhas de Código

- **[Linha 1:](https://github.com/oMatheusBarroso/EuterpeOne/blob/edcb6ff595e6243eca5d1ba60299b107628dc573/EuterpeOne-v6.ino#L1)** está comentado o nome da música, para identificação: `// NOME DA MÚSICA: Davy Jones' Locket`
- **[Linha 2:](https://github.com/oMatheusBarroso/EuterpeOne/blob/edcb6ff595e6243eca5d1ba60299b107628dc573/EuterpeOne-v6.ino#L2)** precisa ser inserido o BPM da música, se conhecido: `float bpm = 120;`
- **[Linha 6:](https://github.com/oMatheusBarroso/EuterpeOne/blob/edcb6ff595e6243eca5d1ba60299b107628dc573/EuterpeOne-v6.ino#L6)** deve ser inserido o pino correto do Arduino em que o buzzer está ligado
- **[Linha 199:](https://github.com/oMatheusBarroso/EuterpeOne/blob/edcb6ff595e6243eca5d1ba60299b107628dc573/EuterpeOne-v6.ino#L199)** se necessário, pode-se transpor a partitura inteira em oitavas alterando o valor numérico: `byte transposition = 1;`
- **[Linha 202:](https://github.com/oMatheusBarroso/EuterpeOne/blob/edcb6ff595e6243eca5d1ba60299b107628dc573/EuterpeOne-v6.ino#L202)** o ritmo de reprodução da música pode ser alterado, trocando o valor numérico: `float rhythm = 1;`

A transposição da partitura começa na **[linha 207](https://github.com/oMatheusBarroso/EuterpeOne/blob/edcb6ff595e6243eca5d1ba60299b107628dc573/EuterpeOne-v6.ino#L207)** e vai até a **[linha 237](https://github.com/oMatheusBarroso/EuterpeOne/blob/edcb6ff595e6243eca5d1ba60299b107628dc573/EuterpeOne-v6.ino#L237)** do código de exemplo (v6).

### Principais Regras

A partitura precisa ser transcrita dentro da seguinte estrutura, para funcionar corretamente:

```
int melody[][2]{
  
  TRANSCRIÇÃO
  
};
```

A forma de organização não interfere no funcionamento, desde que:
- cada nota e sua respectiva duração estejam entre chaves e separadas por vírgula:  `{nota,duração}`
- cada nota esteja separada por vírgulas das demais:  `{nota1,duração},  {nota2,duração}, ...`
- a última nota não seja sucedida por uma vírgula:  `{última_nota,duração}`
- não haja alterações na estrutura acima.

#### Exemplo:

```
int melody[][2]{
  {nota1,duração},  {nota2,duração},
  
  {nota3,duração},
  {nota4,duração},
  
  ...
  
  {última_nota,duração}
};
```

---

## Padronização para Transcrição de Partituras

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

##### Exemplos:
   
Nota         | Código
:----------- | :------:
Dó           | `C()`
Fá sustenido | `Fsus()`
Si bemol     | `Bb()`

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
