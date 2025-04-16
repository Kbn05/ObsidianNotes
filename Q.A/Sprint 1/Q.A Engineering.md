#Chapter1

Un QA (Quality Assurance) es responsable de garantizar que un producto cumpla con determinado estándar de calidad. La calidad del software describe la capacidad del software para satisfacer las necesidades del usuario y a su vez cumplir con los requerimientos funcionales y de diseño especificados.

La calidad de un producto la podemos medir de las siguientes formas:

- Funcionalidad: el producto resuelve correctamente la tarea específica del usuario.
- Fiabilidad: el producto funciona en una variedad de condiciones, particularmente en condiciones extremas.
- Operatividad: el producto ayuda a resolver las tareas de usuario de la forma más rápida y cómoda posible.
- Eficiencia: el producto utiliza los recursos de manera óptima.
- Compatibilidad: el producto funciona según lo esperado en varias plataformas.
- Seguridad: el producto es seguro y mantiene protegidos los datos confidenciales.
- Mantenibilidad: es fácil de entender cómo funciona el producto para mantenerlo y perfeccionarlo.
- Transferibilidad: el producto es fácil de transferir a otra plataforma, como pasarlo de un S.O a otro.

Los QA escriben pruebas basadas en los requisitos iniciales del sistema.

![[beginner-tester.png]]

![[sprint1-steps.png]]

Ahora, en cuanto a las soft skills de un Q.A, se pueden dividir en 4 clases:

* Habilidades de comunicación
Un tester trabaja en equipo e interactúa con todos los miembros del proceso de desarrollo. Por ello es necesario aprender a dirigirse a cada persona y establecer una comunicación eficaz.
![[com-skills.png]]

* Pensamiento analítico
Es la capacidad de estructurar la información, observar relaciones causa-efecto y sacar conclusiones. 

![[smart-think.png]]

* Organización del trabajo y auto-organización
Los Q.A engineers deben tener la mente clara, enfocarse en la tarea más útil y no distraerse con cosas pequeñas; siendo necesarias buenas habilidades de gestión de tiempo y priorización de tareas.
![[work.png]]

* Superpoderes ??
En las pruebas, es especialmente importante la curiosidad, es decir, un interés sincero en cómo funciona todo. Es precisamente el deber de un Q.A, ayudar a encontrar las imperfecciones, para que los usuarios reciban un producto conveniente y útil.
![[super.png]]

#Chapter2 
### SDLC y los diversos roles.

![[SDLC.png]]

**Creación de ideas:** durante esta etapa, el equipo hace una investigación de mercado y formula hipótesis sobre el producto. El resultado debe ser una idea o concepto general de la aplicación que el equipo desea crear.

**Establecimiento de los requisitos**: en este punto, el equipo define los requisitos específicos para la aplicación, incluyendo lo que hay que crear y sus limitaciones. Los analistas aclaran estos requisitos, mientras que los gerentes priorizan las características. Los desarrolladores comienzan diseñando la estructura técnica, y los QA engineers revisan los requisitos para asegurarse de que son prácticos y se les pueden realizar pruebas, ayudando a detectar posibles problemas desde un principio. Esta colaboración garantiza una base sólida para el proyecto y un proceso de desarrollo más fluido.

**Diseño**: los diseñadores UI/UX crean interfaces fáciles de usar y se enfocan en la experiencia del usuario, mientras que los desarrolladores trabajan en la arquitectura del sistema y se aseguran de que sea escalable y funcional. Los QA engineers revisan el diseño para garantizar que este se alinee a los requisitos y que sea viable para ser probado. Pueden identificar desafíos potenciales en la realización de pruebas o lagunas en el diseño, lo que ayuda a garantizar que el producto final sea de alta calidad y se le puedan realizar pruebas.

**Desarrollo y pruebas**: los **desarrolladores** comienzan a programar la aplicación siguiendo las especificaciones establecidas en las etapas anteriores. Los **testers** (QA engineers) trabajan a su lado para identificar y corregir errores, asegurándose de que el producto cumpla con los estándares de calidad antes de su lanzamiento. El resultado es un software funcional aún cuando es posible que existan defectos por corregir.

**Lanzamiento**: Hasta este punto, se han completado todos los pasos y el software está disponible para los usuarios finales. Los **gerentes** supervisan el proceso de lanzamiento en coordinación con las partes interesadas para garantizar un lanzamiento fluido.

**Mantenimiento**: después del lanzamiento, el equipo de **desarrollo** sigue proporcionando actualizaciones y correcciones. Los **testers (QA engineers)** ayudan a garantizar la mejora continua de la calidad, mientras que los **gerentes** monitorizan el feedback de los usuarios y determinan futuras actualizaciones o cambios.

**Discontinuación**: cuando el producto se queda obsoleto, el equipo finalmente decide dejar de dar soporte, y tanto **gerentes** como **analistas** determinan cuándo es momento de ir eliminando gradualmente la aplicación.

### Ciclo de vida de las tareas en Kanban

![[Task-LC.png]]

***Dudas respecto a los estados resuelto y cerrado ejercicio cap. 2, sprint 1

Las nuevas versiones se conocen como lanzamientos; el código de los desarrolladores hacen "merge" al proyecto para ser probado posteriormente por scripts previamente programados por el Q.A team. Las más comunes son:

***Pruebas de humo:

Son pruebas rápidas que validan que las características críticas existentes funcionen correctamente. De ocurrir errores en esta fase no se deben desarrollar más pruebas hasta solucionar las cosas más importantes.

***Pruebas de regresión de las tareas que llegaron al lanzamiento:

Si las pruebas de humo tuvieron éxito, puedes probar las características a continuación; si no funcionaron, entonces el lanzamiento no tiene sentido.

***Pruebas de regresión de las funciones restantes:

Si los pasos anteriores avanzaron sin errores, es necesario realizar una prueba de regresión de las características restantes. En estas se prueba el producto en su totalidad, y se amplia el conjunto de pruebas donde las nuevas funcionalidades pueden haber afectado las antiguas.

#Chapter3 

### Listas de comprobación

Una checklist es una lista simple donde se marcan elementos a medida que se completa una tarea. En Q.A, casi todos los flujos de trabajo comienzan con el conocimiento de los requisitos del producto o características. Cada instrucción o elemento consta de dos partes: un elemento y una descripción de su comportamiento esperado. 

![[checklist-ex.png]]

Around cred: 

email: sof...@gmail.com
pass: qaengineer

### Bugs

Un bug o error es una discrepancia entre los resultados esperados y los actuales de una aplicación o función.

### Creación de lista de comprobación de pruebas (checklist)

**Un punto, una prueba**: un punto debe incluir un solo elemento o resultado esperado.

Ejemplo:

**Trabajar con el campo de correo electrónico**

- Hay un campo de correo electrónico en la página de registro.
- Aparece un mensaje de error cuando el usuario deja el campo de correo electrónico vacío y hace clic en el botón "Registrarse".

**Empieza una frase con un verbo**: Un verbo permite describir la tarea de le mejor manera y facilita la comprensión del punto. 

Ejemplo:  

**Probar el registro**

- Registrarse con un correo electrónico y contraseña válidos.
- Registrarse con un correo electrónico y contraseña no válidos.
- Registrarse con un usuario ya registrado

***No siempre será posible aplicar esta regla, ya que no todas la comprobaciones deben medirse mediante verbos, como por ejemplo: "El campo de correo electrónico se completa con el texto 'Correo electrónico' de forma predeterminada". Sin embargo, si es posible comenzar con un verbo, HAZLO!!!

### No duplicar escenarios de prueba

Debes asegurarte que no hayan pruebas repetidas en la lista.

#Chapter4 

### Informes de errores

Un informe de errores debe contener algunos elementos esenciales:

- Un título con una descripción del error exhaustiva pero breve.
- Los pasos para reproducir el error.
- Los resultados esperados y actuales.
- La configuración del sistema en la que se produjo el error.
- La severidad y urgencia de solucionar el error.

Un informe de errores contiene varias secciones llamadas campos. Algunos son obligatorios, lo que significa que deben completarse cada vez que se crea un informe de errores. Otros son opcionales.

***Campos obligatorios

| Nombre del campo                | Definición                                                                              |
| ------------------------------- | --------------------------------------------------------------------------------------- |
| ID                              | Un identificador único de informe de errores                                            |
| Título                          | Una breve descripción del error                                                         |
| Prioridad o severidad           | La criticidad del error y la urgencia de solucionarlo                                   |
| Configuración del sistema       | Los sistemas operativos, navegadores o versiones de aplicaciones donde aparece el error |
| Pasos a seguir                  | Un caso de prueba o una guía sobre cómo reproducir el error                             |
| Resultados esperados y actuales | Una descripción de los resultados esperados y actuales                                  |

***Campos opcionales

| Nombre del campo       | Propósito                                                                                   |
| ---------------------- | ------------------------------------------------------------------------------------------- |
| Descripción            | Se crea si el título carece de información sobre el error                                   |
| Materiales adicionales | Se indica para ayudar a describir un error (ejemplos: una captura de pantalla o screencast) |
| Condición previa       | Se indica cuando el sistema necesita preparación antes de la prueba                         |
| Condición posterior    | Se indica si es necesario devolver el sistema al estado original tras las pruebas           |


***Ejemplo

**ABUG-3:** La función de geolocalización precisa no se puede apagar después de su primera activación.

**Condición previa**: Activa la función de geolocalización precisa en la configuración.

**Configuración del sistema**: iPhone X iOS 16.1.2

**Severidad**: Crítica

**Pasos para reproducir el error**:

1. Abre la aplicación **Configuración** en el iPhone.

2. Dirígete a **Privacidad y seguridad** > **Ubicación**.

3. Selecciona una aplicación con permisos de ubicación activos.

4. Activa la opción **Ubicación precisa** (si no estaba ya activada).

5. Intenta desactivar la opción **Ubicación precisa**.

**Resultado esperado**:

La opción **Ubicación precisa** debería poder desactivarse, cambiando su estado a **inactiva** (interruptor en gris), y la aplicación debería utilizar únicamente una ubicación aproximada en adelante.

**Resultado actual**:

Al intentar desactivar **Ubicación precisa**, el interruptor no responde o vuelve automáticamente al estado activado (verde). La configuración no se guarda y la opción permanece activa, impidiendo que el usuario recupere el control sobre el nivel de precisión de su ubicación.

### Títulos de los informes de errores

El título describe la esencia del problema, brindando una descripción general antes de entrar a detalle. Por esta razón, el título del informe de errores a menudo se denomina resumen del error.

Para redactar un título, hacemos tres preguntas: "¿Qué? ¿Dónde? ¿Cuándo?" Al mismo tiempo, también intentamos describir el resultado obtenido (en lugar del esperado).


| Pregunta | ¿Cómo interpretar la pregunta?                    | Ejemplo                                  |
| -------- | ------------------------------------------------- | ---------------------------------------- |
| ¿Qué?    | ¿Qué pasó?                                        | La página de inicio de sesión no se abre |
| ¿Dónde?  | ¿En qué lugar de la página se reproduce el error? | La palabra "Around" está en el logotipo  |
| ¿Cuándo? | ¿Qué acción provoca esto?                         | Cuando el usuario hace clic…             |
***En conjunto, el título de un informe de errores podría verse así: "Cuando el usuario hace clic en la palabra 'Around' en el logotipo, la página de inicio de sesión no se abre".

### Pasos para reproducir un error

Reproducir un error significa encontrar el mismo error de software que encontró un QA para solucionarlo o investigarlo más a fondo.

***Ejemplo

**Pasos a seguir**
1. Abre la página de “[Around](https://around-v1.nm.tripleten-services.com/signin?lng=es)” `sin autorización`.

2. Haz clic en el botón "Registrarse".

3. Haz clic en la palabra "Around" en la esquina superior izquierda.

Al escribir los pasos para reproducir un error no es necesario escribir cosas como "enciende el pc", "abre el navegador"... ya que hace difícil encontrar los pasos necesarios. Por tanto, ==**solo deben resaltarse los pasos clave**==. Describe los pasos, comenzando desde la apertura del sitio web o la aplicación que se esté probando.

No se deben excluir datos de prueba específicos, por ejemplo:

Imagina que estás probando un cuadro de texto en un sitio web donde los usuarios pueden dejar un comentario. Ahora imagina que cuando escribes el carácter `&`, la página se congela. En tu informe de errores, debes anotar específicamente el carácter que rompe el cuadro de texto. Simplemente escribir "la página se congela cuando se ingresa un carácter especial" no brindará al equipo de desarrollo suficiente información para encontrar y corregir el error. ==**También recuerda dejar un enlace a la aplicación en cada informe, es una buena práctica.**==

### Severidad y prioridad

Cada error es diferente, y una forma de clasificarlos es por su nivel de influencia en el sistema, o severidad.

1. **Errores bloqueadores:** Con estos errores, ninguno de los elementos del sistema puede funcionar. Por ejemplo, si estás probando un sitio web y la página principal no se carga debido a un error, tienes un error bloqueador.
2. **Errores críticos:** Ocurren cuando una parte importante del sistema no funciona correctamente. El sistema es operable, pero la probabilidad de falla es alta. Por ejemplo, podríamos estar enfrentando un error crítico si el botón "Comprar" no funciona después de que el usuario inicie sesión en su cuenta personal, pero la tienda en general sigue funcionando con normalidad cuando los usuarios no inician sesión.
3. **Errores graves:** En este caso, el sistema funciona, pero no como debería. Básicamente, todas las funciones están activas, pero no funcionan según lo previsto. Por ejemplo, en lugar de un descuento prometido del 5%, la tienda en línea ofrece un descuento del 3% cada vez que un cliente hace clic en el botón "Comprar". El descuento del 3% también está bien, pero no es lo que el equipo de marketing había planeado.
4. **Errores menores:** En este caso, el sistema funciona bien, pero es incómodo de usar. Por ejemplo, digamos que hay un defecto de diseño en la sección "Productos" de la tienda en línea. Esto no impide que los usuarios pidan productos, pero no es una experiencia agradable.
5. **Errores triviales:** Estos bugs no afectan la funcionalidad del programa. Podría ser algo así como un error de texto, donde la sección "Teteras" de una tienda en línea se llama incorrectamente "Tetera", por ejemplo. Estos errores suelen ser fáciles de corregir.

La segunda forma de clasificarlos es por prioridad. Esta es diferente de la severidad, ya que la prioridad depende de cuánto afecta al negocio u organización. Cuanto mayor sea la prioridad, más rápido debe ser solucionado:

1. **Alta prioridad:** ¡El error está causando interrupciones importantes y debe solucionarse lo antes posible! Ejemplo: si los usuarios no pueden realizar una compra en una tienda en línea.
2. **Prioridad media:** El error no es crítico, pero está causando problemas que tienen cierto impacto en el negocio. Ejemplo: si no funciona la clasificación en la sección "Productos".
3. **Baja prioridad:** Estos errores pueden esperar. Es necesario corregirlos, pero solo después de que se hayan solucionado los errores de prioridad alta y media. Ejemplo: la sección "Teteras" de una tienda en línea se llama "Tetera".

### Configuración del sistema

La configuración del sistema describe la configuración particular en la que aparece un error. Esto puede variar según el proyecto y la aplicación. Por ejemplo, si estás probando una aplicación web, debes incluir lo siguiente:

- **Versión de la aplicación**
- **Tipo de navegador:** Chrome, Firefox, Safari o Microsoft Edge
- **Versión del navegador:** Por ejemplo, Safari 16.4.1
- **Sistema operativo (SO):** Windows, macOS, Linux, Android o iOS
- **Versión del SO:** Por ejemplo, Windows 11

### Materiales adicionales: capturas de pantalla o screencast

Los informes de errores generalmente se complementan con capturas de pantalla o screencasts. Se debe delimitar el área de la captura donde se encuentra el error.

En ciertos casos, al existir muchos pasos para reproducir el error, se recurre a los screencast o grabaciones.

Los nombres del archivo deben dejar claro su contenido. A continuación, una plantilla:

{ID de error}-{nombre de la aplicación}-{breve descripción del problema}.png

#Chapter5 

### Casos de prueba

Describe el proceso de verificar que un producto o función trabajan adecuadamente.


| Caso de prueba                                                                          | Informe de error                        |
| --------------------------------------------------------------------------------------- | --------------------------------------- |
| Ayuda a entender si la aplicación funciona adecuadamente, ayudando a encontrar errores. | Registra los errores que se encontraron |

### Composición de casos de prueba

Normalmente, los casos de prueba deben incluir:

1. `ID`.
2. Título.
3. Los pasos de las pruebas.
4. Los resultados esperados.

**Un consejo pro:** dependiendo de la complejidad del caso de prueba y los pasos necesarios, se puede especificar el resultado esperado de cada paso o solo el del proceso completo.

En un caso de prueba, los equipos de testers **también pueden señalar los siguientes elementos:**

1. Condiciones previas: todo lo que debe hacerse o las condiciones que deben cumplirse antes de efectuar una prueba.
2. Condiciones posteriores: el estado en el que el sistema debe encontrarse una vez que se ha realizado el caso de prueba.
3. `Sistema operativo (SO)`: Los errores no siempre se encuentran en todos los sistemas operativos para los que se desarrolló nuestro software.
4. Tipo de dispositivo: el dispositivo que debe emplearse para probar el software (p. ej. el tipo de teléfono inteligente).
5. Breve descripción del objetivo para mostrar qué requisitos cubre el caso de prueba.
6. Enlace a los `requisitos`: es muy útil hacer referencia a los requisitos que hemos utilizado al crear el caso de prueba.
7. Etiqueta: se suele dar a un caso de prueba en función del corte, por ejemplo, de regresión o de humo.
8. Otros componentes: la versión del software, el nombre de los elementos que necesitan ser probados, así como el rol y/o permisos del usuario.

Ahora es necesario asignar estados a los casos de prueba. A continuación se muestran 3 opciones de estado de casos de prueba:


| ¿El resultado esperado coincidió con el resultado obtenido?   | Estado      | Comentario                      | ¿Qué hacer?                                                                           |
| ------------------------------------------------------------- | ----------- | ------------------------------- | ------------------------------------------------------------------------------------- |
| Todo coincidió                                                | Aprobado    | Pasó la prueba                  | Ir al siguiente caso de prueba                                                        |
| El resultado obtenido no coincidió con el resultado esperado. | No aprobado | No pasó la prueba               | Crear un informe de errores                                                           |
| Fue imposible probarlo                                        | Omitida     | No se pudo obtener un resultado | Comenta los detalles del caso de prueba con tus colegas o crea un informe de errores. |

Hablemos un poco más sobre el estado "Omitida". Podemos asignar este estado cuando:

- No puedes replicar la condición previa.
- No tienes suficiente información (por ejemplo, no se facilitó ningún nombre de usuario o contraseña de administrador).
- El servicio no está disponible, por lo que no puedes realizar ningún caso de prueba.

***Ejemplo

**ID:** AROUND-1

**Título**: Agregar una nueva tarjeta

**Condición previa:**

1. Abrir Google Chrome (en la versión 70 o posterior) en modo incógnito en tu computadora.
2. Entrar al sitio web de "Around" mediante este enlace: [https://around-v1.nm.tripleten-services.com/signin?lng=es](https://around-v1.nm.tripleten-services.com/signin?lng=es)
3. Iniciar sesión con tu nombre de usuario y contraseña.

**Pasos de la prueba:**

1. Abrir la ventana para agregar una tarjeta nueva haciendo clic en el botón "+" en la esquina superior derecha de la página principal.
2. Ingresar el texto "Tarjeta de prueba" en el campo "Nombre".
3. Pegar "[https://practicum-content.s3.us-west-1.amazonaws.com/new-markets/qa-sprint-1/Colosseum.jpg](https://practicum-content.s3.us-west-1.amazonaws.com/new-markets/qa-sprint-1/Colosseum.jpg)" en el campo "Enlace a la imagen".
4. Hacer clic en el botón "Guardar".

**Resultado esperado:** aparece una tarjeta nueva en la página principal.

### Crear un caso de prueba

#### Caso de prueba vs lista de comprobación


| Caso de prueba                                                        | Lista de comprobación                       |
| --------------------------------------------------------------------- | ------------------------------------------- |
| Valida cada elemento de la lista de comprobación                      | Una lista de elementos que necesitan probar |
| Almacena información detallada sobre el producto                      | No detallada                                |
| Da oportunidad a cualquier miembro del equipo a ejecutar pruebas      |                                             |
| Contiene scripts de prueba (pasos para obtener el resultado esperado) | No contiene esta información                |

Los casos de prueba deben ser fáciles de entender, por lo que debe tener estructura sencilla y eficaz.

***Consejos para redactar casos de prueba

**Diseñar una sola comprobación por prueba**: Diseñar un caso de prueba con un resultado esperado. Conforme más experiencia, se podrán combinar varias comprobaciones en un solo caso de prueba.

**Un caso de prueba, un dato de prueba**: Los datos de prueba son los datos que necesitas durante la ejecución de la prueba. Puedes utilizar un conjunto de datos de prueba para un caso de prueba, porque sería específico para ese caso de prueba. 

Por ejemplo, si necesitas probar un campo con un nombre corto y otro largo, crea dos casos de prueba diferentes.
Por ejemplo, los pasos del caso de prueba contienen una línea:

Ingresa 10 caracteres en el campo "Nombre": 1234567abc.

La opción incorrecta sería:

En el campo "Nombre", ingresa 10 caracteres: 1234567abc y 10 símbolos: !@#$%^&*().

Esta opción contiene dos conjuntos de datos de prueba. Esto nos trae ciertos problemas:

- Es menos obvio qué se está probando y cuál es su título.
- El orden de la entrada de datos no está claro.
- No está claro si es necesario repetir todos los pasos para ambos conjuntos.
- Es más difícil localizar un problema si este se produce.
- Puedes llegar a olvidarte de comprobar uno de los conjuntos.

**El resultado esperado debe ser inequívoco**: Este debe ser claro para cualquier persona del equipo. Para escribirlo claramente, debe responder a las preguntas: ¿Qué pasó exactamente? ¿Dónde? ¿Cuándo?

Un ejemplo de un resultado esperado ambiguo es el siguiente:

Resultado esperado: todo funciona

Y uno que es claro:

Resultado esperado: la tarjeta está cerrada y el usuario es redirigido a la pantalla principal.

**Un ID único**: El ID de un caso de prueba no debe repetirse.

**Un título único y completo**: 
Un buen título:

- No repite los títulos de otros casos de prueba, para evitar confusiones.
- Es específico y responde a la pregunta “¿Qué estoy comprobando?” o “¿Qué? ¿Dónde? ¿Cuándo?”

Por ejemplo, los siguientes son buenos títulos de los casos de prueba:

- "Visualizar tu propia tarjeta": "¿Qué estoy comprobando?"
- "Visualizar tu propia tarjeta en la página principal después de haberla creado": "¿Qué?, ¿dónde? y ¿cuándo?"

Si solo escribes "Visualizar una tarjeta", no está claro qué tarjeta se muestra ni dónde lo hace.

**Pasos concisos y claros**: 
Al describir los pasos:

- No des demasiados detalles: incluye solo la información necesaria.
- Asegúrate de que cada paso responda a la pregunta “¿Qué hay que hacer?”

Por ejemplo, necesitas verificar que puedes eliminar una tarjeta que ya habías creado. Los pasos podrían ser los siguientes:

1. Presiona el botón "+".
2. Completa todos los campos con cualquier dato válido.
3. Haz clic en "Guardar".
4. Pasa el cursor sobre la tarjeta recién creada.
5. Haz clic en el ícono de la papelera.

**Especifica una condición previa si la prueba requiere de una configuración especial**: Una condición previa contiene los pasos obligatorios necesarios para ejecutar un caso de prueba. Por ejemplo, para iniciar sesión en una cuenta o habilitar ciertos ajustes. Por ejemplo, para crear una tarjeta en la aplicación "Around" necesitas iniciar sesión. Sin esto, no será posible crear un formulario o editarlo. Entonces, en las condiciones previas para los casos de prueba podrías mencionar: "Inicia sesión con tu nombre de usuario y contraseña".

**Ejemplo caso de prueba

**ID:** TRPLTNFRMS-11

**Título**: Comprobación de los campos "Número": entrada de valores largos

**Condición previa:**

1. Seguir el [enlace](https://docs.google.com/forms/) e iniciar sesión con la cuenta de prueba: nombre de usuario/contraseña.

**Pasos**:

1. Hacer clic en el botón “Iniciar un nuevo formulario”.
2. Seleccionar el tipo de pregunta “Respuesta corta” en el formulario abierto.
3. Hacer clic en los tres puntos de la esquina inferior derecha.
4. Hacer clic en “Validación de respuestas”.
5. Elegir “Longitud” y “Número máximo de caracteres”.
6. Introducir 10000000000000000000000000 en el campo “Número”.
7. Hacer clic en el botón “Enviar”.

**Resultado esperado**: Se guarda la respuesta.

### Errores comunes al escribir casos de prueba

- **El caso de prueba no cuenta con datos de prueba.**

Imagina que estás desarrollando un conjunto de casos de prueba para probar la funcionalidad de Google Forms.

**Problema:** no tienes suficientes datos de prueba en el caso de prueba.

![[test-case1.png]]

**Solución:** agrega pasos adicionales e incrementa el tamaño de los datos de prueba. Algunos ejemplos:

- En la ventana de edición que aparece, ingresa "Pregunta modificada" en el campo "Pregunta".
- Haz clic en los tres puntos en la esquina inferior derecha.
- Haz clic en "Descripción".
- Añade una descripción: "Validar el comentario".

![[test-case1-sol.png]]

- **Los títulos de los casos de prueba están duplicados.**

**Problema:** los títulos de unos casos de prueba están duplicados.

![[test-case2.png]]

**Solución:** renombra el caso de prueba. Puedes llamarlo de la siguiente manera:

- Restablece los cambios que hiciste al editar una respuesta corta presionando la tecla Esc.

![[test-case2-sol.png]]

- **Un caso de prueba contiene múltiples escenarios de prueba.**

**Problema:** un caso de prueba contiene diferentes comprobaciones.

![[test-case3.png]]

**Solución:** elimina los elementos 2 y 3 del resultado esperado. Es mejor escribir casos diferentes para los botones "Eliminar descripción" y "Agregar descripción". Este caso de prueba tendrá el siguiente aspecto:

- Resultado esperado: el texto "Texto del comentario" se muestra en el campo "Descripción".

![[test-case3-sol.png]]

- **El ID del caso de prueba no está especificado.**

**Problema:** el ID del caso de prueba no está especificado.

![[test-case4.png]]

**Solución:** agrega el ID del caso de prueba. Por ejemplo, T-23.

![[test-case4-sol.png]]

### Informes de resumen de pruebas

Una vez realizadas las pruebas es momento de redactar un informe de resumen de pruebas.

Este informe brinda una visión general de las actividades efectuadas durante la prueba. Este documento describe los objetivos de la prueba, alcance, casos de prueba que se ejecutaron, errores detectados y otra información relevante. Permite al equipo de producto tener una visión global de las pruebas que se realizaron, asegurando que todos los requisitos se cumplen.

![[test-info.png]]

Sin embargo, los QA engineers a menudo crean informes menos detallados. En estos casos, el informe de resumen de pruebas cuenta con menos campos; solamente contiene elementos esenciales como el ID del caso de prueba, un título conciso y su estado. Por ejemplo:

| ID   | Caso de prueba               | Estado   |
| ---- | ---------------------------- | -------- |
| AR-1 | Agregar nueva tarjeta        | Aprobado |
| AR-2 | Visualizar tu propia tarjeta | Omitida  |
| AR-3 | Eliminar una tarjeta         | Aprobado |

***Si se hubiera detectado algún error, habrías tenido que crear un informe de errores. Para ahorrar tiempo, una buena práctica sería señalar el ID, el título y la prioridad del correspondiente informe de errores junto al ID del caso de prueba en el informe de resumen de pruebas.

