Java es una plataforma de programación que proporciona lo siguiente:

-Java Virtual Machine: Garantiza la independencia de plataforma, pues el código se ejecuta en máquina virtual y se puede portar a OS como Windows y Linux.
-Java Runtime Env: Agrega la máquina virtual y algunos recursos para la ejecución de apps Java.
-JDK: Utilidades para desarrollo de apps Java.

Los programas son escritos en un archivo con extensión .java, posteriormente son compilados para archivos con extensión .class. Estos contienen los códigos que se ejecutarán en la VM, bytecodes.

![[Pasted image 20240403223748.png]]
Java contiene un portafolio de productos para el desarrollo y ejecución de aplicaciones. Actualmente se divide en dos grandes áreas:

JSE: Proporciona entorno de desarrollo de apps pequeñas y medianas, además de conjunto de APIs base y JVM estándar.

JEE: Basado en JSE, se centra en desarrollo de apps empresariales multicapa de gran tamaño y brinda servicios adicionales, herramientas y APIs para hacer más fácil crear apps complejas.

Para comprender la JVM tenemos el siguiente ejemplo:

Un archivo ejemplo.java -> Lo compilamos (pasar de código fuente a código ejecutable) con javac $(nombreArchivo) -> Se genera un $(archivo).class -> Este se ejecuta con el comando java (archivo)

El .class está en bytecodes, el cual al ser observado en formato hexa se puede ver su inicial o número mágico(cafe babe)
Para entender más a detalle el .class se puede explicar paso a paso con el comando: javap -c $(archivo.class)

- "==" (igual a)
- "!=" (diferente de)
- ">" (mayor que)
- ">=" (mayor o igual que)
- "<" (menor que)
- "<=" (menor o igual que)
Todos estos retornan True o False

SHOTCUTS
psvm
sout

Casting Implícitos y explícitos (conversión)
![[Pasted image 20240510181322.png]]
La utilería Scanner no únicamente lee entradas de texto, también archivos o flujos de entrada. No solo existe el .nextLine() para String, sino también .nextDouble(), .nextBool(), etc.
Los objetos en Java se almacenan en heap, Un espacio de memoria con dirección única.

Modificadores de acceso Java:
Public: Cuando especifícas público, puede ser accedido desde cualquier lugar del proyecto
Protected: Permite que los atributos de una clase sean accesibles para otras clases del mismo paquete y por sus subclases sin importar la ubicación
Private: Solo puede ser accedido por la clase misma, o también por medio de getters/setters
Default: Permite el acceso desde el mismo paquete, se establece cuando no se especifica el tipo de dato

En Java se trabaja convencionalmente con paquetes, por lo que es necesario organizar el proyecto de este modo. Los paquetes se nombran de acuerdo con le dominio de la organización, por ejemplo: com.(nombreDominio).(nombreProyecto).(nombrePaquete)

En los paquetes se agrupan clases que comparten una funcionalidad en específico.

Para sobrecargar un método en Java pones @Override sobre este.

En herencia, la subclase puede acceder a todos lo métodos y atributos(public, protected, private) de la superclase.

Las anotaciones como @Override permiten que el código entienda la función que cumple un método o dato.

Ejemplo: para validad un usuario puedes hacerlo con regex, pero es poco reutilizable, en cambio con anotaciones puedes hacerlo fácilmente reutilizable, similar a una interfaz, lo declaras de la siguiente forma:

public @interface validateUser{
	int valor();
}  
Java entiende esto como una anotación. Además hay que agregarle algunas anotaciones obligatorias como:
@Retention - Retención de la anotación, hasta cuándo y cómo estará disponible en tiempo de ejecución(cuándo estará disponible compilación, ejecución, etc.)
@Target - Elementos que se pueden aplicar con esta anotación

Luego lo podremos llamar de la siguiente forma:

public class User {
	private String name;
	private String id;
	@validateUser(valor=18)
	private int edad;
}

Existen 2 clases de polimorfismo, polimorfismo de herencia y de interfaces
En el primero (extends), las subclases heredan de la superclase sus atributos y métodos, proporcionando su propia implementación de métodos heredados(sobrecarga)

El segundo (implements) viene siendo lo mismo pero con las interfaces, aquellas clases que implementen una interfaz heredan sus métodos y pueden hacer su propia implementación de métodos.

ESTRUCTURAS DE DATOS

ArrayList: Permite almacenar una lista de objetos del mismo tipo

Tamaño Fijo: No puede ser modificado una vez creado. No es conveniente de usar si el tamaño de los datos es variable o desconocido.
Ausencia de métodos: No cuentan con métodos para insertar, borrar o buscar elementos de forma eficiente.

Una variable es una referencia o puntero a un espacio de memoria, también considerar lo siguiente:

Object a = new Object();
Object b = new Object();

a==b -> false (Este evalúa la igualdad de los punteros, mas no de los objetos a los que apuntan)
a === b -> true (Este compara el valor al que apuntan las referencias)

Programación orientada a interfaces - ejemplo:

List<E> lista = new ArrayList<>();

Aquí se crea un espacio de memoria que almacenará una lista, este arraylist contendra objetos en formato list, y es posible debido a que arraylist implementa la interfaz de list.

Esto se hace debido a que puede que en cierto momento sea requerido cambiar el tipo de list que se implementa, ya sea por un linkedlist, vector, etc.

No es algo que aplique únicamente a las listas.

ESTRUCTURAS DE DATOS 

ARRAYLIST
Esta estructura se basa en un array dinámico, capaz de almacenar x cantidad de objetos y acomodarlos, ajustando automáticamente su tamaño. De igual modo funciona cuando se elimina un elemento, y es por esto que se usa ampliamente, ya que es fácil de usar y tiene un buen rendimiento en inserción y eliminación de datos.

LINKEDLIST
Esta proporciona una lista enlazada, donde cada elemento contiene una referencia al siguiente elemento de la lista. Sin embargo, en lugar de almacenar objetos contiguos en la memoria, lo que hace es crear punteros para vincular cada elemento, y cada elemento apunta hacia el espacio de memoria del siguiente en la lista, sin tener que estar en el mismo bloque de memoria. Por lo tanto, tampoco es necesario desplazar elementos al incluir o eliminar , a diferencia de un array que debe reposicionar los elementos, en este cada nodo apunta hacia el siguiente elemento, independientemente del espacio de memoria en que se encuentre.

Esto lo hace mas eficiente en inserción y eliminación pero no en búsqueda de elementos en específico.

Es útil cuando se insertan y eliminan elementos frecuentemente pero no para acceder a ellos.

Ejemplos: galería, listas de reproducción o video

VECTOR
Similar a un ArrayList, pero la principal diferencia radica en que sus métodos se encuentran protegidos, por lo que solo se pueden hacer una modificación a la vez por hilo de ejecución, sincronizando los cambios a costo de una mayor exigencia en el rendimiento. También cambia en que este, al alcanzar el máximo de valores establecido automáticamente se ajusta al tamaño que requiera.

STACK
Esta clase implementa una pila, una colección ordenada de elementos donde la inserción o remoción de elementos se da en los extremos. Esto se hace en un orden conocido como LIFO (Last in, first out), el último agregado es el primer eliminado.

Las estructuras de datos pueden ser lineales(arrays) o no lineales(grafos), homogéneos(todos los datos del mismo tipo) o heterogéneos(diferentes tipos de datos dentro), estáticos(tamaño fijo) o dinámicos(tamaño variable)

QUEUE
La cola es similar a la pila, pero con una diferencia conceptual importante, ya que sigue un orden FIFO(First in, first out), el primero en entrar es el primero en salir. Por lo tanto solo se puede insertar un elemento al final de la cola o removerlo del inicio.

DEQUE
Double ended queue o cola de dos puntos es una variación que permite inserción y eliminación de elementos tanto al principio como al final. Una forma sencilla de entender es unir los conceptos de cola y pila.

CIRCULAR QUEUE
La cola circular conecta al último elemento con el primero. Con esto se busca lidiar con los espacios vacíos al remover elementos del inicio.

SET
Un conjunto es una lista no ordenada de elementos que permite almacena un elemento único, es decir, no se pueden repetir elementos.

MAP
Esta interfaz permite asociar pares clave-valor. Especialmente útil para aplicaciones que requieren manipular grandes cantidades de datos a través de su clave. Es implementado por hashmap

HASHMAP
Estructura basada en pares clave-valor almacenados en una tabla hash, usando las claves como referencia para búsqueda. Los diccionarios aceptan cualquier tipo de dato como clave y suelen ser mejor en búsquedas y manipulación de datos. Tiene una complejidad temporal o(1) en inserción, eliminación y modificación de elementos, es decir, su rendimiento no depende del tamaño de recopilación de datos. No mantiene el orden de inserción de los elementos y no garantiza el orden de los elementos de salida.

TREE
El árbol es una estructura no lineal que almacena datos de forma jerárquica y pueden ser accedidos de forma rápida. Es una colección de datos representada por nodos y organizados.

La estructura más común es la binaria, que contiene máximo 2 nodos hijos a partir del nodo inicial. Un nodo puede tener padre, hermanos e hijos; los nodos con hijos son los nodos internos, y sin hijos son los nodos externos.

A partir de la estructura de árbol binario es que se estructura el árbol de búsqueda binaria o BST, que organiza los datos que forma que los valores menores estén a la izquierda de la raíz y valores mayores a la derecha.

BINARY HEAP
Un tipo especial de árbol binario, usado en computación para implementar cola de prioridades. Con esto se puede extraer de forma más eficiente el valor mínimo y máximo de una lista. Difiere del árbol binario en lo siguiente:

Todos los niveles, con excepción del último tienen hijos tanto en la izquierda como en la derecha de la raíz. En el último nivel los hijos se posicionan lo más a la izquierda posible.

Puede ser un heap mínimo para extraer el menor valor del árbol, o heap máximo para extraer el mayor.

GRAFO
Otra estructura no lineal, es un conjunto de nodos(vértices) ordenados o desordenados y conectados por aristas, formando una estructura en forma de red. Pueden ser direccionadas o no direccionadas(flechas).

LIBRERIAS Y FRAMEWORKS

Para hacer uso de alguna librería o framework en Java, debemos ingresar a 'estructura del proyecto' y desde aquí añadir manualmente la dependencia a utilizar.

Las bibliotecas o librerías generalmente se distribuyen en archivos .jar (Java Archive), que contienen clases y otros recursos.

los frameworks se pueden componer, entre otras cosas, de bibliotecas, patrones y buenas prácticas proporcionando una arquitectura para el desarrollo de aplicaciones.

Los dto son clases intermediarias que permiten tomar los datos de un Json y pasarlos a una clase, a mi parecer es similar en cierto modo a una interfaz.

Los java records son clases inmutables que contienen atributos, constructores y métodos de lectura. Con esta clase se logra la inmutabilidad de los objetos una vez son creados.

GESTORES DE PAQUETES JAVA:
Maven
Gradle

ANOTACIONES

@Autowired
@Data
@Service
@Controller
@Bean
@SerializedName

Para el manejo de errores puede usarse try-catch junto con finally en caso que ambos terminen en un mismo resultado, es decir, si tanto el try como el catch tienen la misma salida o return puede usarse finally para evitar duplicar código.
Correción: Finally se usa para cuando se produce un error en try-catch aún así se pueda ejecutar una parte de código contenida en este bloque.

EXCEPCIONES
Todas las excepciones derivan de la clase throwable la cual tiene dos subclases principales: errores y excepciones.

![[Pasted image 20240620120750.png]]

Las excepciones que heredan de Exception se denominan excepciones verificadas, esto significa que deben manejarse dentro de bloques try-catch o declaradas en una cláusula throw en la firma del método (luego de los parámetros y antes de las llaves. Un ejemplo es IoException, que maneja errores de lectura/escritura de datos.

Las excepciones que heredan de Error son aquellas que impiden la recuperación del sistema, como falta de memoria o fallas internas. OutOfMemory por ejemplo indica que Java no puede obtener suficiente memoria del sistema operativo para ejecutar la aplicación. 

También existe la clase RuntimeException, subclase directa de Exception. Las clases que heredan de RuntimeException son excepciones no verificadas. Estas indican errores lógicos del código, como NullPointerException, que indica que el acceso a algún atributo método de un objeto es null. 

Para no hacer uso de muchos catch se puede usar una característica implementada desde java 7 llamada multi-catch, que permite un uso de un único bloque catch que capture múltiples excepciones con el caracter |

Multi-catch solo se permite para excepciones que están relacionadas por jerarquía de herencia. Si dos excepciones comparten jerarquía deberán manejarse en bloque separados.

Java.io es una de los paquetes más importantes que proporciona clases e interfaces para entrada y salida de datos en diversos formatos como archivos, red, teclado, etc. Este se compone de las siguientes clases:

File -> Representa un archivo o directorio en el sistema, permitiendo crear, eliminar, listar y manipular archivos y directorios. Al crear un archivo file se debe pasar la ruta del archivo como argumento al constructor.

File file = new File("C:\\miArchivo.txt");

FileReader-FileWriter -> Se utilizan para leer y escribir datos en archivos de texto. La clase FileReader lee los caracteres de un archivo de texto, mientras que FileWriter se encarga de la escritura. Al instanciar un objeto de la clase FileReader se debe pasar como argumento al constructor un objeto File que contenga la ruta del archivo que se quiere leer. Luego se puede leer el archivo con read() o read(char[]).

File file = new File("C:\\miArchivo.txt");
FileReader reader = new FileReader(file);

int data = reader.read();
while (data != -1) {
    System.out.print((char) data);
    data = reader.read();
}
reader.close();

Con FileWriter es similar pero usando métodos de escritura:

File file = new File("C:\\salida.txt");
FileWriter writer = new FileWriter(file);
writer.write("Hola mundo!");
writer.close();

BufferedReader-BufferedWriter -> Usado para leer y escribir archivos de texto una línea a la vez. Usa un búfer para almacenar datos.

FileInputStream-FileOutputStream -> Leer y escribir datos binarios en un archivo. Esto no solo aplica para archivos de texto, también audio, imagen, video.

ObjectInputSteam-ObjectOutputStream -> Leer y escribir objetos en archivos. Permite almacenar objetos Java en archivos para uso posterior o transferirlo a otras aplicaciones.

Scanner es una clase estándar de Java que permite leer datos de diversas fuentes, incluyendo archivos. Para lectura de archivos se debe crear una instancia de la misma y pasar un objeto de tipo File como argumento, el cual contenga la ruta del archivo. Ejemplo:

try {
            File archivo = new File("archivo.json");
            Scanner scanner = new Scanner(archivo);

            while (scanner.hasNextLine()) {
                String linea = scanner.nextLine();
                System.out.println(linea);
            }
            scanner.close();
        } catch (FileNotFoundException e) {
            System.out.println("Archivo no encontrado!");
        }

Serializar -> Convertir de Java Object a JSON(o cualquier cosa?)
Deserializar -> Convertir de JSON(o cualquier cosa?) a Java Object

final : Cuando marcamos un atributo como final su valor se convierte en inmutable, es decir, no se puede modificar una vez asignado.

static: Útil para las constantes, pues permite que se puedan tomar a traves de "nombreClase.NOMBRE_CONSTANTE" sin tener que instanciar la clase.

Las expresiones lamba son así:

e -> doSomething (algo así xd)
(argumentos) -> {cuerpo de la función}

ej:
(a,b) -> {return a+b;}

Son útiles para usar cuando se requieren ejecutar en una única parte de nuestro código. A diferencia de las convencionales que las solemos definir y llamar por un nombre, estas se ejecutan donde son declaradas y al ser anónimas, solo pueden declararse una única vez.

Stream te permite ejecutar múltiples acciones. Por ejemplo, si quieres ejecutar varios filtros en una lista puedes hacerlo de la siguiente forma:

```java
List<t> list = new ArrayList();

list.stream()
	.sorted() //ordena la lista
	.filter(e -> e.includes("ñ"))//filtra
	.foreach(System.out::println);
```

Stream cuenta con operaciones intermedia y finales, las intermedias son aquellas que se aplican a un stream y retornan un nuevo stream. Por ejemplo filter y map son dos tipos de operaciones intermedias.

Las operaciones finales cierran el strem y retornan un resultado. Estas son forEach, collect y count

También existen otras como: reduce(combina los elementos del stream en un único resultado), skip(salta los primeros elementos del stream), distinc(elimina elementos duplicados), limit(limita el número de elementos mostrados/seleccionados)

Para depuración de un stream, es decir, observar que hace en cada operación intermadia podemos usar la operación intermedia peek, que no altera el flujo de las operaciones.

DATO: los streams permiten el paralelismo(ejecutar varias operaciones en simultáneo)

DATO: los null pueden trabajarse también con Opcional<T>

Ejemplos de multiprocesamiento en colecciones de datos: FindAny, un método para buscar elementos de acuerdo a ciertas condiciones, dando como resultado un Optional.
//Ejemplo de paralelismo, al ejecutarse la búsqueda de múltiples números en simultáneo es posible obtener diferentes resultados en cada ejecución del método.
```java
Optional<Integer> numeroCualquiera = numeros.parallelStream()
                .filter(numero -> numero % 10 == 0) // Filtra los números que son múltiplos de 10
                .findAny();
```

Para estadisticas existen las clases doublesummariseStatistics y intSummariseStatistics que retornan suma, promedio, mínimo, máximo y total de elementos.

```java
List<List<String>> lista = List.of(
  List.of("a", "b"),
  List.of("c", "d")
);

Stream<String> stream = lista.stream()
  .flatMap(Collection::stream);

stream.forEach(System.out::println);
```
Una lista de listas con Strings

Un método estático es un método que pertenece a la clase y no a un objeto de la clase. Es decir, este puede ser utilizado incluso sin instanciar la clase(crear un objeto de esta).
