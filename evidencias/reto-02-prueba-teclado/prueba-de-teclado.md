# Práctica Clase 7 · Reto 2 — Evidencias de recorrido con teclado (MiniModa)

* **Versión / Escenario:** Versión 1, sin aceptar cookies al inicio.
* **Teclas utilizadas:** `Tab`, `Enter` (y evaluación de recorrido/foco).

## Comportamiento y hallazgos del recorrido con teclado

* **No se recorren todos los botones con `Tab`:** El recorrido con `Tab` no pasa por todos los botones de la pantalla; en particular, omite el botón «Comprar ahora» y salta directamente de «Agregar al carrito» hacia «Tu email».
* **Controles alcanzados e interacción con `Enter`:** Fue posible acceder y activar con `Enter` controles como «Guía de talles» (abriendo su pop-up), «Agregar al carrito», «Suscribirme» y «Aceptar» (cookies), además de acceder a los inputs de cantidad de artículos y de email.
* **Aceptación de cookies lograble pero a ciegas:** Finalmente se podían aceptar las cookies con el teclado, pero la dificultad estaba en dar con el botón porque no se sabía dónde se estaba parado visualmente.
* **Ausencia de foco visible (`:focus`):** El foco no se contorneaba ni se marcaba visualmente en pantalla al tabular, obligando a avanzar adivinando en qué elemento se encontraba el foco.
* **Comportamiento del pop-up «Guía de talles» al tabular:** Al pasar por «Guía de talles» y abrir el pop-up con `Enter`, si se continúa tabulando el foco sigue el orden de la página y no ingresa de inmediato al pop-up; para llegar al botón que cierra el pop-up hay que tabular pasando incluso por el botón «Aceptar» de cookies, y el control solo dice «cerrar» sin aclarar qué se cierra.