# CSS Course

## CSS Basico

Cascading Style Sheets

Tres maneras de armar CSS:

 - Go live, escribir propiedades en el mismo html (mala practica)
 - Los estilos como etiquetas en el html (mala practica)
 - Hoja de estilos (recomendada)

### Hoja de estilos

Se coloca en el head:
````html
<link rel='stylesheet' hfef='styles.css'>
````

En la hoja styles.css:

````css
p {
	color: red;
}
````

### Selectores

#### Elemento

````css
li {
	color: red;
}
````

#### Clases

Podes usar el tag `span` para seleccionar algo puntual y cambiarle el estilo, pero no es el caso

Hay que usar las clases para diferenciar:

````html
<li class='faltante'>Harina</li>
````
Hay que colocar el . en css

````css
.faltante {
	color: red;
}
````

#### Id

**Se recomienda solo usar el id especifico en un solo elemento**

````html
<li id='ingrediente-secreto'>Harina</li>
````

````css
#ingrediente-secreto {
	color: red;
}
````

### Propiedades de Texto

````css
p {
	color: red; // color texto
	font-family: ;// tipografias, podes poner mas de una con comas, y si el navegador no la soporta, pasa a la siguiente
	font-size: 13px; // tamaño letra
	font-weight: bold; //negrita u otro grosor, bolder manda al mas grueso 
	font-style: ;//estilo (oblique,italic)
	text-align: ;//posicionar el texto (center,left, justify)
	text-decoration: ;// underline, overline,line-through, podes poner mas de una
	line-height: ;// espacio entre linea y linea
	letter-spacing: 10px; // sepearado entre letras
	text-transform: ;// uppercase,lowercase, capitalize
	text-shadow: ;// sombra, lo veremos mas adelante
}
````
la etiqueta `strong` en htlm sirve para resaltar texto

### Tipografías externas

Buscar google fonts, elegir la version, copias el acceso y lo pegas al lado del link de css en el archivo html. Luego ya la podes seleccionar en css.

Esta es una opcion, la otra y mas recomendable es:

 - Crear una hoja de fonts y anexarla al html
 - En el css:

````css
@font-face {
	font-family: 'nombre de la nueva tipografia';
	src: url (url.ttf) format('truetype') // colocar el formato hace que cargue mas rapido el archivo
	font-weight: 400;// importante para la definicion del grosor y de poder colocar otras tipografias con otros grosores
}
````

 - Descargas la tipografia, y la anexas la url
 - Luego colocarla en el archivo css base

### Modelo de caja

Tiene varias partes:

 - Content - Contenido
 - Padding - Espacio entre el contenido y el borde del elemento
 - Border - Borde
 - Margen - Espacio alrededor de la caja, cuanto separamos una caja de otra caja

Estilo a la caja:

````css
div {
	background:red;
	widht: 200 px;
	height: 200 px;
}
````

### Padding y Margen

#### Padding

````css
.formulario_input {
	padding: 20 px;
	padding-bottom:
	padding-top:
	padding-left:
	padding-right:
}
````
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYzNzYxNzgzNiwtMTMxOTYxMTM0NSwyND
AwMzE1NTUsMjAwMTMwNDczMywtOTI0MDM5MDkzLC01MDU4MzY5
MjYsLTE5NzcwMTE2MDIsLTczNjY3NzE0NiwtMTQ1MjQ0OTEyMC
wyNjY2NzQwOTIsMTk4MTM3MDIyMCwtNDgxMzUxODM5LC0xODUy
Njg3NjU5LC0xMzAzNzk4NTkwXX0=
-->