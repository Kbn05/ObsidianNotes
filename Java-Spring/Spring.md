En Spring contamos con múltiples gestores de paquetes, entre los que se encuentran gradle y maven. Mi aprendizaje por ahora se encuentra guiado por maven. 

Para crear un proyecto en Spring se debe hacer por el siguiente enlace(https://start.spring.io/)
Desde este enlace creas el proyecto y agregas las dependencias requeridas. Para el parcial de móviles me enfoque en usar bases de datos híbridas(SQL y NoSQL) por lo que tuve que importar las dependencias de MongoDB y MySQL. 
Las que considero importantes para cualquier aplicación básica son:

-Spring Security(Con esta implementé seguridad en las peticiones con JWT y asignación de roles, puesto que esta se basa en roles)
-JPA(Con esta se dan una serie de métodos para guardar información en bases de datos, es decir, facilita las operaciones en DB, no es necesario escribir código SQL)
-MySQL Driver(Si vas a trabajar MySQL es indispensable el driver)
-Mongo(Funciona para trabajar con DB NoSQL)
-Lombok(Librería para anottations en Java)
-Spring Web(Construir RestAPIs con Tomcat)

CommandLineRunner Interface
Esta interfaz permite la ejecución de alguna actividad al instante de iniciar la aplicación. Ejemplos prácticos de esta interfaz pueden ser el cargar datos de la DB, realizar conexiones de red, etc. Un ejemplo sencillo de como se puede hacer está a continuación:
```java
@SpringBootApplication
public class MyCommandLineRunner implements CommandLineRunner {
   
   @Override
    public void run(String... args) throws Exception {
        System.out.println("¡Hola, Mundo!");
    }
}
```
Una herramienta importante a considerar en SprinBoot es la inyección de dependencias. A diferencia de como lo suelo hacer, instanciando una clase como:

ClaseEjemplo claseEjemplo = new ClaseEjemplo();

Simplemente lo hacemos con la anotacion @Autowired(Mirar ejemplo práctica SpringBootAlura)

Biblioteca Jackson DataBind -> JsonProperty para serializar (permite pasar de Object A Json con el atributo definido)y JsonAlias para deserializar(leer Json para convertir en Object)

## JPA

JPA es un ORM que incluye métodos que sustituyen el SQL, parecido al SQLAlquemy en Python. Se deben comprender los siguientes conceptos de JPA:

Entity: Entidad en Java creada para representar un objeto en la base de datos. Cada entidad se mapea a una tabla de la base de datos. JPA exige que cada entidad tenga un constructor predeterminado(un constructor vacío).

EntityManager: Interfaz que realiza operaciones CRUD.

JPQL: El lenguaje de consulta de JPA, es mezclar Java con SQL.

## Hibernate

Hibernate proporciona una biblioteca basada en JPA que permite el acceso simplificado a la base de datos. Las entidades principales de hibernate son:

#### @Entity: 
Marca una clase como una entidad que debe ser mapeada a una tabla de la base de datos. Cada entidad corresponde a una table de la db.

#### @Table: 
Hibernate utiliza el nombre de la clase como el nombre de la db, realizando solo la conversión de PascalCase a SnakeCase. Si es necesario que el nombre de la clase sea diferente al de la tabla, esta anotación permite personalizar el mapeo. Con esto se puede especificar el nombre de la tabla, el squema y restricciones de primary key.

```java
@Entity
@Table(name = "mi_tabla")
public class MiEntidad { ... }
```

#### @Id: 
Marca un campo como la PRIMARY KEY de la entidad.

#### @GeneratedValue: 
Utilizada en conjunto con el @Id, especifica cómo se genera automáticamente la clave primaria. Puede utilizarse con estrategias como AUTO, IDENTITY, SEQUENCE o TABLE, según el tipo de db.

```java
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
private Long id;
```
AUTO: Esta estrategia decide por sí mismo cómo generar la clave primaria.
- Se adapta al tipo de base de datos que estás utilizando.
- Si tu base de datos es MySQL, usará `IDENTITY`.
- Si es Oracle, usará `SEQUENCE`.
```java
@Entity
public class Entidad {
 
    @Id
    @GeneratedValue(strategy=GenerationType.AUTO)
    private Long id;

}
```
IDENTITY: Esta estrategia es como un contador que se incrementa automáticamente. Cada vez que se inserta una nueva entidad en la db, la columna id se actualiza para generar un nuevo id.
- Se utiliza principalmente en bases de datos como MySQL y PostgreSQL.
- La clave primaria se genera al insertar un nuevo registro, y el valor se incrementa en 1 para cada nuevo registro.
- Es una opción sencilla y eficiente para bases de datos relacionales.
```java
@Entity
public class Entidad {
 
    @Id
    @GeneratedValue(strategy=GenerationType.IDENTITY)
    private Long id;

}
```
SEQUENCE: Esta estrategia es como un "generador de números" que se encarga de crear secuencias de números únicos, es decir, utiliza una secuencia de la base de datos para generar id's.
- Se utiliza en bases de datos como Oracle, PostgreSQL y DB2.
- Se define una secuencia en la base de datos, y `@GeneratedValue` la utiliza para obtener el siguiente valor de la secuencia.
- Es una opción más robusta que `IDENTITY` porque permite controlar mejor la generación de claves.
```java
@Entity
public class Entidad {
 
    @Id
    @GeneratedValue(strategy=GenerationType.SEQUENCE)
    private Long id;

}
```
TABLE: Esta estrategia es como un "libro de registro" que guarda los valores de las claves primarias. Usa una tabla separada para generar id's. Es menos eficiente pero más portátil entre diferentes proveedores de bases de datos.
- Se utiliza en bases de datos que no tienen soporte para `IDENTITY` o `SEQUENCE`.
- Se crea una tabla especial para almacenar los valores de las claves primarias, y `@GeneratedValue` la consulta para obtener el siguiente valor disponible.
- Es una opción menos común que las otras, pero puede ser útil en algunos casos.
```java
@Entity
public class Entidad {
 
    @Id
    @GeneratedValue(strategy=GenerationType.TABLE)
    private Long id;

}
```
#### @Column
Similar con la anotación @TABLE, hibernate toma por default los valores de los atributos como valores de las columnas de la tabla. De ser necesario que los nombres de la tabla difieran de los atributos, esta anotación permite configurar el nombre de la columna, su tipo de dato y si es obligatoria(NULL)

```java
@Column(name = "nombre_completo", nullable = false)
private String nombre;
```
#### @OneToMany y @ManyToOne

Se utiliza para mapear relaciones de uno a muchos y muchos a uno entre entidades. 

```java
@Entity
public class Autor {
    @OneToMany(mappedBy = "autor")
    private List<Libro> libros;
}

@Entity
public class Libro {
    @ManyToOne
    @JoinColumn(name = "autor_id")
    private Autor autor;
}
```
#### @ManyToMany
Esta permite definir relaciones muchos a muchos entre entidades.

#### @OneToOne
Se utiliza para mapear relaciones uno a uno entre entidades.

#### @JoinColumn
Se usa para especificar la columna que se usara para representar una relación entre entidades. Frecuentemente se usa en conjunto con @OneToMany y @ManyToOne

```java
@ManyToOne
@JoinColumn(name = "autor_id")
private Autor autor;
```
#### @JoinTable
Esta anotación permite mapear relaciones muchos a muchos. Mapea la tabla intermedia que conecta 2 entidades.

```java
@Entity
public class Estudiante {
    @ManyToMany
    @JoinTable(name = "inscripcion",
               joinColumns = @JoinColumn(name = "estudiante_id"),
               inverseJoinColumns = @JoinColumn(name = "curso_id"))
    private List<Curso> cursos;
}
```
#### @Transient 
Marca una propiedad como no persistente, lo cual significa que no se mapeará a una columna de la base de datos.

```java
@Transient
private transientProperty;
```

#### @Enumerated 
Mapea campos enumerados(ENUM) a columnas de la base de datos.

```java
@Enumerated(EnumType.STRING)
private Status status;
```

#### @NamedQuery
Esta anotación permite definir consultas JPQL nombradas que pueden definirse en varias partes de código.

```java
@Entity
@NamedQuery(name = "Cliente.findAll", query = "SELECT c FROM Cliente c")
public class Cliente { ... }
```

#### @Cascade
Se usa para especificar el comportamiento en cascada de operaciones de persistencia, como guardar o eliminar, en relaciones, es decir, que las operaciones CRUD que se realicen a los registros generarán comportamientos en aquellas que se relacionen con estas.

```java
@OneToMany(mappedBy = "departamento")
@Cascade(CascadeType.SAVE_UPDATE)
private List<Empleado> empleados;
```
#### @Embedded y @Embeddable
Representan tipos integrados (embeddable types) que pueden ser utilizados como componentes de entidades.
```java
@Embeddable
public class Direccion{ ... }

@Entity
public class Cliente {
    @Embedded
    private Direccion direccion;
}
```
 Usar variables de entorno en el **``
``Application.properties``:
variable = ${system.var}

Las operaciones que derivan de cascade son:

- PERSIST: si persistes la entidad Post, los Comments relacionados también se persistirán.
- MERGE: si fusionas los detalles de un Post, los Comments relacionados también se fusionarán.
- REMOVE: si eliminas un Post, los Comments relacionados también se eliminarán.
- REFRESH: si actualizas el Post, también se actualizarán los Comments relacionados.
- DETACH: si un Post ha sido desanexado, todos los Comments relacionados también se desanexarán.
- ALL: si realizas cualquiera de las operaciones anteriores en un Post, esa operación se propagará a todos los Comments relacionados.

Fetch Types: Existen don conceptos dentro de esto, 'Lazy' y 'Eager' las dos permiten hacer consultas a la db para obtener información que usará la aplicación.
- Lazy: Lazy Fetch Type permite obtener lo que se necesita en el momento en que se necesita.
```java
@Entity
public class Usuario {
    @OneToMany(fetch = FetchType.LAZY)
    private List<Post> posts;
}
```
- Eager: Eager Fetch Type permite recuperar información más rápido, obteniendo los datos relacionados al mismo tiempo.
```java
public class Usuario {
    @OneToMany(fetch = FetchType.EAGER)
    private List<Post> posts;
}
```


## TESTIIIIING

Vamos a comenzar 3 tipos de testing:

Unitarios: Se suelen hacer en clases o métodos(JUnit y Mockito).

Para realizar testings unitarios se puede hacer con la combinación de teclas alt + insert, seleccionando la opción test. Luego tendremos la opción de modificar nombre, ubicación, los métodos que incluirá, sean heredados o propios, y las opciones BeforeEach y TearDown.

BeforeEach: Al marcar esta opción, se crea un metodo setUp con annotation @BeforeEach el cual generealmente se usa para inicializar objetos antes de ejecutar los test.

TearDown:

Para llevar a cabo esto se suelen usar patrones como **Arrange**, **Act** and **Assert**(inicializar, activar el método y evaluar los resultados obtenidos con los esperados) o también **Given**, **When** y **Then**, que son similares al anterior, los cuales a su vez son conocidos como BDD(Behavior Driven Development). El ejemplo lo podemos observar a continuación:

![[Pasted image 20240828171016.png]]

El Arrange se aplica en el método con annotation @BeforeEach, donde se inicializan todas las dependencias que se usarán en el método.

El Act cuando se activa el método y se prueba lo que debe hacer.

Por último, con el Assert comparamos lo obtenido con lo esperado, controlando a su vez las posibles excepciones que pueden ocurrir y los resultados.

En caso de querer hacer pruebas de controllers aislados podemos hacerlo mediante la annotation @WebMvcTest, que evalua cada controller de forma aislada sin cargar todo el contexto de SpringBoot 

Integración: Evalúan la funcionalidad completa del código. Para esta nos podemos apoyar con la nnotation SpringBootTest


Para ejecutar las pruebas de un projecto Maven, podemos ahcerlo con el comando **mvn test** 