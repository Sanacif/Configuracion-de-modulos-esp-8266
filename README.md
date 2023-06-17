# Configuracion-de-modulos-esp-8266
Este es un proyecto que se hizo en el ITU para la materia de transmisión de datos 

MODULO EMISOR

Se incluye la biblioteca ESP8266WiFi, que proporciona las funciones necesarias para trabajar con el módulo ESP8266 y establecer una conexión WiFi.

Se definen las variables ssid y password para configurar el nombre de la red WiFi y la contraseña respectivamente.

Se define la constante clave con un valor de 5.

Esta variable se utilizará para aplicar un desplazamiento a los caracteres de un texto y así codificarlos.

FUNCION CODIFICAR

Se declara la función codificar que recibe un objeto de tipo String llamado texto y devuelve un objeto de tipo String con el texto codificado.

Dentro de la función codificar, se inicializa textoCodificado con el valor "I".

Se obtiene la longitud del texto usando texto.length() y se guarda en la variable longitud.

Se inicia un bucle for que recorre cada carácter del texto original.

En cada iteración, se obtiene el carácter en la posición i utilizando texto.charAt(i) y se guarda en la variable caracter.

Se aplica el desplazamiento a caracter sumándole la clave de cifrado, y se guarda el resultado en la variable caracterCodificado.

El carácter codificado se agrega al texto codificado utilizando el operador +=, concatenándolo a textoCodificado.

Una vez terminado el bucle, se retorna textoCodificado como resultado de la función codificar.

FUNCION WifiServer

Luego del cierre de la función codificar, se declara un objeto WiFiServer llamado server en el puerto 80.

En la función setup(), se inicializa la comunicación serial a una velocidad de 115200 baudios y se espera un breve tiempo.

Se configura el modo del WiFi en modo estación con WiFi.mode(WIFI_STA).

Se inicia la conexión WiFi utilizando WiFi.begin(ssid, password). El código espera hasta que la conexión sea establecida utilizando un bucle while y se muestra un mensaje en el Monitor Serial indicando el estado de la conexión.

Una vez conectado a la red WiFi, se imprime la dirección IP local de la placa ESP8266 en el Monitor Serial.

Finalmente, en la función loop(), se crea un objeto WiFiClient llamado client y se verifica si hay una conexión disponible utilizando server.available().

Si hay una conexión, se crea un mensaje de texto con el valor "ola santi" y se llama a la función codificar() para obtener el texto codificado.

Se envía el texto codificado al cliente utilizando client.print(textoCod), y se espera un breve tiempo antes de repetir el bucle loop().


MODULO RECEPTOR

Se incluye la biblioteca ESP8266WiFi, que proporciona las funciones necesarias para trabajar con el módulo ESP8266 y establecer una conexión WiFi.

Se definen las variables ssid y password para configurar el nombre de la red WiFi y la contraseña, respectivamente.

Se define la variable host con la dirección IP del módulo emisor al que se va a conectar.

Se define la constante clave con un valor de 5. Esta variable se utilizará para aplicar un desplazamiento inverso a los caracteres recibidos y así decodificarlos.

FUNCION DECODIFICAR

Se declara la función decodificar que recibe un objeto de tipo String llamado textoCodificado y devuelve un objeto de tipo String con el texto decodificado.

Dentro de la función decodificar, se inicializa textoDecodificado como una cadena vacía.

Se obtiene la longitud del texto codificado utilizando textoCodificado.length() y se guarda en la variable longitud.

Se inicia un bucle for que recorre cada carácter del texto codificado.

En cada iteración, se obtiene el carácter codificado en la posición i utilizando textoCodificado.charAt(i) y se guarda en la variable caracterCodificado.

Se aplica el desplazamiento inverso a caracterCodificado restando la clave de cifrado, y se guarda el resultado en la variable caracterDecodificado.

El carácter decodificado se agrega al texto decodificado utilizando el operador +=, concatenándolo a textoDecodificado.

Una vez terminado el bucle, se retorna textoDecodificado como resultado de la función decodificar.

En la función setup(), se inicializa la comunicación serial a una velocidad de 115200 baudios y se espera un breve tiempo.

Se configura el modo del WiFi en modo estación con WiFi.mode(WIFI_STA).

Se inicia la conexión WiFi utilizando WiFi.begin(ssid, password). El código espera hasta que la conexión sea establecida utilizando un bucle while y se muestra un mensaje en el Monitor Serial indicando el estado de la conexión.

Una vez conectado a la red WiFi, se muestra un mensaje indicando que se ha establecido la conexión.

En la función loop(), se introduce una pausa de 5 segundos con delay(5000).

Se muestra un mensaje en el Monitor Serial indicando que se está intentando conectar al host (módulo emisor) especificado.

Se crea un objeto WiFiClient llamado client.

Si no se puede establecer la conexión con el host utilizando client.connect(host, 80), se muestra un mensaje indicando que la conexión ha fallado y se retorna a la función loop().

Se lee el mensaje recibido desde el host utilizando client.readStringUntil('\r') y se guarda en la variable message.

Se llama a la función decodificar() pasando el mensaje recibido como argumento para obtener el texto decodificado.

Se muestra en el Monitor Serial el mensaje recibido, ya decodificado.


