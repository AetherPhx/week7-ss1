# INTRODUCCIÓN
Hasta el momento hemos redactado en CSS plano y este es útil y suficiente para pequeños proyectos. Sin embargo, ahora vamos a profundizar en los estilos aprendiendo sobre preprocesadores CSS.
## ¿Qué es Preprocesador CSS?
Los preprocesadores CSS son herramientas que extienden las capacidades del CSS y permiten escribir estilos de manera más eficiente.
## Ventajas
1. TODO código CSS es SASS, por lo que es fácil de implementar preprocesadores a partir de código ya desarrollado de CSS.
2. Permiten dividir el CSS en múltiples archivos y luego importarlos, mejorando la organización del código.
3. Permiten definir variables para colores, tamaños, fuentes, etc. Esto facilita la la consistencia y el mantenimiento del código.
4. Permiten anidar selectores aumentando la legibilidad de los mismos selectores y la comprensión de los estilos aplicados.
## Desventajas
1. No todo código SASS es CSS, por lo que no se puede regresar de SASS a CSS fácilmente.
2. Necesitas configurar y usar herramientas de compilación para compilar SASS a CSS.

# SASS
## Variables
Permiten almacenar valores como colores, fuentes o tamaños en variables, facilitando la reutilización y el mantenimiento.
```scss
$name: value; // Sintaxis
$primary-color: #fff; // Ejemplo
```
## Scope
Permiten definir variables globales y locales.
```scss
$primary-color: #fff;
body{ background-color: $primary-color;
}
section{ background-color: $primary-color: #000;
}
// Body tendrá el color de la variable global.
// Section tendrá el color de la variable local.
```
## Anidamiento
Permite definir selectores dentro de otros selectores para dar mayor legibilidad.
```scss
nav{
    ul{
        display: flex;
        // More flex props
        li{
            list-style: none;
            a{ text-decoration: none;
            }
        }
    }
}
```
## Ampersan Padre
Permite definir un selector que agrega el valor siguiente al selector padre.
```scss
.nav-menu{
    &__list{
        display: flex;
        // More flex props
        &__item{
            list-style: none;
            &__link{ text-decoration: none;
            }
        }
    }
}
```
```css
.nav-menu__list{
    display: flex;
    /* More flex props */
}
.nav-menu__list__item{ list-style: none;
}
.nav-menu__list__item__link{ text-decoration: none;
}
/* Potenciado al usar BEM */
```
## Import
Permite trabajar en diferentes archivos scss importando sus estilos y variables.
```scss
main.scss{
    @import 'reset.scss'; // Aplica el reset
    @import 'global-variables.scss'; // Define variables globales
    section{ color: $primary-color;
    }
}
reset.scss{
    *{
        box-sizing: border-box;
        padding: 0;
        margin: 0;
    }
    body{ min-height: 100dvh;
    }
}
global-variables.scss{
    $primary-color: #fff;
    $secondary-color: #000;
}
```