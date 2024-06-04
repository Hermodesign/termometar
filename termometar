#include <LiquidCrystal.h>

const int sensorPin = A0; // Pin na kojem je povezan senzor
const float baselineTemp = 20.0; // Osnovna temperatura za poređenje

// Inicijalizacija LCD-a sa pinovima koje koristimo
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
  Serial.begin(9600);
  lcd.begin(16, 2); // Postavljanje LCD-a sa 16 kolona i 2 reda

  for (int pinNumber = 6; pinNumber < 9; pinNumber++) {
    pinMode(pinNumber, OUTPUT); // Postavljanje pinova 6, 7 i 8 kao izlazne
    digitalWrite(pinNumber, LOW); // Inicijalno isključivanje LED lampica
  }

  // Prikaz početne poruke na LCD ekranu
  lcd.print("Nikola M.");

}

void loop() {

  for (int broj = 0; broj < 999; broj++) {
    lcd.setCursor(10, 0);
    lcd.print(broj);

  int sensorVal = analogRead(sensorPin);
  Serial.print("Sensor Value: ");
  Serial.print(sensorVal);

  float voltage = (sensorVal / 1023.0) * 5.0;
  Serial.print(", Volts: ");
  Serial.print(voltage);
  Serial.print(", degrees C: ");

  float temperature = (voltage - 0.5) * 100.0;
  Serial.println(temperature);

  // Prikaz temperature na LCD ekranu
  lcd.setCursor(0, 1); // Postavi kursor na drugi red
  lcd.print("Temp: ");
  lcd.print(temperature);
  lcd.print(" C"); // Dodaj razmake da obrišeš prethodne karaktere

  // Logika za kontrolu LED lampica na osnovu temperature
  if (temperature < baselineTemp) {
    digitalWrite(6, LOW); // Promenjen pin sa 2 na 6
    digitalWrite(7, LOW); // Promenjen pin sa 3 na 7
    digitalWrite(8, LOW); // Promenjen pin sa 4 na 8
  } else if (temperature >= baselineTemp && temperature < baselineTemp + 2) {
    digitalWrite(6, HIGH); // Promenjen pin sa 2 na 6
    digitalWrite(7, LOW);  // Promenjen pin sa 3 na 7
    digitalWrite(8, LOW);  // Promenjen pin sa 4 na 8
  } else if (temperature >= baselineTemp + 2 && temperature < baselineTemp + 5) {
    digitalWrite(6, HIGH); // Promenjen pin sa 2 na 6
    digitalWrite(7, HIGH); // Promenjen pin sa 3 na 7
    digitalWrite(8, LOW);  // Promenjen pin sa 4 na 8
  } else {
    digitalWrite(6, HIGH); // Promenjen pin sa 2 na 6
    digitalWrite(7, HIGH); // Promenjen pin sa 3 na 7
    digitalWrite(8, HIGH); // Promenjen pin sa 4 na 8
  }

  delay(1000); // Pauza od 1 sekunde pre sledećeg očitavanja

  }
}
