#Chapter1 

![[checklist-sprint3.png]]

### URL's

![[url-est.png]]

| Elemento                       | Descripción                                                                                                                                                                                                                         | Ejemplos                                                                                                                                                                                                                                      | Es obligatorio |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| Esquema                        | El protocolo que se utiliza para transmitir datos                                                                                                                                                                                   | `http://` `https://`                                                                                                                                                                                                                          | +              |
| Nombre de usuario y contraseña | Información del usuario que solicita datos                                                                                                                                                                                          | `miguel:thebestqa`                                                                                                                                                                                                                            | -              |
| Nombre de host                 | Una dirección única de una aplicación web                                                                                                                                                                                           | `google.com`                                                                                                                                                                                                                                  | +              |
| Puerto                         | Un puerto es un tipo específico de conexión. La mayoría de las veces, no es necesario ingresarlo; el servidor usará automáticamente el puerto correcto.                                                                             | `443`                                                                                                                                                                                                                                         | -              |
| Ruta                           | La dirección de una página concreta en una aplicación web. Está separada por barras `/`.                                                                                                                                            | `/search/:` a página de búsqueda `/profile/:` el perfil de usuario                                                                                                                                                                            | -              |
| Parámetros de solicitud        | Información adicional que se envía al servidor, por ejemplo, para solicitar datos específicos. Se enumera después del signo `?` y está separada por `&`.                                                                            | `https://www.google.com/search?q=figma`: `q=figma` significa que estás buscando la palabra `figma` en Google                                                                                                                                  | -              |
| Ancla                          | Una indicación adicional que te permite acceder directamente a la parte necesaria de una página web, por ejemplo, al título o a un párrafo en particular. Es especialmente útil en páginas extensas que contienen varias secciones. | `https://developer.chrome.com/docs/devtools/network/#overview`: El `#overview` ancla lleva al usuario directamente a la sección "Descripción general" de la página. Es especialmente útil en páginas extensas que contienen varias secciones. |                |

Una solicitud está estructurada según las reglas de transmisión de datos de HTTP. Consta de cuatro partes:

- una línea de inicio;
- encabezados;
- una línea divisoria vacía;
- cuerpo del mensaje.

***Ejemplo:
![[http-structureQuery.png]]

#### Encabezados de solicitud

**Los encabezados de solicitud** representan información adicional que el front-end envía al back-end.

Hay:

- encabezados generales;
- encabezados de solicitud;
- encabezados de entidad.

Mira cómo se ven estos encabezados en este ejemplo:

![[req-header.png]]

**Los encabezados de solicitud** contienen información adicional sobre el cliente:

|Encabezado|Descripción|
|---|---|
|Host|Nombre del dominio del recurso|
|User-agent|Descripción del entorno: el nombre y la versión del navegador, el nombre y la versión del sistema operativo|
|Accept-language|Idiomas admitidos en la respuesta|

**Los encabezados generales** contienen parámetros que se transfieren tanto en solicitudes como en respuestas:

|Encabezado|Descripción|
|---|---|
|Connection|El parámetro que indica el estado de la conexión entre el cliente y el servidor|
|Upgrade-Insecure-Requests|El parámetro indica que el cliente prefiere una respuesta encriptada|

**Los encabezados de entidad** establecen las características del contenido del cuerpo:

|Encabezado|Descripción|
|---|---|
|Content-type|El tipo de datos transmitidos: texto, imagen, audio, video|
|Content-length|Longitud del contenido en bytes|

Este cuerpo de mensaje está en formato `JSON`.

Una solicitud HTTP completa puede tener el siguiente aspecto:

``` JSON
POST /subscribe/ HTTP/1.1
Host: сinemart.com
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.106 Safari/537.36
Accept-Language: en
Connection: keep-alive
Content-type: application/json

{
"surname": "Williams",
"name": "Sam",
"age": 28,
"email": "samw@tripleten.com"
}
```
### Respuestas HTTP

![[http-structureResponse.png]]

#### Línea de estado

**La línea de estado** incluye la versión del protocolo, un código de estado y un mensaje de estado.

Los códigos de estado se dividen en cinco grupos diferentes:

|Códigos|Descripción|Ejemplo|
|---|---|---|
|1xx|Informativo|102: la solicitud ha sido recibida, pero el procesamiento aún está en curso.|
|2xx|Éxito|200: OK, la solicitud ha sido procesada con éxito.|
|3xx|Redirección|302: el recurso solicitado está temporalmente disponible en otra dirección.|
|4xx|Error a nivel de cliente|404: la página solicitada por el usuario no ha sido encontrada en el servidor.|
|5xx|Error a nivel de servidor|500: error interno del servidor.|

#### Encabezados de respuesta

**Los encabezados de respuesta** contienen más información sobre el back-end y el tipo de datos para el front-end.

La estructura de los encabezados es similar a la de una solicitud HTTP:

- Encabezados generales (como para una solicitud HTTP).
- Encabezados de respuesta.
- Encabezados de entidad (como para una solicitud HTTP).

**Los encabezados generales** contienen parámetros que se transmiten tanto en una solicitud como en una respuesta. Ejemplo: "Connection" es el estado de la conexión entre un cliente y un servidor, y "Date" es la fecha de creación de la respuesta del servidor.

**Los encabezados de respuesta** permiten a un servidor transmitir información adicional que no cabe en la línea de estado. Ejemplo: "Server" es el software que utiliza un servidor para gestionar la solicitud y generar la respuesta, y "Location" indica la ubicación exacta de un recurso.

**Los encabezados de entidad** establecen las características del contenido dentro del cuerpo del mensaje. Ejemplo: "Content-Type" es el tipo de datos que contiene la respuesta.

### Visualización de req-res

![[devTools-network.png]]
La imagen muestra el filtro activado por tipo de recurso: `XHR`. También puedes filtrar los recursos por `JS` (scripts), `CSS` (estilos), `Doc` (documentos) e `Img` (imágenes). Generalmente, para analizar interacciones específicas programadas por el área de desarrollo, debes enfocarte en las solicitudes etiquetadas como `fetch` en la columna `Type`.

La pestaña "Red" en las herramientas de desarrollo despliega información detallada acerca de los recursos intercambiados entre el front-end y el back-end:

- Los nombres de los recursos transmitidos a través de la red por el front-end y el back-end (la columna "Name").
- El tiempo de carga (columna "Time").
- El tamaño de los archivos (columna "Size").
- La información adicional sobre las solicitudes al servidor, por ejemplo, el volumen de tráfico.

### Anulación de respuestas

#### ¿Por qué cambiar la respuesta del servidor?

- **Comprender cómo funciona una aplicación:** Al anular las respuestas, puedes observar la conexión entre las acciones del usuario y las solicitudes que se envían. Esto puede resultar útil cuando a la documentación del proyecto le falta información sobre la aplicación y tienes que encontrarla por tu cuenta.
- **Detectar errores:** Al ver las solicitudes y respuestas sin procesar, puedes intentar identificar dónde se produce un error. A su vez, estas solicitudes y respuestas se pueden adjuntar al informe de errores para que el área de desarrollo pueda corregir el error antes.
- **Probar el lado del cliente y el lado del servidor por separado:** Por ejemplo, cuando el lado del cliente ha finalizado un proceso, pero el código de back-end aún está en progreso, puedes ajustar la respuesta del servidor para pruebas determinadas.

#### Cómo cambiar la respuesta del servidor

Para cambiar la respuesta del servidor, normalmente necesitarás un proxy como Fiddler, Charles, Burp o Requestly. Dado que cambiar la respuesta del servidor es tan útil, DevTools también agregó esta función. La primera vez que hagas esto, deberás configurar DevTools.

#### Configurar una carpeta de anulaciones

Las respuestas suelen provenir del servidor. Pero cuando las anulamos, provienen de nuestra computadora. Necesitamos hacer dos cosas:

1. Configurar una carpeta para almacenar nuestras anulaciones.
2. Dar permiso a Chrome para acceder a esa carpeta.

Solo necesitarás seguir estos pasos una vez, a menos que luego decidas eliminar la carpeta o quieras agregar otra carpeta diferente.

1. Accede al panel de Fuentes en DevTools. Busca la pestaña Anulaciones. Si no la ves, puede que tengas que hacer clic en la doble flecha a un lado. ⏩
2. Haz clic en "➕ Seleccionar carpeta para anulaciones".
3. Aparecerá una ventana de selección de carpetas. Esta es la carpeta donde guardarás tus archivos editados. Puedes elegir cualquier nombre y colocar la carpeta en cualquier lugar, pero elegimos "Anulaciones QA" y la colocamos en nuestro escritorio. Te sugerimos hacer lo mismo.
4. Se te pedirá que permitas que DevTools acceda a esta carpeta. Haz clic en "Permitir".
5. Ahora verás la carpeta "Anulaciones QA". También hay una casilla de verificación que activa o desactiva las anulaciones. ¡Déjala seleccionada y lo tendrás todo listo para continuar!

### Cookies

**Las cookies** son los datos que se almacenan en el dispositivo del usuario. El servidor genera los datos, que se almacenan en su computadora o smartphone. Cuando el usuario vuelve a abrir la aplicación, el servidor recibe de nuevo los datos.

Las cookies pueden almacenar diferentes datos:

1. **Datos para la autenticación**. Por ejemplo, inicias sesión en una aplicación web, luego cierras la pestaña y, después de un tiempo, vuelves a abrir la aplicación. No tendrás que ingresar tu nombre de usuario y contraseña una vez más, ya que los datos del estado de autorización se almacenan en cookies.
2. **Datos de usuario**. Por ejemplo, información sobre hoteles, geolocalización, idioma y moneda que el usuario ha utilizado para sus consultas.
3. **Datos para recopilar estadísticas**. Por ejemplo, estadísticas sobre el dispositivo o las páginas visitadas por el usuario. Basándose en las estadísticas, el equipo de desarrollo de la aplicación saca conclusiones y toma decisiones sobre cómo funciona una funcionalidad concreta.

### LocalStorage

El **almacenamiento local (Local Storage)** consiste de datos almacenados en el navegador. Es diferente de las cookies, porque los datos del almacenamiento local no se transfieren al servidor, y solo los emplea el lado del cliente de la aplicación.

#### Cómo borrar datos del almacenamiento local

Ahora imagina que tienes que probar la aplicación en un nuevo usuario. El usuario no tiene la tarifa y los requisitos seleccionados, por lo que debes eliminar todos los datos de almacenamiento local:

1. Abre DevTools → busca la lista desplegable "Almacenamiento local" → haz clic con el botón derecho en la URL de la aplicación.
2. Haz clic en "Borrar".

### Memoria cache

La memoria **caché** (almacenamiento en caché) son los datos de una página web. Cuando abres imágenes, audio, videos o páginas web, se almacenan en tu dispositivo.

Las cookies y el almacenamiento local facilitan el uso de la aplicación. El usuario no necesita ingresar los mismos datos cada vez, por ejemplo, el nombre de usuario, la contraseña y el número de teléfono.

La memoria caché del navegador tiene otro propósito. Cuando abres una página web de nuevo, se cargará más rápido porque el navegador tomará los archivos del almacenamiento en caché y no del servidor.

A veces, la causa de los errores está en la memoria caché. Imagina que encuentras un error y creas un ticket en el rastreador de errores. El área de desarrollo corrige el error y devuelve el problema para probarlo. Ahora debes asegurarte de que todo funcione bien. Pruebas la aplicación de nuevo, pero nada cambia. El error aún ocurre, pero el área de desarrollo afirma haberlo corregido.

Lo más probable es que los datos simplemente se almacenaron en la memoria caché de tu navegador. Es por eso que ves la versión anterior de la página desde tu computadora y no la nueva versión desde el servidor. Para solucionar el problema, tienes que borrar la memoria caché.

#Chapter2 

### Elementos de una interfaz

#### Elementos generales

Los elementos generales de una interfaz son el menú principal, el menú contextual y la barra de desplazamiento. Prácticamente todas las aplicaciones web los tienen.

1. **El menú principal** es el elemento clave de la interfaz de usuario de una aplicación web que te permite navegar entre sus secciones.
2. El **menú contextual**, o **menú emergente**, es el menú de acciones disponible para el elemento seleccionado.
3. **La barra de desplazamiento** es un elemento que mueve la parte visible de la ventana hacia arriba y abajo, o hacia la izquierda y derecha.
4. **Encabezados y pies de página**. Estos elementos suelen contener información importante, como el logotipo de la empresa, información de contacto y enlaces.
5. **Herramientas de búsqueda**. Las barras y herramientas de búsqueda ayudan a los usuarios a encontrar contenido específico.
#### Elementos de acción

Los elementos de acción le permiten al usuario ejecutar acciones. Estos incluyen íconos, botones y enlaces.

1. **Un ícono** es una imagen pequeña que ilustra una acción. Al hacer clic sobre ella, esta inicia tal acción. Por ejemplo, si haces clic en el ícono de enlace en una página de Wikipedia, puedes ir a la página vinculada.
2. **Un botón** es un elemento que contiene texto. Al hacer clic en él, se ejecuta una acción específica. Por ejemplo, navegar hacia la página de un producto específico.
3. **Un enlace** es un elemento de conexión de una aplicación web, el cual puede hacer referencia a un elemento, como una imagen o un bloque de texto en una página web, o a un objeto, ya sea un archivo, una carpeta u otra página web.
#### Elementos auxiliares

Los elementos auxiliares le dan al usuario una sugerencia acerca de la función que realizan otros elementos de una página web. Estos incluyen etiquetas, sugerencias emergentes y marcadores de posición.

1. Una **etiqueta** explica elementos (p. ej. las opciones en un cuestionario).
2. Una **sugerencia emergente** es un texto que explica un elemento al pasar el cursor sobre él.
3. **Un marcador de posición** es una sugerencia dentro de un formulario que muestra la información que debes ingresar.

#Chapter3 
### Pruebas de formularios y validaciones 

Primero se hacen las pruebas positivas y luego las negativas.

Para comenzar, el equipo de testers ingresa datos válidos que se establecen en los requisitos. Debes asegurarte de que, en este caso, la aplicación realice sus funciones principales.

Por ejemplo, los campos "Nombre de usuario" y "Contraseña" del formulario de registro aceptan solo caracteres del alfabeto latino, números, un guion y un punto.

El registro debe ser exitoso si ingresas el nombre de usuario disponible `anna-qa-engineer` y la contraseña `anna.password123`, así como si llenaste el resto de los campos correctamente.

Cuando ejecutes pruebas negativas, asegúrate de que la aplicación no se detenga. Lo ideal sería que genere un mensaje de error.

Si introduces datos no válidos, como caracteres no permitidos, en cualquier campo del formulario, aparecerá un mensaje de error. Esto significa que los datos en el formulario no pasaron la validación.

#### Validación

La **validación** es un mecanismo que comprueba la exactitud de la entrada de datos por parte de un usuario.

Si la validación es exitosa, la aplicación funcionará correctamente; de lo contrario, el usuario verá un mensaje en el que se indica que los datos del campo no son válidos.

#Chapter4 

### Pruebas multiplataforma

Los usuarios pueden acceder a una aplicación desde diferentes dispositivos y navegadores, por lo que esta puede comportarse diferente en, digamos, una computadora portátil con Windows y Google Chrome que en un iPhone con Safari. Para probar todas estas diferentes combinaciones necesitarás efectuar pruebas **multiplataforma** y **entre navegadores**.

#### Plataformas

El usuario puede usar aplicaciones en una computadora portátil, un teléfono inteligente o una tableta. Estas son **plataformas**, es decir, dispositivos que son necesarios para trabajar con aplicaciones.

Existen dos tipos de plataformas:

- **Escritorio**: computadoras de escritorio y portátiles.
- **Móviles**: teléfonos inteligentes y tabletas.

El área de desarrollo adapta una misma aplicación a varias plataformas creando versiones de escritorio y móviles, lo que facilita el uso del servicio tanto en pantallas pequeñas como grandes.

Las versiones móviles y de escritorio se prueban por separado. Puede ocurrir que la versión de escritorio coincida con los diseños y los requisitos, pero la versión móvil no: los botones, las sugerencias y otros elementos aparecen en los lugares equivocados.

#### Sistemas operativos

El usuario se comunica con un dispositivo a través de un conjunto de programas, algunos de los cuales manejan las señales del teclado y el mouse y otros permiten crear y eliminar archivos.

El conjunto de programas para la comunicación entre el dispositivo y la persona que lo usa se denomina **sistema operativo**, abreviado como **SO**. Algunos ejemplos de sistemas operativos son Windows, Android y macOS.

Tienes que probar las aplicaciones que se ejecutan en diferentes sistemas operativos por separado. Si la versión de iOS de una aplicación cumple con los requisitos y diseños, la versión de Android podría presentar problemas. Por ejemplo, el diseño, los botones y la ubicación de los elementos pueden diferir.

Tienes que probar diferentes combinaciones de plataformas y sistemas operativos. En un caso una aplicación podría funcionar sin problemas, mientras que en otro podría presentar errores.

Por ejemplo, alguien del equipo de testers se aseguró de que en una computadora portátil con Windows la aplicación funciona como se describe en los requisitos y los diseños. A continuación, abre la misma aplicación en un teléfono con Windows y observa que el diseño no coincide con los diseños y que es inconveniente usar los botones.

Para garantizar que una aplicación se ajuste a los requisitos y diseños de cualquier plataforma y sistema operativo, se ejecutan **pruebas multiplataforma**. Prueban que:

- La interfaz de usuario coincida con el diseño.
- La funcionalidad coincida con lo establecido en los requisitos.

### ¿Cómo seleccionar el S.O para probar la aplicación?

***1. Consultar los requisitos 

Los requisitos para una aplicación suelen establecer un conjunto de sistemas operativos para dispositivos de escritorio y móviles. Si es así, estos son los sistemas que tienes que probar.

Por ejemplo, los requisitos para Urban Routes indican estos SOs: las versiones de escritorio de Windows y macOS y las móviles de Android y iOS.

***2. Preguntar a la gerencia

A veces no hay ninguna descripción de los SOs en los requisitos, en cuyo caso puedes preguntar al gerente de proyectos cuáles de ellos soportan la aplicación para probarlos.

***3. Consulta las estadísticas generales de un SO

A veces no hay estadísticas locales para una aplicación, por ejemplo, cuando un servicio está en sus primeras etapas. En este caso, puedes consultar las estadísticas generales sobre los sistemas operativos en el país para el que se desarrolla la aplicación.

En el sitio web [https://gs.statcounter.com/](https://gs.statcounter.com/), por ejemplo.

### Pruebas entre navegadores

Debes probar la **compatibilidad entre navegadores**, es decir, la capacidad de una aplicación para funcionar de la misma manera en diferentes navegadores. Ejecutar **una prueba entre navegadores** significa asegurarse de que en diferentes navegadores la ubicación, el color y la forma de los elementos, así como el texto de la interfaz coincidan con el diseño.

#### Cuándo realizar pruebas entre navegadores

Los cambios en una aplicación pueden deberse a:

- La lógica del funcionamiento
- El diseño

Debes ejecutar una prueba entre navegadores si se realizaron algunos cambios en el **diseño**.

Si solo se agregó o modificó la lógica de la aplicación, no necesitas probar la compatibilidad entre navegadores. Solo debes probar una función nueva o modificada en un navegador.

La siguiente tabla te ayudará a recordar cuándo debes efectuar una prueba entre navegadores:

|Cambio|Dónde probar|
|---|---|
|Diseño|En todos los navegadores soportados|
|Lógica|En un navegador soportado|
|Lógica y diseño|La lógica: en uno de los navegadores soportados — El diseño: en todos los navegadores soportados|

### Seleccionar navegadores para pruebas

`Para ahorrar recursos, pueden probar solo los navegadores compatibles o los más populares.`

Puedes probar navegadores de la misma manera que los sistemas operativos

#### Elegir navegadores en función de su popularidad

Imagina que tienes que probar una aplicación de escritorio para Windows desarrollada para el mercado internacional.

Para comprobar la compatibilidad entre navegadores, es necesario saber qué navegadores son populares en todo el mundo. Puedes utilizar [https://gs.statcounter.com/](http://gs.statcounter.com/)

#### Elegir navegadores en función de su motor

Puede haber muchos navegadores populares. Para ahorrar tiempo en las pruebas entre navegadores, puedes elegir navegadores según la popularidad de su **motor**.

**Un motor de navegación** es un programa dentro de un navegador que ayuda a visualizar páginas web y sus elementos.

Algunos navegadores usan el mismo motor. Significa que su lógica de visualización es similar. Por ejemplo, Google Chrome, Opera y Microsoft Edge utilizan el mismo motor. Para cada motor, puedes elegir el navegador más popular y realizar pruebas solo en él.

|Motor|Navegadores|
|---|---|
|Blink|Google Chrome, Opera 15+, Microsoft Edge 79+|
|WebKit|Apple Safari, Google Chrome for iOS|
|Gecko|Mozilla Firefox|

### Versiones de navegador

Al igual que los sistemas operativos, los navegadores tienen versiones. Los elementos de la interfaz pueden funcionar de manera diferente o mostrarse de forma diferente en diferentes versiones de un navegador.

Si cuentas con las estadísticas de la aplicación, puedes consultarlas y ver qué versiones de los navegadores son las más populares y probarlas.

Si no hay tales estadísticas, puedes probar la última versión. Por lo general es la más popular y la mayoría de usuarios tienen activada la actualización automática. Puedes descargar la última versión de un navegador en el sitio web oficial.

#Chapter5 

### Pruebas de diseño web responsive

**Las aplicaciones adaptativas** son aplicaciones capaces de cambiar entre diferentes tamaños de pantalla.

**La resolución de la pantalla** es el tamaño de una imagen en una pantalla en `píxeles`.

Hay dos enfoques para garantizar que el diseño se adapte a diferentes tamaños de pantalla: **diseño adaptativo** y **diseño responsivo**. Ambas opciones a menudo se denominan "adaptativas".
#### Diseño adaptativo

La aplicación utiliza **breakpoints** específicos (lo que significa "puntos de ruptura", "puntos de inflexión") para ajustarse al tamaño de la pantalla:

1. El área de diseño define los breakpoints en el diseño.
2. El área de desarrollo los agrega al código.
3. Cuando el ancho de la pantalla alcanza esos "puntos", el diseño se "rompe" (se transforma para ajustarse al nuevo ancho).

Por ejemplo, el área de diseño definió los breakpoints siguientes:

- 320 píxeles: para smartphones,
    
- 960 píxeles: para tabletas,
    
- 1200 píxeles: para navegadores de escritorio.
    

Si la ventana del navegador se reduce a 960 píxeles, el diseño cambia a tableta, y si se reduce a 320 píxeles, a móvil.

Cuando alguien visita un sitio web adaptativo, el servidor determina el dispositivo y responde con el diseño requerido: escritorio, tableta o smartphone.

### Diseño responsivo

Mientras que el diseño adaptativo tiene breakpoints, el diseño responsivo se adapta al ancho de la pantalla en cualquier punto. Este diseño, también conocido como diseño fluido, se extiende en todas las direcciones sin saltos bruscos de la imagen.

Las proporciones y tamaños de los elementos en un diseño responsivo se dan en porcentajes, no en píxeles. Como resultado, todos los componentes se "estiran" suavemente en función de la resolución de la pantalla. Es por eso que este diseño se llama fluido.

### Herramientas para probar la versión móvil de un sitio web

Hay dos formas de probar una aplicación móvil:

- En un dispositivo móvil real: las empresas suelen tener dispositivos de prueba.
- En una computadora de escritorio: en Toggle Device Toolbar, que está integrada en DevTools.

#### Pruebas en dispositivos móviles reales

En dispositivos reales, realizas las siguientes pruebas:

- **Compatibilidad multiplataforma y entre navegadores**: la aplicación web debe funcionar y visualizarse correctamente en todos los sistemas operativos y navegadores móviles soportados.
- **El teclado en pantalla**: debes asegurarte de que el diseño no se desplace cuando aparece el teclado.
- **Gestos que no pueden efectuarse en una computadora**: por ejemplo, pellizcar con dos dedos para alejar una imagen.

#### Pruebas con DevTools

En DevTools, solo puedes probar algunas funciones de la aplicación móvil:

- Cómo el diseño de la aplicación web se ajusta a diferentes tamaños de pantalla.
- Cómo se comporta el diseño cuando cambia la orientación de la pantalla.
- Algunos gestos, por ejemplo, el gesto de deslizar.

Comprueba qué gestos puedes probar en DevTools:

![[devTools-mobile.png]]

Aprende a elegir la resolución de pantalla:

1. Consulta los requisitos y diseños: si se indican las resoluciones compatibles para la aplicación, prueba solo esas.
2. Si las resoluciones no se indican, consulta a tu gerente de proyecto. El equipo a menudo acuerda de antemano qué resoluciones utilizar para las pruebas para cubrir pantallas tanto grandes como pequeñas.
3. Si no hay acuerdo, intenta consultar las estadísticas locales. Te dirán qué resoluciones de dispositivos reciben mucho tráfico de personas que usan la aplicación.
4. Si no tienes estadísticas de la aplicación, busca las estadísticas generales sobre resoluciones para saber qué resoluciones son las más populares. Sigue el enlace para ver un ejemplo de estas estadísticas: [https://gs.statcounter.com/screen-resolution-stats](https://gs.statcounter.com/screen-resolution-stats)

#### Matriz de compatibilidad

Sin embargo, no es necesario probar 38 combinaciones para cubrir todas las variables de entorno. Puedes utilizar la matriz de compatibilidad de navegadores.

**La matriz de compatibilidad de navegadores** es una tabla en la que las filas contienen los requisitos de los sistemas operativos y las columnas contienen los de los navegadores.

#### Pasos para crear una matriz de navegadores

Puedes utilizar este algoritmo:

1. Relaciona cada navegador con un SO de escritorio y móvil uno por uno. Por ejemplo, para el navegador Chrome puedes seleccionar Windows 10 y Android 12, Windows 11 y Android 11 para Firefox, y así sucesivamente.
2. No olvides que algunos navegadores no son compatibles con algunos sistemas operativos.
3. Tendrás una tabla que te sugerimos utilizar para verificar cada SO y navegador al menos una vez.
4. Marca en azul la intersección entre un SO y un navegador. Estas celdas corresponden a los entornos compatibles.
5. Llena las resoluciones soportadas en las celdas azules si puedes comprobarlas. Las resoluciones se pueden comprobar en dispositivos reales o en DevTools.
