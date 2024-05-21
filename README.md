/*============================================================================
  Trabalho A3 
  Projeto: Função para funcionamento da Câmara de corrosão por névoa salina
  AUTORES: Kayc Fernandes.
  INSTITUIÇÃO: Una Betim
  DATA DE MODIFICAÇÃO: 
  DATA DE INÍCIO: 16 de Maio de 2024.
  =============================================================================*/


#define PinAcionaBomba 11
#define Ventilador1 5
#define Ventilador2 4

 int i=1;

void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);

  int i=1;

  pinMode(PinAcionaBomba, OUTPUT);

}

void loop() {
  // put your main code here, to run repeatedly:

  while (i=1){
        delay(1000);

    digitalWrite(PinAcionaBomba, HIGH);

    delay(5500);

    digitalWrite(PinAcionaBomba, LOW);
    }
    
}
