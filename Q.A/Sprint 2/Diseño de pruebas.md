#Chapter1 

![[checklist-sprint2.png]]

Los requisitos de la aplicación describen sus principales características y funcionalidades. Estos son cruciales en pruebas, pues permiten comprender el resultado esperado.

### Análisis de requisitos: identificación de los objetos de prueba

El primer paso será identificar los objetos de prueba de estos requisitos. Esto significa definir lo que necesitarás para hacer pruebas, lo cual te ayudará durante las siguientes etapas del análisis de requisitos.

#### Objetos de prueba 

Los **objetos de prueba** son partes de la aplicación que necesitan probarse. Estos objetos se identifican durante el análisis de requisitos.

**Requisitos de funcionalidad**

Se describe cómo debería funcionar la aplicación. Con base en estos requisitos y diseños, el área de desarrollo escribe código y el equipo de QA engineers diseña las pruebas.

### Descomposición de requisitos

Para analizar los requisitos correctamente, hay que seguir los siguientes pasos:

1. **Descomponer:** hay que descomponer cada requisito en bloques atómicos. 
2. **Visualizar**: consiste en crear gráficos o diagramas sencillos (mapas mentales y diagramas de flujo) para entender cómo encajan los bloques atómicos.
3. **Buscar zonas grises**: consiste en buscar escenarios que los requisitos quizá no mencionen de forma explícita.

#### Cómo descomponer los requisitos

Para descomponer los requisitos puedes seguir estas tres sencillas reglas:

1. Con frecuencia, los requisitos pueden descomponerse en varias partes.

***Ejemplo***: El formulario de selección de direcciones de Urban Routes tiene dos campos de entrada: "Desde" y "Hasta". Estas son las partes más pequeñas en que puedes descomponer el requisito del formulario de selección de una sola dirección. 

2. Los requisitos deben descomponerse en bloques atómicos.

***Ejemplo***: Puedes descomponer las restricciones de entrada del campo "Desde" así:

- Entrada: letras del alfabeto latino
- Entrada: números
- Entrada: espacios
- Entrada: guiones
- Entrada: puntos
- Entrada: comas
- Entrada: de 1 a 50 caracteres

Este es el nivel atómico, lo que significa que no puedes descomponer más este requisito.

2. Los requisitos no deben descomponerse más allá de la descripción.

***Ejemplo***: Si los requisitos del campo "Desde" no mencionan mayúsculas ni minúsculas, será suficiente con verificar cualquier carácter del alfabeto latino. No será necesario que descompongas en mayúsculas ni minúsculas.

***Ejemplo descomposición de requisitos

![[requ-urban-routes.png]]

### Visualización de requisitos: mapa mental

Después de la descomposición, el siguiente paso es visualizar los requisitos. Un diagrama ilustrativo te ayudará a estructurar y comprender la información de los requisitos con mayor facilidad.

#### Cómo dibujar un mapa mental

Tu tarea es dividir progresivamente los requisitos en los elementos que mejor describan a las funciones.

Recuerda la lección anterior, cuando primero identificaste grandes secciones para bosquejar la estructura y luego descompusiste estas secciones aún más. Necesitas hacer lo mismo con la visualización: primero pon en el mapa partes grandes de los requisitos y luego descompón cada una hasta el nivel atómico.

![[mind-map.png]]

### Diagrama de flujo

Mientras que un mapa mental muestra lo que hay en una aplicación, un diagrama de flujo describe cómo funciona la aplicación.

Un **diagrama de flujo** muestra el orden de los pasos que hay que seguir para resolver una tarea específica en una aplicación.

#### Representaciones

Un rectángulo redondeado representa el inicio y el final de un diagrama de flujo.

Un rectángulo ordinario representa una acción. Por ejemplo, "Detenerse".

Un rombo representa una condición, esto significa que el proceso continuará en una rama que coincida con el resultado. Por ejemplo:

- ¿Se muestra la señal para caminar?
- ¿Se cumple la condición?
- ¿El valor es correcto?

![[flow-chart.png]]

### Zonas grises y búsqueda de requisitos

Cuando la información en los requisitos no es suficiente para comprender por completo determinada funcionalidad, aparecen **zonas grises**.

***Tipos de zonas grises

- **Requisitos no especificados o incompletos.** Con frecuencia, los notarás solo después de haber leído los requisitos dos o tres veces. Por ejemplo, ¿cómo debería responder el sistema si ingresamos la misma dirección en los campos "Desde" y "Hasta"? ¿Debería mostrarse un mensaje de error? ¿O debería generarse una ruta?
- **Requisitos implícitos.** Con frecuencia, quienes escriben la documentación excluyen los requisitos que consideran obvios. Por ejemplo, se debe poder hacer clic en el logotipo de Urban Routes en la esquina superior izquierda. Al hacer clic en él, se debería abrir la página principal de la aplicación de Routes.
- **Los diseños y los requisitos no coinciden.** Por ejemplo, los diseños de Routes contienen los tipos de transporte en el siguiente orden: automóvil personal, a pie, taxi, bicicleta, scooter y automóvil compartido. Pero en los requisitos se especifica el siguiente orden: automóvil personal, automóvil compartido, taxi, scooter, bicicleta y a pie.
- **Faltan requisitos.** Esto también sucede. Por ejemplo, los requisitos para Routes no describen la funcionalidad de algunos elementos en el mapa. Por ejemplo, los botones Mapa/Satélite están en los diseños, pero no se describe cómo deberían funcionar.

#### ¿Qué debes hacer cuando encuentras zonas grises?

1. **Sigue intentando.** Digamos que haces clic en un botón de la interfaz de Urban Routes y, dado que los requisitos no son claros, no sabes con seguridad qué pasará después. Puedes intentar diferentes escenarios, como volver a cargar la página. ¡No dudes en probar métodos al azar!
2. **Revisa escenarios de pruebas similares.** Examina casos de pruebas similares para ver si hay alguna pista. ¡No olvides revisarlos todos para dominar la asignación! La solución que hayas encontrado para una zona gris puede volver a serte útil más adelante.
3. **Aclara los requisitos.** Una vez que hayas identificado las zonas grises, es esencial preguntarles a las personas adecuadas para aclararlas. Recuerda: ¡La comunicación es clave! Aunque dependiendo del proyecto o la empresa esto puede variar, idealmente deberías preguntarle a la gerencia o al equipo de analistas. Pregúntales acerca del concepto de la aplicación y las expectativas del usuario, e infórmales cualquier zona gris. Te darán una respuesta o podrás consultarlo con el cliente. Puede que incluso actualicen los requisitos.

Consejos:

- Trata de imaginar cómo debería funcionar la aplicación.
- Ponte en el lugar del usuario: ¿Está todo claro y es práctico?
- Hazte preguntas: ¿qué propósito tiene una prueba específica?, ¿cómo funciona?, ¿con qué otros elementos está relacionada?
- Elabora un plan de pruebas y piensa qué tipo de pruebas se necesitan para esa función. Esto hará que los requisitos necesarios sean más claros.

### Pruebas funcionales y no funcionales

Una **prueba funcional** tiene como objetivo comprobar la funcionalidad de un producto de software. En esencia, cada QA engineer debe asegurarse de que todo funcione como se describe en los requisitos.

Una prueba funcional podría analizar estos aspectos:

- **La** **lógica de un sistema**: por ejemplo, probar la lógica que determina cómo se calcula el precio de un viaje.
- **La interacción del usuario con un servicio**: por ejemplo, cómo cambia la escala de un mapa cuando haces clic en él.
- **La visualización de datos**: por ejemplo, cómo se le muestra la información de un viaje al usuario.

Un **requisito funcional** podría ser algo así: "al completarse el campo 'Hasta' y hacer clic en el botón 'Enviar', la aplicación debe enviar un correo electrónico a la dirección indicada". Este requisito describe lo que la aplicación debe ser capaz de realizar. En otras palabras, describe su funcionalidad.

Una **prueba no funcional** verifica las características de un sistema. La documentación del producto también suele contener los **requisitos no funcionales**, que se refieren a aquellas características del producto que no afectan de forma directa su funcionalidad.

Digamos que decidimos actualizar nuestra aplicación Urban Routes con una nueva función: un botón para cambiar de idioma, de tal forma que la aplicación sea más fácil de usar en diferentes países. A continuación se indican los requisitos de esta nueva función:

***"Se debe agregar un botón para cambiar de idioma en la esquina superior derecha de Urban Routes. Debe ser un menú desplegable con los siguientes idiomas: inglés, español y portugués. El inglés está seleccionado por defecto. Una vez que el usuario selecciona un idioma del menú desplegable, la interfaz de la aplicación se traduce al idioma elegido".

Para verificar que la aplicación cumple estos requisitos, necesitamos comprobar lo siguiente:

- Si la aplicación cambia al idioma seleccionado (prueba funcional).
- Si todos los elementos están traducidos al idioma seleccionado (prueba no funcional).

Los principales tipos de pruebas no funcionales son las **pruebas de seguridad** y las **pruebas de rendimiento**.

Algunos proyectos también requieren de **pruebas de usabilidad** y **pruebas de localización**. Respectivamente, estas pruebas determinan si es fácil interactuar con el software y si el texto se tradujo de forma correcta.

#Chapter2 

### Diseño de pruebas

El diseño de pruebas consiste en crear **`casos de prueba`**. Cuando analizas requisitos, te preguntas "¿Qué debo probar?". Cuando creas casos de prueba, te preguntas "**¿Cómo hago la prueba?**".

¿Por qué son necesarios los casos de prueba? Es para asegurarnos de que el software se pruebe minuciosamente. Sin los casos de pruebas, las pruebas serán al azar y podríamos correr el riesgo de ignorar pasos y escenarios importantes. Los casos de prueba garantizan que se examinen todos los aspectos del software y que las pruebas se realicen de forma sistemática.

#### Reglas para el diseño de pruebas

Hay 5 reglas para el buen diseño de pruebas:

* **Podrías necesitar varios casos de prueba para verificar un requisito**
Por ejemplo, según un requisito, "el mapa de Urban Routes es escalable". Puedes probar esta funcionalidad de diferentes maneras:

- con los botones "+" y "-" en la interfaz;
- con la rueda de un mouse o un panel táctil;
- con gestos en dispositivos móviles.
* **Un caso de prueba equivale a una prueba.** 
Si pruebas el escalado del mapa de Urban Routes, sería conveniente crear dos casos de prueba: uno para el botón "+" y otro para el botón "-". Si se combinan ambas pruebas en un solo caso y uno de los botones tiene un bug, no sabrás cuál es el responsable.

* **Las pruebas no deben duplicar la funcionalidad.** 
Supongamos que ya probaste el botón "+" en el caso de prueba "Escalado del mapa Urban Routes". Esto significa que no necesitas un caso de prueba para "Visualización del botón '+' en la interfaz". Obviamente, el botón aparece.

* **Diseña tus pruebas dentro de los requisitos.** 
Si en los requisitos no se describe cómo funcionará un smartphone a -120 °C, no escribas un caso de prueba en el que necesites sumergir el dispositivo en nitrógeno líquido.

* **Las pruebas deben cubrir todos los requisitos.** 
Debes asegurarte de que todos los casos de prueba comprueben todas las funciones.

### Pruebas positivas y negativas

#### Casos de prueba positivos

Un **caso de prueba positivo** verifica que una aplicación funcione de manera correcta **de acuerdo con un requisito particular y cuando se usen datos** válidos.

Por ejemplo, los requisitos indican que los campos "Desde" y "Hasta" pueden contener entre 1 y 50 caracteres. Si un usuario ingresa una dirección entre 1 y 50 caracteres, no habrá ningún error.

Más ejemplos:

- Un microondas tiene una función de grill. Una prueba positiva es comprobar si puedes activar esta función y que funciona correctamente.
- Una calculadora debe ser capaz de sumar dos números. Una prueba positiva sería comprobar que la suma es correcta.

#### Casos de prueba negativos

Los **casos de prueba negativos** verifican que la aplicación responda con éxito cuando se usa de manera incorrecta o cuando se utiliza un dato no válido. La aplicación debe lograr manejar con éxito un error para responder frente a un comportamiento inesperado del usuario.

Por ejemplo, no puedes dividir entre cero. En una calculadora, una prueba negativa sería comprobar que el sistema reaccione si intentas dividir entre cero.

Otro ejemplo:

Los requisitos indican que los campos "Desde" y "Hasta" solo pueden contener letras del alfabeto latino, números, espacios, guiones, puntos y comas. Si un usuario ingresa la dirección "East 2nd Street / 601", la aplicación no deja de funcionar, pero aparece el mensaje "Introduce una dirección".

***Consejo: Primero, realiza las pruebas positivas. Son más importantes, ya que prueban que los requisitos estén correctamente implementados.

***Ejemplo***
#### Los requisitos para un nuevo servicio de correo electrónico

**Escenario de redacción de correos electrónicos**

Campos: Para, CC, Asunto, Cuerpo principal.

- En los campos "Para" y "CC" se introduce una dirección de correo electrónico.
- En el campo "Asunto" se indica el tema del correo electrónico.
- El "Cuerpo principal" es donde se escribe el texto del mensaje.
- Los campos "Para" y "Asunto" son obligatorios.

**Escenario de gestión del correo electrónico**

Acciones: marcar como no leído, marcar como no deseado, eliminar.

- Puedes marcar un correo electrónico como leído en cualquier carpeta.
- Si marcas un correo electrónico como no deseado, aparecerá en la carpeta "Correo no deseado". Puedes marcar un correo electrónico como no deseado en cualquier carpeta excepto en la de "Correo no deseado".
- Un correo electrónico eliminado va a la papelera. Puedes eliminar un correo electrónico desde cualquier lugar, excepto la papelera.

### Partición de clases de equivalencia

Una de las técnicas fundamentales del diseño de pruebas que nos permite agrupar los datos de nuestras pruebas (realizar una partición), lo que reduce la cantidad de pruebas necesarias sin disminuir su eficacia.

#### ¿Qué es la equivalencia?

La **equivalencia** es la igualdad de los objetos. En las pruebas, los valores equivalentes son aquellos que una aplicación procesa de la misma manera.

Por ejemplo, según [los requisitos](https://practicum-content.s3.us-west-1.amazonaws.com/new-markets/qa-sprint-1/esp/v2/Requisitos_para_Urban_Routes.pdf) de los campos de dirección en Urban Routes, "La longitud aceptada es de 1 a 50 caracteres".

Esto quiere decir que la aplicación procesa los valores de 1 a 50 caracteres de longitud de la misma manera. Los valores con longitudes mayores que 50 caracteres se procesan diferente, por ejemplo, mediante un mensaje de error.

El equipo de testers combina estos valores en **clases de equivalencia**. Se explica con la siguiente imagen:

![[data-eq.png]]

Por lo tanto, ¿qué vemos cuando realizamos pruebas? En lugar de realizar muchas pruebas para cada grupo, puedes realizar la prueba con un valor de cada grupo. La aplicación reaccionará a cualquiera de ellos de la misma manera. Puedes escoger los siguientes valores:

- 0 caracteres (dejar el campo vacío genera un resultado no válido).
- 20 caracteres (20 es más de 1 y menos de 50, por lo tanto, debe ser válido).
- 52 caracteres (52 es más de 50, por lo tanto, debe ser no válido).

### ¿Cómo identificar las clases de equivalencia?

La técnica de partición de clases de equivalencia permite disminuir la cantidad de pruebas, puesto que solo debes comprobar un valor de cada clase.

#### Paso 1: Descompón el requisito en `bloques atómicos`

Consulta los requisitos de Urban Routes. La tabla con las restricciones de entrada para los campos "Desde" y "Hasta" indican: "Solo letras del alfabeto latino, números, espacios, guiones, puntos y comas. Admiten entre 1 y 50 caracteres. Los espacios antes y después de una dirección se borran cuando se quita el enfoque".

El primer paso para elegir los valores de prueba consiste en descomponer este requisito en bloques atómicos. De este modo, obtendrás dos bloques:

1. **Tipo de caracteres de entrada**. Los caracteres permitidos son los siguientes: letras del alfabeto latino, números, espacios, guiones, puntos y comas.
2. **Longitud aceptable del texto**. La longitud que se acepta del texto es de 1 a 50 caracteres.

#### Paso 2: Define las clases para cada bloque atómico

En la lección anterior, ya identificamos tres clases para el bloque "Longitud aceptable del texto":


| Valores                    | Reacción de la aplicación |
| -------------------------- | ------------------------- |
| Campo vacío (0 caracteres) | Error                     |
| Entre 1 y 50               | Sin error                 |
| Entre 51 y más             | Error                     |

### Un rango y un conjunto de valores

Una clase de equivalencia puede ser un rango o un conjunto de valores.

- Un **rango** es un intervalo de números con límites, por ejemplo, 1-50.
- Un **conjunto de valores** es un grupo de valores que no se puede dividir en intervalos. Por ejemplo, cuando seleccionas un idioma de una lista desplegable en un sitio web, un conjunto estará compuesto por los idiomas que puedes seleccionar. Otro ejemplo es el siguiente: "Una contraseña debe contener caracteres especiales". En este ejemplo, la clase "Contraseña con caracteres especiales" será un conjunto porque no puedes dividir sus valores de prueba en intervalos.

Veamos el bloque "Tipo de caracteres de entrada": "Los caracteres permitidos son letras del alfabeto latino, números, espacios, guiones, puntos y comas". Las clases de equivalencia para este requisito serán los conjuntos; por ejemplo, "Una dirección con números".

Para identificar las clases de equivalencia, debes responder la siguiente pregunta: "¿Qué valores son correctos y cuáles son incorrectos?".

- Una **entrada válida** consistiría en letras del alfabeto latino, números, espacios, guiones, puntos y comas.
- Una **entrada no válida** incluiría cualquier otro carácter especial que no esté mencionado en los requisitos (p. ej.: una barra diagonal `/`).

Vamos a comenzar creando una tabla con todas las clases de equivalencia y los valores de prueba que identifiquemos.

![[eq-chart.png]]

Ahora sabes que una clase de equivalencia es un rango de números o un conjunto de valores que hace que una aplicación reaccione de la misma manera.

Utiliza el siguiente algoritmo para identificar las clases de equivalencia:

1. Descompón el requisito en bloques atómicos.
2. Para cada bloque, identifica el tipo de clase: un rango de números o un conjunto de valores.
3. Identifica los valores correctos. Puedes encontrarlos en los requisitos.
4. Identifica los valores incorrectos. Incluyen todo lo que no se identificó en la tercera etapa.
5. Descubre lo que ocurre si introduces valores incorrectos.

### ¿Cómo elegir los valores de prueba?

Una hipótesis habitual sobre hacer pruebas es que, si una aplicación procesa correctamente un valor de una clase, hará lo mismo con el resto de los valores. Del mismo modo, si cualquiera de los valores de una clase genera un error, ocurrirá lo mismo con todos los valores de esa clase.

Entonces, para elegir un valor de prueba, solo debes tomar cualquier valor dentro de la clase.

Sin embargo, no se deben utilizar valores límite, los cuales son valores en los límites de un rango. Por ejemplo, 1 y 50 son los valores límite de la clase "La longitud del texto es de 1 a 50 caracteres". Estos se utilizarán para un propósito distinto, por lo que no aparecerán en este grupo de prueba.

Ahora se muestra la tabla con sus correspondientes datos de prueba:

![[testdata-chart.png]]

### Valores límite

Un **valor límite** es un valor equivalente al valor mínimo o máximo permitido.

Ya conoces los requisitos del campo de teléfono en el formulario para pedir un taxi en Urban Routes: Los requisitos indican que un número de teléfono puede contener de 10 a 12 caracteres, es decir, 10 y 12 son los límites de la clase.

Asegúrate de comprobar siempre los valores límite, pues los bugs suelen aparecen allí.

#### Cómo encontrar los límites

Se permiten varios tipos de datos en los rangos:

- números enteros (1, 2, 3...)
- números decimales (0.1, 0.2, 0.3...)
- intervalos de tiempo (horas, días, meses)

Para identificar los valores límite, debes estudiar los requisitos. Los requisitos pueden definir los límites de diferentes maneras:

- **Intervalo numérico claro:** cuando sabemos los valores mínimo y máximo exactos, por ejemplo, "De 10 a 12 caracteres".
- **Rango claro:** cuando sabemos el rango, pero no sabemos los valores exactos, por ejemplo, "Números positivos".
- **Intervalo numérico poco claro:** cuando tenemos valores aproximados que debemos esclarecer, como "Mayoría de edad".
- **Rango poco claro:** cuando tenemos un rango aproximado con límites sin definir, por ejemplo: "Una persona de cualquier edad puede obtener un pasaporte".

#### Algoritmo general para el diseño de pruebas basadas en valores límite

Imaginemos que tienes que comprobar un campo en el que debes ingresar el número de minutos. Un usuario puede ingresar de 15 a 45 minutos. El tipo de datos es un intervalo de tiempo. El `intervalo` es 1 minuto.

Aquí verás el orden en el que deberías probar los valores límite:

1. Identifica el tipo de datos y el intervalo: un intervalo de tiempo y 1 minuto.
2. Comprueba que la aplicación funciona bien con los valores límite del rango: 15 y 45.
3. Muévete un intervalo fuera del rango y comprueba los siguientes valores: 14 y 46.
4. Muévete un intervalo dentro del rango y comprueba los siguientes valores: 16 y 44.

La siguiente lista te ayudará a recordar cómo definir tus datos de prueba en los límites:

- LI: límite inferior
- LS: límite superior
- LI - 1: límite inferior - un intervalo
- LS + 1: límite superior + un intervalo
- LI + 1: límite inferior + un intervalo
- LS - 1: límite superior - un intervalo

### ¿Cómo utilizar clases de equivalencia y valores límite juntos?

Digamos que puedes recargar el saldo de tu celular por un importe entre $1 y $49.99. Por lo tanto, no puedes utilizar un monto inferior ni superior al indicado.

Tipo de datos: un número entero con dos decimales, donde la parte entera es para los dólares y la parte decimal es para los centavos. El intervalo es de 0.01.

Clases de equivalencia:

- 0.00 — 0.99
- 1.00 — 49.99
- 50.00 y más

¿Cómo puedes probar que se recargó el saldo utilizando las técnicas de las clases de equivalencia y los valores límite de manera óptima? Primero, tienes que probar los valores dentro de la clase y, luego, debes utilizar el algoritmo para probar los valores límite:

1. **Prueba los valores dentro de las clases:** 00.50, 2.50 y 55.00. Si las pruebas son satisfactorias, ve al siguiente paso. Si no, no tiene sentido seguir probando la aplicación. No funciona.
2. **Prueba los valores límite:** 0.00 y 00.99, 1.00 y 49.99, y 50.00. Si las pruebas con estos valores son exitosas, la aplicación funciona bien. La última clase carece de límite máximo, por lo que no es necesario probarla.
3. **Prueba los valores un intervalo fuera de los límites:** 1.00, 0.99 y 50.00, y 49.99. Si las pruebas son satisfactorias, habrás confirmado que los límites son correctos. No se puede establecer un valor fuera de los límites de la primera clase: no es posible recargar el saldo con una suma negativa.
4. **Prueba los valores en un intervalo dentro de los límites:** 0.01 y 0.98, 1.01 y 49.98, y 50.01. Si las pruebas son exitosas, significa que la aplicación funciona como se requiere dentro de todo el rango; por lo tanto, el sistema reacciona a los valores de una clase de la misma manera.

### Optimización de pruebas

El principio más importante de optimización es reducir el número de duplicados antes de las pruebas.

Identificamos tres clases de equivalencia para la longitud de un texto: "La longitud del texto es de 1 a 50 caracteres", "La longitud del texto es de 51 caracteres o más" y "Campo vacío". Vuelve a observar los datos de prueba y encuentra los duplicados.

Esta es la tabla después de la optimización completa de las pruebas:

![[opt-chart.png]]

### Situaciones complicadas

Hay situaciones en las que dos requisitos de la documentación se solapan.

Por ejemplo, un banco te permite hacer una transferencia de una cuenta a otra según dos condiciones:

1. No puedes transferir menos de $5 ni más de $5000 de una vez.
2. El importe de la transferencia no puede superar el saldo de la cuenta.

Ambos requisitos deben cumplirse al mismo tiempo.

Teniendo en cuenta la primera condición, puedes dividir el intervalo en tres clases con los siguientes rangos de valores:

| N.º de la clase | Rango, $       | Comportamiento del sistema    |
| --------------- | -------------- | ----------------------------- |
| Clase А         | 0 - 4.99       | La transferencia es imposible |
| Clase B         | 5.00 - 5000.00 | La transferencia es posible   |
| Clase C         | 5000.01 - ∞    | La transferencia es imposible |

### ¿Cómo trabajar con tareas?

Imagina que tu tarea es "Probar una nueva funcionalidad". Esta descripción no está completa, porque no está claro qué funcionalidad necesitas probar, la versión de la aplicación ni los requisitos.

Cuando describas una tarea, deberías prestar atención a los siguientes aspectos:

- Contexto, es decir, de dónde viene esta tarea y cómo cambió la aplicación. Por ejemplo, la aplicación tiene una nueva funcionalidad para atraer a más usuarios.
- Recursos, por ejemplo, quién puede darte los requisitos o la versión de la aplicación para probarla.
- Fechas límite, es decir, cuándo debe estar todo listo.
- Implementación, es decir, lo que hay que hacer y dónde informar el resultado. Por ejemplo:
    - Obtener y analizar la nueva versión con cambios y los requisitos de la funcionalidad que se modificó.
    - Diseñar los casos de prueba.
    - Realizar las pruebas.
    - Escribir informes de errores, si se encuentran.

### Descomposición de tareas

Recuerda la tarea de la lección anterior en la que tenías que probar la nueva funcionalidad "Búsqueda de lugares":

**Prueba nuevas funcionalidades de "Búsqueda de lugares"**

Descripción de la tarea: añadimos la funcionalidad "Búsqueda de lugares" en la nueva versión 1.1. Tienes que probarla de acuerdo con los requisitos e informar los errores en Jira.

Puedes descargar la versión 1.1. aquí. Aquí tienes los requisitos. Arturo es nuestro analista de funcionalidad. Puedes hacerle preguntas.

Los cambios afectarán la funcionalidad de construcción de rutas: en la versión 1.1., hay que hacer pruebas de regresión de esta funcionalidad según sus casos de prueba.

Después de la prueba, marca el estado aprobado/no aprobado de los casos de prueba.

Fecha límite: 30 de enero

Echa un vistazo a la forma en la que puedes descomponerlo:

1. Analiza los requisitos de la funcionalidad.
2. Diseña pruebas en forma de casos de prueba.
3. Ejecuta las pruebas en la nueva versión de la aplicación.
4. Crea informes de errores si los resultados esperados no coinciden con los resultados reales.

Comprueba si puedes dividir las subtareas en tareas más pequeñas. Por ejemplo, no se puede dividir la tarea "Crear informes de errores". Sin embargo, "Diseño de la prueba" puede dividirse en subtareas:

- Utilizar clases de equivalencia.
- Utilizar los valores límite.
- Optimizar las pruebas.

La tarea "Estudiar los requisitos de funcionalidad" también puede dividirse en distintos pasos. Intenta utilizar verbos específicos en las subtareas para dejar claro lo que hay que hacer:

- Leer los requisitos.
- Descomponer y visualizar los requisitos.
- Encontrar las zonas grises.
- Preguntar al analista (Arturo) para aclarar las dudas.

#Chapter4 
### Documentación de pruebas

#### Redacción de informe

Sigue esta guía para redactar informes de errores eficaces:

- recuerda las relaciones de causa y efecto;
- describe una cadena lógica;
- resalta las ideas principales;
- organiza tus pensamientos.

Describe la cadena lógica completa al informar de un bug. Por ejemplo:

1. Abre la aplicación.
2. Introduce tu nombre de usuario y contraseña en el formulario de acceso.
3. Ve a la página siguiente.
4. Selecciona una línea de la lista desplegable.
5. Pulsa el botón OK.
6. En la ventana emergente, haz clic en el botón "No".
7. **Aquí** se produce un error.

### ¿Cómo crear una lista de comprobación a partir de un mapa mental?

A partir de la siguiente imagen:

![[mind-map-ub.png]]

Al mirar el mapa mental, puedes crear esta lista de comprobación de varios niveles:

![[req-ub.png]]

### ¿Cómo utilizar clases de equivalencia en los casos de prueba?

![[testcase-data-chart.png]]

Con base en los datos de la tabla sacaremos los casos de prueba.

Como ya sabes, cada caso de prueba debe incluir solo una comprobación y un conjunto de datos de prueba. Esto significa que debemos crear un caso de prueba para cada valor de prueba de la tabla (las columnas "Datos de prueba dentro de la clase" y "Datos de prueba en los límites").

La tabla final deberá ser así:

![[testcase-full-data.png]]

### Práctica Sprint 2 

**Requisitos:**

El formulario de registro de usuario debe contener los siguientes campos:

1. Nombre completo (texto, de 5 a 50 caracteres).
2. Correo electrónico (texto, debe ser una dirección de correo electrónico válida).
3. Contraseña (texto, de 8 a 16 caracteres, debe contener al menos un dígito, una letra mayúscula y una letra minúscula).
4. Confirmar contraseña (texto, debe ser el mismo que el campo Contraseña).
5. Fecha de nacimiento (fecha, el usuario debe tener al menos 13 años).

Al completar el formulario y presionar el botón Enviar, el sistema debe validar las entradas y mostrar un mensaje de error o crear una cuenta de usuario.

### **Ejercicio**

Este es un ejercicio de autoevaluación; el equipo de supervisión no lo revisará. Complétalo como mejor consideres y luego mira el video para ver la solución.

**1. Visualiza los requisitos del formulario de registro.** Crea un mapa mental y un diagrama de flujo para visualizar los requisitos del formulario de registro de usuario. Tiene que incluir todas las interacciones y dependencias posibles entre los campos y las respuestas del sistema. Puedes utilizar [draw.io](http://draw.io/) o cualquier otra herramienta para dibujar tu mapa mental y diagrama de flujo.

**2. Identifica las clases de equivalencia y los valores límite para los campos de entrada, y elige los valores de prueba para cada clase y límite.**

**3. Escribe casos de prueba para el proceso de registro en función de los valores de prueba identificados**. Cada caso de prueba debe contener un ID, título, pasos y resultado esperado. Asegúrate de cubrir tanto los casos de prueba positivos como los negativos.

Cuando completes los tres ejercicios, compara tu solución con los videos a continuación.

