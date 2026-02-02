# ⚡ Calculadora Cyberpunk 2077 ⚡

Una calculadora y conversor binario con temática cyberpunk futurista, inspirada en Night City. Diseño responsive con efectos neón y animaciones que evocan un ambiente tecnológico del futuro.

## 🎮 Características

- **Calculadora básica**: Suma, resta, multiplicación y división
- **Conversor binario/decimal**: Convierte números entre sistemas numéricos
- **Diseño responsive**: Adaptable a cualquier dispositivo
- **Estética cyberpunk**: Efectos neón, fuentes futuristas y animaciones
- **Interfaz intuitiva**: Navegación por pestañas entre funcionalidades

## 🚀 Cómo Usar

### Calculadora

1. Navega a la pestaña **"Calculadora"**
2. Ingresa el primer número en el campo "Número 1"
3. Ingresa el segundo número en el campo "Número 2"
4. Selecciona la operación deseada (Suma, Resta, Multiplicación o División)
5. El resultado aparecerá automáticamente

### Conversor Binario

1. Navega a la pestaña **"Conversor"**
2. **Para Binario → Decimal**: Ingresa un número binario (solo 0s y 1s)
3. **Para Decimal → Binario**: Ingresa un número decimal entero
4. Los resultados se mostrarán en tiempo real

## 💻 Estructura del Código

### HTML - Estructura de Navegación

```html
<div class="nav-buttons">
    <button class="nav-btn active" onclick="showSection('calculator')">Calculadora</button>
    <button class="nav-btn" onclick="showSection('converter')">Conversor</button>
</div>
```

El sistema de navegación utiliza botones que cambian entre las secciones de calculadora y conversor.

### CSS - Efectos Neón y Animaciones

```css
h1 {
    color: #00ffff;
    text-shadow: 0 0 20px rgba(0, 255, 255, 0.8),
                 0 0 40px rgba(0, 255, 255, 0.5);
    animation: glow 2s ease-in-out infinite alternate;
}

@keyframes glow {
    from {
        text-shadow: 0 0 20px rgba(0, 255, 255, 0.8),
                     0 0 40px rgba(0, 255, 255, 0.5);
    }
    to {
        text-shadow: 0 0 30px rgba(0, 255, 255, 1),
                     0 0 60px rgba(0, 255, 255, 0.8);
    }
}
```

Los efectos de resplandor neón se crean mediante `text-shadow` y animaciones CSS que alternan la intensidad del brillo.

### CSS - Fondo Multicapa Cyberpunk

```css
body::before {
    content: '';
    background: url('...') center/cover no-repeat;
    filter: brightness(0.4);
    z-index: -2;
}

.container::before {
    content: '';
    background: url('...') center/cover no-repeat;
    opacity: 0.08;
    border-radius: 20px;
}
```

Se utilizan pseudoelementos `::before` para crear capas de fondo con imágenes de ciudades cyberpunk, aplicando filtros para ajustar la visibilidad.

### JavaScript - Función de Navegación

```javascript
function showSection(sectionName) {
    const sections = document.querySelectorAll('.section');
    const buttons = document.querySelectorAll('.nav-btn');
    
    sections.forEach(section => {
        section.classList.remove('active');
    });
    
    buttons.forEach(button => {
        button.classList.remove('active');
    });
    
    document.getElementById(sectionName).classList.add('active');
    event.target.classList.add('active');
}
```

Esta función oculta todas las secciones, luego muestra solo la seleccionada añadiendo la clase `active`.

### JavaScript - Calculadora en Tiempo Real

```javascript
function calcular() {
    const num1 = parseFloat(num1Input.value);
    const num2 = parseFloat(num2Input.value);
    const operation = operationSelect.value;

    if (isNaN(num1) || isNaN(num2) || operation === '') {
        resultDisplay.textContent = '---';
        return;
    }

    let resultado;

    switch(operation) {
        case 'suma':
            resultado = num1 + num2;
            break;
        case 'resta':
            resultado = num1 - num2;
            break;
        // ... más operaciones
    }

    resultDisplay.textContent = resultado.toFixed(2);
}

num1Input.addEventListener('input', calcular);
num2Input.addEventListener('input', calcular);
operationSelect.addEventListener('change', calcular);
```

La calculadora usa `addEventListener` para detectar cambios en los inputs y ejecutar la función de cálculo automáticamente. Utiliza `parseFloat()` para convertir los valores de texto a números y `switch` para ejecutar la operación correspondiente.

### JavaScript - Conversor Binario → Decimal

```javascript
function convertirBinarioADecimal() {
    const valor = binaryInput.value.trim();

    if (valor === '') {
        binaryResult.textContent = '---';
        return;
    }

    // Validar que solo contenga 0s y 1s
    if (!/^[01]+$/.test(valor)) {
        binaryResult.textContent = 'ERROR';
        return;
    }

    const resultado = parseInt(valor, 2);
    binaryResult.textContent = resultado;
}
```

La función utiliza una expresión regular (`/^[01]+$/`) para validar que el input solo contenga 0s y 1s. Luego usa `parseInt(valor, 2)` donde el segundo parámetro `2` indica que debe interpretar el string como binario.

### JavaScript - Conversor Decimal → Binario

```javascript
function convertirDecimalABinario() {
    const valor = decimalInput.value.trim();

    if (valor === '') {
        decimalResult.textContent = '---';
        return;
    }

    const num = parseInt(valor);
    if (isNaN(num) || num < 0) {
        decimalResult.textContent = 'ERROR';
        return;
    }

    const resultado = num.toString(2);
    decimalResult.textContent = resultado;
}
```

Convierte el número decimal a binario usando el método `.toString(2)`, donde `2` es la base numérica (binaria).

### CSS - Responsive Design

```css
@media (max-width: 768px) {
    .container {
        padding: 25px;
        width: 95%;
    }

    .nav-buttons {
        flex-direction: column;
    }
}

@media (max-width: 480px) {
    h1 {
        font-size: 1.6em;
    }
}
```

Los media queries ajustan el diseño según el tamaño de pantalla. En tablets los botones se apilan verticalmente, y en móviles se reducen los tamaños de fuente.

### CSS - Scrollbar Personalizado

```css
.container::-webkit-scrollbar {
    width: 8px;
}

.container::-webkit-scrollbar-thumb {
    background: linear-gradient(180deg, #00ffff, #ff00ff);
    border-radius: 10px;
}
```

El scrollbar se personaliza con un gradiente neón que va de cian a magenta, manteniendo la estética cyberpunk.

## 🎨 Paleta de Colores

- **Cian neón**: `#00ffff` - Textos principales y bordes
- **Magenta neón**: `#ff00ff` - Etiquetas y acentos
- **Fondo oscuro**: `rgba(10, 10, 30, 0.95)` - Contenedor principal
- **Transparencias**: Efectos de cristal esmerilado (glassmorphism)

## 🔤 Fuentes Utilizadas

- **Orbitron**: Títulos y números (estilo tecnológico)
- **Rajdhani**: Etiquetas y textos (moderna y legible)

Ambas fuentes se cargan desde Google Fonts:
```html
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;500;700&display=swap" rel="stylesheet">
```

## 📱 Compatibilidad

- ✅ Navegadores modernos (Chrome, Firefox, Safari, Edge)
- ✅ Dispositivos móviles y tablets
- ✅ Pantallas desde 320px hasta 4K

## 🛠️ Tecnologías

- HTML5
- CSS3 (Flexbox, Grid, Animations, Media Queries)
- JavaScript Vanilla (ES6+)
- Google Fonts

## 📝 Validaciones

### Calculadora
- Verifica que ambos números sean válidos
- Previene división por cero (muestra "ERROR")
- Muestra resultados con 2 decimales

### Conversor
- **Binario**: Solo acepta caracteres 0 y 1
- **Decimal**: Solo acepta números enteros positivos
- Muestra "ERROR" para entradas inválidas

## 🎯 Características Técnicas

- **Cálculo en tiempo real**: Los resultados se actualizan mientras escribes
- **Sin recarga de página**: Todo funciona con JavaScript del lado del cliente
- **Validación instantánea**: Feedback inmediato sobre errores
- **Diseño adaptativo**: Se ajusta automáticamente al tamaño de pantalla

## 🌟 Mejoras Futuras Posibles

- Agregar más operaciones (potencias, raíces, etc.)
- Conversor hexadecimal y octal
- Historial de cálculos
- Temas personalizables
- Modo oscuro/claro
- Atajos de teclado

---

**Desarrollado con 💜 y ⚡ en el espíritu de Night City**
