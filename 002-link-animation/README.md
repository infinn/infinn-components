# 🇺🇸 English

## ✨ Animated Link with Hover Effect

This tutorial guides you through creating an animated component where each letter of a link moves upward when hovered over. Simultaneously, another version of the letter appears from below, creating a dynamic and visually appealing effect.

### 🚀 What Does the Code Do?

This component splits the link text into individual letters. When you hover over it, the letters "move up" and are replaced by others from below, each with a different color. The animation is staggered thanks to a small delay between letters.

---

### 🛠️ Component Code

#### 🔧 Initial Variables

```astro
---
const { href, text, blank = false } = Astro.props;
const delay = 0.01;
---
```

- Extract the `href`, `text`, and `blank` properties from the props passed to the component.
- `blank` defaults to `false`, meaning the link will not open in a new tab unless specified.
- Define the constant `delay` with a value of `0.01`, which staggers the letter animations.

#### 🌟 HTML Structure

```astro
<a href={href} class="link" target={blank ? "_blank" : "_self"}>
```

- Create an `<a>` element with the `href` attribute linking to the specified URL.
- The `link` class applies general styles to the link.
- Set the `target` attribute to `"_blank"` if `blank` is `true` to open the link in a new tab, or `"_self"` to open it in the same tab.

```astro
<div class="text-wrapper">
```

A main wrapper surrounds each letter of the original text (`text`) and applies the upward movement animations.

```astro
{text.split("").map((letter, i) => (
    <span 
        style={`transition-delay: ${delay * i}s;`} 
        class="letter up">
        {letter === " " ? "\u00A0" : letter}
    </span>
))}
```

Split the text into individual characters with `.split("")`.

**Generate a `<span>` for each character (`letter`):**
- Apply a `transition-delay` style calculated as `delay * i`, where `i` is the character index, **to stagger the animation.**
- Assign the class `letter up`, which initially positions the letters in place (`translateY(0)`).
- **If the character is a space**, replace it with `"\u00A0"` (non-breaking space) to maintain spacing.

```astro
<div class="text-wrapper overlay">
```

Create another wrapper with the class `overlay`, positioning the overlapping text above the base text.

```astro
{text.split("").map((letter, i) => (
    <span 
        style={`transition-delay: ${delay * i}s;`} 
        class="letter down">
        {letter === " " ? "\u00A0" : letter}
    </span>
))}
```

Same as the previous `.map`, **but the letters have the class `letter down`**, which initially positions them shifted downward (`translateY(100%)`).

#### 🎨 CSS Styles

```css
.link {
    overflow: hidden;
    position: relative;
    display: block;
    white-space: nowrap;
    width: max-content;
    height: auto;
}
```

Define the link container:

- `overflow: hidden`: **Hides content outside the container boundaries.**
- `position: relative`: Necessary for absolutely positioning child elements.
- `white-space: nowrap`: **Prevents text from wrapping onto multiple lines.**
- `width: max-content`: Adjusts the width to the content.

```css
.text-wrapper {
    width: max-content;
}
```

Adjust the width of the text wrappers.

```css
.text-wrapper.overlay {
    position: absolute;
    inset: 0;
    color: #2563eb;
}
```

Place the overlapping text over the base text and apply a blue color.

```css
.letter {
    display: inline-block;
    transition: transform 0.3s ease-in-out;
}
```

Style the letters as inline elements with a smooth `transform` transition.

```css
.letter.down {
    transform: translateY(100%);
}
```

Initially, **letters with this class are shifted downward.**

```css
.letter.up {
    transform: translateY(0);
}
```

Initially, letters with this class are in their normal position.

```css
.link:hover .letter.down {
    transform: translateY(0);
}
```

On hover, letters shifted downward (`down`) move to their normal position.

```css
.link:hover .letter.up {
    transform: translateY(-100%);
}
```

On hover, letters in their normal position (`up`) move upward.

---

## 📖 How to Use It

**Import the component into your Astro file:**

`/index.astro`
```astro
---
import Links from "./components/Links.astro" // File location
---
```

Use it on your page:

```astro
<Links href="/" text="Home" />
<Links href="https://www.instagram.com" text="Instagram" blank />
```

- In the first link, the text is "Home" and opens in the same tab.
- In the second, the text is "Instagram" and opens in a new tab, thanks to the `blank` attribute.

# 🇨🇱 Español

## ✨ Link Animado con Efecto de Hover

Este tutorial te guía para crear un componente animado en el que cada letra de un enlace se desplaza hacia arriba al pasar el ratón. Al mismo tiempo, aparece otra versión de la letra desde abajo, creando un efecto visual dinámico y atractivo.

### 🚀 ¿Qué hace el código?

Este componente divide el texto del enlace en letras individuales. Cuando pasas el ratón sobre él (hover), las letras "suben" y son reemplazadas por otras desde abajo, cada una con un color diferente. La animación está escalonada gracias a un pequeño retraso entre las letras.

---

### 🛠️ Código del Componente

#### 🔧 Variables Iniciales

```astro
---
const { href, text, blank = false } = Astro.props;
const delay = 0.01;
---
```

- Extraemos las propiedades `href`, `text`, y `blank` de los props enviados al componente.
- `blank` tiene un valor por defecto de `false`, lo que significa que si no lo especificamos, el enlace no se abrirá en una nueva pestaña.
- Definimos la constante `delay` con un valor de `0.01`, que escalona las animaciones de las letras.

#### 🌟 Estructura del HTML

```astro
<a href={href} class="link" target={blank ? "_blank" : "_self"}>
```

- Creamos un elemento `<a>` con el atributo `href` para enlazar a la URL especificada.
- La clase `link` aplica estilos generales al enlace.
- Configuramos el atributo `target` como `"_blank"` si `blank` es `true`, para abrir el enlace en una nueva pestaña, o como `"_self"` para abrirlo en la misma.

```astro
<div class="text-wrapper">
```

Usamos un contenedor principal que envuelve cada letra del texto original (`text`) y aplica las animaciones de desplazamiento hacia arriba.

```astro
{text.split("").map((letter, i) => (
    <span 
        style={`transition-delay: ${delay * i}s;`} 
        class="letter up">
        {letter === " " ? "\u00A0" : letter}
    </span>
))}
```

Dividimos el texto en caracteres individuales con `.split("")`.

**Generamos un `<span>` por cada carácter (`letter`):**
- Aplicamos un estilo `transition-delay` calculado como `delay * i`, donde `i` es el índice del carácter, **para escalonar la animación.**
- Asignamos la clase `letter up`, que posiciona inicialmente las letras en su lugar (`translateY(0)`). 
- **Si el carácter es un espacio**, lo reemplazamos con `"\u00A0"` (espacio no separable) para mantener el espaciado.

```astro
<div class="text-wrapper overlay">
```

Creamos otro contenedor con la clase `overlay`, que posiciona el texto superpuesto encima del texto base.

```astro
{text.split("").map((letter, i) => (
    <span 
        style={`transition-delay: ${delay * i}s;`} 
        class="letter down">
        {letter === " " ? "\u00A0" : letter}
    </span>
))}
```

Igual que el anterior `.map`, **pero las letras tienen la clase `letter down`**, que inicialmente las posiciona desplazadas hacia abajo (`translateY(100%)`).

#### 🎨 Estilos CSS

```css
.link {
    overflow: hidden;
    position: relative;
    display: block;
    white-space: nowrap;
    width: max-content;
    height: auto;
}
```

Definimos el contenedor del enlace:

- `overflow: hidden`: **Ocultamos contenido fuera de los límites del contenedor.**
- `position: relative`: Necesario para posicionar los elementos hijos absolutamente.
- `white-space: nowrap`: **Prevenimos que el texto se divida en varias líneas.**
- `width: max-content`: Ajusta el ancho al contenido.

```css
.text-wrapper {
    width: max-content;
}
```

Ajustamos el ancho de los contenedores del texto.

```css
.text-wrapper.overlay {
    position: absolute;
    inset: 0;
    color: #2563eb;
}
```

Colocamos el texto superpuesto sobre el texto base y aplicamos un color azul.

```css
.letter {
    display: inline-block;
    transition: transform 0.3s ease-in-out;
}
```

Estilizamos las letras como elementos en línea con una transición suave en los cambios de `transform`.

```css
.letter.down {
    transform: translateY(100%);
}
```

Inicialmente, **las letras con esta clase están desplazadas hacia abajo.**

```css
.letter.up {
    transform: translateY(0);
}
```

Inicialmente, las letras con esta clase están en su posición normal.

```css
.link:hover .letter.down {
    transform: translateY(0);
}
```

Al pasar el ratón, las letras desplazadas hacia abajo (`down`) se mueven a su posición normal.

```css
.link:hover .letter.up {
    transform: translateY(-100%);
}
```

Al pasar el ratón, las letras en la posición normal (`up`) se desplazan hacia arriba.

---

## 📖 Cómo Usarlo

**Importa el componente en tu archivo Astro:**

`/index.astro`
```astro
---
import Links from "./components/Links.astro" // La ubicación del archivo
---
```

Úsalo en tu página:

```astro
<Links href="/" text="Inicio" />
<Links href="https://www.instagram.com" text="Instagram" blank />
```

- En el primer enlace, el texto es "Inicio" y se abre en la misma pestaña.
- En el segundo, el texto es "Instagram" y se abre en una nueva pestaña gracias al atributo `blank`.