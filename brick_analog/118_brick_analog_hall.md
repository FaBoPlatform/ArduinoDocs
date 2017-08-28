# #117 Switch Brick

<center>![](/img/100_analog/product/118.jpg)
<!--COLORME-->

## Overview
スライドスイッチを使用したBrickです。

I/OピンよりスライドスイッチのON/OFFをデジタル値で取得できます。

## Connecting

![](/img/100_analog/connect/118_new_with_arduino.jpg)


## Sample Code

A0コネクタにスイッチを接続し、D2にLEDを接続する。

```c
#define hallPin A0 // Hallピン
#define ledPin 2 // LEDピン

void setup() {
  // Hallピンを入力用に設定
  pinMode(hallhPin, INPUT);
  // LEDピンを出力用に設定
  pinMode(ledPin, OUTPUT);
}

void loop() {
  // Hallの値を取得
  int hallFlag = digitalRead(hallPin);

  // スイッチがONならLEDをつける
  if (hallFlag == HIGH) {
    digitalWrite(ledPin, HIGH);
  } else {
    digitalWrite(ledPin, LOW);
  }
}
```

## 構成Parts
- Hall

## GitHub

https://github.com/FaBoPlatform/FaBo/tree/master/118_hall
