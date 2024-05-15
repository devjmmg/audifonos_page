# audifonos_page
Página que simula la promoción de productos de audífonos agregando degradados, animaciones, soporte para imaganes avif y webp, estilo Mobile first, FlexBox y CSS Grid.

#Degradado en textos

El siguiente código hace un degradado de izquierda a derecha de azul a verde
.degradado-verde {
    color: transparent;
    background: linear-gradient(to right, var(--primario) 0%, var(--secundario) 100%);
    -webkit-background-clip: text;
}

#Degrdado como fondo con imagen y soporte a imagenes avif y webp

Con el codigo de GitHub: https://gist.github.com/codigoconjuan/3bbdf0f2920cd9c65187128dd1c032cc

Lo agregamos en un archivo js y tambien lo cargamos en nuestro proyecto, despues agregamos la imagen con degrdado.

Este degrdado va hacia abajo en dispositivos menores a 992px

.notavif.notwebp .sobre-sound { --> Cuando no soporte avif ni webp
    background-image: linear-gradient(to bottom, transparent 50%, var(--primario) 0%),url(../img/imagen-mujer.jpg); --> Cargue imagen jpg
}

.webp .sobre-sound { -->cuando soporte imagenes webp
    background-image: linear-gradient(to bottom, transparent 50%, var(--primario) 0%),url(../img/imagen-mujer.webp); -->Cargue imagen webp
}

.avif .sobre-sound { -->Cuando soporte iamgenes avif
    background-image: linear-gradient(to bottom, transparent 50%, var(--primario) 0%),url(../img/imagen-mujer.avif); -->Cargue imagen avif
}

Esta clase contiene el resto de las propiedades de la clase

.sobre-sound{
    background-repeat: repeat ,no-repeat;
    background-position: right center;
    background-size: cover;
}

Cuando el dispositivo sea mayor de 992px el degrdado va a ir a la derecha utilizando el mismo concepto para soportar imagenes.

@media (min-width: 992px) {
    .notavif.notwebp .sobre-sound {
        background-image: linear-gradient(to right, var(--primario) 50%, transparent 0%),url(../img/imagen-mujer.jpg);
    }
    
    .webp .sobre-sound {
        background-image: linear-gradient(to right, var(--primario) 50%, transparent 0%),url(../img/imagen-mujer.webp);
    }
    
    .avif .sobre-sound {
        background-image: linear-gradient(to right, var(--primario) 50%, transparent 0%),url(../img/imagen-mujer.avif);
    }
    /*
    .sobre-sound{
        background-image: linear-gradient(to right, var(--primario) 50%, transparent 0%),url(../img/imagen-mujer.jpg);
    }
    */
}

Flexbox y CSS Grid del codigo 

.sobre-sound-grid {
    display: grid;
    grid-template-rows: repeat(2,50rem);
    row-gap: 5rem;
}

@media (min-width: 992px) { 
    .sobre-sound-grid {
        grid-template-rows: unset;
        row-gap: unset;
        grid-template-columns: repeat(2,1fr);
        column-gap: 4rem;
        padding: 10rem 10rem 10rem 0;
    }
}

.sobre-sound__texto {
    grid-row: 2 / 3;
    color: var(--blanco);
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.sobre-sound__texto h2 {
    font-size: 4rem;
    font-weight: normal;
}

.sobre-sound__texto span {
    font-weight: 900;
}

.sobre-sound__texto p {
    font-size: 2rem;
    line-height: 2;
}

#Animaciones

.producto {
    background-color: var(--grisClaro);
    margin-bottom: 2rem;
    padding-left: 3rem;
    color: var(--primario);
    border-radius: 2rem;
    min-height: 20rem;
    
    background-repeat: no-repeat;
    background-position: 90% center;
    background-size: 13rem;
    
    display: flex;
    flex-direction: column;
    justify-content: center;

    /*
    Propiedad (property): Indica qué propiedad CSS debe ser afectada por la transición. Por ejemplo, color, background-color, width, height, etc. También se puede utilizar el valor all para aplicar la transición a todas las propiedades que cambien.
    */

    transition-property: transform background;

    /*
    Duración (duration): Especifica la duración de la transición. Puede ser un valor en segundos (por ejemplo, 1s) o en milisegundos (por ejemplo, 1000ms).
    */

    transition-duration: .5s;

    /*
    Función de temporización (timing-function): Define cómo cambia la velocidad de la transición durante su ejecución. Algunos valores comunes son ease, linear, ease-in, ease-out, ease-in-out, entre otros.
    */

    transition-timing-function: ease;

    /*
    Retardo (delay): Opcionalmente, especifica un tiempo de espera antes de que comience la transición. Puede ser un valor en segundos o milisegundos.
    */

    transition-delay: .1s;

    /*
    Otro ejemplo mas corto podría ser:

    .elemento {
        transition: width 1s ease-in-out 0.5s;
    }

    */

}

Cuando nos posicionesmos en el producto va a tener una tranformacion (transform) en su escala (scale) se hara mayor y rotara (rotate) un poquito, tambien la letra se hara más grande y tendra el cursos de mano.
 
.producto:hover {
    transform: scale(1.1) rotate(-1deg);
    background-size: 15rem;
    cursor: pointer;
}

@media (min-width:  768px) { 
    .producto:hover {
        transform: scale(1.1) rotate(-1deg);
        background-size: 28rem;
    }
}