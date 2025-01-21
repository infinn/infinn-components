# Estructura HTML 📝
Primero, vamos a crear la estructura básica de nuestro menú. Aquí tenemos el código HTML que define todo lo necesario para mostrar un menú interactivo en nuestra página web:

```html
<header>
  <section class="menu-section">
    <div class="menu-header">
      <div class="menu-header-content">
        <button id="menuButton" class="menu-button">Menu</button>
      </div>
    </div>

    <div id="menuContainer" class="menu-container">
      <div class="menu-content">
        <div class="navigation-menu">
          <div class="hidden-section"></div>
          <nav class="main-navigation">
            <ul>
              <li><a href="/" class="nav-link">Home</a></li>
              <li><a href="/" class="nav-link">Work</a></li>
              <li><a href="/" class="nav-link">About</a></li>
              <li><a href="/" class="nav-link">Contact</a></li>
            </ul>
          </nav>
        </div>

        <nav>
          <ul class="social-navigation">
            <li><a href="/" class="social-link">Instagram</a></li>
            <li><a href="/" class="social-link">Twitter</a></li>
            <li><a href="/" class="social-link">GitHub</a></li>
            <li><a href="/" class="social-link">Mail</a></li>
          </ul>
        </nav>
      </div>
    </div>
  </section>
</header>
```

### Explicación de los elementos:
> - **`<button id="menuButton" class="menu-button">Menu</button>`**: Este botón tiene un `id` que **nos ayudará a manipularlo con JavaScript**. El texto del botón es "Menu" y servirá para abrir o cerrar el menú.
> - **`<div id="menuContainer" class="menu-container">`**: Es el contenedor principal del menú. **Se mostrará u ocultará cuando hagamos clic en el botón**.
> - **`<div class="menu-content">`**: Aquí va el contenido del menú, dividido en dos secciones principales: la navegación del sitio y las redes sociales.
> - **`<nav class="main-navigation">`**: Aquí definimos los enlaces de navegación para las páginas como *"Home", "Work", "About" y "Contact"*.
> - **`<nav>` y `.social-navigation`**: Sección para los enlaces de redes sociales como *Instagram, Twitter, GitHub y Mail*.

---

# Estilos CSS 🎨
A continuación, vamos a darle estilo a nuestro menú. Este código CSS hace que el menú sea interactivo, con animaciones y transiciones suaves. Aquí está el desglose:

#### Definición de variables en root 🔧
```css
:root {
  --primary-color: #2563eb;
  --hover-color: #1e40af; 
  --background-color: #1c1917;
  --white-color: #ffffff; 
}
```

> - `--primary-color`: Definimos el color principal del diseño.
> - `--hover-color`: Este color se aplica cuando el usuario pasa el mouse sobre un elemento.
> - `--background-color`: Usamos este color para los fondos.
> - `--white-color`: Este es el color blanco utilizado en el texto.

#### ✨ Estilos del `header` y `.menu-section`:

El `header`, la parte superior del sitio, donde se colocan el botón y el contenedor del menú.

```css
header {
  display: flex;
  justify-content: center; /* Centra el contenido en el encabezado. */
}

.menu-section {
  position: absolute;
  top: 0;
  width: 100%;
  display: flex;
  justify-content: center; /* Centra el contenido dentro de la sección. */
}
```

> - `display: flex;`: Organiza los elementos dentro del header en una fila.
> - `justify-content`: center;: Centra el contenido horizontalmente.

#### Estilos para el **`.menu-header`** y **`.menu-header-content`**:
```css
.menu-header {
  width: 100%;
  position: absolute;
  top: 0;
  z-index: 50;
  pointer-events: none;
}

.menu-header-content {
  display: flex;
  justify-content: center;
  padding: 2rem;
  mix-blend-mode: difference; /* Contrasta los colores del fondo con los del contenido. */
}
```

#### Estilos para **`.menu-button`** y su interacción:
```css
.menu-button {
  pointer-events: auto;
  color: var(--primary-color);
  transition: color 0.5s ease;
  font-weight: 800;
}

.menu-button:hover {
  color: var(--hover-color);
}
```

#### Estilizando el contenedor del menú:
```css
.menu-container {
  display: none;
  grid-template-rows: 1fr auto;
  max-width: 1250px;
  width: 100%;
  z-index: 40;
  padding: 1rem;
  background-color: var(--background-color);
  padding-top: 2rem;
  border-radius: 0.5rem;
  animation: menuCloseAnimation 0.7s ease-in-out forwards;
}
```
> - `display: none;`: El menú estara oculto por defecto.
> - `animation: menuCloseAnimation 0.7s ease-in-out forwards;`: Se aplica una animación para el cierre del menú.


#### Estilos para las **secciones de navegación**:
```css
.navigation-menu {
  display: none;
  opacity: 0;
  grid-template-columns: repeat(2, 1fr);
  animation: fadeIn forwards ease-in-out;
  animation-delay: 0.7s;
  animation-duration: 0.3s;
}

.main-navigation ul {
  list-style: none;
  padding: 0;
}

.nav-link {
  font-size: 2rem;
  font-weight: 600;
  color: var(--white-color);
  text-decoration: none;
  transition: color 0.3s ease;
}

.nav-link:hover {
  color: var(--primary-color);
}
```

#### Estilos para **redes sociales**:
```css
.social-navigation {
  display: none;
  grid-template-columns: repeat(4, 1fr);
  text-align: center;
  font-size: 1.5rem;
  font-weight: 600;
  list-style: none;
  padding: 0;
  opacity: 0;
  color: var(--white-color);
  animation: fadeIn forwards ease-in-out;
  animation-delay: 0.7s;
  animation-duration: 0.3s;
}

.social-link {
  color: var(--white-color);
  text-decoration: none;
  transition: color 0.3s ease;
}

.social-link:hover {
  color: var(--primary-color);
}
```

## Animaciones en CSS 💥

```css
@keyframes menuOpenAnimation{
    0%{
        height: 56px;
        width: 56px;
    }
    50%{
        width: 100%;
    }
    100%{
        height: 726px;
    }
}
@keyframes menuCloseAnimation{
    0%{
        height: 726px;
        width: 100%;
    }
    50%{
        height: 56px;
        width: 100%;
    }
    100%{
        width: 56px;
    }
}
@keyframes menuOpenAnimationBlock {
    from {
        transform: translateY(-200px);
        height: 56px;
        width: 56px;
    }
    to {
        transform: translateY(0);
        height: 56px;
        width: 56px;
    }
}
@keyframes menuCloseAnimationBlock {
    from {
        transform: translateY(0);
        height: 56px;
        width: 56px;
    }
    to {
        transform: translateY(-200px);
        height: 56px;
        width: 56px;
    }
}
  
@keyframes fadeIn {
    from {
        opacity: 0;
    }
    to {
        opacity: 1;
    }
}
```

Estas animaciones ayudan a abrir y cerrar el menú de forma fluida, además de hacer que los enlaces de navegación y redes sociales aparezcan con una animación de desvanecimiento.

---

# JavaScript: Lógica para Abrir y Cerrar el Menú 🎬

Ahora que tenemos la estructura y el estilo, vamos a darle interactividad al menú usando JavaScript. Primero, declaramos las variables que vamos a manipular.



```js
const menuButton = document.getElementById("menuButton");
const menuContainer = document.getElementById("menuContainer");
const navigationMenus = document.querySelectorAll(".navigation-menu");
const socialNavigation = document.querySelector(".social-navigation");

let isMenuOpen = false;
```
> - `menuButton`: El botón que abrirá o cerrará el menú.
> - `menuContainer`: El contenedor que contiene el menú.
> - `isMenuOpen`: Un booleano que verifica si el menú está abierto o cerrado.
```js
function toggleMenu() {
  menuButton.disabled = true;

  if (!isMenuOpen) {
    menuContainer.style.display = "grid";
    menuContainer.style.animation = "menuOpenAnimation 0.7s ease-in-out forwards";

    setTimeout(() => {
      navigationMenus.forEach(menu => menu.style.display = "grid");
      socialNavigation.style.display = "grid";
      menuButton.textContent = "Close";
      menuContainer.style.animation = "menuOpenAnimation 0.7s ease-in-out forwards";
      menuButton.disabled = false;
    }, 700);
  } else {
    menuContainer.style.animation = "menuCloseAnimation 0.7s ease-in-out forwards";
    navigationMenus.forEach(menu => menu.style.display = "none");
    socialNavigation.style.display = "none";

    setTimeout(() => {
      menuButton.textContent = "Menu";
      menuContainer.style.animation = "menuCloseAnimation 0.7s ease-in-out forwards";
    }, 700);

    setTimeout(() => {
      menuContainer.style.display = "none";
      menuButton.disabled = false;
    }, 1400);
  }

  isMenuOpen = !isMenuOpen;
}
menuButton.addEventListener("click", toggleMenu);
```
> - **Declaración de variables**: Seleccionamos los elementos que necesitamos manipular, como el botón de menú, el contenedor del menú y las secciones de navegación.
> - **Abrir menú**: Si el menú está cerrado, se muestra con una animación de apertura y el texto del botón cambia a "Close".
> - **Cerrar menú**: Si el menú está abierto, se aplica una animación de cierre y el texto del botón vuelve a "Menu".


