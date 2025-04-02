To build an image use

***docker build -t (name-file) (location)***
flags:
-t: it search docker images by name

Then, select the host port & name. Docker can put a name randomly if you don't

With ***docker compose*** you can create a multi-container project, for example a project that use 2 images, one for view an other for db.

Use ***docker compose up*** in the folder to build the project

Use ***docker compose watch*** you can run your project an see the changes in the project instantly

To persist data even if you delete a container, use ***volumes***. This is a location in your filesystem managed by Docker.
Example:

```Dockerfile
todo-database: 
	# ... volumes: 
		- database:/data/db 
# ... volumes: 
	database:
```

In this example, the volume element nested in todo-database tells ***compose*** to mount the volume named database to /data/db in the container for the todo-database service.

The top-level volumes defines and configures a volume named database that can be used by any of the service in the compose file.

Container data is isolated from our local filesystem, but if you want to access data from your container, you should use ***bind mounts***. This lets you share a directory from your host filesystem into the container.
Example:
```compose.yaml
todo-app: 
	# ... 
	volumes: 
		- ./app:/usr/src/app 
		- /usr/src/app/node_modules
```
The volume element tells compose to mount the local folder ./app (local filesystem) to /usr/src/app (container)
Este bind mount sobrescribe el contenido estático del directorio /usr/src/app en el contenedor y crea lo que se conoce como un contenedor de desarrollo

La segunda instrucción previene al bind mount de sobrescribir el directorio del contenedor node_modules, esto para preservar las dependencias instaladas y no se realicen cambios.

With ***docker init*** Docker create for you all the required files needed.