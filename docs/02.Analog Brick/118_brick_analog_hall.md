# #118 Hall Brick

![](../img/100_analog/product/118.jpg)

スライドスイッチを使用したBrickです。

I/OピンよりスライドスイッチのON/OFFをデジタル値で取得できます。

## 接続

![](../img/100_analog/connect/118_new_with_arduino.jpg)


## ソースコード

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
