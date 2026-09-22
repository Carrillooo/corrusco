# 🏆 Musculoskeletal Challenge

Concurso educativo sobre **anatomía musculoesquelética**: 20 preguntas tipo test, 3 comodines,
modo presentador e interfaz limpia y cercana para proyectar en clase (16:9).

La interfaz sigue las **Human Interface Guidelines de Apple**: colores del sistema, tipografía SF,
tarjetas redondeadas, materiales translúcidos (Liquid Glass solo en la barra de controles),
movimiento breve y preciso, y áreas táctiles de 44 pt como mínimo.

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
| `M` | Silenciar todo (música y efectos) |
| `N` | Música de fondo sí o no |
| `F` | Pantalla completa |

---

## 🎵 Música y efectos

Todo el audio se **genera en el navegador** con la Web Audio API: no hay ni un solo archivo de sonido,
así que no puede fallar por una descarga, y la música es original — no reproduce ninguna sintonía
de ningún programa real.

- **Sintonía de apertura** al pulsar *Comenzar concurso*.
- **Música de concurso** en bucle de cuatro compases (bajo, colchón de acordes, bombo y charles)
  que **sube de intensidad con la dificultad**: 92 pulsos por minuto y sin batería en las fáciles,
  116 con arpegio en las extremas.
- El volumen **baja solo** durante los 1,5 s de tensión previos a la respuesta y mientras corre un
  temporizador, para que se oiga bien la cuenta atrás.
- **Efectos propios** para: elegir respuesta, confirmar, acierto (fanfarria), fallo, tic-tac,
  últimos 5 segundos, fin de tiempo, llegada a la pregunta 20 y victoria final.
- **Cada comodín tiene su efecto**: tijeretazos en el 50/50, dos toques de llamada en el teléfono
  y pasar de hoja con campanita en los apuntes.

Botón 🔊 para silenciarlo todo y botón 🎵 para quitar solo la música dejando los efectos.

## 🌗 Aspecto claro y oscuro

La app arranca con el aspecto del sistema y el botón ☀️/🌙 lo cambia a mano (se recuerda).
El claro va mejor con proyector y luz encendida; el oscuro, con la clase a oscuras.

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

Probado automáticamente en Chromium con 128 comprobaciones: las 20 respuestas correctas, el 50/50
(nunca borra la correcta, no se puede usar dos veces), los tres comodines de un solo uso, la parada
correcta de los temporizadores, una partida completa de la pregunta 1 a la 20, el cálculo final,
el guardado en `localStorage`, los atajos de teclado, el cambio de aspecto claro/oscuro, la ausencia
de controles solapados en la barra superior y el reinicio — sin errores en consola.

El audio se comprueba aparte (24 verificaciones): que la música arranca con el concurso, que el
secuenciador avanza, que sigue el nivel de dificultad, que baja de volumen en la tensión y en los
temporizadores, que los dos interruptores y la tecla `N` funcionan y se recuerdan, y que para al
llegar al resultado. Además se renderiza el audio sin reproducirlo para medir que ni la música ni
los efectos saturan.
