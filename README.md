# MentorBitIR

Esta librería está diseñada para que puedas detectar la presencia de objetos de una forma muy sencilla usando tu placa MentorBit y el módulo de sensor Infrarrojo (IR).

Si estás empezando en el mundo de la electrónica, ¡no te preocupes! MentorBit está pensado para que aprender sea fácil y divertido. Esta placa ya incluye un montón de componentes (LEDs, pulsadores, pantallas, etc.) y utiliza conectores especiales (JST) para que puedas añadir nuevos sensores y módulos sin tener que pelearte con un montón de cables. Pásate por nuestra web para saber más de MentorBit y nuestros productos [pinchando aquí](https://digitalcodesign.com/).

![Render del Módulo MentorBit de Detector IR.](https://github.com/DigitalCodesign/MentorBit-DetectorIR/blob/main/assets/IRDetector_Module.png)

Con esta librería, podrás saber si hay un objeto (como tu mano) delante del sensor y usar esa información para crear proyectos interactivos.

## Descripción
### ¿Qué es un sensor detector de objetos por IR?

Imagina los sensores que abren las puertas de un supermercado o los que activan los grifos automáticos en un baño público. ¡Funcionan de forma muy parecida!

Un sensor infrarrojo (IR) emite un haz de luz que es invisible para el ojo humano. Si un objeto se cruza en su camino, la luz rebota y es detectada de vuelta por el sensor. De esta forma, el sensor sabe que tiene algo delante. Es como tener unos ojos que ven en la oscuridad.

### ¿Qué hace esta librería?

La librería MentorBitIR simplifica al máximo el uso del sensor. Se encarga de leer la señal del módulo y te devuelve una respuesta simple y directa: true (sí, hay un objeto) o false (no, no hay nada).

Gracias a ella, podrás centrarte en lo más importante: ¡qué hará tu proyecto cuando detecte algo!

### ¿Qué puedes construir con este sensor?

- Un robot esquiva-obstáculos que cambia de dirección al detectar una pared.
- Un contador de personas que incrementa un número cada vez que alguien pasa por una puerta.
- Un dispensador automático de gel o jabón que se activa al acercar la mano.
- Una alarma que suena si alguien intenta abrir un cajón o una caja.

## Cómo empezar
Usar la librería es muy sencillo. Solo sigue estos pasos para tener tu sensor detectando objetos en pocos minutos.

1. **Conexión del Módulo**
Antes que nada, conecta tu módulo de sensor DHT11 a uno de los puertos Digitales de Entrada/Salida dentro de la zona de Puertos para Módulos en tu placa MentorBit. ¡Y listo! No necesitas más cables.

2. **Instalación de las Librerías**
Para que tu placa MentorBit pueda comunicarse con el sensor, solo necesitas instalar una librería. El gestor del IDE de Arduino se encargará del resto.

- Abre tu entorno de programación IDE de Arduino.
- Ve al menú *Programa -> Incluir Librería -> Administrar Librerías...*
- En el buscador, escribe ***MentorBitIR*** y haz clic en "Instalar".
- El IDE detectará que esta librería necesita otra para funcionar y te preguntará si quieres instalarla también. Haz clic en "Install all" o "Instalar todo".

![Ejemplo de búsqueda en el gestor de librerías del IDE de Arduino.](https://github.com/DigitalCodesign/MentorBit-DetectorIR/blob/main/assets/library_instalation_example.png)

¡Y ya está! Con eso tienes todo lo necesario para empezar a programar.

## Ejemplo Básico: Detectar un Objeto
El siguiente código es todo lo que necesitas para comprobar continuamente si hay un objeto frente al sensor y mostrar un mensaje en tu ordenador.

### Copia y pega este código en tu IDE:

```c++
// 1. Incluimos la librería que acabamos de instalar.
#include <MentorBitIR.h>

// Definimos el pin digital al que hemos conectado el módulo.
#define IR_PIN 2

// 2. Creamos un objeto 'miSensor' y le indicamos el pin que vamos a usar.
MentorBitIR miSensor(IR_PIN);

void setup() {
    // Inicializamos la comunicación con el ordenador para poder ver los mensajes.
    Serial.begin(9600);
    Serial.println("Sensor IR listo para detectar objetos...");
}

void loop() {
    // 3. Usamos la función para saber si hay un objeto presente.
    // El resultado se guarda en una variable de tipo booleano (true o false).
    bool objetoDetectado = miSensor.objetoPresente();

    // 4. Usamos un 'if' para decidir qué mensaje mostrar.
    if (objetoDetectado) {
        Serial.println(">> ¡Objeto detectado! <<");
    } else {
        Serial.println("--- No hay objeto ---");
    }

    // Esperamos un poco antes de la siguiente comprobación.
    delay(300);
}
```
### Para ver el resultado:

1. Carga el código en tu placa MentorBit.
2. Abre el **Monitor Serie** del IDE de Arduino.
3. ¡Verás cómo aparecen las lecturas de luz cada segundo!

## Funciones Principales

- <code>MentorBitIR(uint8_t ir_pin)</code>
   - **¿Qué hace?** Es el constructor. Crea el objeto que te permitirá controlar el sensor. Debes indicarle a qué pin digital de tu MentorBit has conectado el módulo.
   - **¿Cuándo se usa?** Al principio de tu código, antes del <code>setup()</code>, para declarar tu sensor.

- <code>bool objetoPresente()</code>
   - **¿Qué hace?** Comprueba si hay un objeto en el rango de detección del sensor.
   - **¿Cuándo se usa?** Cada vez que quieras comprobar si hay un objeto, normalmente dentro de la función <code>loop()</code>. Devuelve <code>true</code> si hay un objeto y <code>false</code> si no lo hay.

## Recursos Adicionales

¿Quieres saber más sobre el módulo o necesitas comprar uno? Aquí tienes algunos enlaces que te serán de utilidad:

- [Web del fabricante](https://digitalcodesign.com/)
- [Tienda Online de Canarias](https://canarias.digitalcodesign.com/shop)
- [Tienda Online de Península](https://digitalcodesign.com/shop)
- [Web Oficial de MentorBit](https://digitalcodesign.com/mentorbit)
- [Web Oficial de MentorBit módulo de emisor/receptor infrarrojo (IR)](https://canarias.digitalcodesign.com/shop/00038935-mentorbit-modulo-de-emisor-receptor-infrarrojo-ir-8125)
- [Manual de usuario del MentorBit módulo de emisor/receptor infrarrojo (IR)](https://drive.google.com/file/d/1y6n8XlWD55eUwJZRgIksOTscO2gO2OmY/view?usp=drive_link)
- [Modelo 3D de MentorBit módulo de emisor/receptor infrarrojo (IR) en formato .STEP](https://drive.google.com/file/d/1PMYMwlcQm9u1tMXjADVbzd8WsTtbaTwW/view?usp=drive_link)
