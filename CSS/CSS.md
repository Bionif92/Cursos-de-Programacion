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
**Podes colocar mas de una clase, dejas un espacio y escribis la siguiente**

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
	// otra forma
	padding: 10px 0 20px 20px;//arriba, derecha, abajo, izquierda
	// otra forma
	padding: 20px 50 px// arriba/abajo y derecha/izquierda
}
````

#### Margen

````css
.box {
	margin: 10 px; // separación entre cajas
	margin-top: // y todos los vistos en el anterior
	margin: auto; // centra el contenido
}
````

Colapsan los margenes, dejando el mas grande creado, superponiéndose 

### Bordes

````css
.box {
	border-width: 3px;// espesor
	border-color: ; // color
	border-style: black; // estilo (ej solid)
	border-radius: 5px; // redondear el borde (px o %)
	border: 3px solid black;// reemplaza primeras tres
	border-top: ;// left, right, bottom
	border-radius: 5 px 10 px// arribaizq/abajoder y arribader/abajoizq y con las 4 tambien podemos
}
````

### Tamaño de la caja

````css
.box {
	box-sizing: border-box;// hace que el padding el border y el content se ajusten a la medida inicial
}
````

### Colores

 - RGB (red-green-blue)
Hay 256 colores por cada uno (0-255)

````css
.box {
	background: rgb (255,0,0);// red
	background: rgba (255,0,0,0.8);// agregas opacidad
}
````
Busca rgba picker en google y podes ver todos los tonos

 - Hexadecimal

Similar al anterior pero con sistema hexa(16):
0,1,2,3,4,5,6,7,8,9,a,b,c,d,e,f

````css
.box {
	background: #n1n2n3n4n5n6 // n1 red, n2 tono del rojo n1, n3 verde, n5 azul
	background: #n1n2n3n4 // n1 rojo, n2 verde, n3 azul
}
````
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjExNzY2NjE3MSwxODE5ODk1NzQsLTkxOT
gxNjM5OSwtNzE2NDQwNDI5LDExMDIzNzM1NjEsLTYyMDU1Njg2
LC04NTI3NjAwNjYsNDA5OTc0NDYzLDkyMTkzNzExNCwtNDEzMD
M1MTI4LC0xNjEzODQ4NjY2LC04MTI0MjIxNzYsMjExODI1NTIx
NywtMTU3MTc3MTAwLC0xMzE5NjExMzQ1LDI0MDAzMTU1NSwyMD
AxMzA0NzMzLC05MjQwMzkwOTMsLTUwNTgzNjkyNiwtMTk3NzAx
MTYwMl19
-->