# Teste

lalala

## teste2

lalalala

```c
#include <Servo.h>
const int pinoservo = 7;
int state = 0;

Servo s;
int pos = 30;

void setup() {
  s.attach(pinoservo);
  s.write(pos);
  delay(1000);
  s.detach();
  Serial.begin(9600); // Default communication rate of the Bluetooth module
}

void loop() {
  if(Serial.available() > 0){ // Checks whether data is comming from the serial port
    Serial.println("Algo foi ativado");
    state = Serial.read(); // Reads the data from the serial port
    Serial.println(state);
    s.attach(pinoservo);
    s.write(pos);
    delay(1000);
    s.detach();
 }

 if (state == '0') {
  Serial.println("Desliga");
  pos = 0;
  state = 0;
 }
 else if (state == '1') {
  Serial.println("Liga");
  pos = 60;
  state = 1;
 } 
}
```
