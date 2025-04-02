
New folder called python-api

config python enviroment (it's just like docker) which allow customize according to libraries or dependencies required for the project
cmd(bash):  python3 -m venv <name>

A new folder will be created and it includes an .exe file that we´ll use as our new interpreter.

Once it's done, check if the terminal use the v-env, if not, we must specify the path to file activate.bat and execute. Then, when we have our terminal working with v-env we need to install fastapi:

>pip install fastapi[all]

Now, config a simple server using this:

from fastapi import FastAPI

app = FastAPI()


@app.get("/")
async def root():
    return {"message": "Hello World"}

Then, run the server: 

uvicorn main:app

<github>
If you need to submit changes to github:

git init
git add .
git commit -m "Initial commit"
gir remote -v
git remote add origin https://github.com/<your-username>/<your-repo>.git
git branch -m master
git push -u origin master

If there's a conflict:

git pull origin main --allow-unrelated-histories

And then git push

git log(check out the changes log)
git diff (file)
git log --online -> copy hash
git restore -source hash (file)

branches
show branches -> git branch
create a branch -> git checkout -b (branchName)
move through branches -> git switch (brachName)
if you wanna push, specify the branch you were, ex:
git push origin (branch)

To merge branches(from main) -> git merge (branchName)
If you want to revert some changes on staging use:
 git reset HEAD -- {file}
README INFO
https://www.aluracursos.com/blog/como-escribir-un-readme-increible-en-tu-github

BADGES EXAMPLES
https://shields.io/badges
</github>

If you have your main file inside a directory you must specify the path through command line, like this:

uvicorn app.main:app --reload
(server) (dir).(file):(instance)

<database>
Instead of use Postgres as the video, I'm going to use MySQL. To connect with database, put this command:

mysql -u (user) -p

Once we work with mysql, it works. Instead using SQL, we can use SQLAlquemy, it's an ORM and works as an database manager, just that you don't communicate through SQL, instead, it use any programming language to create tables and execute queryes to the database.

To encrypt passwords use the library passlib, the command is:

> pip install passlib[bcrypt]


disco duro Virtual

Particion de montaje, administrador de discos, accion, crearVHD(crea un archivo y le asignas la ruta en un punto de mosntaje ya establecido)(VHDX Versión nueva), inicializar en GPT, formatear


se debe guardar de todo proyecto flutter:
lib
pubspec.yaml

<postman>

From Postman we can create an enviroment according to the context, it means If you are working on dev env, you dont need to modify the endpoint for each request or the auth token as well.
You create an env and then define the variables that you are working on. For ex:

variable: URL 
current value: http://127.0.0.1/

and the you replace on each endpoint like this: {{URL}}post

Also you can custom the env in test section, in this example it takes the value from response:

pm.environment.set("JWT", pm.response.json().access_token);

</postman>

Query params allows you define, for example, que search criteria, or some option into the URL, and it's simple to do, just put {{URL}}?(parameter) = (value)

pip freeze > requirements.txt

Send to an .txt file all the dependencies required for the project

pip freeze -r requirements.txt

Install all the dependencies specified into the req.txt

Shared Preferences almacena datos de la app en formato clave-valor

No puedo estructurar mis datos en SharedP, pero puedo acceder fácilmente mediante c-v

¿Qué es una sesión?

netstat -a (puertos)