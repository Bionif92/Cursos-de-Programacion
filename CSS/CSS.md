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

#### Herencia

Hay propiedades que pueden heredarse de los padres

Los elementos buscan en los elementos superiores ciertas propiedades

`widht: inherit` // si queremos que herede cierta propiedad
`color:initial` // mantiene el de defecto , unset si queremos dejecto del inherit, revert intenta encontrar estilo al usuario o sino vuelve a inherit

#### Cascada

Especificidad - Puntuación de un estilo

El orden en el que colocas las propiedades es importante

**Si la especificidad es igual, la ultima propiedad es la que queda en el estilo
Si el elemento es mas especifico, le da prioridad (usando clases)**

**Se es mas especifico con un id que una clase**

**Si el estilo se lo damos en el htlm, esa es de mayor prioridad que el id**

Si al valor de css, le anexamos al lado `!important` esta va a ser la maxima prioriridad

### Pseudo-Clases

Seleccionar un estado especifico de un elemento que seleccionamos

````css
h1:hover { // el elemento cambia cundo el mouse esta encima
	color: ;
}

.header__nav-item  a:not(:hover) {//para cuando no esta encima
	text-decoration: none;
}
````
`active` cuando se hace clic sobre el elemento

````css
li:first-child { // busca el primer li
	color: ;
}
````
`last-child`ultimo
`nth-child(n)` selecciona el elemento que queramos
`nth-child(2n)` saltea de a uno, podes cambiar el primer valor
`nth-of-type(n)`no tiene en cuenta otros hijos que no sean li en este caso, para la busqueda del elemento
`not(.excluir)` selecciona todos menos el que tiene la clase excluir

````css
div:empty { // solo a los elementos vacios
	background-color: ;
}
````

````css
:root { // selecciona a los elementos raiz
	color: ;
}
````

````css
input[type='checkbox']:checked { // si esta chequeado da este estilo
	color: ;
}
````

````css
a:link { // elemento que no fue visitado
	color: ;
}
a:visited // para ya visitados
````

````css
input:valid { // si es valido el input
	color: ;
}
input:invalid// si es invalido
````

#### Is, Where y Has

````css
section:is(.elemento1, .elemento2, .elemento3) { // agrupa los elementos dentro de uno que lo contiene
	color: ;
}
where da la misma especificidad que el elemento, is da una arriba
section:has (.elemento1)// modifica el elemento si lo tiene
ul:has(+div) // seleccionamos el ul que tiene un div a continuacion
label:has(input:valid)// le da estilo al label que tiene la condicion
````

### Pseudo-Elementos

Representa una parte especifica de un elemento

````css
h1::first-letter { // selecciona la primera letra del h1
	color: ;
}
div::first-line // primera linea del div
h1::selection // cuando lo seleccionas con el mouse 
input::placeholder//modificarlo
li::marker// cambia los puntitos de la li
li::before // podes poner un contenido extra entre el punto y el contenido de la lista
li::after// lo mismo que el anterior pero para despues
````

### Metodología BEM

Block Element Modifier

Reutilizar codigo como las clases

Bloque: componente de pagina que podemos reutilizar (barra de navegacion, formulario)

Elemento: parte de un bloque (iconos)

Ej en html: Bloque: `class='lista'`
Elemento: `class='lista__item item--importante'` esta ultima es la clase modificadora del elemento

````css
.lista__item {// las propiedades generales
}

.item--importante {// el item especifico
}
````

Si hay mas listas y queremos modificar una puntual, colocamos clase modificadora:
`class=lista lista--vieja` y en css:

````css
.lista--vieja {// cambia toda esa lista elegida
}
````

### Display

Tenemos dos `<a>`uno al lado del otro:

````css
a {
	display:block;// ocupa ancho disponible, comienza nueva linea
}
````
Convetimos elemento de linea`a` en uno de bloque

````css
p { //dos p uno al lado del otro
	display:inline// los pone en la misma linea
}
````
padding y margin solo funcionan horizontalmente en elementos en línea

En una tabla, tiene un `display:table-cell` por defecto

La funcion `display:inline-block` tiene las propiedades para modificar en bloque, viendose todos en una  misma linea

`display:none` no ocupa espacio en la pagina y no se ve

### Posición relativa

Los objetos tienen `position:static` como predefinida
````css
.box { 
	position:relative;// permite mover el elemento desde su posicion original, a una relativa a ese punto
}
````
Permite las cuatro propiedades: top, bottom, left, right para los otros elementos
Prioridad a left contra right
Prioridad a top contra bottom
Nueva propiedad: `z-index` pones en valores de a 10, la box en 10 y el elemento que queres mandar adelante, valor de 20

### Posición Absoluta

````css
.box--blue{ 
	position:absolute;// lo primero que hace es no acupar lugar en la pagina
damos los valores desde el punto arriba a la izquierda de la ventana para posicionar
}
````

Para que los ceros no sean en la ventana y si en la caja, ponemos a la caja `position:relative`, pero solo sirve si es un hijo

**Si pones bottom:0, arranca desde el bottom de la caja, importante ya que no es igual al movimiento de la posicion relativa del punto anterior**

**Si pones las cuatro posiciones en 0 y el margin en auto, el elemento se centra en el bloque**

### Ventanas Modal

Creas un modal con las clases

Pones al modal position absolute y sale del flujo
El contenido del modal, colocarlo en una caja para darle estilo
Pones un background color black, width:100vw.height:100vh para que tenga contraste en toda la pagina
Para el boton de cerrado del modal, poner la caja con position relative, y moverlo donde queremos

**Podes usar etiqueta dialog para abrir y cerrar el modal sin necesidad de programar en js -- ver en internet**

**Ver dialog:backdrop tambien**

### Posición Fixed y Sticky

````css
.box{ 
	position:fixed;// como el absolute, pero no puedo poner una caja contenedora y usarla como relative a esa, ademas la caja se queda fija aunque hagamos scroll
	position:sticky;// scrolleas y se vuelve fija en la pantalla a partir del punto que le colocaste (en el ej. top=20px)
}
````

### Transiciones 

Gradual la transición de un estado a otro en un elemento

La transición tiene que estar en el elemento inicial

````css
.box{ 
	color: red;
	transition property: ;// ej: color, podes poner all para que todas transicionen, pero hace el navegador mas lento
	transition duration: 1s;
	transition delay: 3s;// despues de 3 s empieza transición
}

.box:hover{
	color:white;
}
````

#### Curvas de Bezier

Movimiento de la caja suave o brusco

````css
.box{ 
	transition-property:left;
	transition-duration:1s;
	transition-timing-function: ;// ease:defecto, ease-in:lento a brusco,ease-in-out:lento/brusco/lento, ease-out:lineal
	left:0;
}

.body:hover .box {
	left:400px
}
````
La curva de bezier son funciones para describir la velocidad

Buscarlas en internet https://cubic-bezier.com/

y colocarla `transition-timing-function: cubic-bezier() ;`

### Desbordamiento (overflow)

Manejar contenido que sobresale de su contenedor

````css
.box{ 
	overflow: ;//visible:defecto, hidden:se oculta, scroll: si queremos solo un scroll overflow-y:scroll, auto: el mejor de los cuatro
}
````

### Control flujo de texto

Una caja que tiene texto

````css
.box{ 
	white-space: ;//normal:defecto,nowrap: no hay saltos de linea,pre: salto de linea puestos en el html, pre-wrap: lo mismo que el anterior pero si ve que desborda hace salto
	text-overflow: ;//ellipsis:tres puntitos si se desborda contenido y lo ponemos en hidden, clip:palabra se recorta
	word-break: breal-all;//rompe la palabra si se desborda y la manda abajo, anywhere: si la palabra es largas la rompe
	text-wrap: balance// balancea el texto para que quede parejo, pretty: que no queden palabras sueltas al final y al inicio, usada mayormente en parrafos
}
````

### Object Fit y Object Position

Como se comporta contenido cuando se le da ancho y alto 

````css
.img{ 
	width: 400px;
	lenght:200px;
	object-fit: ;// fill:defecto, se adapta, contain: imagen entre una vez en la resolucion que le dimos, una de las dos dimensiones esta al 100%, cover: se adapta, none: medida original del objeto, scale-down: elige entre contain y none y se queda con la mas chica
	object-position: ;//muestra la posicion de la imagen con las 4 direccionales(top,bottom)
}
````

### Contorno (outline)

Entre el margin y los bordes estan los contornos, no ocupa espacio

````css
.box{ 
	outline-offset: ; // separacion del borde
	outline-color: ;
	outline-style: ;
	outline-width: ;
}
````
Si queremos dar un borde por encima del borde cuando pasamos por arriba con el mouse, usamos esta propiedad con `hover`

En los input aparece por defecto cuando pasamor por arriba del mouse. Para sacarlo:

````css
.input:focus.visible{ 
	outline: none;
}
````

### Emmet

Plug in para facilitar la creación de cosas en htlm y css

HTML
```` html
html enter -- crea el tag html
h1 enter -- crea el tag h1
ul>li -- crea ul con li adentro
ul>li*4>a -- crea un ul con 4 li que tienen a adentro
ul>li*4>a.link -- Clase link al a
ul>li*4>a#link -- Id link al a
{} -- le colocas el contenido adentro 
{link $} -- coloca el contenido como link 1, link 2
```` 
CSS
```` css
header {
	m10 -- margin:10px //10 solo es px, 10p es 10%, 10
	bgc -- background-color
}
```` 

## CSS Flexbox

### Introducción a Flexbox

Otro modelo de caja: que el contenido de la caja sea flexible y se adapte a la visualización

Hay dos elementos:

 - Caja contenedora
 - Flex items

Los elementos son unidireccionales, van en la dirección que elegimos

Modos:

 - Row
 - Row-Reverse
 - Column
 - Column-Reverse

Ejes:

 - Main Axis - Eje principal, donde se mueven los elementos
 - Cross Axis - Eje cruzado al principal

### Flex Direction

Creamos una caja con clase flexbox y tres item con clase flex-items para el ejemplo

````css
.flexbox {
	display:flex; // lo primero que hacen los elementos es alinearse y adaptarse, lo que no pueden es crecer su tamaño definido
	flex-direction: row-reverse; // cambian de direccion, tienen por defecto ocupar todo el cross axis
	direction: ;//ltr:left to right y rtl - esto verlo aparte no para flexbox
}

.flex-items {

}
````

### Flex Wrap y Flex Flow

Flex Wrap nos permite controlar el comportamiento de los flex items cuando el espacio del contenedor es insuficiente

````css
.flexbox {
	display:flex;
	flex-wrap: //cambiar o no nueva linea, nowrap: no cambia y es por defecto, wrap: si cambia, wrap-reverse: se comporta a la inversa
}

.flex-items {

}
````

Flex Flow habla del flujo flexible: nos permite decidir la direccion y el wrap

````css
.flexbox {
	display:flex;
	flex-flow: row, wrap; // da direccion y wrap
}

.flex-items {

}
````

### Alineación en los ejes

````css
.flexbox {
	display:flex;
	flex-flow: row, wrap; 
	justify-content: ;// alinear item en eje principal, start:defecto al inicio, end:al final, center: centro, space-between: espaciados a la misma distacia, space-around:espaciado con margen en los bordes, space-evenly: espaciados con misma distancia entre ellos y los bordes
	align-items: ; // alinear los items en el eje cruzado separando la estructura en cajas mas chicas, stretch: defecto,se estiran los elementos para ocupar la flexbox, start: ocupan el contenido que tienen adentro, si no tienen tamaño definido los items, end: posiciona al final, center: centro, baseline: se intenta hacer una alineacion de texto
	align-content: ;//alinear los items en el eje cruzado pero obviando la separacion de la estructura de cajas mas chicas, usa las propiedades de justify-content
}

.flex-items {

}
````
`Justify-content` una o mas lineas en eje principal
`Align-items` se usa cuando hay una sola linea en eje cruzado
`Align-content` se usa cuando hay mas de una linea en eje cruzado

**Para un solo item que queremos centrar, ponemos center en justify-content y align-items o colocar margin:auto en el item**

### Order

El orden que se representan los elementos en pantalla, solo su orden visual no cambia el DOM

````css
.flexbox {
}

.flex-items {
	order:0;// por defecto, tenemos que darle el orden a cada elemento para su representacion visual (-1,0,1,2,3)
}
````
Con todos order:1, tienen la misma jerarquia

### Flex Basis, Shrink y Grow

Flex item son los **hijos directos** del contenedor

````css
.flexbox {
	gap:20px; // separacion entre elementos
}

.flex-items {
	flex-grow: 1;//defecto en 0, le dice que del espacio disponible ocupar todo el espacio. Si a otro elemento le coloco 2, le da el doble de espacio que a los otros elementos
	flex-shrink: ;//hasta cuando se puede encoger cuando se achica la ventana, 0: los elementos no se van a encoger luego de alcanzar su tamaño base, lo mismo que con grow, se le pone valor y el mas alto se encoge mas
	flex-basis: 150px;// esto es lo maximo que te podes achicar, es la minima dimension en direccion del eje principal, es auto por defecto
	flex: ;// resume a las tres anteriores grow,shrink,basis
}
````

### Align Self

Alineación del hijo al lugar donde queremos

````css
.flexbox {
	
}

.item-5 {
	align-self: ;// funciona cuando flexbox tiene align-items, valores:start,end,center,baseline,strech (ocupar todo)
}
````

### Layout con Flexbox

No se coloca height normalmente en los elementos porque rompe la estructura cuando se achica o en las versiones de otros dispositivos, se usa min-height realmente

## Responsive Design

### Bloques y Multimedia flexible

#### Bloques

Contenedores o elementos que se adaptan fluidamente a las resoluciones de pantalla

````css
bloque {
	min-width:
	max-width: // para ajustar la resolucion de la pantalla si cambia
	min-height: // recomendada para que no se desborda
}
````
Contenido flexible sin necesidad de usar flexbox

Si hay dos elementos y ponemos `diplay:inline-block`, si movemos la resolucion no se adapta, para eso usar flexbox

Para eso ponemos los bloques dentro de un contenedor y le ponemos flexbox

#### Multimedia

**Imágenes flexibles**

````css
img {
	max-width:100%;// se adapta al dispositivo
	height:auto;
}
````

**Video flexible**

Lo ponemos en un container:

````css
container {
	position:relative;
	max-width: 100%;
	padding-top: 56,25%;//forma vieja de hacerlo
	height:0;
}

video {
	position:absolute;
	top:0;
	left:0;
	max-width: 100%;
}
````

Nueva forma de hacerlo

````css
container {
	max-width: 100%;
	aspect-ratio: 16/9;
}

video {
	max-width: 100%;
}
````

### Atributos SRCSET y SIZES

**Tema de HTML**

Son atributos para elegir la mejor imagen ante un responsive design

````html
<img src:'dalto-small.png' srcset='dalto-small.png 400 w,dalto-medium.png 600w, dalto.png 1000 w' sizes='(max-width: 400px)300px, (max-width: 600px)500px, 900px'>
// en srcset definimos las imagenes y sus tamaños, y en sizes cual usar
````
Cuando carga la mas grande, no vuelve a las mas pequeñas, solo sirve si la resolución es chica y luego se agranda

### Picture, Source y Media

**Tema de HTML**
Etiqueta picture y source
Atributo media

Para cuando queremos cargue una imagen según la resolución

````html
<picture>
	<source media='(max-width: 400 px)'srcset='dalto-small.png'>
	<source media='(max-width: 600 px)'srcset='dalto-medium.png'>
	<img src='dalto.png'>
// de menor a mayor las imagenes
</picture>
````

Lo mismo que el tema anterior
Soporta webp- ver video Dalto si es necesario

### Media Queries

Adaptar nuestra pagina web a distintas resoluciones

````css
@media print {// solo para el medio de impresión
	body {
		font-size:24pt;
	}
}
````

````css
@media screen and (max-width:500px){// solo aplica para la pantalla y con la condicion de max width
	body {
		font-size:24pt;
	}
}
````
Podes usarla para una flexbox que esta en row, modificarla a columna cuando llega a un width

````css
@media screen and (max-width:600px){// 
	flexbox {
		flex-direction: column;
	}
}
````

### Holy Grail

Tiene 5 secciones: header, main, dos columnas laterales y un footer
En el header puso un nav
En el div puso el main y las dos columnas aside

Coloco en body
````css
body {
	display:flex;
	flex-direction:column;
	align-items:start;
	min-height:100vh
}

footer {
	margin-top:auto
}
````
El segundo aside lo hizo desaparecer cuando baja el tamaño de la ventana
````css
@media screen and (max-width:600px){
	aside:last-child {
	display:none;
	}
}
````
Y cuando baja mas la resolución

````css
@media screen and (max-width:400px){
	main-wrapper {
	flex-direction:column;
	}
}
````
Centra todo el contenido y le da max width para que no se extienda el contenido

### Mobile First

Primero pensar en el celular

El proceso lo haces como si fuera en celu y después con @media le damos min:800 px para verlo cuando la agrandemos

### Feature Queries

Queries si soporta el navegador la feature, sino lo romperia
````css
@supports (display:grid){
	body {
		display:grid;
	}
}

@supports not (display:grid){
	body {
		display:flex;
	}
}
````

### Container Queries

Según propiedades del contenedor dar estilo a elementos internos
````css
.container {
	container-type:inline-size;
	container-name:main; // esto para que solo lo haga en este y no en todos
}

@container main(max-width:500) { //elegimos un solo contenedor
	p {
		font-size:20px;
	}
}
````
Con esto funciona para todos los container

## CSS Grid

### Introducción a Grid

Sistema de diseño bidimensional - crear interfases o layouts complejos

La grilla trabaja en columnas y filas a la vez

Partes:

 - Grid Container
 - Grid Items
 - Bordes de la cuadricula (separan items)
 - Grid Tracks (una fila o una columna)
 - Grid Cell (unidad del item) 
 - Grid Area (mas de una celda unida)

### Creando un grid

````css
.grid {
	display:grid; // cada elemento se pone en una fila
	grid-template-columns: 200px 200px;//medida de las columnas, y dependiendo de cuantas coloques, son la cantidad de columnas
	direction:rtl// igual que con flex, puede cambiarse
	grid-template-rows: ;// cantidad de filas y medida
}

.grid-item {
}
````

### Unidades Auto y FR

````css
.grid {
	display:grid; 
	grid-template-columns: auto 200px;// ocupa tamaño de la ventana pero al elemento podemos ponerle el ancho deseado, quedando el elemento y el espacio en blanco dentro de la columna
	grid-template-rows: 1fr 1fr;
}

.grid-item {
}
````

Con `auto`, agarra el espacio que sobra y lo reparte entre los elementos que tengan la función auto sacando el contenido de cada uno

Si cambiamos `auto` por `fr`ajusta el espacio disponible y el contenido de forma igual, a menos que el contenido sobrepase la medida en tal caso trata de ajustarse

Se usa mas `fr`

### Repeat() y MinMax()

````css
.grid {
	display:grid; 
	grid-template-columns: repeat(4,1fr); // repite 4 columnas de 1 fr, podes agregar otras columnas al lado del repeat()
	grid-template-columns: repeat(3,1fr 2 fr); // repite el patron 
	grid-template-columns: minmax(300px,700px) // crea una columna adaptable, podemos poner mas y usar repeat 
	grid-template-rows: ;
}

.grid-item {
}
````

### Grid Explicito e Implícito

Hay dos tipos de grid:

 - Explicito (creamos con las template)
 - Implícito (no creadas y se adaptan a la grilla)

````css
.grid {
	grid-auto-rows: 80px; // por ahora solo se crean filas abajo, pero podemos cambiar la direccion y vamos a tener que colocar las auto columns
	grid-auto-flow:column; // cambia el esquema, creando nuevas columnas,dense: rellena espacios vacios, se usa cuando hay muchos elementos
}

.grid-item {
}
````

### Grid Gap

La separación entre elementos

````css
.grid {
	column-gap: 10px;
	row-gap: 10px;
	padding: 20px; // para que quede igual a las separaciones de los elementos
}

.grid-item {
}
````

### Grid Dinámico y Responsive

````css
.grid {
	display:grid; 
	grid-template-columns: repeat(auto-fit, minmax(150px,1fr));// crea columnas para adaptar el contenido
	grid-template-rows: ;
	grid-auto-flow: row;
}

.grid-item {
}
````
La diferencia entre `auto-fit` y `auto-fill`:

 - Auto fit: adapta las columnas
 - Auto fill: rellena con mas columnas, vacias si no hay mas elementos

### Grid Row y Grid Column

Las cantidad de grid row y grid column es la cantidad de row y de column +1 en cada caso.
Empieza grid row, despues elemento, despues grid row y asi...

````css
.grid {
}

.grid-item:first child {
	grid-row-start:1;
	grid-column-start:1;
	grid-row-end:3;
	grid-column-end:3 o span 2;// agranda el bloque para un item, podes poner span 2 que agranda en columna dos espacios
	grid-column:1/span2; //abrevia lo anterior visto
}
````
**Si queremos poner una imagen, en ves de ponerla como item, ponerla como background en css**

### Grid Flow: Dense

Cuando hay muchos elementos para la grilla, y agrandamos algun item que cuando modificamos la pantalla no entra correctamente en la imagen

````css
.grid {
	grid-auto-flow:dense;// se rellena pero no respeta la posicion impuesta
}

.grid-item:first child {
}
````

### Grid Area

Asignar un elemento a un área especifica que nosotros dimos en grid

````css
.grid {
}

.grid-item:first child {
	grid-area: span 2/span 3; // row/column crecer dos filas y crecer tres columnas, se pone la posicion antes de cuanto crece
}
````

Otra forma de hacerlo

````html
body
	header
	nav
	main
	aside 
	footer
````

````css
.grid {
// otra forma de crear el área
	grid-template-areas: 
	"header header header"
	"nav main aside"
	"footer footer footer"
	;
}

header {
	grid-area: header;
}

nav {
	grid-area: nav;
}

main {
	grid-area: main;
}

aside {
	grid-area: aside;
}

footer {
	grid-area: footer;
}
````

Saca el header y el footer del div para el main aside y nav
lo hace flex para esos tres elementos
y hace un grid para los de adentro

### Alineación en Grid

````css
.grid {
	justify-items: ;// mueve elemento en su cuadricula,strech por defecto, start center y end mas comunes pero hay mas, self-start self-end tiene la direccion del hijo en cuenta, left y right tambien son opciones
	justify-content: ;// mover la grilla completa, center, space-around, space-evenly, space-between
	align-items: ;//mismo que justify pero en el eje vertical
	align-content: ;//mismo que justify pero en el eje vertical
}

.grid-item:first child {
	justify-self: ;// mueve el item independiente de la grilla
}
````

### Sub Grid

Hijos de un Grid Item también formen parte de la grilla principal

Creas un sub-grid item adentro del item:

````css
.grid {
	
}

.grid-item:first-child {
	display:grid;
	grid-template-columns: repeat (4, 1fr);// cambiarlo a subgrid
	grid-template-rows: repeat (4, 1fr);// cambiarlo a subgrid
	gap:10px;
}

.sub-grid-item {
	text-align:center;
	width:200px; //sobresale, por lo que se superpone a la grilla, para eso hay que cambiar el grid template
}
````

### Pagina Web

El role button en el label es para la accesibilidad

Con el # en el link no se resetea la pagina

El * en css selecciona todos los elementos del documento

Siempre se pone una caja, en este caso el div profile wrapper para limitar la caja y darle estilo con css al contenido

Para centrar data adentro de grid, poner place-content:center

Lo siguiente para poner una capa oscura en la imagen
````css
background-image: linear-gradient(#0007,#0007), url('dalto.png');
````

## Animaciones 

### Transiciones (Repaso)

````css
barra {
	width: 10%;
	transition: width 1s linear;// tarda un segundo en completar la transicion
	transition: width 1s steps(10)// se carga en un segundo en 10 partes
	background-color:blue;
	transition: background-color .6s steps(6)// va cambiando del azul al rojo en 6 pasos
}

barra:active {
	width: 100%
	transition-duration: 4s;// tarda 4 segundos en volver
	background-color:red;
}

@media (prefers-reduced-motion: reduce) {// para desactivar las animaciones para un epileptico
	.barra {
		transition: none;
	}
}
````

### Animaciones

Transición entre un estado a otro, pero a diferencia de las anteriores podemos ejecutarlas cuando queramos y no con un evento disparador, y se puede repetir las veces que queramos

````css
.barra {
	background-color:blue;
	width:10%;
	animation-name: llenar-barra;
	animation-duration: 2s;// se ejecuta una sola vez
	animation-delay: 3s;//puede ser negativo para que la animacion alla arrancado desde antes
	animation-fill-mode: ;// como vas a quedar cuando finalices, backwards: modo antes de animación,forwards: arranca como esta incialmente, cambia a la animacion y queda con la animacion del final, both: arranca con las propiedades de la animacion inicial y queda como la animacion al final
	animation-timing-function: linear;// la curva
	animation-iteration-count: ;//repeticion, infinite/3/
	animation-direction: ;// reverse/alternate/alternate-reverse
	animation-play-state: ;//puede usarse con hover o active para aprovechar esta propiedad, running(defecto)/paused
}

@keyframes llenar-barra //nombre que le ponemos a anim {
	from {
		width:0%;
	}
	to{
		width:100%;
	}
}
````

### Botones Animados

Armo un:

 - Wave Button
 - Neon Button

Ver video o buscar en internet, para armarlo, son muchos pasos

Uso after, before y animaciones, y el filter drop shadow

#### Efecto TypeWriter 

Parrafo con el texto, usa el filter drop shadow en el container para iluminarlo

````css
body {
	display:flex;
}

.container {
	margin:auto;
}

.text {
	animation: grow 3s both steps(7);
	overflow:hidden;
	position:relative;
}

.text::before { //simula la barra de escritura
	content:'';
	width:1px;
	height:100%;
	background-color: blanco;
	position:absolute;
	right:0;
	animation: titilar .36s infinite alternate
}

@keyframes grow {
	from {
		width:0%;
	}
	to {
		width:100%;
	}
}

@keyframes titilar {
	from {
		opacity:0;
	}
	to {
		opacity:1;
	}
}
````

### Animaciones basadas en Scroll

Dos tipos de formas de definir un timeline basado en scroll:

 - Por la barra de desplazamiento
 - Por visión del elemento en la pantalla

#### Por barra de desplazamiento del body
````css
body {
	height: 200vh;//para que aparezca el scroll
}
.box {
	position:fixed;
}

.barra {
	padding: 40px;
	background-color: blue;
	border-radius: 30px;
	width: 10%;
	animation-name: llenar-barra;
	animation-fill-mode: both;
	animation-timing-function: linear;
	animation-timeline: scroll ();//ahora depende la animación del scroll
}

@keyframes llenar-barra {
	from {
		width:0%;
	}
	to{
		width:100%;
	}
````

#### Por barra desplazamiento del container
````css
body {
	height: 200vh;//para que aparezca el scroll
}
.container {
	scroll-timeline: --containerScroll block;
	overflow-y: scroll;
}

.box {
	position:fixed;
}
.barra {
	padding: 40px;
	background-color: blue;
	border-radius: 30px;
	width: 10%;
	animation-name: llenar-barra;
	animation-fill-mode: both;
	animation-timing-function: linear;
	animation-timeline: --containerScroll;
}

@keyframes llenar-barra {
	from {
		width:0%;
	}
	to{
		width:100%;
	}
````

#### Por visión del elemento en pantalla
````css
body {
}

.crecedor {
	height: 100vh; //puso dos secciones entre la caja para que se vea animación solamente
}

.box {
	animation: llenar-barra;
	animation-timeline: view();//empieza cuando se ve en la pantalla y termina cuando sale de la pantalla
}
````
**Para este podemos hacer que se empiece a ver cuando otro elemento se vea con `view-timeline` como en el de scroll**

### Rango de animaciones

````css
body {
}

.crecedor {
	height: 100vh;
}

.box {
	animation: llenar-barra;
	animation-timeline: view();
	animation-range-start: cover 50% ;// defecto normal,en este caso arranca luego de la mitad del view port
	animation-range-ende: cover 80%;
}
````

Usar esta pagina para ver la animación como quedaría:

https://scroll-driven-animations.style/tools/view-timeline/ranges/#range-start-name=cover&range-start-percentage=0&range-end-name=cover&range-end-percentage=100&view-timeline-axis=block&view-timeline-inset=0&subject-size=smaller&subject-animation=reveal&interactivity=clicktodrag&show-areas=yes&show-fromto=yes&show-labels=yes

## Web Hosting

### Introducción al web hosting

Subir pagina a internet

Tipos hosting:

 - Hosting compartido (un servidor, muchas paginas web adentro, versión mas económica, para trafico bajo)
 - VPS (un servidor dividido en maquinas virtuales con recursos asignados, para trafico mediano)
 - Hosting dedicado (dedicar servidor completo para un solo cliente, necesidad de alto rendimiento, trafico alto)
 - Cloud hosting (distribuir todo tu trafico a través de una red de servidores que hace que todo sea mas escalable y flexible, trafico adaptable)

Hay que buscar proovedor de hosting

Requisitos del proovedor necesarios:

 - Soporte 24/7
 - Equipo que solucione todos nuestros problemas
 - Alto rendimiento
 - Confiabilidad
 - Almacenamiento en estado solido
 - Diversidad y flexibilidad
 - Backups
 - Facil de usar

Recomendado: **Hostinger**

El dominio llama al servidor y nos muestra lo que la pagina tiene

https://www.hostg.xyz/SH6cZ

Que plan elegir: Business, plan de 24 meses

### Subir tu WEB a INTERNET

Tablero principal de la pagina de hosting, administración de archivos

Arrastras todos tus archivos a la carpeta public.html

Otro sistema para subir pagina web es usando FTP, forma estandar de transferir archivos desde tu computadora al servidor que aloja tu web

Hay que 


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4ODM4NTgyOTYsMzg5NjgzMDc5LDMzNz
gzMjgyMywyMTQxMjcxMTgyLC0xOTk5MzE3Njc1LDEzNzI5Mjg4
MTAsMjI4NjYwMzMxLDc4MTYyMzQzNCw5NDk2MDIxMywyMTQ2Mj
cxNzgwLC0xMzg4MjIzNjM2LC04OTgzMzY3LDk4OTM0MjY0Niwt
MTIzMjE1ODc4MSwtNTYxMjQxNzQ1LC0xNjMyNDg5NDE0LC0xMT
EzNjkxNTI1LDExNTg4OTQ2OTQsLTY5NTU3NDkzOCw3MTYzMjAx
M119
-->