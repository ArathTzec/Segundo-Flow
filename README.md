# Segundo Flow
Este repositorio contiene el segundo ejercicio en Node Red, el cual consiste en enviar información cada segundo.

## Material necesario
Para poder realizar necesario es necesario tener instalado:
- [Node.js](https://github.com/nodesource/distributions/blob/master/README.md) Usar la versión LTS v16x e instalar los build tools.
- [Node-Red](https://nodered.org/docs/getting-started/local)

## Instrucciones

**No olvides primero abrir node red desde la terminal con node-red**

Da clic en el menú, ubicado en el botón de hamburguesa en la esquina superior derecha de la interfaz de Node-Red. Ahora da clic en Importar y después en Clipboard. Verás un cuadro de dialogo como el siguiente, pega el código json que respaldaste en la lección anterior.

Haz clic en la opción new flow, lo que abrirá una pestaña nueva y colocará ahí los nodos importados. Ahora haz clic en Importar.

>Nota que la pestaña nueva tiene el mismo nombre que la anterior. Haz doble clic en el nombre de la pestaña y cambia su nombre a Segundo Flow.

Cambia la configuración del nodo inject para que el payload sea un timestamp que se repita cada 15 segundos:
Agrega un nodo function y conecta la salida de inject a la entrada de function y la salida de function a la entrada de debug.

Ahora copia el siguiente código y pégalo en el cuadro de texto de las propiedades del nodo function. Éste código toma el mensaje enviado por el nodo inject en formato UNIX y lo convierte a un formato legible.


// Lo que está después de “//” son comentarios
// Crea un objeto Date a partir del payload enviado por timestamp
var date = new Date(msg.payload);
// Cambia el payload para que sea una fecha con formato
msg.payload = date.toString();
// Regresa el mensaje para que se envíe al sigueinte nodo
return msg;

Si corres tu programa dando clic en Deploy; verás que cada 15 segundos da la fecha y hora en un lenguaje legible.

## Resultados
Una vez completados los pasos anteriores se deberá ver una ventana que cada segundo se estará actualizando, como se ve en [Pantalla_Node-Red.png](https://github.com/ArathTzec/Segundo-Flow/blob/main/Pantalla_Node-Red.png)
