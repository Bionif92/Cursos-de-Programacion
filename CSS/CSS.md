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
 - Cross Axis - Eje perpendicular al principal

### Flex Direction

Creamos una caja con clase flexbox y tres item con clase flex-items para el ejemplo

````css
.flex-items {

}

.flexbox {

}
````

<!--stackedit_data:
eyJoaXN0b3J5IjpbODAzMTEwOTY0LDE2MjQ1NzA4NiwtNjc4MT
M3NDQ5LDEwMDU4MjczMTYsLTExMjk0MjM0MjYsLTE0MzQzMzY0
MjYsODQyNjQ3MzM0LDgyMjg4NjAwOSwtODc3MTQxNzE3LC0yMD
Y3MTQ4MDI0LC0xNTY1NDU1OTc3LDc0Njg5NDgwNywxNTMyNzc3
MjY1LDE1Nzk0MDcyNjAsLTExNTY1OTg1NTYsLTkyNTc2Nzg0Mi
wtMTU5MTcwNjQxNSw0Mzg4Mjk1NjAsLTEyMjExNjEzMzAsMTQ5
NTYxNDgzOV19
-->