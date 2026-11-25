# Práctica Clase 7 · Barreras de accesibilidad y visuales — MiniModa



## Reto 1. Escaneo con Lighthouse (Versión 1)

* **URL analizada:** `https://simonethg.github.io/minimoda-test/practicas/clase-07/kit/`
* **Puntaje de accesibilidad:** `71 / 100`
* **Estado de validación:** Validado visualmente en la página.
* **Evidencia:** [Reporte HTML de Lighthouse (`prueba-accesibilidad.html`)](./evidencias/reto-01-lighthouse/prueba-accesibilidad.html)

### Errores marcados por Lighthouse (`score: 0`)

| Error en Lighthouse | Qué significa en palabras simples | Criterio WCAG 2.2 y nivel | Confirmado en página | 
| ----- | ----- | ----- | ----- | 
| Botones sin nombre accesible (`button-name`) | Un botón no tiene texto visible ni etiqueta accesible; un lector de pantalla solo dice "botón" sin aclarar su función. | **4.1.2** Nombre, función, valor (Nivel A) | Validado visualmente | 
| Contraste insuficiente (`color-contrast`) | El texto tiene bajo contraste frente al fondo (`2.84:1`, `#999999` sobre `#ffffff`) y cuesta leerlo. | **1.4.3** Contraste mínimo (Nivel AA) | Validado visualmente | 
| Falta atributo `lang` en `<html>` (`html-has-lang`) | La página no declara su idioma en `<html>`, lo que puede afectar cómo pronuncian los lectores de pantalla. | **3.1.1** Idioma de la página (Nivel A) | Validado visualmente | 
| Imágenes sin atributo `alt` (`image-alt`) | Falta texto alternativo en una imagen, por lo que no se describe su contenido a quien no la ve. | **1.1.1** Contenido no textual (Nivel A) | Validado visualmente | 
| Nombre accesible no coincide con texto visible (`label-content-name-mismatch`) | El botón muestra *"Agregar al carrito"* pero su `aria-label` dice `"btn-primary"`. | **2.5.3** Etiqueta en el nombre (Nivel A) | Validado visualmente | 
| Objetivos táctiles pequeños o muy juntos (`target-size`) | Los botones de talle (`18px × 18px`) tienen tamaño/espaciado menor al mínimo recomendado (`24px`). | **2.5.8** Tamaño del objetivo táctil mínimo (Nivel AA) | Validado visualmente | 

## Reto 2. Recorrido con el teclado (Versión 1)

* **Teclas permitidas:** `Tab`, `Shift+Tab`, `Enter`, `Espacio` y `Esc`.
* **Criterios WCAG 2.2 a evaluar:** `2.1.1` (Teclado), `2.1.2` (Sin trampa de foco), `2.4.3` (Orden del foco), `2.4.7` (Enfoque visible), `2.4.11` (Foco no tapado - mínimo).
* **Evidencia:** [Notas de prueba de teclado (`prueba-de-teclado.md`)](./evidencias/reto-02-prueba-teclado/prueba-de-teclado.md)

### Notas del recorrido

* **No se recorren todos los botones con `Tab`:** Al tabular, el foco **no pasa por todos los botones**; en particular, no pasa por el botón **«Comprar ahora»** y salta desde **«Agregar al carrito»** hacia **«Tu email»**.
* **Aceptación de cookies lograble, pero difícil de ubicar sin foco visible:** Finalmente se podían aceptar las cookies con el teclado, pero la dificultad estaba en dar con el botón porque no se sabía dónde se estaba parado visualmente, ya que el foco no se contorneaba ni se marcaba en pantalla.
* **Interacción parcial y sin indicador visual de foco:** Donde sí llegó el foco (`Tab` + `Enter`), se pudo abrir el pop-up/modal de **«Guía de talles»**, acceder a los inputs de **cantidad** y **email**, y activar **«Agregar al carrito»**, **«Suscribirme»** y **«Aceptar»** cookies, pero sin ver el foco en pantalla (avanzando adivinando).
* **Comportamiento del pop-up «Guía de talles» al tabular:** Al abrir el pop-up con `Enter` y continuar tabulando, el foco sigue el orden de la página en lugar de ingresar de inmediato al pop-up; llega a su botón de cierre recién después de pasar por el botón «Aceptar» de cookies, y el control solo dice «cerrar» sin aclarar qué se cierra.

### Tabla de hallazgos de teclado

| Barrera | Criterio WCAG 2.2 (`2.1.1`, `2.1.2`, `2.4.3`, `2.4.7`, `2.4.11` o `A CONFIRMAR`) | Cómo la encontré | A quién afecta | 
| ----- | ----- | ----- | ----- | 
| El recorrido con `Tab` omite el botón **«Comprar ahora»** y salta de **«Agregar al carrito»** a **«Tu email»** | **2.1.1** Teclado *(y revisar **2.4.3** Orden del foco)* | Tabulando por la ficha de producto con Narrador/teclado y comprobando que no enfoca **«Comprar ahora»** | Personas que dependen del teclado o lector de pantalla para operar todos los controles | 
| Ausencia de contorno o marca visual del foco al navegar con `Tab`, dificultando dar con controles como el botón **«Aceptar»** de cookies y obligando a avanzar adivinando | **2.4.7** Enfoque visible | Recorriendo con `Tab` y activando con `Enter` sin ver el foco contorneado ni marcado en pantalla (se lograba aceptar las cookies al dar con el botón) | Personas que navegan con teclado sin ratón, personas con baja visión o con trastornos de atención | 
| Al abrir el pop-up de «Guía de talles» con `Enter`, `Tab` sigue el orden de la página y recién llega al cierre tras pasar por «Aceptar» cookies, anunciando solo «cerrar» | **2.4.3** Orden del foco *(y revisar **2.1.2** / **4.1.2**)* | Abriendo el pop-up con `Enter`, tabulando por la página y escuchando el botón de cierre | Personas que navegan con teclado o lector de pantalla al interactuar con modales/pop-ups | 
| Activación con `Enter` en controles alcanzables (*Guía de talles*, *Agregar al carrito*, *Suscribirme*, *Aceptar* cookies, inputs de cantidad y email) | **2.1.1** Teclado *(funcional en esos controles; pendiente confirmar cierre/salida con `Esc`/`Tab` y orden del foco en el modal)* | Presionando `Tab` hasta los controles alcanzables y activándolos con `Enter` (incluyendo dar con *Aceptar* cookies sin contorno visible) | Usuarios de teclado (el control responde a `Enter` cuando recibe foco; no aplica a los omitidos como *Comprar ahora*) | 
| Posible foco tapado al llegar al campo de email con el banner de cookies abierto | `A CONFIRMAR` *(revisar **2.4.11** Foco no tapado - mínimo)* | Tabulando hacia el campo de email sin aceptar cookies; confirmar si el banner cubre el elemento enfocado | Personas que usan teclado o aumento de pantalla | 

## Reto 3. Lector de pantalla (Narrador en Windows)

* **Herramienta utilizada:** Narrador (recorrido con `Tab` sobre la pantalla).
* **Evidencia:** [Notas del Narrador (`prueba-lector-pantalla.md`)](./evidencias/reto-03-lector-pantalla/prueba-lector-pantalla.md)

### Observaciones registradas con Narrador

| Elemento | Qué anuncia hoy (Narrador / `Tab`) | Qué debería anunciar | Criterio WCAG 2.2 | Arreglo en HTML (en una línea) | 
| ----- | ----- | ----- | ----- | ----- | 
| Botón del carrito | Sin nombre (no anuncia nombre accesible) | «Carrito, botón» | **4.1.2** Nombre, función, valor (A) | `<button class="icono-carrito" type="button" aria-label="Carrito">...</button>` | 
| Botones de talle | Solo «botón de activación» (no indica a qué talle se refiere) | El talle correspondiente y botón, por ejemplo: «Talle 2, botón» / «Talle 6, botón» | **4.1.2** Nombre, función, valor (A) *(y **2.4.6** Encabezados y etiquetas)* | `<button class="talle" type="button" aria-label="Talle 2" aria-pressed="false">2</button>` | 
| Botón «Agregar al carrito» | Solo «botón primario» (por tener `aria-label="btn-primary"`) | «Agregar al carrito, botón» | **2.5.3** Etiqueta en el nombre (A) *(y **4.1.2**)* | `<button class="btn btn-primario" type="button" id="agregar">Agregar al carrito</button>` | 
| Botón «Comprar ahora» | No lo narra porque `Tab` no pasa por el botón (salta de *Agregar al carrito* a *Tu email*) | «Comprar ahora, botón» (al recibir foco con `Tab`) | **2.1.1** Teclado (A) *(y **2.4.3** Orden del foco)* | Asegurar que el botón sea `<button type="button">Comprar ahora</button>` en el orden de tabulación (`tabindex` no negativo / sin bloquear foco) | 
| Botón de cierre del pop-up «Guía de talles» | Solo «cerrar» (se alcanza después de tabular por «Aceptar» cookies) | «Cerrar guía de talles, botón» (con foco atrapado/gestionado dentro del modal al abrirlo) | **4.1.2** Nombre, función, valor (A) *(y **2.4.3** Orden del foco)* | `<button type="button" aria-label="Cerrar guía de talles">×</button>` | 
| Campo «Tu email» | Se alcanza tras saltar desde «Agregar al carrito» | «Tu email, edición» / campo de correo electrónico asociado a su etiqueta | **4.1.2** Nombre, función, valor (A) *(y **1.3.1** Información y relaciones)* | `<label for="email">Tu email</label><input id="email" type="email" placeholder="Tu email">` | 

## Reto 4. Celular, zoom y Versión 2

* **Cambio pedido en Versión 2:** Únicamente un banner/etiqueta de **«Envío gratis»** sobre la foto del producto.
* **Evidencias visuales (375 px):**
  * Versión 1: [Captura superior (`v1-375px-arriba.png`)](./evidencias/reto-04-responsive-v1-v2/v1-375px-arriba.png) · [Captura inferior (`v1-375px-abajo.png`)](./evidencias/reto-04-responsive-v1-v2/v1-375px-abajo.png)
  * Versión 2: [Captura superior (`v2-375px-arriba.png`)](./evidencias/reto-04-responsive-v1-v2/v2-375px-arriba.png) · [Captura inferior (`v2-375px-abajo.png`)](./evidencias/reto-04-responsive-v1-v2/v2-375px-abajo.png)

### Comparación Versión 1 vs. Versión 2 en vista de dispositivo

* **Cambio pedido presente en Versión 2:** Se muestra el badge/banner **«Envío gratis»** arriba a la izquierda sobre la imagen principal de la campera.
* **Diferencias NO pedidas en Versión 2:**
  * **Ausencia del botón «Agregar al carrito»:** En la captura de Versión 2 no aparece el botón *«Agregar al carrito»* (solo queda *«Comprar ahora»*), a diferencia de la Versión 1.
  * **Desaparición del rayado rojo alrededor de «Cantidad»:** En Versión 1 se veía un área con rayado rojo diagonal alrededor del campo *«Cantidad»*; en Versión 2 ya no está.
* **Desplazamiento lateral y problemas compartidos en ambas versiones:** Se observan barras de desplazamiento horizontal en DevTools, el banner superior *"Hasta 3 cuotas sin interés en toda la colección de"* aparece cortado en el borde derecho, la tabla de talles se extiende hacia el margen derecho y el banner fijo de cookies ocupa la franja inferior.

## Reto 5. Tabla consolidada de hallazgos y 3 issues para GitHub

### Tabla de hallazgos confirmados

| Hallazgo | Criterio WCAG | Cómo lo encontraste | ¿Lo detectó Lighthouse? | 
| ----- | ----- | ----- | ----- | 
| El botón del carrito no tiene nombre accesible (y los botones de talle solo anuncian «botón de activación» sin indicar el talle) | **4.1.2** Nombre, función, valor (Nivel A) | Escaneando con Lighthouse y recorriendo con el Narrador / `Tab` | Sí (para el botón del carrito sin nombre accesible) | 
| El botón «Agregar al carrito» anuncia «botón primario» en vez de su texto visible por tener `aria-label="btn-primary"` | **2.5.3** Etiqueta en el nombre (Nivel A) | Escaneando con Lighthouse y comprobando con el Narrador | Sí | 
| El recorrido con `Tab` no pasa por todos los botones: omite «Comprar ahora» y salta de «Agregar al carrito» a «Tu email» | **2.1.1** Teclado (Nivel A) *(revisar **2.4.3**)* | Recorriendo con `Tab` y Narrador en la ficha de producto | No | 
| Falta contorno o marca visual del foco al avanzar con `Tab` (se logra aceptar cookies al dar con el botón, pero sin saber dónde se está parado visualmente) | **2.4.7** Enfoque visible (Nivel AA) | Navegando con `Tab` y `Enter` en la ficha de producto | No | 
| Al abrir el pop-up de «Guía de talles» con `Enter`, `Tab` sigue el orden de la página, recién llega al cierre tras pasar por «Aceptar» cookies y el control solo dice «cerrar» | **2.4.3** Orden del foco *(y **4.1.2** Nombre, función, valor)* | Probando con `Tab` y Narrador al abrir el pop-up de «Guía de talles» | No | 
| En Versión 2, además del banner «Envío gratis» pedido, desaparece el botón «Agregar al carrito» (y cambia el rayado rojo de «Cantidad») con desplazamiento horizontal y banner superior cortado | Hallazgo visual / responsive no pedido *(revisar **1.4.10** Reflujo si aplica)* | Comparando capturas de Versión 1 y Versión 2 en DevTools (modo dispositivo) | No | 

### Issues abiertos en GitHub

* **#3 (`Accesibilidad`):** El recorrido con Tab omite el botón «Comprar ahora» y salta a «Tu email».
* **#4 (`Accesibilidad`):** Falta contorno o marca visual del foco al navegar con Tab por la ficha de producto.
* **#5 (`Visual`):** En Versión 2 desaparece el botón «Agregar al carrito» y persiste recorte/scroll horizontal.
```[cite: 8]
