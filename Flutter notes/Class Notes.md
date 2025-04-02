disco duro Virtual

Particion de montaje, administrador de discos, accion, crearVHD(crea un archivo y le asignas la ruta en un punto de mosntaje ya establecido)(VHDX Versión nueva), inicializar en GPT, formatear


se debe guardar de todo proyecto flutter:
lib
pubspec.yaml

dart permite herencia, en contexto de POO, this se refiere a esta clase, el super a la superclase(clase de la cual se hereda), tengo una variable a nivel de clase y otra a nivel de constructor, las 2 se llaman igual y por tanto se usa this para diferenciar entre la variable del const y de class

final permite que una variable se inicialice una única vez.(como el const)
los constructores no se heredan. Por tal razón, se llama al constructor de la clase padre por medio de "super()".

sobrecarga => métodos con el mismo nombre pero con diferentes parámetros.

void function {funcion}
void function => funcion

ambas hacen lo mismo, pero en la flecha solo se puede ejecutar una acción, para ejecutar más de una se requieren las llaves.
! -- indica que la variable no será nula. ex => _holi!

modificador late -> es como una promesa, no mostrará los errores en compilación, sino una vez se ejecute. Ejemplo:
Variable no inicializada y no nullable puede modificarse con late para no mostrar error en compilación en caso de no inicializarse, sino mostrarlo al momento de ejecución.

el constructor permite construir/instanciar un objeto de una clase.

para hacer fetch a las API's en Flutter necesitas installar la "librería"? http y modificar el androidManifest añadiendo lo siguiente(path desde la raíz del proyecto: android\app\src\main\AndroidManifest.xml):

<uses-permission android:name="android.permission.INTERNET" />