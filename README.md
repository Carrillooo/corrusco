# 🏆 Musculoskeletal Challenge

Concurso educativo tipo *game show* sobre **anatomía musculoesquelética**: 20 preguntas tipo test,
3 comodines, modo presentador y estética premium para proyectar en clase (16:9).

Todo está en **un único archivo autocontenido** (`index.html`): sin instalación, sin dependencias,
sin archivos externos. Los sonidos se generan con la Web Audio API, así que nada puede "dejar de funcionar".

---

## ▶️ Cómo ejecutarlo

**Opción 1 — la más rápida (recomendada para clase)**

Haz doble clic en `index.html`. Se abre en el navegador y funciona al 100 % (Chrome, Edge, Firefox o Safari).

**Opción 2 — servidor local** (por si prefieres una URL)

```bash
python3 -m http.server 8080      # y abre http://localhost:8080
# o
npx serve .
```

Una vez abierto: pulsa **⛶** (o la tecla `F`) para ponerlo a pantalla completa en el proyector.

---

## 🎮 Cómo se juega

1. **COMENZAR CONCURSO**.
2. El concursante elige A, B, C o D → la respuesta queda **seleccionada pero no se revela**.
3. El presentador pulsa **CONFIRMAR** → 1,5 s de animación de tensión.
4. Se revela: **verde** si es correcta; **roja** la fallada y **verde** la correcta si falla.
5. Aparece el **WHY?** con la justificación y el botón **SIGUIENTE PREGUNTA →**.
6. Tras la pregunta 20: pantalla final con aciertos, fallos, porcentaje y comodines usados.

**Dificultad:** 1–5 🟢 Easy · 6–10 🟡 Medium · 11–15 🟠 Hard · 16–20 🔴 Extreme
(la interfaz cambia de color e intensidad en cada tramo).

---

## 🎯 Comodines (uno solo de cada, no reutilizables)

| Comodín | Qué hace |
|---|---|
| ✂️ **50/50** | Elimina dos respuestas incorrectas al azar (nunca la correcta) y las desactiva. |
| 📱 **Teléfono** | Abre un modal: **🌐 Internet (20 s)** o **☎️ Llamada (2:00)**. Cualquiera de las dos **gasta el mismo comodín**. |
| 📝 **Apuntes** | 20 segundos para consultar los apuntes; al acabar: *"CIERRA LOS APUNTES"*. |

Los temporizadores tienen cuenta atrás gigante, aro de progreso, aviso visual y sonoro en los
últimos 5 segundos, botón de **finalizar antes** y botón de **reiniciar**.

---

## ⌨️ Atajos de teclado

| Tecla | Acción |
|---|---|
| `A` `B` `C` `D` | Seleccionar respuesta |
| `Enter` | Confirmar (o pasar a la siguiente si ya está revelada) |
| `→` / `←` | Siguiente / anterior pregunta |
| `1` `2` `3` | 50/50 · Teléfono · Apuntes |
| `P` | Abrir/cerrar el panel del presentador |
| `Esc` | Cerrar modales / panel |
| `M` | Silenciar o activar el sonido |
| `F` | Pantalla completa |

---

## 🎬 Modo presentador (`P` o el botón 🎬)

Panel lateral que **desplaza** la pantalla (no tapa la pregunta) y permite:

- Ver la **respuesta correcta** y la **justificación** antes de enseñarlas al público.
- Ir a la siguiente/anterior, **confirmar**, **revelar**, **marcar correcta/incorrecta a mano**,
  **reabrir** una pregunta y **reiniciar el concurso**.
- Activar manualmente cualquier comodín, ver cuáles siguen disponibles y **reiniciar el temporizador**.
- Saltar directamente a cualquiera de las 20 preguntas (pasa el ratón por encima del número para ver su enunciado).

---

## 💾 Guardado automático

El estado (pregunta actual, respuestas, comodines gastados, sonido) se guarda en `localStorage`,
así que **si la página se recarga por accidente no se pierde el progreso**.
Para empezar de cero: *Reiniciar concurso* en el panel del presentador o *Jugar de nuevo* al final.

---

## ✅ Verificado

Probado automáticamente en Chromium con 98 comprobaciones: las 20 respuestas correctas, el 50/50
(nunca borra la correcta, no se puede usar dos veces), los tres comodines de un solo uso, la parada
correcta de los temporizadores, una partida completa de la pregunta 1 a la 20, el cálculo final,
el guardado en `localStorage`, los atajos de teclado y el reinicio — sin errores en consola.
