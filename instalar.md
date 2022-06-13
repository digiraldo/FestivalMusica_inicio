
npm install sass

<!-- Instalamos la dependencia de desarrollo no la anterior -->
npm install sass --save-dev


<!-- Modificar package.json para compilar sass -->
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },

    "scripts": {
    "sass": "sass src/scss:build/css"
  },
<!-- Aplicamos watch para que automaticamente actualice los scripts que estamos editando, recarga todo -->
      "scripts": {
    "sass": "sass --watch src/scss:build/css"
  },

  <!-- Llamamos los scripts para compilar -->
  npm run sass

  <!-- HACER LO MISMO PERO CON GULP -->
  <!-- Requerimos versión global y local de Gulp -->
  <!-- Abrimos como administrador  power shell(Click aux abrir como admin) o terminal mac o linux (inicio con sudo) -->
  <!-- Ver. Global -->
  sudo npm install -g gulp
  gulp -v

  <!-- Regresamos a Terminal de Studio Code e instalamos la version local de Gulp -->
  npm i --save-dev gulp

  <!-- Para que funcione creamos archivo gulpfile.js -->
  <!-- Estas son funciones de JavaScript -->
  <!-- VER ARCHIVO gulpfile.js ej: abajo -->
function tarea() {
    console.log('Desde la primer tarea');
}
  <!-- Hacemos disponible la tarea -->
  exports.nuevatarea = tarea;
  <!-- con la linea anterior la dejamos disponible desde la terminal con gulp -->
  gulp nuevatarea
  <!-- Hacemos un callback para finalizar las tareas -->

  <!-- lo encontramos como callback, como function o fn, o com done -->
  function tarea(callback) {
    console.log('Desde la primer tarea');
    callback();
}
  function tarea(fn) {
    console.log('Desde la primer tarea');
    fn();
}
  function tarea(done) {
    console.log('Desde la primer tarea');
    done();
}

<!-- -----------163. Compilando SASS con Gulp----------- -->
<!-- en la pagina de gulp en plugins -->
https://gulpjs.com/plugins
<!-- instalamos gulp-sass como desarrollo -->
npm i --save-dev gulp-sass

npm i --save-dev gulp-plumber



//** Forma Anterior */
 // Sin la ralla al piso y la extencion, sass ya lo sabe, disponible globalmente en todos los archivos
/* 
@import 'base/variables';
@import 'contenido/contenido';

body {
    background-color: $azul;
}
*/


## HTML
    <h1 class="prueba">Probando Mixing</h1>
    <h2 class="texto">Texto de Prueba</h2>

## _header.scss
@use 'base/mixins' as m;

.prueba {
    @include m.heading(v.$amarillo, true)
}

.texto {
    @include m.heading
}

## _mixins.scss
@use 'variables' as v;

@mixin heading($color: v.$rosa, $border-radius: false) {
     text-transform: uppercase;
     font-size: 2.4rem;
     color: $color;
     letter-spacing: 8px;
     background-color: v.$negro;

     @if $border-radius {
          border-radius: 4rem;
     }
}


## 177. Creando un Snippet para los Media Queries

CTL+Shift+P
User Snippets
scss.json

	"media query": {
		"prefix": "mq",
		"body": [
			"@include m.$1 {\n\t$2\n}"
		]
	}

  ## 178. Creando un Snippet para importar Variables y Mixins
{
"media query: digiraldo": {
		"prefix": "mq",
		"body": [
			"@include m.$1 {\n\t$2\n}"
		],
		"description": "Usar telefono, tablet, desktop o desktopXL\n telefono: 480px;\n tablet: 768px;\n desktop: 992px;\n desktopXL: 1200px;\n"
	},
	"Importar mixins: digiraldo": {
		"prefix": "imm",
		"body": [
			"@use 'base/mixins' as m;"
		],
		"description": "imm = Importar Mixins\n"
	},
	"Importar variables: digiraldo": {
		"prefix": "imv",
		"body": [
			"@use 'base/variables' as v;"
		],
		"description": "imm = Importar Variables\n"
	}
}


## 187. Utilizando Gulp para crear imágenes Webp
npm i --save-dev gulp-webp

## 188. Aligerar imágenes con Gulp
# la Version 8.0.0 no funciona
npm install --save-dev gulp-imagemin@7.1.0
# El procesamiento de imágenes requiere tenerlas en cache
npm i --save-dev gulp-cache

## 189. Creando imágenes Avif
npm i --save-dev gulp-avif
npm install --save-dev gulp-avif

## 191. Creando un Snippet para las imágenes
CTL+Shift+P
User Snippets
html.json

{
  "Imagenes: digiraldo": {
	"prefix": "im",
	"body": [
		"<picture>"
			"\t<source srcset=\"$1\" type=\"image/avif\">",
			"\t<source srcset=\"$2\" type=\"image/webp\">",
			"\t<img loading=\"lazy\" width=\"200\" height=\"300\" src=\"$3\" alt=\"$4\">"
		"</picture>"
	],
	"description": "Insertar imagenes avif, webp, jpg y png\n\tFormatos adminitos:\n\t\t.avif\n\t\t.webp\n\t\t.jpg\n\t\t.png\n"
	},
	"Videos: digiraldo": {
	"prefix": "vi",
	"body": [
        "<video autoplay muted loop> <!-- para los controles se usa: controls -->"
            "\t<source src=\"$1\" type=\"video/mp4\">"
            "\t<source src=\"$2\" type=\"video/ogg\">"
            "\t<source src=\"$3\" type=\"video/webm\">"
        "</video>"
	],
	"description": "Insertar Videos mp4, ogg y webm\n\tFormatos adminitos:\n\t\t.mp4\n\t\t.ogg\n\t\t.webm\n"
	}
}



## CSS
CTL+Shift+P
User Snippets
css.json

{
  	"Media Querie: digiraldo": {
		"prefix": "mq",
		"body": "@media (min-width: $1) {\n    $2\n}",
		"description": "Media Querie Base"
	},

	"Media Querie 480px - Telefono: digiraldo": {
		"prefix": "mq-1-480",
		"body": "@media (min-width: 480px) {\n    $1\n}",
		"description": "Se utiliza para las pantallas de los Celulares"
	},

	"Media Querie 768px - Tablet: digiraldo": {
		"prefix": "mq-2-768",
		"body": "@media (min-width: 768px) {\n    $1\n}",
		"description": "Se utiliza para las pantallas de las Tablets"
	},

	"Media Querie 992px - pantalla: digiraldo": {
		"prefix": "mq-3-992",
		"body": "@media (min-width: 992px) {\n    $1\n}",
		"description": "Se utiliza para las pantallas de las Laptops con baja resolucion"
	},

	"Media Querie 1140px - Laptop: digiraldo": {
		"prefix": "mq-4-1440",
		"body": "@media (min-width: 1140px) {\n    $1\n}",
		"description": "Se utiliza para las pantallas de las Laptop o Computadores portatiles"
	}
}

## 206. Mejorar el performance del código con Gulp y CSS Nano
npm i --save-dev cssnano autoprefixer postcss gulp-postcss
gulp css

## 207. ¿Qué es un Sourcemap, para que sirve y como se crea?
npm i --save-dev gulp-sourcemaps

# Copiar archivos y carpetas En PowerShell
copy-Item -path 'c:\SourceFolder\*.foo' -destination 'c:\DestFolder'
copy-Item -path 'c:\SourceFolder' -destination 'c:\DestFolder' -Recurse -Force -Passthru

copy-Item -path 'C:\Users\disan\OneDrive - Office 365\Documents\GitHub\curso\web\FestivalMusica_inicio' -destination 'C:\Users\disan\OneDrive - Office 365\Documents\GitHub\curso\web\cem2' -Recurse -Force -Passthru

## 208. Mejorando Código JS con Terser y Gulp
npm i gulp-terser-js


Fuente: https://www.enmimaquinafunciona.com/pregunta/17150/escribir-un-powershell-script-para-copiar-archivos-con-cierta-extension-de-una-carpeta-a-otra

https://matthewtrainingcenter.org/
@media (min-width: 480px) {
  .tribe-events-event-image {
    display: inline-block; /* Acepta margin y width y no se puede colocar elemento al lado */
}
}



### Activar servicios apache y mysql
Buscar: servicios