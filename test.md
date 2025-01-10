# bp_11. hafta çip ile seven segment

<img src="https://csg.tinkercad.com/things/4DcRPmGBupx/t725.png?rev=1732781997523000000&amp;s=&amp;v=1&amp;type=circuits" title="" alt="" style="zoom:100%;">

## Örnek Kod

```cpp
void setup()
{
  pinMode(8, OUTPUT);
  pinMode(9, OUTPUT);
  pinMode(10, OUTPUT);
  pinMode(11, OUTPUT);
}

void loop()
{
 digitalWrite(8,LOW);
 digitalWrite(9,LOW);
 digitalWrite(10,LOW);
 digitalWrite(11,LOW);
  delay(1000);
 digitalWrite(8,HIGH);
 digitalWrite(9,LOW);
 digitalWrite(10,LOW);
 digitalWrite(11,LOW);
  delay(1000);
 digitalWrite(8,LOW);
 digitalWrite(9,HIGH);
 digitalWrite(10,LOW);
 digitalWrite(11,LOW);
  delay(1000);
 digitalWrite(8,HIGH);
 digitalWrite(9,HIGH);
 digitalWrite(10,LOW);
 digitalWrite(11,LOW);
  delay(1000);
 digitalWrite(8,LOW);
 digitalWrite(9,LOW);
 digitalWrite(10,HIGH);
 digitalWrite(11,LOW);
  delay(1000);
 digitalWrite(8,HIGH);
 digitalWrite(9,LOW);
 digitalWrite(10,HIGH);
 digitalWrite(11,LOW);
  delay(1000);
 digitalWrite(8,LOW);
 digitalWrite(9,HIGH);
 digitalWrite(10,HIGH);
 digitalWrite(11,LOW);
  delay(1000);
 digitalWrite(8,HIGH);
 digitalWrite(9,HIGH);
 digitalWrite(10,HIGH);
 digitalWrite(11,LOW);
  delay(1000);
 digitalWrite(8,LOW);
 digitalWrite(9,LOW);
 digitalWrite(10,LOW);
 digitalWrite(11,HIGH);
  delay(1000);
 digitalWrite(8,HIGH);
 digitalWrite(9,LOW);
 digitalWrite(10,LOW);
 digitalWrite(11,HIGH);
  delay(1000);

}

```

## Donanım Gereksinimleri

- 4 adet LED
- 4 adet 220Ω direnç
- Arduino board
- Bağlantı kabloları

## Pin Konfigürasyonu

- LED 1: Pin 8
- LED 2: Pin 9
- LED 3: Pin 10
- LED 4: Pin 11

## LED Durum Tablosu

| Adım | LED 1 (8) | LED 2 (9) | LED 3 (10) | LED 4 (11) | İkili Sayı |
| ---- | --------- | --------- | ---------- | ---------- | ---------- |
| 1    | LOW       | LOW       | LOW        | LOW        | 0000       |
| 2    | HIGH      | LOW       | LOW        | LOW        | 0001       |
| 3    | LOW       | HIGH      | LOW        | LOW        | 0010       |
| 4    | HIGH      | HIGH      | LOW        | LOW        | 0011       |
| 5    | LOW       | LOW       | HIGH       | LOW        | 0100       |
| 6    | HIGH      | LOW       | HIGH       | LOW        | 0101       |
| 7    | LOW       | HIGH      | HIGH       | LOW        | 0110       |
| 8    | HIGH      | HIGH      | HIGH       | LOW        | 0111       |
| 9    | LOW       | LOW       | LOW        | HIGH       | 1000       |
| 10   | HIGH      | LOW       | LOW        | HIGH       | 1001       |

## Sistem Analizi

1. Setup Fonksiyonu:
   
   - 4 pin çıkış olarak ayarlanır (8-11 arası)

2. Loop Fonksiyonu:
   
   - Her adımda belirli bir LED kombinasyonu yaratılır
   - Her kombinasyon 1 saniye sürer
   - Toplam 10 farklı kombinasyon oluşturulur

## Çalışma Prensibi

- Sistem ikili (binary) sayı sistemine göre çalışır
- LED'ler sırayla 0000'dan 1001'e kadar olan sayıları temsil eder
- Her adım arasında 1 saniyelik bekleme süresi vardır
- Sıralı bir sayaç gibi çalışır
