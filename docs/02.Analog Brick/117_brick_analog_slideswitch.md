# #117 Switch Brick

![](../img/100_analog/product/117.jpg)
<!--COLORME-->

## Overview
スライドスイッチを使用したBrickです。

I/OピンよりスライドスイッチのON/OFFをデジタル値で取得できます。

## 接続

![](../img/100_analog/connect/117_new_with_arduino.jpg)


## ソースコード

A0コネクタにスイッチを接続し、D2にLEDを接続する。

```c
#define switchPin A0 // スイッチピン
#define ledPin 2 // LEDピン

void setup() {
  // スイッチピンを入力用に設定
  pinMode(switchPin, INPUT);
  // LEDピンを出力用に設定
  pinMode(ledPin, OUTPUT);
}

void loop() {
  // スイッチの値を取得
  int switchFlag = digitalRead(switchPin);

  // スイッチがONならLEDをつける
  if (switchFlag == HIGH) {
    digitalWrite(ledPin, HIGH);
  } else {
    digitalWrite(ledPin, LOW);
  }

}
```

## 構成Parts
- スライドスイッチ

## GitHub

https://github.com/FaBoPlatform/FaBo/tree/master/117_slideswitch
