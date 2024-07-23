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

Buscar google fonts, elegir la version, copias el acceso y lo pegas al lado del link de css en el archivo html
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjM4MDUxNjE1LC0xOTc3MDExNjAyLC03Mz
Y2NzcxNDYsLTE0NTI0NDkxMjAsMjY2Njc0MDkyLDE5ODEzNzAy
MjAsLTQ4MTM1MTgzOSwtMTg1MjY4NzY1OSwtMTMwMzc5ODU5MF
19
-->