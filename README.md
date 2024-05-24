/*============================================================================
  Trabalho A3 | Modelagem e simulação do mundo físico-químico
  Projeto: Função para funcionamento da Câmara de corrosão por névoa salina
  AUTORES: Kayc Fernandes & Ebert Costa.
  INSTITUIÇÃO: Una Betim
  DATA DE MODIFICAÇÃO: 23 de Maio de 2024
  DATA DE INÍCIO: 16 de Maio de 2024.
  =============================================================================*/

#define RelePin 8
#define Buzzer 10

const unsigned long TempoDesligado = 1.8e6; // 30 minutos em milissegundos
const unsigned long TempoLigado = 30000; // 30 segundos em milissegundos

enum State { DESLIGADO, LIGADO };
State estado = DESLIGADO;
unsigned long previousMillis = 0;

void setup() {
  Serial.begin(9600);

  pinMode(RelePin, OUTPUT); // definindo o relé como uma saída digital
  digitalWrite(RelePin, LOW); // O circuito inicia-se com o relé desligado

  pinMode(Buzzer, OUTPUT); // definindo buzzer como saída digital
  digitalWrite(Buzzer, LOW); // o circuito começa com o buzzer desligado
}

void loop() {
  
  unsigned long currentMillis = millis(); // Obtém o tempo atual em milissegundos

  if (estado == DESLIGADO && (currentMillis - previousMillis >= TempoDesligado)) {

    previousMillis = currentMillis; // Atualiza o último tempo de referência

      digitalWrite(RelePin, HIGH); // Liga o relé
      digitalWrite(Buzzer, HIGH); // Liga o buzzer

    estado = LIGADO; // Atualiza o estado para LIGADO

    } else if (estado == LIGADO && (currentMillis - previousMillis >= TempoLigado)) {

      previousMillis = currentMillis; // Atualiza o último tempo de referência

        digitalWrite(RelePin, LOW); // Desliga o relé
        digitalWrite(Buzzer, LOW); // Desliga o buzzer

      estado = DESLIGADO; // Atualiza o estado para DESLIGADO
  }

}