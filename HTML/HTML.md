# HTML Course

## HTML Básico

Hyper Text Markup Languague

Es la estructura de la pagina Web

### Etiquetas

````html
<tag>.....</tag>
````

### Estructura inicial

````html
<!DOCTYPE  html> // version html
<html  lang="en"> // idioma
<head> // formato pagina, no visible
	<meta  charset="UTF-8">
	<meta  name="viewport"  content="width=device-width, initial-scale=1.0">
	<title>Primera Web</title>
</head>
<body>
// aca va mi pagina
</body>
</html>
````

### Párrafos

````html
<p>.....</p>
````

### Encabezados

````html
<h1>.....</h1>
````
Tenemos hasta el h6, podemos agregarlos todos de una con `h$*6`
Mas chico el numero, mas chico el encabezado

**Se usa solo un h1 por pagina web**

### Listas

Dos tipos: ordenadas y desordenadas

#### Ordenadas

````html
<ol>.....</ol>
````
adentro van los `<li> ` items

Van a ir con numeros al inicio, ordenados, como estandar (podes cambiar con Css)

#### Desordenadas

````html
<ul>.....</ul>
````
adentro van los `<li> ` items

Van a ir con puntos al inicio, ordenados, como estandar (podes cambiar con Css)

### Enlaces

````html
<a>.....</a>
````

#### Atributos 

Caracteristicas de los elementos

Tenemos que colocarle el atributo de hipervinculo

````html
<a href='https://url'>.....</a>
````

**Podes enlazar otros htlm para moverte entre paginas**

#### Enlance en otra Pestaña

````html
<a href='https://url' target='_blank'>.....</a>
````

#### Atributo titulo

````html
<a href='https://url' target='_blank'title='titulo'>.....</a>
````

Te muestra cuando pasas con el mouse por encima ese titulo

### Imágenes 

````html
<img src='imagen.png'alt='texto'title=''>
````
`alt`muestra un texto descriptivo si la imagen no carga

Se autocierra el html de imagen

### Rutas

Ruta absoluta - podes acceder desde cualquier lado

Ruta relativa - cambia si modificas la posición del archivo

````html
<a href='../listas.html'>Apartado de listas</a>
````
Para ir una carpeta para atras
Para la misma carpeta o para adelante, escribi la carpeta en las que se encuentra como la ruta

### Formularios

````html
<form>
	<input type='text'>
	<imput type='submit'>
</form>
````

Hay muchas variantes de input type (email, password, checkbox, radio, file, date)

Atributos importantes en formularios:

 - required (obliga a colocar el dato para avanzar)
 - name (le coloca la etiqueta al valor)
 - placeholder (lo que esta escrito en el campo antes de completarlo)
 - value (se guarda el dato para despues usarlo en js)

### Divisor

Bloque divisor
````html
<div>.....</div>
````
Podemos colocar cosas adentro de esta caja

## HTML Avanzado

### Meta etiquetas, comentarios e iconos

#### Comentarios

````html
<!--comentario-->
````

#### Iconos

Icono de la ventana

````html
<link rel='icon' href='icono.png'type='image/png'>
````
Imagen de 32x32 o 64x64 px

#### Meta etiquetas

Describir ciertos aspectos de nuestra web - Como se llama la web en un enlace o búsqueda google
Ej
````html
<meta  charset="UTF-8"> // contiene todos los caracteres

<meta  name="viewport"  content="width=device-width, initial-scale=1.0"> // zoom 100% con ancho adaptado al dispositivo
````

````html
<meta  name='description' content='Esta pagina se trata de ...'>
<meta name='keyword' content='palabraclave1,palabraclave2'> // busqueda google
Otras meta: author, robots (importante, buscar en google),title,OG (importante)
````
Podes generar con:
https://metatags.io/

### TextArea

Para escribir texto, que puede cambiar sus dimensiones de la caja

````html
<textarea placeholder='Deja tu mensaje'>...</textarea>
// readonly atributo para solo leer
// disable atributo no podes hacerle clic
// maxlength='140'
// rows='5' puede escribir solo 5 lineas
````

Hay que modificar en css, para restringir la caja y sus dimensiones a lo que queremos

````css
textarea {
	min-width:100%;
	resize:vertical;//solo puede moverse la caja de forma vertical
	min-height: ;
	max-height: ;
	// tenes que poner tu tipografia si queres modificar la predefinida
	// para que el texto se adapte form-sizing, todavia no esta implementada
}
````

### Labels

Etiquetar elemento

````html
<label>Nombre Completo</label>
````

Luego modificar con css el estilo. Para modificar posición, modificas la otra caja contra la que esta pegada o usar:
`line-height: ;`

**Para que no sea redundante el label con el placeholder, poner un ejemplo en el place holder**

Para que al clickear label te mande al lugar donde tenes que completar, al input le pones un `id` y al label le pones el atributo `for` apuntando al `id`

### Select, Datalist y Option

#### Select

Seleccionar una opcion entre varias opciones

````html
<select type='type-of-user'>
	<option value='user1'>option1</option>
	<option value='user2'>option2</option>
</select>
// el value es para despues usarlo con js
````

en css, no se puede retocar mucho las posiciones

#### Datalist

Escribimos algo y se autocompleta

````html
<input list='referente'>
<datalist id='referente'type='type-of-user'>
	<option value='user1'>option1</option>
	<option value='user2'>option2</option>
</datalist>
// podes cambiar el value a option1 para que aparezca el nombre del referente y no user1
````

### FieldSet y Legend

Agrupar y etiquetar los elementos de un formulario

````html
<form> 
	<fieldset>
		<legend>Información basica</legend>
		<imput type='text'placeholder='Nombre'>
		<imput type='text'placeholder='Apellido'>
	</fieldset>
</form>
````

### Details and Summary

Contenido desplegable

````html
<details>
	<summary>Texto Inicial</summary>
	Texto Desplegable // o un h1, un ul, lo que necesites
</details>
````
Para FAQs son muy frecuentes

### Enlaces Avanzado

#### Enlace a otro elemento
````html
<a href='#proceso'>Proceso</a>
````
Le pones el id al apartado que queres que te lleve este vinculo

#### Descargar el contenido

````html
<a href='terms.html'download>Descargar</a>
````

#### Mandar a otra pagina

````html
<a href='bebita.com' rel='noopener' target= '_blank'>Bebita.com</a>
// noopener -- no permite el acceso a window.open
// noreferrer -- lo mismo que el anterior y tampoco de donde viene la persona, visita anonima
// nofollow -- no la indexes
podes usar las tres a la vez, para dar libre albedrio al usuario
````

#### Mandar un mail

````html
<a href='mailto:mail'download>Mandar Mail</a>
// en vez de mailto, puede ser tel (telefono)
````

### Tablas

````html
<table>
	<tr>//fila
		<th>Dato 1</th>//Encabezado
		<th>Dato 2</th>
		<th>Dato 3</th>
	</tr>
	<tr>//fila
		<td>Dato 1</td>//columna
		<td>Dato 2</td>
		<td>Dato 3</td>
	</tr>
// Subtotal podes usar th
</table>
// Para decirle al navegador las partes de la tabla,los englobamos en thead,tbody y tfoot
// para anexar dos filas, atributo colspan='2'
````

### Audio y Video

#### Video

Extensión mp4

````html
<video autoplay controls muted src='video.mp4'>
Tu navegador no soporta video // Mensaje si no reproduce
</video>
// reproducción automatica en silencio
// loop atributo para bucle
````

Subtitulos con:

````html
<track src='subtitulos.vtt'default kind='captions' srclang='es' label='Español (Latinoamérica)'>
````

#### Audio

Lo mismo que video cambiando el tag por audio

Convertí el archivo en audio para que no pese mucho y cargue mas rápido 

### Lazy Loading

Contenido va cargándose cuando el usuario llega esa sección

````html
// atributo loading='lazy'
````

Baja tiempo de carga a objetos que se veran cuando scrolleas


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwNDQwNjI4NjksMTE5NTgzNDY2NywtOT
I3ODA3MDQyLC0xNDQ3Nzc5ODYzLC0xMzEyNzYyODI3LC0xMzU5
MDc5NjUxLC0xMTcxMDMyMTQyLC0xMTM5ODE1NTMzLC02NTcyOD
I5MzMsMTUyNDI3NjE0NCwyMDMyMTM4Mjk0LC0zOTY0NzA1Miwt
MTI5MTU4OTY0MCwxMjY0MTk5ODkzLC04ODExODQ0NjQsMTY0Mj
QxMDA0NywtMzg5NzQwMDYsLTE2NDMzMDY3ODAsMTQwMzg5NjIx
Miw0OTc4NjkzMDhdfQ==
-->