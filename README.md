# car_mt_gear_display

This project use Arduino nano V3(Processor ATmega168) and MAX7219 and two Hall sensors to detect current gear of a MT car.

![Image](images/1.jpg)


# Program

## gear_display

This is a test project. It shows 0-9 A-Z 中国, 38 chars. The code is not very good, it just an experiment.


## gear_display_hall

This is the real project.

It can run in two mode: 1.setup mpde, 2.normal mode

### 1. setup mode

- Display `R, N, 1, 2, 3, 4, 5, 6, 7`, each char stay 2 seconds, wait user to put car in the specified gear.
- Read values of two sensors many times and take the avg value
- Store sensor values for all the gears


### 2. normal mode


- Read values of two sensors
- Find the most match gear
- Display the gear on 8x8 display


## Char generator

[Char Generator](https://xantorohara.github.io/led-matrix-editor/)

It can generate very beautiful font for many chars, 0-9 A-Z a-z and some symbols.
But we can not use it in our code, we must convert it to our style.

```
const uint64_t PROGMEM IMAGES1[] = {
  0x3c66666e76663c00,  // 0
  0x7e1818181c181800,  // 1
  0x7e060c3060663c00,  // 2
  ...
}
```

convert to:

```
unsigned char font2[][8] = {
  { 0x00, 0x3c, 0x66, 0x76, 0x6e, 0x66, 0x66, 0x3c },  // 0
  { 0x00, 0x18, 0x18, 0x1c, 0x18, 0x18, 0x18, 0x7e },  // 1
  { 0x00, 0x3c, 0x66, 0x60, 0x30, 0x0c, 0x06, 0x7e },  // 2
  ...
}
```

flip the bytes horizontaly.




# BOM

Arduino Nano V3 (Processor ATmega168)                 x1
MAX7219 8x8 LED Display                               x1
Hall sensor A3144 (TO-92-49E)                         x2
N52 Grade High-Strength Neodymium Iron Boron Magnet   x1
cables                                                x some