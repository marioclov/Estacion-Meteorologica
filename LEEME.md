##Explicación del funcionamiento de la app en **App Inventor**:

1. **Pantalla principal**: La aplicación muestra una interfaz con un botón para conectar al dispositivo ESP32 vía Bluetooth. También tiene etiquetas que muestran los datos de **temperatura** y **humedad** recibidos del sensor DHT11.

2. **Conexión Bluetooth**:
   - El usuario selecciona el dispositivo ESP32 desde una lista de dispositivos Bluetooth disponibles.
   - Cuando se establece la conexión y se presiona el botón de recargar, la aplicación envía un comando (por ejemplo, `"rec"`) al ESP32 para solicitar los datos del sensor.

3. **Recepción de datos**:
   - Una vez conectado, el ESP32 envía las lecturas del sensor DHT11 (temperatura y humedad) a la aplicación vía Bluetooth.
   - La aplicación recibe los datos y los muestra en la pantalla, actualizando las etiquetas correspondientes con los valores de temperatura y humedad.

4. **Botones y funcionalidad**:
   - Puede haber botones para desconectar el dispositivo ESP32 del bluetooth y que este pueda volver a su modo reposo (deep-sleep).

##Flujo típico de la app:

1. El usuario abre la app en el dispositivo móvil.
2. Se presiona un botón para iniciar la búsqueda de dispositivos Bluetooth.
3. El usuario selecciona el ESP32 y se establece la conexión.
4. La app envía un comando al ESP32 para solicitar la lectura del sensor.
5. El ESP32 responde con los datos, y la app los muestra en pantalla.

(Hay que tener en cuenta que en la primera conexión es posible que el telefono (Android) tenga que conectarse manualmente al dispositivo ESP32, normalmente en el apartado bluetooth de los ajustes del telefono, se conecta al dispositivo ESP32 llamado "ESP32test". Solo es necesario hacer eso la primera vez que se conectan los dos dispositivos)
