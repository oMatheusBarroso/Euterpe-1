# EuterpeOne
A code to read songs transposed (within standards) from scores and run them on an Arduino Uno with a buzzer.
Um código para ler músicas transpostas (dentro dos padrões) de partituras e executar elas em um Arduino Uno com buzzer.

## ESCALA MAIOR NATURAL

Todas as TAGS DE NOTAS precisam vir acompanhadas por parêntesis.
   Ex.: C() ou Gsus()

A exceção é a pausa, que deve ser usada sem os parêntesis.
   Ex.: pausa     ---   correto
        pausa()   ---   INCORRETO
        
### LISTA DE TAGS
- - - - - - - - - - - - - - - - - - - - - -
TAG       - Nota             - Frequência
- - - - - - - - - - - - - - - - - - - - - -
pausa     - Pausa / Silêncio - 0 Hz
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
C         - Dó               - 264 Hz
Csus      - Dó sustenido     - 280 Hz
Db        - Ré bemol         -  idem
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
D         - Ré               - 297 Hz
Dsus      - Ré sustenido     - 313 Hz
Eb        - Mi bemol         -  idem
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
E         - Mi               - 330 Hz
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
F         - Fá               - 352 Hz
Fsus      - Fá sustenido     - 374 Hz
Gb        - Sol bemol        -  idem
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
G         - Sol              - 396 Hz
Gsus      - Sol sustenido    - 418 Hz
Ab        - Lá bemol         -  idem
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
A         - Lá               - 440 Hz
Asus      - Lá sustenido     - 467 Hz
Bb        - Si bemol         -  idem
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
B         - Si               - 495 Hz 
___________________________________________


## OITAVAS

O código suporta 2 oitavas acima e 1 oitava abaixo das notas naturais.
Para utilizar as oitavas, basta colocar sua representação entre os parêntesis das notas:
                nota(oitava)

Representação das oitavas:
          - natural
    n     - natural

    I     - 1 oitava acima
    II    - 2 oitavas acima
    III   - 3 oitavas acima
    IV    - 4 oitavas acima

    i     - 1 oitava abaixo
    ii    - 2 oitavas abaixo
    iii   - 3 oitavas abaixo

Exemplos:
 - Dó natural -------------------- C()
 - Sol natural ------------------- G(n)
 - Dó, 1 oitava acima ------------ C(I)
 - Fá sustenido, 1 oitava acima -- Fsus(I)
 - Si bemol, 2 oitavas acima ----- Bb(II)
 - Lá bemol, 1 oitava abaixo ----- Ab(i)


##FIGURAS E TEMPOS
-------------------------------------------------
É necessário inserir o ritmo/passo da música em BPM (batidas por minuto) no início do código para que o tempo das figuras seja calculado.

Por padrão o ritmo será 120 BPM.
------------------------------------------------- 
LISTA DE TAGS - - - - - - - - - - - - - - - - - -
- - - - - - - - - - - - - - - - - - - - - - - - -
TAG       - Nota          - Duração
- - - - - - - - - - - - - - - - - - - - - - - - -
sbre      - Semibreve     - 1

mini      - Mínima        - 1/2
smini     - Semínima      - 1/4

col       - Colcheia      - 1/8
scol      - Semicolcheia  - 1/16

fusa      - Fusa          - 1/32
sfusa     - Semifusa      - 1/64
-------------------------------------------------
Assim como as notas, as TAGS DE FIGURA devem ser acompanhadas por parêntesis.

   Ex.: sbre() ou mini()
 
-------------------------------------------------
Pontos de aumento e diminuição da duração:
 
Para alterar a duração das notas, basta colocar
sua representação entre os parêntesis das figuras 

                 figura(duração)

Representação dos pontos duração:
          - natural
    n     - natural
    p     - ponto de aumento
    s     - staccato (ponto de diminuição)

Exemplos:
 - Semibreve, natural ----- sbre()
 - Mínima, natural -------- mini(n)
 - Colcheia, aumentada ---- col(p)
 - Mínima, diminuida ------ mini(s)
