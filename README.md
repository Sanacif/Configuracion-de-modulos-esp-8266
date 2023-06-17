# Configuracion-de-modulos-esp-8266
Este es un proyecto que se hizo en el ITU para la materia de transmisión de datos 
Se incluye la biblioteca ESP8266WiFi, que proporciona las funciones necesarias para trabajar con el módulo ESP8266 y establecer una conexión WiFi.
Se definen las variables ssid y password para configurar el nombre de la red WiFi y la contraseña respectivamente.
Se define la constante clave con un valor de 5. Esta variable se utilizará para aplicar un desplazamiento a los caracteres de un texto y así codificarlos.
Se declara la función codificar que recibe un objeto de tipo String llamado texto y devuelve un objeto de tipo String con el texto codificado.
Dentro de la función codificar, se inicializa textoCodificado con el valor "I".
Se obtiene la longitud del texto usando texto.length() y se guarda en la variable longitud.
Se inicia un bucle for que recorre cada carácter del texto original.
En cada iteración, se obtiene el carácter en la posición i utilizando texto.charAt(i) y se guarda en la variable caracter.
Se aplica el desplazamiento a caracter sumándole la clave de cifrado, y se guarda el resultado en la variable caracterCodificado.
El carácter codificado se agrega al texto codificado utilizando el operador +=, concatenándolo a textoCodificado.
Una vez terminado el bucle, se retorna textoCodificado como resultado de la función codificar.
Luego del cierre de la función codificar, se declara un objeto WiFiServer llamado server en el puerto 80.
En la función setup(), se inicializa la comunicación serial a una velocidad de 115200 baudios y se espera un breve tiempo.
Se configura el modo del WiFi en modo estación con WiFi.mode(WIFI_STA).
Se inicia la conexión WiFi utilizando WiFi.begin(ssid, password). El código espera hasta que la conexión sea establecida utilizando un bucle while y se muestra un mensaje en el Monitor Serial indicando el estado de la conexión.
Una vez conectado a la red WiFi, se imprime la dirección IP local de la placa ESP8266 en el Monitor Serial.
Finalmente, en la función loop(), se crea un objeto WiFiClient llamado client y se verifica si hay una conexión disponible utilizando server.available().
Si hay una conexión, se crea un mensaje de texto con el valor "ola santi" y se llama a la función codificar() para obtener el texto codificado.
Se envía el texto codificado al cliente utilizando client.print(textoCod), y se espera un breve tiempo antes de repetir el bucle loop().
