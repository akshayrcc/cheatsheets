# angular

* App framework
* Two versions
* Component based
* Modular


## Table of Contents

   * [Basic commands](#Basic-commands)
   * [Containers](#Containers)
   * [Images](#Images)


## Features

* Data binding
* Templates
* CLI

## CLI
- sudo npm install -g @angular/cli
- ng --version
- ng new project001
- cd project001
- ng serve --open 
- ng generate component todoComponent
- ng generate service todoService
- ng generate module appRoutingModule



## angular project structure
- .editorconfig : It stores the editor specific settings

- tslint.json, tsconfig.json : IT sets how TS will work and control for error checking..

- main.ts : here it starts, which loads all files.


## To add addtional framework
eg. 
-  npm install bootstrap --save-dev
-  npm install jquery --save-dev


- In file angular.json   under styles .. you can use bootstrap

## Updating to latest dependencies
```sh
npm install -g npm-check-updates
ncu -u
npm update
npm install
```

