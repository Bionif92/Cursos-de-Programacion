# HTML Course

Hyper Text Markup Languague

Es la estructura de la pagina Web

### Etiquetas:

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

### Parrafos:

````html
<p>.....</p>
````

### Encabezados:

````html
<h1>.....</h1>
````
Tenemos hasta el h6, podemos agregarlos todos de una con `h$*6`
Mas chico el numero, mas chico el encabezado

**Se usa solo un h1 por pagina web**

### Listas:

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
<a href='../listas.html'>
````
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE5NDc2MzgyMSwxMDI4NjYxMjM3LC01Mj
EwNzA3MjgsMTc1NDE4NjY2LC0xOTE2NTE0NTMxLC0xMTAwNTEy
ODA1LDc4NDI4NTM3MCwxMTg3OTI3NjU2LDEwOTA0NTMzMzgsLT
EyMjEyMDkzNDksLTE0ODg3OTI5NywxNDcwNjQ5ODQ2LC0xNzI3
ODYwNjQxLC0xMTY0NDAzMzcxXX0=
-->