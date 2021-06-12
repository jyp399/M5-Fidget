#M5 Fidget Device 

##Table of contents
*[General info](#general-info)
*[Technologies](#technologies)

##General info
This project creates a fidget device using the M5 Atom device in its corresponding housing and PCB

##Technologies 
Project is created with Arduino
*M5Atom library version: 0.0.1
*FastLED library version: 3.4.0

##```
#include "M5Atom.h"
#include <FastLED.h>

#define NUM_LEDS 25
#define DATA_PIN 27

CRGB leds[NUM_LEDS];

void setup() {
  FastLED.addLeds<WS2812, DATA_PIN>(leds, NUM_LEDS);
  M5.begin(true, false, true);
  delay(50);
  Serial.begin(19200);
}

uint8_t count = 0;
uint8_t count1 = 0;

void loop() {
  for (int i = 0; i <= 25; i++) {
    leds[i] = CRGB::Green;
  }
  FastLED.show();
  delay(10);
  for (int i = 0; i <= 25; i++) {
    leds[i] = CRGB::Black;
  }
  FastLED.show();
  delay(50);
  if (M5.Btn.wasPressed()) {
    count++;
    Serial.println(count);

    delay(250);
    M5.update();
  }
}
```
