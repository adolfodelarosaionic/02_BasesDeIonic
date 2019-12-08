# Bases de Ionic                                     9 clases    45:06

## Introducción a la sección                                     01:38

:+1:

## Temas puntuales de la sección                                 00:20

Esta es una sección corta, pero nos prepara el suelo para la sección 5. Aquí puntualmente trabajaremos lo siguiente:

1. Navegación entre pantalla con su animación respectiva

2. Cambiar el root de la aplicación (página inicial)

3. Implementar un botón de retorno

4. Módulo para agrupar todos los componentes personalizados que hagamos.

5. Introducción al componente de listas de ionic

6. Componente header

El objetivo es dejar la base para la siguiente sección y tener una primera interacción con las funcionalidades del día a día de una aplicación de ionic.

## Inicio del proyecto - Componentes                             04:30

[Documentación Oficial de Ionic](https://ionicframework.com/), en la sección [Get Started](https://dashboard.ionicframework.com/signup?source=framework-home&hsid=b3d6f4f06431132278cc7fba82b5c233&) podemos crear una cuenta de Ionic, con lo que podemos tener acceso a recursos privados de su plataforma, hay aplacaciones en la version de pago muy interesantes, una la utilidad [ionic creator](https://creator.ionic.io) nos permite crear visualmente toda la aplicación de Ionic es decir toda la interface.

En la sección [Installation](https://ionicframework.com/docs/installation/cli) tenemos el comando:

`npm install -g ionic` que nos permite instalar Ionic CLI.

Una vez intalado Ionic podemos crear un proyecto Ionic en blanco con el siguiente comando:

`ionic start componentes black`

Esto tarda varios minutos, hasta que se nos pregunta que **framework** vamos a utilizar:

<img src="images/ionicstart.png">

Una vez que se ha creado el proyecto, levantamos el servidor con:

`ionic serve -o`

Esto ejecuta la aplicación en la URL `http://localhost:8100/home` la cual se ve así:

<img src="images/localhost1.png">

También lo podemos ver como en un dispositivo movil:

<img src="images/localhost2.png">

## Cambiando la pantalla principal de la aplicación              05:47

Como se puede apreciar dentro de `src/app/home` tenemos los archivos: 

```
home.module.ts
home.page.html
home.page.scss
home.page.spec.ts
home.page.ts
```

En `home.page.html` esta el texto que se ve en la página.

<img src="images/home.png">

Muchos suelen dejar la `home` como el inicio de la aplicación. Nosotros vamos a borrar toda la carpeta `home` sin miedo. 

<img src="images/homeError.png">

Como podemos ver el error lo tenemos en el archivo `app-routing.module.ts`, si lo abrimos vemos que tenemos:

```js
const routes: Routes = [
  { path: '', redirectTo: 'home', pathMatch: 'full' },
  { path: 'home', loadChildren: () => import('./home/home.module').then( m => m.HomePageModule)},
];
```
En el segundo `path` se hace referencia a `./home/home.module` y como lo hemos eliminado nos marca error, elimine,os esa línea.

```js
const routes: Routes = [
  { path: '', redirectTo: 'home', pathMatch: 'full' }
];
```

<img src="images/sinhome.png">

En Ionic podemos crear **páginas** y **componentes** la diferencia es que una página contiene un archivo de rutas, un componente no lo tendra. 

Para crear podemos pulsar el comando `ionic g` y se nos presentaran todas las opciones que podemos crear:

<img src="images/ionic-g.png">

Lo que vamos a crear es una página en una carpeta `pages` que se llame `inicio`, usando:

`ng generate page pages/inicio --dry-run`

Nos indica todo lo que hara:

```
CREATE src/app/pages/inicio/inicio-routing.module.ts (347 bytes)
CREATE src/app/pages/inicio/inicio.module.ts (472 bytes)
CREATE src/app/pages/inicio/inicio.page.html (125 bytes)
CREATE src/app/pages/inicio/inicio.page.spec.ts (647 bytes)
CREATE src/app/pages/inicio/inicio.page.ts (256 bytes)
CREATE src/app/pages/inicio/inicio.page.scss (0 bytes)
UPDATE src/app/app-routing.module.ts (493 bytes)
```

Ejecutamos el comando:

`ng generate page pages/inicio`

Esto nos crea todo lo anterior

<img src="images/inicio.png">

Podemos observar que en el archivo `app-routing.module.ts` se ha incluido la ruta LazyLoad para esta nueva página:

```js
const routes: Routes = [
  { path: '', redirectTo: 'home', pathMatch: 'full' },
  {
    path: 'inicio',
    loadChildren: () => import('./pages/inicio/inicio.module').then( m => m.InicioPageModule)
  }
];
```

Solo debemos cambiar que la redirección se haga a `inicio` en lugar de `home` como estaba anteriormente.

```
const routes: Routes = [
  { path: '', redirectTo: 'inicio', pathMatch: 'full' },
  {
    path: 'inicio',
    loadChildren: () => import('./pages/inicio/inicio.module').then( m => m.InicioPageModule)
  }
];
```

<img src="images/pantallaInicio.png">

## Navegación entre páginas                                      05:03

## Back Button - Botón para regresar a la página anterior        07:38

## Módulo de componentes - Header                                11:21

## ion-list: Listas en ionic - Parte 1                           08:30

## Código fuente de la sección                                   00:19
