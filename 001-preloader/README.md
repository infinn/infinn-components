# 🇺🇸 English 

## Animated Preloader with HTML, CSS, and JavaScript

### Layout
Start by creating the structure for the preloader in your HTML file.

```html
<div class="preloader-container">
	<div class="preloader" id="preloader">
        <!-- Your SVG goes here -->
		<svg class="preloader-icon" viewBox="0 0 50 50" id="preloader-svg">
            <!-- Icon path can go here -->
        </svg>
	</div>
</div>
```

- `<div class="preloader-container">`

This is the **main container**. Its purpose is to wrap the entire preloader and ensure it's positioned correctly on the page. It acts as the "frame" controlling its appearance.

- `<div class="preloader" id="preloader">`

This is the **inner container**. It will house the animation. We'll add styles and animations to make it cover the entire screen while the page loads.

- `<svg class="preloader-icon" viewBox="0 0 50 50" id="preloader-svg">`

This is where we place the icon we want to animate. SVG (Scalable Vector Graphics) is perfect for animations because it maintains quality regardless of size. This icon will move and resize using CSS.

> 💡 **Tip**: You can use any SVG you like. If you don't have one, websites like [SVG Repo](https://www.svgrepo.com/) are great resources.

### Styles

#### Styling the Main Container
```css
.preloader-container {
	position: sticky;
	top: 0;
	width: 100%;
}
```

- `position: sticky;`:  

Ensures the container stays visible at the top while scrolling. Although the preloader will disappear later, this property **keeps it visible if needed.**

- `top: 0;`:  

Fixes the container to the top edge of the window.
   
- `width: 100%;`:  

Ensures the container spans the full width of the screen.

#### Styling the Preloader
```css
.preloader {     
	position: absolute;     
	top: 0;     
	width: 100vw;     
	height: 100vh;     
	display: flex; 
}
```

- `position: absolute;`:  

Positions the preloader absolutely, overlaying it on top of all page content.
  
- `top: 0;`, `width: 100vw;`, `height: 100vh;`:  

Makes the preloader cover the entire screen (100% width and height of the viewport).
   
- `display: flex;`:  

Prepares the preloader for flexible alignment, making it easier to position the SVG icon.

#### Styling the SVG Icon

```css
.preloader-icon {     
	fill: var(--gray-color, #1d1d1d);     
	transform: scale(5);     
	width: 100%;     
	height: 100%;     
	animation: fadeOut 1.5s forwards ease-in-out;     
	animation-play-state: paused; 
}
```

- `fill: var(--gray-color, #1d1d1d);`:  

**Fills the icon with a color.** We use a CSS variable here for easy customization.

- `transform: scale(5);`:  

Scales the icon to appear larger initially.

- `animation: fadeOut 1.5s forwards ease-in-out;`:  

Defines an animation called `fadeOut` lasting 1.5 seconds. The `forwards` property maintains the end state.    

- `animation-play-state: paused;`:  

Pauses the animation initially, to be activated later as needed.


##### Defining Animations 

**Fade Out**

```css
@keyframes fadeOut {     
	0% { transform: scale(5); }     
	50% { transform: scale(0.5) translateY(0); }     
	100% { transform: scale(0.5) translateY(-300%); } 
}
```

 **Fade In**

```css
@keyframes fadeIn {     
	0% { transform: scale(0.5) translateY(-300%); }     
	50% { transform: scale(0.5) translateY(0); }     
	100% { transform: scale(5); } 
}
```

### JavaScript to Control the Preloader
#### Selecting the Elements

```js
const preloader = document.getElementById("preloader");
const preloaderSvg = document.getElementById("preloader-svg");
let isAnimationRunning = false;
```

Here we select the preloader and the SVG icon for dynamic manipulation. We also define a variable to track whether the animation is active.

#### Controlling the Preloader

```js
window.onload = () => {
	isAnimationRunning = true;
	runPreloaderAnimation();
	const links = document.querySelectorAll("a");
	links.forEach(link => {
		if (link.target !== "_blank") {
			link.addEventListener("click", event => {
				document.body.style.overflow = "hidden";
				event.preventDefault();
				runPreloaderAnimation();
				setTimeout(() => {
					window.location.href = link.href;
				}, 1000);
			});
		}
	});
};
```

- **`window.onload`**: Starts the animation when the page finishes loading.
- **Intercepting Links**: Blocks scrolling, plays the animation, and redirects afterward.

#### Running the Animation

```js
function runPreloaderAnimation() {
    if (isAnimationRunning) {
        preloaderSvg.style.animationPlayState = "running";
        document.body.style.overflow = "auto";
        setTimeout(() => {
            preloader.style.display = "none";
            isAnimationRunning = false;
        }, 1500);
    } else {
        preloader.style.display = "flex";
        preloaderSvg.style.animation = "fadeIn 1s forwards ease-in-out";
        setTimeout(() => {
            isAnimationRunning = true;
        }, 1500);
    }
}
```

This code determines whether to show or hide the preloader based on the animation state.

# 🇨🇱 Español

## Preloader Animado con HTML, CSS y JavaScript

### Maquetación
Comienza creando la estructura del preloader en tu archivo HTML.

```html
<div class="preloader-container"> 
	<div class="preloader" id="preloader"> 
        <!-- Aquí va tu SVG -->
		<svg class="preloader-icon" viewBox="0 0 50 50" id="preloader-svg">
            <!-- Path del ícono puede ir aquí -->
        </svg>
	</div> 
</div>
```

- `<div class="preloader-container">` 

Este es el **contenedor principal**. Su función es envolver todo el preloader y asegurarse de que quede en la posición correcta en la página. Es el "marco" que controla dónde aparece.
- `<div class="preloader" id="preloader">`

Este es el **contenedor interno**. Dentro de él estará la animación. Le añadiremos estilos y animaciones para que ocupe toda la pantalla mientras la página se carga.
- `<svg class="preloader-icon" viewBox="0 0 50 50" id="preloader-svg">`
   
Aquí colocamos el ícono que queremos animar. SVG (Gráficos Vectoriales Escalables) es perfecto para animaciones porque mantiene la calidad sin importar el tamaño. Este ícono se moverá y cambiará de tamaño gracias a CSS.

>💡 **Tip**: Puedes usar cualquier SVG que desees. Si no tienes uno, hay páginas como [SVG Repo](https://www.svgrepo.com/) donde puedes conseguirlos.

### Estilos

#### Estilizando el contenedor principal
```css
.preloader-container { 
	position: sticky; 
	top: 0; 
	width: 100%; 
}
```

- `position: sticky;`:  

Hace que el contenedor se mantenga visible en la parte superior mientras hacemos scroll. Aunque el preloader desaparecerá después, esta propiedad **asegura que esté visible si fuera necesario.**

- `top: 0;`:  

Fija el contenedor al borde superior de la ventana.
   
- `width: 100%;`:  

Se asegura de que el contenedor ocupe todo el ancho de la pantalla.

#### Estilizando el preloader
```css
.preloader {     
	position: absolute;     
	top: 0;     
	width: 100vw;     
	height: 100vh;     
	display: flex; 
}
```

- `position: absolute;`:  

Coloca el preloader en una posición absoluta, superponiéndolo a todo el contenido de la página.
  
- `top: 0;`, `width: 100vw;`, `height: 100vh;`:  

Hace que el preloader cubra toda la pantalla (100% del ancho y alto del viewport).
   
- `display: flex;`:  

Prepara el preloader para alinear su contenido de forma flexible, facilitando el posicionamiento del ícono SVG.

#### Estilizando el ícono SVG

```css
.preloader-icon {     
	fill: var(--gray-color, #1d1d1d);     
	transform: scale(5);     
	width: 100%;     
	height: 100%;     
	animation: fadeOut 1.5s	forwards ease-in-out;     
	animation-play-state: paused; 
}
```

- `fill: var(--gray-color, #1d1d1d);`:  

**Rellena el ícono con un color**. Aquí usamos una variable CSS para que sea fácil cambiarlo.

- `transform: scale(5);`:  

Escala el ícono para que se vea más grande al inicio.

- `animation: fadeOut 1.5s forwards ease-in-out;`:  

Define una animación llamada `fadeOut` que dura 1.5 segundos. Usa `forwards` para mantener el estado final.    

- `animation-play-state: paused;`:  

Pausa la animación inicialmente para activarla solo cuando queramos.


##### Definiendo animaciones 

**Fade Out**

```css
@keyframes fadeOut {     
	0% { transform: scale(5); }     
	50% { transform: scale(0.5) translateY(0); }     
	100% { transform: scale(0.5) translateY(-300%); } 
}
```

 **Fade In**

```css
@keyframes fadeIn {     
	0% { transform: scale(0.5) translateY(-300%); }     
	50% { transform: scale(0.5) translateY(0); }     
	100% { transform: scale(5); } 
}
```

### JavaScript para controlar el preloader
#### Seleccionando los elementos

```js
const preloader = document.getElementById("preloader"); 
const preloaderSvg = document.getElementById("preloader-svg"); 
let isAnimationRunning = false;
```

Aquí seleccionamos el preloader y el ícono SVG para manipularlos dinámicamente. También definimos una variable para rastrear si la animación está activa.

#### Controlando el preloader

```js
window.onload = () => { 
	isAnimationRunning = true; runPreloaderAnimation(); 
	const links = document.querySelectorAll("a"); 
	links.forEach(link => { 
		if (link.target !== "_blank") {
			link.addEventListener("click", event => { 
				document.body.style.overflow = "hidden"; 
				event.preventDefault(); 
				runPreloaderAnimation(); 
				setTimeout(() =>{ 
					window.location.href = link.href; 
				}, 1000); 
			}); 
		} 
	}); 
};
```

- **`window.onload`**: Inicia la animación cuando la página termina de cargar.
- **Interceptar enlaces**: Bloqueamos el scroll, reproducimos la animación y redirigimos después.

#### Ejecutando la animación

```js
function runPreloaderAnimation() {
    if (isAnimationRunning) {
        preloaderSvg.style.animationPlayState = "running";
        document.body.style.overflow = "auto";
        setTimeout(() => {
            preloader.style.display = "none";
            isAnimationRunning = false;
        }, 1500);
    } else {
        preloader.style.display = "flex";
        preloaderSvg.style.animation = "fadeIn 1s forwards ease-in-out";
        setTimeout(() => {
            isAnimationRunning = true;
        }, 1500);
    }
}
```

Este código controla si mostramos u ocultamos el preloader dependiendo del estado de la animación.

