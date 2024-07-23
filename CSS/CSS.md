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

Podes usar el tag `span` para seleccionar algo puntual y cambiarle el estilo, pero no es el caso

#### Clases

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

````html
<li id='ingrediente-secreto'>Harina</li>
````

````css
.faltante {
	color: red;
}
````
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYwMzk4MTQ0MiwtMTMwMzc5ODU5MF19
-->