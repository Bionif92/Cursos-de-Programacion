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
	background: #n1n2n3n4 // n1 rojo, n2 verde, n3 azul, n4 opacidad
}
````
**html color code es el mas util buscando en google para elegir tu color**

### Unidades de medida

Unidades absolutas:

 - Pixeles
 - mm, cm, in (para impresión)

Unidades relativas:

Unidad que depende de otro valor

 - Porcentaje (del elemento padre)
 - em (va al elemento padre, se fija en la propiedad y lo multiplica por el valor del em. Si no tiene esa propiedad, busca al siguiente)
 - rem (va a buscar el elemento raiz, html, y multiplica el valor)
 - vh (viewport height) altura de la pantalla, es un porcentaje, vw (viewport width)
 - vmax: compara el vh y vw y da el mas grande, lo mismo con vmix

### Fondos

````css
.box {
	background-color: ;
	background-image: url();// podes poner url
	background-size: ;// 100 % se adapta al ancho, contain obliga imagen a adaptarse, cover rellena
	background-position: center;// left, right, top, bottom
	background-repeat: no-repeat;// no repite la imagen, repeat-x o y repite en los ejes
	background-attachment: fixed;// mueve la imagen mientras hacer scroll
	background: ;// una forma de agregar las propiedades todas juntas, ver en internet
}
````

### Gradientes

Transición entre colores

````css
.box {
	background: linear-gradient(position,color1 %,color2,color3);// position: to right, to bottom, to left, to top; el % dice cuanto de ese color poner
	background: radial-gradient(color1,color2);
	background: conic-gradient(color1,color2);
}
````

### Sombras

Tres tipos:

 - Box shadow- caja
 - Text shadow - texto
 - Drop shadow - imagen

````css
.box {
	box-shadow: 1horizontal 2vertical 3desenfoque 4extension a difuminar 5color// las primeras 4 propiedades en px, el tercero es el mas importante
}

p {
	text-shadow: 1horizontal 2vertical 3desenfoque 4color;
}
````

Para imagenes png que no tenga fondo:

````css
img {
	filter: drop shadow (1horizontal 2vertical 3desenfoque 4color);
}
````

## CSS Intermedio

### Selectores Avanzados

#### Selector de Atributos

````css
img [src='image.png'] {

}
// para todas las imagenes que terminen con png - scr$='png'
// para imagenes que empiezan con image - src^='image'
````

#### Selector Descendente

````css
ul li { // busca li dentro de ul
}
````

````css
li > strong { // si o si strong tiene que ser hijo de li
}
````

#### Comentario

````css
/* Comentario*/
````

#### Selector Adyacente

````css
h1 + p { // le da estilo al primer p que este despues de h1
}
// h1 + p + p -- a un p que le sigue a un p que le sigue a un h1
````

#### Selector hermanos generales

````css
h1 ~ p { // le da estilo a todos los p que este despues de h1
}
````

#### Selector multiple

````css
h1, p { 
}
````

### Herencia, Cascada y Especificidad


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ0NzgxMDIzNiwxMTQyMTUyODgxLDEyMj
MwMTI0MTAsMTQ3MTk1NjkyMyw1Mjg2NjA4NzUsLTE5ODU4ODI2
ODAsMTc0OTI3OTQ2OCwxMzM3ODk5MDIwLC0xMzE4MjY0MjYxLC
0xMDE4MTUzMDk5LC0xNTQzMzAzMzM2LDE3NTExMTYxNDksODA0
MTA4NjQzLC0xOTYwOTgwNzgsMTM1Njc0ODQxNSwtMTQzNzI1ND
I5MSwtMTM1NDM5NTMwLC02MDQ4NjA2NDAsMTMzNDU0MjQzLC05
NzQyNzk3MzJdfQ==
-->