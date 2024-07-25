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
<textarea placeholder='Deja tu mensaje'>....</textarea>
// readonly atributo para solo leer
// disable atributo no podes hacerle clic
// maxlength='140'
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
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA1Mjg1OTA1NCwtMTQ3NDIxNzE1NiwyMT
M2NTcwNjIyLDE2MTA1MDk2NTgsLTEyNzk0NjcwNjUsLTExNDEx
NzI3OTYsLTE5MjkxMzQ4MzEsNDQ2MzM0Mjg3LC0xMTY3NDE0OT
kxLDExNTYxNDY4NzcsMTAyODY2MTIzNywtNTIxMDcwNzI4LDE3
NTQxODY2NiwtMTkxNjUxNDUzMSwtMTEwMDUxMjgwNSw3ODQyOD
UzNzAsMTE4NzkyNzY1NiwxMDkwNDUzMzM4LC0xMjIxMjA5MzQ5
LC0xNDg4NzkyOTddfQ==
-->