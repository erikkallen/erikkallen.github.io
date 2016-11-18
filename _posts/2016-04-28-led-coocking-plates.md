---
title: Mini kitchen with LED cooking top
date: 2016-04-28 23:11:11 Z
categories:
- kitchen
- led
- pwm
layout: post
image: "/images/play_kitchen_led.jpg"
---

Recently I constructed a wooden play kitchen for my daughter.
The kitchen came as a self build package.

After quite a bit of sanding and a few extra screws I had the basic structure ready

![Building basic structure](/images/basic_structure.jpg){: .rounded .project-image-medium}

Of course beeing an engineer this is when the fun stuff started, so I decided to make a few changes to the plan.
First I bought some 0804 Red SMD led's off ebay, next I went to the local plastic plate supplier and picked up a tinted plate of 30 x 40 x 0.5 cm, and finally got some long shaft 10k potentiometers. I still had an Arduino mini laying around and some proto PCB.

The schematics for the board can be found [here](/images/keuken_ailynn_schema.pdf)

This is what it kind of looks like on a breadboard

![Breadboard view](/images/keuken_ailynn_bb.png){: .project-image-medium .rounded}

So I soldered one hot plate up to see if it has the desired effect and luckily it was to my liking.

![LED Test](/images/led_test.jpg){: .rounded .project-image-medium}

What remained was to do the other 3 plates and the front panel controls.

![Front panel controls](/images/front_panel_controls.jpg){: .rounded .project-image-medium}

All that was left to do was mount the assembly and behold! we have a working stove.

![Play kitchen](/images/play_kitchen_led.jpg){: .rounded}

To save power I run the Arduino on a 1 MHz clock instead of the default of 8 MHz

The Arduino code used is the following:


{% highlight c %}
int knop1 = A3;
int knop2 = A1;
int knop3 = A5;
int knop4 = A2;

int oven = A0;

int plaat1 = 3;
int plaat2 = 5;
int plaat3 = 6;
int plaat4 = 9;

int oven_led = 11;

int pot_power = 10;


void setup() {
  // declare the ledPin as an OUTPUT:
  pinMode(plaat1, OUTPUT);
  pinMode(plaat2, OUTPUT);
  pinMode(plaat3, OUTPUT);
  pinMode(plaat4, OUTPUT);
  pinMode(oven_led, OUTPUT);

  pinMode(pot_power, OUTPUT);

  //Serial.begin(57600);

}

void loop() {
  digitalWrite(pot_power, HIGH);
  // read the value from the sensor:
  int knop1Value = analogRead(knop1);
  int knop2Value = analogRead(knop2);
  int knop3Value = analogRead(knop3);
  int knop4Value = analogRead(knop4);

  digitalWrite(pot_power, LOW);

  //Serial.println(knop2Value);

  int knop1Out = map(knop1Value, 0,2023,0,255);
  int knop2Out = map(knop2Value, 0,2023,0,255);
  int knop3Out = map(knop3Value, 0,2023,0,255);
  int knop4Out = map(knop4Value, 0,2023,0,255);

  analogWrite(plaat1, knop1Out);
  analogWrite(plaat2, knop2Out);
  analogWrite(plaat3, knop3Out);
  analogWrite(plaat4, knop4Out);



  delay(100);
}{% endhighlight %}
