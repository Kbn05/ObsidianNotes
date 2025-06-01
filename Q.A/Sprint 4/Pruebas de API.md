#Chapter1 

### Arquitectura de la aplicación

Hay tres componentes en la arquitectura cliente-servidor:

- El cliente: la aplicación con la que trabaja el usuario.
- El servidor: el sistema al que acceden los usuarios para obtener los datos.
- La red: el sistema de múltiples dispositivos que ayuda al cliente y al servidor a intercambiar datos.

**API (de Application Programming Interface, interfaz de programación de aplicaciones)** es la interfaz que ayuda a las aplicaciones a interactuar entre sí. A través de la API, intercambian datos mediante solicitudes y respuestas

### Soluciones de arquitectura

#### Características de REST

REST (de Representational State Transfer, transferencia de estado representacional) es una de las formas de diseñar una API. Su característica principal es su **facilidad para la visualización de datos**. En otros estilos de arquitectura, los datos "se envuelven" en una capa adicional de etiquetado. No hay una capa adicional en REST, por lo que queda claro de inmediato a partir de las solicitudes y respuestas lo que le ocurre a los datos.

Por ejemplo, el método POST crea datos y el método DELETE los elimina.

***Códigos de estado existentes:

|Códigos|Descripción|Ejemplo|
|---|---|---|
|1xx|Mensajes informativos|102: la solicitud ha sido recibida, pero aún se está procesando.|
|2xx|Mensajes de éxito|200: OK, la solicitud ha sido procesada con éxito.|
|3xx|Redirección|302: el recurso solicitado está temporalmente disponible en otra dirección.|
|4xx|Errores a nivel de cliente|404: la página solicitada por el usuario no ha sido encontrada en el servidor.|
|5xx|Errores a nivel de servidor|500: error interno del servidor.|

#### Configuración de parámetros

Ya sabes que puedes especificar parámetros de solicitud en la URL. Te permiten especificar exactamente qué datos se deben enviar.

Los parámetros se especifican de la siguiente manera: `key=value` (clave=valor). Se enumeran en la URL después del signo `"?"` y se separan por el signo `"&"` si hay varios parámetros. Por ejemplo, en la solicitud `clothing.com?type=sweatshirt&color=white`, las claves son "type" y "color" y los valores son "sweatshirt" (sudadera) y "white" (blanco).

En la pestaña Body, puedes personalizar exactamente cómo quieres leer la respuesta:

- Pretty (Bonito) te permite ver el cuerpo de la respuesta de una manera fácil de leer: con elementos resaltados e indentado.
- Raw presentará la respuesta "sin procesar": sin indentar y sin elementos resaltados.
- Preview (Vista previa) muestra el resultado. Por ejemplo, si la respuesta es la página de un sitio web, puedes comprobar cómo se ve.
- Visualize (Visualizar) te permite convertir datos en un gráfico o tabla.

Hay otra forma de agregar un parámetro: el botón Bulk Edit (edición masiva). Está en la pestaña Query Params (Parámetros de consulta) a la derecha.

### cURL y generación de solicitudes por consola
#### ¿Qué es cURL?

cURL es una aplicación para gestionar solicitudes HTTP(S). Si tienes macOS o Windows 10, ya la tienes en tu computadora. Si tienes una versión anterior de Windows o Linux, tendrás que instalar cURL. Por ahora, no necesitarás la aplicación en sí, ya que lo harás todo a través de Postman.

cURL funciona con solicitudes HTTP(S) a través de una **consola**.

***Para convertir de curl a postman haz clic en file -> import y pega el comando

### Informe de errores para API

Los campos obligatorios de un informe de errores de una API son ligeramente diferentes a los que has visto con anterioridad:

- En los pasos es necesario escribir el método de solicitud, los parámetros, la URL y el cuerpo de solicitud, si existe.
- En el entorno se debe especificar la dirección del servidor al cual se está enviando la solicitud.
- El resultado esperado debe contener la respuesta descrita o basada en la documentación.
- La respuesta que se haya obtenido debe estar en el resultado actual.

La información adicional y otros parámetros opcionales se especifican según sea necesario.

- Los datos que tuviste que agregar a la base de datos para la prueba.
- Un enlace a la documentación de la API o al menos una selección relevante de esta.
- Una explicación de por qué esto es un error y cuáles podrían ser las consecuencias. Por ejemplo, la API comenzó a devolver un estado adicional. La siguiente API también lo recibe y "se bloquea", lo cual causa errores.

Después de enviar la solicitud, y observar un mensaje de error, necesitas prestar atención a:

- El nivel de registro: `[ERROR]`.
- El mensaje de que ha ocurrido un error: `Unexpected error` (error inesperado).
- La descodificación de la información de error. El contenido de la descodificación difiere entre una aplicación y otra.
    
    - `"stack"`: una lista de paquetes y strings de código de programa que se ejecutaron antes de que ocurriera el error. Esta es información útil para el área de desarrollo, ya que la pueden utilizar para determinar dónde surgió el problema.
	    
    - `"message"`: Mensaje de error: "Unexpected string in JSON at position 16". Dice que se encontró un error de sintaxis en `JSON`al procesar la solicitud: hay un string en la posición 16, pero se esperaba algún otro tipo de datos.
	    
    - `"statusCode"`: estado de error: 400 Bad Request (Solicitud no válida).
        
    - `"body"`: el cuerpo de la solicitud que causó el error.
        
    - `"expose":true` y `"type":"entity.parse.failed"`: son parámetros internos del generador de registros y se agregan de forma automática. Esta información no es necesaria.
        

`\r\n\`, `\n`, `\` se encuentran en la transcripción del error. Estos son caracteres especiales de formato de texto que agregan indentaciones y guiones. Es más conveniente visualizar los registros de esta forma, por ejemplo, con la herramienta [Online JSON Viewer](https://jsonviewer.stack.hu/).
