# 🖼️ Basic Image Editor - Editor de Imágenes Básico

Editor de Imágenes
Un editor de imágenes sencillo pero poderoso para transformaciones básicas.

## 📝 Descripción

Este Basic Image Editor es una aplicación web ligera que permite realizar ediciones básicas a imágenes directamente en el navegador. Con una interfaz intuitiva y minimalista, los usuarios pueden aplicar filtros, ajustar colores y voltear imágenes sin necesidad de software complejo.

## ✨ Características Principales

- 🔄 Aplicar efectos de desenfoque (blur)

- 🌗 Ajustar contraste de la imagen

- 🌈 Rotar tonos (hue-rotate)

- 🟤 Aplicar efecto sepia

- ↔️ Voltear imagen horizontal/verticalmente

- ⬇️ Descargar la imagen editada

- 🎨 Interfaz con diseño atractivo y oscuro

## 🛠️ Tecnologías Utilizadas

- **HTML5** - Estructura de la aplicación

- **CSS3** - Estilos y diseño responsive

- **JavaScript Vanilla** - Lógica y manipulación del DOM

- **Canvas API** - Para procesamiento y descarga de imágenes

## 🚀 Funcionamiento

La aplicación funciona completamente en el cliente (frontend) y no requiere backend. Estos son los componentes clave:

### 🖌️ Manipulación de Imágenes

El corazón de la aplicación está en el archivo `script.js` donde se implementan las funciones principales:

```javascript
function addFilter() {
    image.style.filter = `blur(${filterA.value}px)
                        contrast(${filterB.value}%)
                        hue-rotate(${filterC.value}deg)
                        sepia(${filterD.value}%)`;
}
```

Esta función combina todos los filtros seleccionados y los aplica a la imagen usando la propiedad `filter` de CSS.

### 🔄 Volteado de Imagen

```javascript
function flipImage() {
    if (flipXBtn.checked) {
        image.style.transform = "scaleX(-1)";
    } else if (flipYBtn.checked) {
        image.style.transform = "scaleY(-1)";
    } else {
        image.style.transform = "scale(1,1)";
    }
}
```

Usa transformaciones CSS para voltear la imagen horizontal o verticalmente según la selección del usuario.

### ⬇️ Descarga de Imagen

```javascript
downloadButton.onclick = () => {
    const canvas = document.createElement("canvas");
    const ctx = canvas.getContext("2d");
    // ... configuración del canvas ...
    ctx.drawImage(img, -canvas.width / 2, canvas.height / 2, canvas.width, canvas.height);
    const link = document.createElement("a");
    link.download = 'edited-image.png';
    link.href = canvas.toDataURL();
    link.click();
};
```

Esta función crea un canvas temporal, aplica los filtros y transformaciones, y luego genera un enlace de descarga.

## 🎮 Cómo Usar la Aplicación

1. **Sube una imagen** haciendo clic en "Choose an Image"

1. **Ajusta los controles deslizantes** para aplicar filtros:

    - Blur: Añade desenfoque

    - Contrast: Ajusta el contraste

    - Hue-Rotate: Cambia los tonos de color

    - Sepia: Aplica efecto sepia

1. **Selecciona la orientación** con los botones de radio

1. **Descarga tu imagen editada** con el botón "Download Image"

## 📥 Instalación y Desarrollo

Para ejecutar localmente o contribuir al proyecto:

1. Clona el repositorio:

    ```bash
    git clone https://github.com/tu-usuario/basic-image-editor.git
    ```

1. Abre el archivo `index.html` en tu navegador

1. ¡Listo! No se requieren dependencias adicionales

## 🌟 Fragmentos Destacados

### Manejo de Eventos

```javascript
const sliders = document.querySelectorAll(".filter input[type='range']");
sliders.forEach((slider) => {
    slider.addEventListener("input", addFilter);
    slider.addEventListener("input", showRangeValue);
});
```

Este código muestra cómo se manejan los eventos de los controles deslizantes para aplicar los filtros en tiempo real.

### Lectura de Archivos

```javascript
uploadButton.onchange = () => {
    resetFilter();
    const reader = new FileReader();
    reader.readAsDataURL(uploadButton.files[0]);
    reader.onload = () => {
        image.setAttribute("src", reader.result);
    };
};
```

Aquí se usa la API FileReader para cargar la imagen seleccionada por el usuario y mostrarla en el editor.

## 🎨 Diseño Responsive

El CSS utiliza unidades relativas (vmin) y un diseño basado en grid para asegurar que la aplicación se vea bien en diferentes tamaños de pantalla:

```css
.wrapper {
    width: 85vw;
    min-height: 50vmin;
    display: grid;
    grid-template-columns: 5fr 7fr;
}
```
