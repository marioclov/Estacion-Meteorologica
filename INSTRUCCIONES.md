### Instrucciones detalladas para construir una estación meteorológica con ESP32, DHT11, pantalla SH1106 y botón

#### Materiales necesarios:
- 1 ESP32
- 1 Sensor de temperatura y humedad DHT11
- 1 Pantalla OLED SH1106
- 1 Botón pulsador
- 1 Fuente de alimentación de 9V (pila de 9V)
- Cables

---

### **Paso a paso para construir el circuito**:

#### 1. **Conexiones del Sensor DHT11 (Sensor de temperatura y humedad)**:
   El sensor **DHT11** tiene tres pines: alimentación, tierra y datos. Conéctalos de la siguiente forma:
   
   - **VCC (pin de alimentación)** → Pin **3.3V** del ESP32.
   - **GND** → Pin **GND** del ESP32.
   - **DAT (señal de datos)** → Pin **D4** (GPIO4) del ESP32.

   > **Nota**: Este pin del sensor DHT11 es responsable de enviar la señal de temperatura y humedad al ESP32.

#### 2. **Conexiones de la Pantalla OLED SH1106**:
   La pantalla OLED utiliza el protocolo **I2C** para comunicarse con el ESP32, y sus pines se conectan de la siguiente manera:
   
   - **VDD** → Pin **3.3V** del ESP32 (alimentación).
   - **GND** → Pin **GND** del ESP32 (tierra).
   - **SCK (reloj I2C)** → Pin **D22 (GPIO22)** del ESP32.
   - **SDA (datos I2C)** → Pin **D21 (GPIO21)** del ESP32.

   > **Nota**: Los pines SCK y SDA del ESP32 corresponden al bus de comunicación I2C. Asegúrate de conectarlos correctamente.

#### 3. **Conexiones del Botón Pulsador**:
   El botón pulsador se conecta de manera sencilla al ESP32. Conéctalo de la siguiente forma:
   
   - Un terminal del botón → Pin **D12 (GPIO12)** del ESP32.
   - El otro terminal del botón → **GND** del ESP32 (tierra).

   > **Nota**: Este botón puede utilizarse para cambiar entre diferentes pantallas o iniciar acciones como la actualización de datos.

#### 4. **Conexión de la fuente de alimentación (pila de 9V)**:
   Para alimentar el ESP32 con la pila de 9V, realiza la conexión de la siguiente manera:

   - El **terminal positivo** de la pila de 9V se conecta a **VIN** del ESP32.
   - El **terminal negativo** de la pila de 9V se conecta a **GND** del ESP32.

   > **Nota**: La entrada **VIN** en el ESP32 regula el voltaje de entrada para alimentar todo el circuito.

---

### **Explicación de la función de cada componente**:

1. **ESP32**: Es el cerebro del sistema. Recoge los datos del sensor DHT11, controla la pantalla OLED y reacciona a las pulsaciones del botón.
  
2. **DHT11**: Este sensor mide la **temperatura** y la **humedad** del entorno. Envía estos valores al ESP32, que los procesa y muestra en la pantalla.

3. **Pantalla OLED SH1106**: Muestra la información de la estación meteorológica, como los valores de temperatura y humedad. El ESP32 utiliza el protocolo I2C para comunicarse con la pantalla.

4. **Botón pulsador**: Este botón puede ser utilizado para realizar acciones dentro del programa, como actualizar los datos o cambiar entre diferentes pantallas en la pantalla OLED.

---

### **Explicación del funcionamiento de la app en App Inventor:**

1. **Pantalla principal**: La aplicación muestra una interfaz con un botón para conectar al dispositivo ESP32 vía Bluetooth. También tiene etiquetas que muestran los datos de **temperatura** y **humedad** recibidos del sensor DHT11.

2. **Conexión Bluetooth**:
   - El usuario selecciona el dispositivo ESP32 desde una lista de dispositivos Bluetooth disponibles.
   - Cuando se establece la conexión y se presiona el botón de recargar, la aplicación envía un comando (por ejemplo, `"rec"`) al ESP32 para solicitar los datos del sensor.

3. **Recepción de datos**:
   - Una vez conectado, el ESP32 envía las lecturas del sensor DHT11 (temperatura y humedad) a la aplicación vía Bluetooth.
   - La aplicación recibe los datos y los muestra en la pantalla, actualizando las etiquetas correspondientes con los valores de temperatura y humedad.

4. **Botones y funcionalidad**:
   - Puede haber botones para desconectar el dispositivo ESP32 del bluetooth y que este pueda volver a su modo reposo (deep-sleep).

Flujo típico de la app:

1. El usuario abre la app en el dispositivo móvil.
2. Se presiona un botón para iniciar la búsqueda de dispositivos Bluetooth.
3. El usuario selecciona el ESP32 y se establece la conexión.
4. La app envía un comando al ESP32 para solicitar la lectura del sensor.
5. El ESP32 responde con los datos, y la app los muestra en pantalla.

> **Nota**: Hay que tener en cuenta que en la primera conexión es posible que el telefono (Android) tenga que conectarse manualmente al dispositivo ESP32, normalmente en el apartado bluetooth de los ajustes del telefono, se conecta al dispositivo ESP32 llamado "ESP32test". Solo es necesario hacer eso la primera vez que se conectan los dos dispositivos
