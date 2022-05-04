[![Foo](https://img.shields.io/badge/Version-1.0-brightgreen.svg?style=flat-square)](#versions)
[![Foo](https://img.shields.io/badge/Website-AlexGyver.ru-blue.svg?style=flat-square)](https://alexgyver.ru/)
[![Foo](https://img.shields.io/badge/%E2%82%BD$%E2%82%AC%20%D0%9D%D0%B0%20%D0%BF%D0%B8%D0%B2%D0%BE-%D1%81%20%D1%80%D1%8B%D0%B1%D0%BA%D0%BE%D0%B9-orange.svg?style=flat-square)](https://alexgyver.ru/support_alex/)

[![Foo](https://img.shields.io/badge/README-ENGLISH-brightgreen.svg?style=for-the-badge)](https://github-com.translate.goog/GyverLibs/Psychrometer?_x_tr_sl=ru&_x_tr_tl=en)

# Psychrometer
Библиотека для определения влажности по сухому и мокрому термометру для Arduino
- Библиотека не привязана к термометру, принимает чисто температуру
- Хитрая аппроксимация таблиц парциального давления
- Возможность откалибровать постоянную психрометра

### Совместимость
Совместима со всеми Arduino платформами (используются Arduino-функции)

## Содержание
- [Установка](#install)
- [Инициализация](#init)
- [Использование](#usage)
- [Пример](#example)
- [Версии](#versions)
- [Баги и обратная связь](#feedback)

<a id="install"></a>
## Установка
- Библиотеку можно найти по названию **Psychrometer** и установить через менеджер библиотек в:
    - Arduino IDE
    - Arduino IDE v2
    - PlatformIO
- [Скачать библиотеку](https://github.com/GyverLibs/Psychrometer/archive/refs/heads/main.zip) .zip архивом для ручной установки:
    - Распаковать и положить в *C:\Program Files (x86)\Arduino\libraries* (Windows x64)
    - Распаковать и положить в *C:\Program Files\Arduino\libraries* (Windows x32)
    - Распаковать и положить в *Документы/Arduino/libraries/*
    - (Arduino IDE) автоматическая установка из .zip: *Скетч/Подключить библиотеку/Добавить .ZIP библиотеку…* и указать скачанный архив
- Читай более подробную инструкцию по установке библиотек [здесь](https://alexgyver.ru/arduino-first/#%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0_%D0%B1%D0%B8%D0%B1%D0%BB%D0%B8%D0%BE%D1%82%D0%B5%D0%BA)

<a id="init"></a>
## Инициализация
```cpp
Psychrometer psy;
```

<a id="usage"></a>
## Использование
```cpp
float getHumidity(float dry, float wet);            // получить влажность из (темп. сух., темп. влажн.)
float calibrate(float dry, float wet, float hum);   // калибровка А по (темп. сух., темп. влажн., реальная влажн.)
void setP(long p);                                  // установить давление (в Паскалях)
void setPmm(float p);                               // установить давление (в мм. рт. ст.)
void setA(float a);                                 // установить постоянную психрометра  
float getA();                                       // получить постоянную психрометра  
```

<a id="example"></a>
## Пример
```cpp
#include <Psychrometer.h>
Psychrometer psy;

void setup() {
  Serial.begin(9600);  
  
  //psy.setP(99085);            // установить давление в Па
  psy.setPmm(745);              // установить давление в мм. рт. ст.  
  
  // получить влажность по (темп. сухая, темп. влажная)
  Serial.println(psy.getHumidity(15.0, 12.5));
  
  // калибровка постоянной прибора
  //psy.calibrate(15.0, 12.5, 30);	// (темп. сух., темп. влажн., реальная влажн.)
  // получить новую А можно из psy.getA()
  //psy.setA(0.0007947);        // установить постоянную прибора (по умолч. 0007947)
}

void loop() {
}
```

<a id="versions"></a>
## Версии
- v1.0

<a id="feedback"></a>
## Баги и обратная связь
При нахождении багов создавайте **Issue**, а лучше сразу пишите на почту [alex@alexgyver.ru](mailto:alex@alexgyver.ru)  
Библиотека открыта для доработки и ваших **Pull Request**'ов!