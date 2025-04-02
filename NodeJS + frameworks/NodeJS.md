To start a new NodeJS proyect type:

npm init -y(set info project values as default)

Then appears 2 files to config:
-package.json
-packages-lock.json
Where you can modify according to the dependencies or test modules, or linters you would need.

And th you can start installing packages like express, nodemon, bcrypt...

npm install <package>

There are 2 types of import:
-D
-S

Then, if we want to work with TS type the next commands:

npm install typescript tslint -D

With this you install the linter for TS and the interpreter for it. Then you must inicialize the config file with this:

tsc --init

This creates an editable tsconfig.json where you can config how will work TS, there's an example:

{
    "compilerOptions": {
      "module": "commonjs",
      "rootDir": "./src",
      "esModuleInterop": true,
      "target": "es6",
      "moduleResolution": "node",
      "sourceMap": true,
      "outDir": "./build/js"
    },
    "lib": ["es2015"],
    "include": ["src/**/*"],
    "exclude": ["node_modules", "build"]
  }

Then, must run the compiler
./node_modules/.bin/tslint --init

It creates a tslint.json, modify this:

{
  "defaultSeverity": "error",
  "extends": ["tslint:recommended"],
  "jsRules": {},
  "rules": {
    "no-console": false
  },
  "rulesDirectory": []
}




