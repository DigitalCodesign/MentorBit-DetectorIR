# MentorBitIR

Librería para la detección de objetos mediante sensor infrarrojo (IR) en módulos compatibles con MentorBit.

## Descripción

La librería `MentorBitIR` permite detectar la presencia de objetos utilizando un sensor infrarrojo (IR) en módulos compatibles con MentorBit. Devuelve un valor booleano que indica si se ha detectado un objeto dentro del rango del sensor. Es útil para aplicaciones de detección de proximidad, conteo de objetos y evitación de obstáculos.

**Importante:** La detección puede verse afectada por el color y la reflectividad del objeto.

## Modo de Empleo

1.  **Instalación:**
    * Abre el IDE compatible con MentorBit.
    * Ve a "Herramientas" -> "Gestionar librerías..."
    * Busca "MentorBitIR" e instálala.

2.  **Ejemplo básico:**

    ```c++
    #include <MentorBitIR.h>

    MentorBitIR irSensor(2); // Sensor IR conectado al pin 2

    void setup() {
      Serial.begin(9600);
      Serial.println("Sensor IR inicializado.");
    }

    void loop() {
      if (irSensor.objetoPresente()) {
        Serial.println("Objeto detectado.");
      } else {
        Serial.println("No se detecta objeto.");
      }
      delay(500);
    }
    ```

## Constructor y Métodos Públicos

### Constructor

* `MentorBitIR(uint8_t ir_pin = 0)`: Crea un objeto `MentorBitIR`.
    * `ir_pin`: Número de pin al que está conectado el sensor IR. Si no se especifica, se asume que no está conectado a ningún pin inicialmente.

### Métodos

* `bool objetoPresente()`: Devuelve `true` si se detecta un objeto, `false` en caso contrario.
