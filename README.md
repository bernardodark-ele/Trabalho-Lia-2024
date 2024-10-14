# Trabalho-Lia-2024

## Sistema de Alarme com Sensor de Movimento

### Descrição

Este projeto implementa um sistema de alarme simples utilizando um sensor de movimento PIR e um Arduino. O sistema detecta movimento em um ambiente e, ao identificar uma presença, aciona um alarme sonoro utilizando um buzzer. Este projeto é ideal para quem deseja aprender os conceitos básicos de sensores e automação com Arduino.

### Componentes Necessários

- 1x Arduino Uno (ou similar)
- 1x Sensor de Movimento PIR
- 1x Buzzer
- 1x LED (opcional, para indicar o estado do alarme)
- 1x Resistor 220Ω (para o LED, se usado)
- Protoboard
- Fios de conexão

### Montagem do Circuito

1. Conecte o pino VCC do sensor PIR ao pino 5V do Arduino.
2. Conecte o pino GND do sensor PIR ao pino GND do Arduino.
3. Conecte o pino de saída do sensor PIR (OUT) a um pino digital do Arduino (por exemplo, pino 2).
4. Conecte o terminal positivo do buzzer ao pino digital do Arduino (por exemplo, pino 3) e o terminal negativo ao GND.
5. (Opcional) Se estiver utilizando um LED, conecte o anodo (perna longa) ao pino digital do Arduino (por exemplo, pino 4) e o catodo (perna curta) ao resistor de 220Ω, que deve ser conectado ao GND.

### Código Fonte

```cpp
int pirPin = 2;    // Pino do sensor PIR
int buzzerPin = 3; // Pino do buzzer
int ledPin = 4;    // Pino do LED (opcional)

void setup() {
  pinMode(pirPin, INPUT);
  pinMode(buzzerPin, OUTPUT);
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int sensorState = digitalRead(pirPin);
  
  if (sensorState == HIGH) {
    digitalWrite(buzzerPin, HIGH); // Ativa o buzzer
    digitalWrite(ledPin, HIGH);     // Ativa o LED
    Serial.println("Movimento detectado!");
    delay(1000);                    // Aguarda 1 segundo
  } else {
    digitalWrite(buzzerPin, LOW);  // Desativa o buzzer
    digitalWrite(ledPin, LOW);      // Desativa o LED
  }
}
