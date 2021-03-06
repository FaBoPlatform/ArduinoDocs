# #112 IR LED Brick

![](../img/100_analog/product/112.jpg)
<!--COLORME-->

## Overview
赤外線LEDを使ったBrickです。

I/Oピンから赤外線LEDをON/OFFを制御することができます。

## 接続
アナログコネクタ(A0〜A5)、またはデジタルコネクタ(2〜13)のいずれかに接続します。

![](../img/100_analog/connect/112_ir_connect_2.jpg)

### IchigoJam
OUTコネクタのいずれかに接続します。


## Parts Specification
| Document |
|:--|
| [OSI5LA5113A](http://akizukidenshi.com/catalog/g/gI-04311/) |

## 回路図
![](../img/100_analog/schematic/112_ir_led.png)

## ソースコード
### for Arduino
A0コネクタに赤外線LED Brick、A1コネクタにボタンBrickを接続し、ボタンが押されたら赤外線LEDを発光させます。

```c
#define irledPin A0
#define buttonPin A1

void setup() {
  pinMode(irledPin, OUTPUT);
  pinMode(buttonPin, INPUT);
}

void loop() {
  
  int buttonState = digitalRead(buttonPin);

  if (buttonState == HIGH) {
    digitalWrite(irledPin, HIGH);
  }
  else {
    digitalWrite(irledPin, LOW);
  }

}
```

## 構成Parts
- 5mm 赤外線LED OSI5LA5113A

## GitHub
- https://github.com/FaBoPlatform/FaBo/tree/master/112_ir_led
