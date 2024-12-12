# MentorBit-DetectorIR

Esta librería está diseñada para interactuar con el módulo Detector IR de MentorBit. Permite detectar la presencia de un objeto frente al sensor IR.

Puedes encontrar el producto y más material de electrónica y robótica en nuestra tienda oficial: [https://digitalcodesign.com/shop](https://digitalcodesign.com/shop)

## Modo de Empleo

Una vez que tengas la librería instalada en el Arduino IDE, inclúyela en tu proyecto con la siguiente línea:

```cpp
#include <MentorBitIR.h>
```

## Constructor

### `MentorBitIR(uint8_t ir_pin = 0)`

Este constructor inicializa el pin del módulo. Se debe especificar el pin donde está conectado el detector IR. El parámetro `ir_pin` es opcional.

```cpp
MentorBitIR detector(2);  // Pin digital 2
```

## Métodos Principales

### `objetoPresente()`

Devuelve `true` o `false` dependiendo de si hay un objeto frente al sensor. El color del objeto afecta significativamente la detección.

```cpp
bool objeto = detector.objetoPresente();
```
