# CURSO DE TRANSFOMRACIONES Y TRANSICIONES EN CSS

- [CURSO DE TRANSFOMRACIONES Y TRANSICIONES EN CSS](#curso-de-transfomraciones-y-transiciones-en-css)
- [5 Razones para usar animaciones en la web](#5-razones-para-usar-animaciones-en-la-web)
- [Propiedades para crear animaciones con CSS y propiedades animables](#propiedades-para-crear-animaciones-con-css-y-propiedades-animables)
- [Pseudo-clases y pseudo-elementos en las animaciones](#pseudo-clases-y-pseudo-elementos-en-las-animaciones)
- [Timing functions, planos y ejes](#timing-functions-planos-y-ejes)
- [Transform Translate](#transform-translate)
- [Transform rotate, scale, skew y matrix](#transform-rotate-scale-skew-y-matrix)
- [Backface visibility 9/20](#backface-visibility-920)
- [Efecto Parallax 10/20](#efecto-parallax-1020)
- [Efecto parallax: estilos CSS 11/20](#efecto-parallax-estilos-css-1120)
- [Transition property y duration 12/20](#transition-property-y-duration-1220)
- [Transition timing function y delay13/20](#transition-timing-function-y-delay1320)
- [Movimiento impulsado por la acción 14/20](#movimiento-impulsado-por-la-acción-1420)
- [Propiedades recomendadas y no recomendadas para animar 17/20](#propiedades-recomendadas-y-no-recomendadas-para-animar-1720)
- [Aceleración de hardware y la propiedad will-change 18/20](#aceleración-de-hardware-y-la-propiedad-will-change-1820)
- [Preferencias de movimiento reducido 19/20](#preferencias-de-movimiento-reducido-1920)

# 5 Razones para usar animaciones en la web

1. **Las animaciones tienen beneficio para nuestro cerebro**: Ayudan a reducir la carga cognitiva, y generar atención en espacios realmente importantes.
2. **Las animaciones se comunican**: Las figuras emiten diversos mensajes que nos ayudan a asociar situaciones en la vida real.
3. **Las animaciones conectan contextos**: Si ejecutaríamos una App móvil y la web de un mismo sitio(ejemplo: Platzi), la animación ayudaría a que logremos relacionarlos y reconozcamos de manera rápida de quien se trata. (Platzi)
4. **Coreografía de UI**: Las animaciones deben comunicar el mismo mensaje.
5. **Las animaciones llaman la atención**:Si bien es cierto que las animaciones son visualmente entretenidas y cómodas, ayudan a resaltar ciertas cosas de nuestro sitio web.

# Propiedades para crear animaciones con CSS y propiedades animables
- Propiedades animables.
  > **Animables** que sus valores cambien gradualmente durante un periodo de tiepo determinado.

- La propiedad `transition` por si sola nos puede ser de mucha ayuda al momento de aparecer elementos en la pantalla.
  > Por ejemplo, si tuviéramos un menu de navegación en la version mobile de nuestro sitio web y quisiéramos que aparezca en la pantalla de manera suave al hacer click, bastaría con aplicar la siguiente declaración al `menu: transition: all 300ms ease-in-out`.

  > PERO aquí viene lo interesante… para que la **transición** funcione correctamente, la propiedad que esperamos que cambie de manera suave tiene que contener un valor que pueda aumentar o disminuir progresivamente, por ejemplo, de 0 a 1.

  > ¿Qué quiere decir todo esto? Que si intentamos hacer que este menu aparezca suavemente solamente haciendo lo siguiente:

  > ```css
  > .menu {
  >   display: none;
  > }
  > .menu.active {
  >   display: block;
  > }
  > ```
  >
  > **ESTO NO FUNCIONARÍA.**
  > Para que funcione, una buena opción sería hacer lo siguiente:
  >
  > ```css
  > .menu {
  >   opacity: 0;
  >   visibility: hidden;
  > }
  > .menu.active {
  >   opacity: 1;
  >   visibility: visible;
  > }
  > ```

  > De esta manera, el valor **progresivo** del opacity _(0 a 1)_ nos ayuda a que la transición pueda ejecutarse perfectamente.
  **¿Y el visibility?** Sin esta propiedad, lo único que estaríamos haciendo es hacer invisible el menu, pero el elemento seguiría ahí. Por eso, al agregar un `visibility: hidden`, podemos quitar el elemento del DOM para evitar interactuar accidentalmente con el mientras este esta invisible.

  > Y así como este ejemplo, podemos darnos cuenta que estas transiciones funcionan perfectamente si quisiéramos que un elemento del **DOM** cambie suavemente el color, opacidad e incluso el tamaño, todas propiedades con valores _progresivos_.

# Pseudo-clases y pseudo-elementos en las animaciones
Para las animaciones es importante mencionar un concepto llamado **triger** que no es más que un accionador de las animaciones.

También es bueno tener en cuenta que las **pseudo-clases** y los **pseudo-elementos** son distintos entre sí, ambos se escriben como una extensión de nuestro selector después de dos puntos: `:hover`, `:after`; sin embargo, una **pseudo-clase** es básicamente un estado que podemos manipular, por ejemplo, el estado `hover`, el estado `active`, el estado `visited`, etc.

Un **pseudo-elemento**, como su nombre lo dice, es un elemento que no está declarado explícitamente desde nuestro HTML, pero lo podemos crear con CSS, por ejemplo `before` y `after`, *¿cómo sabes que es un pseudo-elemento y no una pseudo-clase?* ¡Fácil! Simplemente preguntate: ***¿existe el estado before?*** Verás que la respuesta es **no**, no existe ningún estado `before` porque este es un **pesudo-elemento**, por el contrario, si te preguntas: ***¿existe el estado :hover?*** Aquí la respuesta es **sí**, porque hover sí es una **pseudo-clase**.

[PSEUDO-CLASSES](https://developer.mozilla.org/es/docs/Web/CSS/Pseudo-classes#indice_de_las_pseudo-clases_est%C3%A1ndar)

[PSEUDO-ELEMENTOS](https://developer.mozilla.org/es/docs/Web/CSS/Pseudo-elements#lista_de_pseudoelementos)

# Timing functions, planos y ejes

Elaces que hay que visitar.

- [El contexto de apilamiento](https://developer.mozilla.org/es/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)
- [easing-function](https://developer.mozilla.org/en-US/docs/Web/CSS/easing-function)
- [Easing functions specify the rate of change of a parameter over time.](https://easings.net/)
- [cubic-bezier](https://cubic-bezier.com/)

**Timinig function**

La función de ***tiempo*** de animación especifica la curva de velocidad de una animación. La curva de velocidad define el ***TIEMPO*** que usa una animación para cambiar de un conjunto de estilos CSS a otro.

`animation-timing-function: linear|ease|ease-in|ease-out|ease-in-out|step-start|step-end|steps(int,start|end)|cubic-bezier(n,n,n,n)`


**Opciones**
- ***linear*** La animación tiene la misma velocidad de principio a fin.
- ***ease*** Valor por defecto. La animación tiene un comienzo lento, luego rápido, antes de que termine lentamente.
- ***ease-in*** La animación tiene un comienzo lento.
- ***ease-out*** La animación tiene un final lento.
- ***ease-in-out*** La animación tiene un comienzo lento y un final lento.
- ***step-start*** Equivalente a pasos (1, inicio)
- ***step-end*** Equivalente a pasos (1, fin)
- ***steps(int,start|end)*** Especifica una función paso a paso, con dos parámetros. El primer parámetro especifica el número de intervalos en la función. Debe ser un número entero positivo (mayor que 0). El segundo parámetro, que es opcional, es el valor “inicio” o “final”, y especifica el punto en el que se produce el cambio de valores dentro del intervalo. Si se omite el segundo parámetro, se le asigna el valor “fin”
- ***cubic-bezier(n,n,n,n)*** Defina sus propios valores en la función cubic-bezier. Los valores posibles son valores numéricos de 0 a 1.

# Transform Translate

Básicamente `translate()` te permite mover un elemento en el eje **X** o **Y** *¡O ambos!* básicamente este ejemplo que ya había puesto en una clase anterior, vas de un punto A a un punto B:

![Imagen](https://media.giphy.com/media/gCSOFQybTbM3pome6c/giphy.gif)

Ahora, ¡la propiedad `transform` usos muy interesantes! Un uso que a mí me encantó mucho cuando lo conocí es la posibilidad de poder centrar elementos, tanto verticalmente como horizontalmente, por ejemplo, suponiendo que tenemos un elemento padre con `position: relative;` y un elemento hijo con `position: absolute;`

![imagen2](https://static.platzi.com/media/user_upload/transform-04326ea9-9395-4220-8913-e80a912fee8b.jpg)

Podemos centrarlo usando `transform` y las propiedades `top y left`! ¿Cómo? Simplemente hay que decirle al elemento hijo que se muevan **50%** en su `top` y su `left`:

![imagen3](https://static.platzi.com/media/user_upload/center-not.centered-222d8f24-03c6-4abe-9d6d-73ef7dfe4f4e.jpg)

Pero esto no está centrado… Aquí es donde podemos usar `transform` 😉 Simplemente le decimos que tanto en **X** como en **Y** se mueva **-50%**, es decir, que retroceda el **50%** de sí mismo, de esa forma quedará totalmente centrado 😄

![imagen4](https://static.platzi.com/media/user_upload/centered-810822aa-bf74-47b9-bc32-5414b06f65b2.jpg)

De esa forma siempre se mantendrá centrado el elemento, esta forma de centrar me encanta cuando trabajamos con elementos posicionados absolutamente 😉.

# Transform rotate, scale, skew y matrix
[Transform](https://developer.mozilla.org/en-US/docs/Web/CSS/transform)

# Backface visibility 9/20
Con la propiedad backface-visibility podemos hacer cosas geniales como tarjetitas que se voltean.

La razón por la que no se estaban aplicando los estilos a los elementos es porque al inicio los selectores estaban escritos así: `.face .front`. Al estar escritos de esa manera, CSS esta buscando un elemento con clase `.front` dentro de un elemento con clase `.face`, lo cual no tenemos. Ese espacio entre un selector y otro es lo que ocasiona este comportamiento. 
Es como si hiciéramos lo siguiente:

```html  
  <div class="padre">
  	<div class="hijo"></div>
  </div>
```

```css
  .padre .hijo {
	  background-color: red;
  }
```

En el CSS anterior, gracias a ese espacio entre selectores es que podemos acceder al elemento con clase `.hijo` dentro del elemento con clase `.padre`
.

**PERO** ese no era el HTML que teníamos nosotros. Lo que teníamos era lo siguiente:

```html
  <div class="card">
  	<div class="face front"></div>
  	<div class="face back"></div>
  </div>
```

Entonces, ¿cómo seleccionamos esos div en CSS? Quitándole el espacio entre selectores.

```css
  .face.front {
  	background-color: red;
  }
```

De esta manera, al escribir los selectores sin espacios (todo junto), le estamos diciendo a CSS que queremos aplicar esos estilos al elemento que tenga las dos clases, tanto `.face` como `.front`.

# Efecto Parallax 10/20
**¿QUE ES PARALLAX?**

Efecto de paralaje o parallax es una técnica en la que el fondo se mueve a una velocidad distinta que la del contenido. El resultado es un ligero efecto de profundidad, dejando ver partes que antes no podías visualizar. Te ayuda a sumergirte totalmente en el contenido, similar al efecto 3D.

# Efecto parallax: estilos CSS 11/20

Cálculo: [(valor de la perspectiva en .parallax-container) - (valor de la distancia del translateZ dónde queremos calcular el scale)] / (valor de la perspectiva en .parallax-container)
En nuestros casos:
(8-5)/8=3/8=0.375
(8-2)/8=6/8=0.75

# Transition property y duration 12/20

¡La propiedad transition es la que hace toda la magía! Si ya tienes un elemento con un estado inicial y otro elemento con un estado final, entonces simplemente basta con que le ponas esta propiedad y se animará sin problema 😉.

Es decir, pasaras de tener esto:

![imgtransition1](https://media.giphy.com/media/6cnPXsppWlEPdbaaCt/giphy.gif)

A tener esto:

![imgtransition2](https://media.giphy.com/media/gCSOFQybTbM3pome6c/giphy.gif)

# Transition timing function y delay13/20
[TRANSICIONES](https://developer.mozilla.org/en-US/docs/Web/CSS/transition)

# Movimiento impulsado por la acción 14/20

Se trata de darle un toque más natural a la animación 🤔, es decir, en lugar de que sea una animación completamente linear podemos jugar con ellas para que tenga diferentes velocidades tanto de subida como de bajada, incluso podemos lograr que un objeto se comporte de forma más natural, por ejemplo, el efecto de un rebote 😄.

![img_rebote](https://media.giphy.com/media/T6nrjB3afwmBtINqKt/giphy.gif)

Si, ademas de esto, cuando se declaran los valores de transition en el :hover, realmente 2 de los valores estan de mas, se pudo haber escrito de la siguiente manera

```css
.div:hover{
	transform: translateX(200px);
	transition-duration: 1.5s;
}
```

# Propiedades recomendadas y no recomendadas para animar 17/20

Al hacer animaciones debemos fijarnos que no sean demasiado costosas computacionalmente para que no parezcan inestables y poco fluidas.

Para ello, debemos comprender un concepto clave llamado: el proceso de renderizado.

Resulta que, como el navegador no entiende el código que hacemos, debe hacer una transformación de ese código para que finalmente pueda ser entendido y visualizado en la pantalla.

Esa transformación se hace en una serie de pasos como los que puedes ver a continuación:

![img-clase17](https://static.platzi.com/media/user_upload/browser-rendering%20%281%29-3bf8f82c-dcca-4cd0-b1fd-2f6f1bededea.jpg)

Sin embargo, los pasos que nos interesan en este momento son los últimos 3: Layout, Paint y Composite. Cada uno cumple un papel muy importante, pero no todas las propiedades pasan por estos 3 procesos.

Si una propiedad debe pasar por el paso de Layout, obligatoriamente debe pasar por Paint y Composite también. Si una propiedad debe pasar por el paso de Paint, obligatoriamente debe pasar por Composite también. Pero, si una propiedad debe pasar por el paso de Composite, no debe pasar por ningún otro paso.

Con lo anterior, podemos darnos cuenta de que hay propiedades que requieren un costo mayor que otras al tener que pasar por más pasos. Puedes revisar el proceso de renderizado que realiza cada propiedad en esta página: https://csstriggers.com/. Revisemos algunas de ellas:

- **Propiedad** `height`: En cada uno de los motores de renderizado, podemos darnos cuenta por la imagen de abajo que requiere de los pasos de Layout, Paint y Composite, lo cual es bastante costoso.
  >![Height](https://static.platzi.com/media/user_upload/height-2570e121-258b-48ce-be1b-8db416697b01.jpg)

- **Propiedad** `background-color`: Es una propiedad que no afecta el diseño (Layout) pero requiere una nueva capa de pintura (Paint), lo cual la hace una propiedad también costosa.
  >![Background-color](https://static.platzi.com/media/user_upload/background-color-e2fa18c3-ffca-4e46-a3b8-ef263a00cdc6.jpg)

- **Propiedades** `transform` y `opacity`: Estas dos propiedades sólo requieren del paso de Composite, lo cual las hace muy baratas de animar. Si necesitas modificar propiedades como width y left (propiedades costosas), puedes reemplazarlas usando la propiedad transform para tratar de lograr el mismo efecto.
  >![transform](https://static.platzi.com/media/user_upload/transform-1167320b-389a-4b40-b335-316cf586a5a9.jpg)
  >![opacity](https://static.platzi.com/media/user_upload/opacity-b606d9c1-cef8-4678-bfb5-59edfb81ef59.jpg)

Finalmente, si sabemos por cuáles pasos de renderizado pasa cada una de las propiedades, sabremos con exactitud cuáles propiedades son más costosas y menos recomendadas para animar (como height, width y background-color), como también, cuáles propiedades son menos costosas y más recomendadas para animar (como transform y opacity).

Te comparto esta lectura por si quieres conocer más a profundidad cómo trabaja el motor de cada navegador con cada uno de los pasos que describimos anteriormente: https://hacks.mozilla.org/2017/08/inside-a-super-fast-css-engine-quantum-css-aka-stylo/

# Aceleración de hardware y la propiedad will-change 18/20
```css
  /* Para que lo tengan en cuenta que: */
  transition: transform 500ms ease;

  /* es lo mismo que decir: */
  transition-property: trnasform;
  transition-duration: 500ms;
  transition-timing-function: ease;
```

# Preferencias de movimiento reducido 19/20

Un muy buen modo de hacer que un usuario que tenga preferencias de movimiento reducido tenga una buena experiencia de usuario es usar este pequeña pieza de CSS que permite hacer que todas las animaciones se reduzcan:

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```
Si, se que el **!important** parece raro pero es un excelente modo de anular cualquier animación en caso de que el usuario prefiera las animaciones reducidas sin tener que preocuparse por cada animación en específico que tenemos en nuestro sitio.

Esto hace parte de un reset stylesheet que suelo usar bastante por si quieren verlo https://piccalil.li/blog/a-modern-css-reset/

En relacion a la accesibilidad, cuando hablamos de transiciones, hay personas que pueden no querer ver las transiciones. Tu te podrías preguntar, ¿Quién no quiere ver las transiciones, si estas son geniales? Bueno, hay personas diversas en la viña del Señor.

El punto es que en el navegador hay un opción para **“deshabilitar”** este tipo de movimientos. Cuando esta opción este prendida, nosotros tendríamos que haber puesto un **media queria**, mejor conocido como `@media`. Y si, los media queries no solo sirven para hacer responsive design!

La manera en como lo hacemos es la siguiente:

```css
@media (prefers-reduced-motion: no-preference){
	Your: code;
}
```

En el apartado de **Your: code;**, solo tendríamos que cambiar el código para que ya no haya transiciones tan alocadas y el usuario pueda ver algo menos escandaloso. En la clase dan un muy buen ejemplo practico.

