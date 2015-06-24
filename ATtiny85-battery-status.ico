/*
basesd sketch named "Analog Input" from Examples -> 03.Analog
created by David Cuartielles, modified 30 Aug 2011, By Tom Igoe
http://arduino.cc/en/Tutorial/AnalogInput
*/

/* original circuit made by niq_ro from http://www.tehnic.go.ro
http://nicuflorica.blogspot.ro/
http://arduinotehniq.blogspot.com/
1) uC: ATtiny85 (ATtiny45) at 1MHz (internal clock)
2) common chatode RGB LED code OSTA5131A-C, see http://nicuflorica.blogspot.ro/2012/12/arduino-uno-si-un-led-multicolor-rgb.html
- an 180ohms resistor at pin D0 (phisical pin 5) in series with RED LED at GND
- an 100ohms resistor at pin D1 (phisical pin 6) in series with GREN LED at GND
- an 100ohms resistor at pin D2 (phisical pin 7) in series with BLUE LED at GND
3) a voltage divisor 1:4 made like this: +BAT --|=10k=|-|=10k=|-|=10k=|-A2|=10k=|-GND, pin A2 is phisical pin 3
- for tests can use an 10-50kohms variabile resistor put at +5V and GND, midle at A2 (phisical pin 3)
4) Vcc (phisical pin 8) at 5V
5) GND (phisixcal pin 4) at GND
*/

int sensorPin = A2;   // select the input pin for the potentiometer / resistor divider
int ledRPin = 0;      // select the pin for the RED LED
int ledGPin = 1;      // select the pin for the GREEN LED
int ledBPin = 2;      // select the pin for the BLUE LED

int u = 0;  // variable to store the value coming from the sensor

float k=4.95/5; // corection voltage
// define voltage steps:
int treapta1 = 552/k;       // Ubat=10,8V
int treapta2 = 604/k;       // Ubat=11,8V
int treapta3 = 690/k;       // Ubat=13,5V
int treapta4 = 735/k;       // Ubat=14,37V (14,4V)



void setup() {
  // declare the ledPins as an OUTPUT:
  pinMode(ledRPin, OUTPUT);  
  pinMode(ledGPin, OUTPUT);
  pinMode(ledBPin, OUTPUT);
}

void loop() {
/*
  // all leds are off
    digitalWrite(ledRPin, LOW);    // turn the red led off
    digitalWrite(ledGPin, LOW);    // turn the green led off
    digitalWrite(ledBPin, LOW);    // turn the blue led off
*/ 
  
  // read the value from the sensor:
  u = analogRead(sensorPin);    

// voltage below 10,8V
if (u < treapta1)
{
  digitalWrite(ledGPin, LOW);    // turn the green led off
  digitalWrite(ledBPin, LOW);    // turn the blue led off

  digitalWrite(ledRPin, HIGH);   // turn the red led on
  delay(100);
  digitalWrite(ledRPin, LOW);    // turn the red led off
  delay(100);
  digitalWrite(ledRPin, HIGH);   // turn the red led on
  delay(100);
  digitalWrite(ledRPin, LOW);    // turn the red led off
  delay(1000);
}

// voltage ower 10,8V & below 11,8V
if (u > treapta1 && u < treapta2)
{
  digitalWrite(ledGPin, LOW);    // turn the green led off
  digitalWrite(ledBPin, LOW);    // turn the blue led off

  digitalWrite(ledRPin, HIGH);   // turn the red led on
  delay(100);
}

// voltage ower 11,8V & below 13,5V
if (u > treapta2 && u < treapta3)
{ 
  digitalWrite(ledBPin, LOW);    // turn the blue led off
 
  digitalWrite(ledRPin, HIGH);   // turn the red led on
  delay(500);
  digitalWrite(ledRPin, LOW);    // turn the red led off
  delay(100);
  digitalWrite(ledGPin, HIGH);   // turn the green led on
  delay(200);
}

// voltage ower 13,5V & below 14,37V
if (u >= treapta3 && u < treapta4)
{ 
  digitalWrite(ledRPin, LOW);    // turn the red led off
  digitalWrite(ledBPin, LOW);    // turn the blue led off

  digitalWrite(ledGPin, HIGH);   // turn the green led on
  delay(100);
}

// voltage ower 14,37
if (u > treapta4)
{
  digitalWrite(ledRPin, LOW);    // turn the red led off
  
  digitalWrite(ledGPin, HIGH);   // turn the green led on
  delay(500);
  digitalWrite(ledGPin, LOW);   // turn the green led off
  delay(100);
  digitalWrite(ledBPin, HIGH);   // turn the blue led on
  delay(200);
}
}
