# MentorBit-DetectorIR

## Descripción

Esta librería está construida por Digital Codesign para interactuar con el Módulo Detector IR, diseñado principalmente para el kit educacional MentorBit. El Detector IR permite detectar la presencia de un objeto frente al sensor, ideal para proyectos de detección de movimiento o proximidad.

Puedes encontrar nuestro Módulo MentorBit y mucho más material de electrónica y robótica en nuestra tienda oficial: [https://digitalcodesign.com/shop](https://digitalcodesign.com/shop)

## Modo de Empleo

Una vez que tengamos la librería instalada desde el Arduino IDE, necesitamos incluir la librería con la siguiente línea:

```cpp
#include <MentorBitIR.h>
```

### Constructor

Una vez incluida la librería, usamos el constructor para crear el objeto del módulo **Detector IR**, y definimos el pin al que está conectado el sensor IR:

```cpp
MentorBitIR detector(PIN_IR);
```

Donde `PIN_IR` es el pin al que está conectado el sensor **IR**.

### Uso

Con el objeto `detector` definido, podemos verificar si hay un objeto presente frente al sensor utilizando la función `objetoPresente()`, que devuelve un valor de tipo `bool`:

#### Verificar si hay un objeto presente

```cpp
bool objeto = detector.objetoPresente();
```

Esta función devuelve `true` si un objeto está presente frente al sensor, y `false` si no lo está. El color del objeto puede afectar la precisión de la detección.

### Configuración de puertos

Si deseas configurar puertos personalizados, puedes usar la función `configPort()` para asignar los pines y configuraciones de puertos que necesitas:

```cpp
Port port;
port.type = 'm';
port.gpios[0] = 2;  // Pin de configuración
port.gpios[1] = 3;  // Pin IR
detector.configPort(port);
```

Donde `port` es un objeto de tipo `Port` que contiene las configuraciones necesarias.

## Atributos

- `PIN_IR`: Define el pin al que está conectado el sensor **IR**.
