// NOME DA MÚSICA: Davy Jones' Locket
  float bpm = 120;                         // Ritmo em BPM

// Definições ----------------------------------------------------------------

  const byte buzzerPin = 13; // Buzzer (pino 13)
  const byte buttonPin = 10; // Botão de Configuração (pino 10)

  const byte n = 1; // Duração natural
  const float p = 1.5; // Ponto de Aumento
  const float s = 0.5; // Staccato
  
  const byte I = 2; // 1ª oitava acima
  const byte II = 4; // 2ª oitava acima
  const byte III = 8; // 3ª oitava acima
  const byte IV = 16; // 4ª oitava acima
  const float i = 0.5; // 1ª oitava abaixo
  const float ii = 0.25; // 2ª oitava abaixo
  const float iii = 0.125; // 3ª oitava abaixo

  float dur_sbre = 60/bpm * 4 * 1000;
  // duração da semínima: '60/bpm' --- com bpm = 120 - duração = 0,5s
  //                                                 - semibreve = 2s (4x)
  float dur_mini = dur_sbre * 1/2;
  float dur_smini = dur_sbre * 1/4;
  
  float dur_col = dur_sbre * 1/8;
  float dur_scol = dur_sbre * 1/16;
  
  float dur_fusa = dur_sbre * 1/32;
  float dur_sfusa = dur_sbre * 1/64;

  int arrayRows;
  
  int note;
  int duration;

// Notas musicais e oitavas --------------------------------------------------

  const byte pausa = 0; // Pausa / Silêncio
  
  int OctavesReturn(int frequency, float octave){
    if (octave == 0)
      return frequency;
    return round(frequency * octave);
  }
  
  // Dó
  int C(float octave = 0){
    int frequency = 264;
    return OctavesReturn(frequency, octave);
  }
  
  // Dó sustenido
  int Csus(float octave = 0){
    int frequency = 280;
    return OctavesReturn(frequency, octave);
  }
  
  // Ré bemol
  int Db(float octave = 0){
    return Csus(octave);
  }
  
  // Ré
  int D(float octave = 0){
    int frequency = 297;
    return OctavesReturn(frequency, octave);
  }
  
  // Ré sustenido
  int Dsus(float octave = 0){
    int frequency = 313;
    return OctavesReturn(frequency, octave);
  }
  
  // Mi bemol
  int Eb(float octave = 0){
    return Dsus(octave);
  }
  
  // Mi
  int E(float octave = 0){
    int frequency = 330;
    return OctavesReturn(frequency, octave);
  }
  
  // Fá
  int Fa(float octave = 0){
    int frequency = 352;
    return OctavesReturn(frequency, octave);
  }
  
  // Fá sustenido
  int Fasus(float octave = 0){
    int frequency = 374;
    return OctavesReturn(frequency, octave);
  }
  
  // Sol bemol
  int Gb(float octave = 0){
    return Fasus(octave);
  }
  
  // Sol
  int G(float octave = 0){
    int frequency = 395; // Abaixei 1 Hz para testar se para de xiar
    return OctavesReturn(frequency, octave);
  }
  
  // Sol sustenido
  int Gsus(float octave = 0){
    int frequency = 418;
    return OctavesReturn(frequency, octave);
  }
  
  // Lá bemol
  int Ab(float octave = 0){
    return Gsus(octave);
  }
  
  // Lá
  int A(float octave = 0){
    int frequency = 440;
    return OctavesReturn(frequency, octave);
  }
  
  // Lá sustenido
  int Asus(float octave = 0){
    int frequency = 467;
    return OctavesReturn(frequency, octave);
  }
  
  // Si bemol
  int Bb(float octave = 0){
    return Asus(octave);
  }
  
  // Si
  int B(float octave = 0){
    int frequency = 495;
    return OctavesReturn(frequency, octave);
  }

// Figuras e tempos ----------------------------------------------------------

  int FiguresReturn(float duration, float increment){
    if(increment == 0)
      return round(duration);
    return round(duration * increment);
  }
  
  // Semibreve
  int sbre(float increment = 0){
    return FiguresReturn(dur_sbre, increment);
  }
  
  // Mínima
  int mini(float increment = 0){
    return FiguresReturn(dur_mini, increment);
  }
  
  // Semínima
  int smini(float increment = 0){
    return FiguresReturn(dur_smini, increment);
  }
  
  // Colcheia
  int col(float increment = 0){
    return FiguresReturn(dur_col, increment);
  }
  
  // Semicolcheia
  int scol(float increment = 0){
    return FiguresReturn(dur_scol, increment);
  }
  
  // Fusa
  int fusa(float increment = 0){
    return FiguresReturn(dur_fusa, increment);
  }
  
  // Semifusa
  int sfusa(float increment = 0){
    return FiguresReturn(dur_sfusa, increment);
  }

  int testefinal(float increment = 0){
    int dur_sbre1 = 2000;
    if (increment == 0)
      return 1 * dur_sbre1;
    return 2 * dur_sbre1;
  }

// README file

// T R A N S C R I Ç Ã O ~~~ D A ~~~ P A R T I T U R A

byte transposition = 1;     // Transposição
// Inserir oitava

float rhythm = 1;     //Ritmo
// Inserir velocidade de reprodução: 0.5 -- 1 -- 1.25 -- 2 -- 2.75 -- etc...

// Davy Jones' Locket
int melody[][2]{
  {D(),mini()},  {E(),smini()},
  
  {Fa(),mini()},  {G(),smini()},
  
  {A(),mini()},  {C(I),scol()},  {Bb(),col(p)},

  {A(),mini(p)},
  
  {A(),mini()},  {Bb(),smini()},

  {C(I),mini()},  {D(I),scol()},  {Bb(),col(p)},

  {A(),mini()},  {G(),smini()},

  {A(),mini(p)},

  {Bb(),mini()},  {C(I),smini()},

  {A(),mini()},  {Fa(),smini()},

  {G(),mini()},  {Bb(),scol()},  {A(),col(p)},

  {Fa(),mini()},  {D(),smini()},

  {E(),mini()},  {C(),smini()},

  {A(i),mini()},  {E(),smini()},

  {D(),mini(p)},

  {D(),mini()},  {pausa,smini()}
};

// Funções de Controle -------------------------------------------------------

void StartupMelody(){
  tone(buzzerPin, G(), 200);
  delay(200);
//  tone(buzzerPin, E(), 200);
//  delay(200);
//  tone(buzzerPin, Fa(), 200);
//  delay(200);
  tone(buzzerPin, Fa(), 200);
  delay(200);

  delay(500);
}

void PausedMelody(){
  tone(buzzerPin, Fa(), 200);
  delay(200);
  tone(buzzerPin, G(), 200);
  delay(200);
  
  delay(500);
}

void PlayMelody(){
  for(int selectedRow = 0; selectedRow < arrayRows; selectedRow++){
    note = melody[selectedRow][0] * transposition;
    duration = melody[selectedRow][1] / rhythm;

    if(selectedRow > 0 && note == melody[selectedRow-1][0]){
      noTone(buzzerPin);
      delay(50);
    }
    
    tone(buzzerPin, note);
    delay(duration);
  }
}

void StopMelody(){
  noTone(buzzerPin);
}

void setup() {
  Serial.begin(9600);
  StartupMelody();
  delay(1000);
  pinMode(buzzerPin, OUTPUT);
  pinMode(buttonPin, INPUT);
  arrayRows = (sizeof(melody)/sizeof(melody[0]));

  PlayMelody();

  StopMelody();
}

void loop() {
  
}
