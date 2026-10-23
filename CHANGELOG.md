# Historial de cambios — chart (gráfica intradía Polygon.io)

Formato de versión: `vMAYOR.REV` (ej. `v03.01`).

**Organización de la carpeta:** en la carpeta principal solo queda `chart_current.html` (la versión vigente). Cada versión numerada se guarda en `backup/` (ej. `backup/chart_v03_06.html`), y `chart_current.html` es siempre una copia exacta de la última de ellas.

**Versión vigente: v03.19** (`backup/chart_v03_19.html` = `chart_current.html`)

> Nota sobre la numeración: hubo dos ramas en la serie v02. La rama de junio llegó a v02.31; la de septiembre/octubre se reinició desde v02.10 y llegó a v02.20. A pesar del número menor, **v02.20 es la más reciente**, y v03 parte de ella para evitar confusión.

## [v03.19] - 2026-10-22
### Agregado
- **Rango de cada día** en la gráfica de precio: en el centro de cada día se muestra en grande **(máx − mín) / mín en %**. Debajo va el tamaño del rango y el mín – máx (si no cabe, solo el tamaño).
  - Se calcula sobre lo que se muestra: con presets activos (por ejemplo Open + Close) usa solo esas barras.
  - Se dibuja detrás de las velas, como marca de agua.
  - Botón on/off **Day range %** en la barra de indicadores.
  - No aplica a barras diarias.

## [v03.18] - 2026-10-16
### Cambiado
- Medición: el **3.er clic solo borra** la medición (línea, rectángulo y caja). El siguiente clic empieza una medición nueva (punto A).

## [v03.17] - 2026-10-16
### Agregado
- **Herramienta de medición con dos clics:** el 1.er clic marca el punto A y el 2.º clic marca el punto B.
  - Aparece una caja flotante junto a B con el **Δ** (en verde si sube, en rojo si baja), el **%** (en gráficas de precio), las **barras** entre A y B, el **tiempo transcurrido**, los dos valores y las dos horas ET.
  - Se dibuja la línea A→B con un rectángulo sombreado.
  - El 3.er clic empieza una medición nueva. **Esc** la borra.
  - Funciona en precio, MACD, RSI, 30 min y cross-asset.
  - Arrastrar (pan) no cuenta como clic.
  - La medición se borra al cambiar de frame (Prev/Next, vista, presets, archivo).

## [v03.16] - 2026-10-16
### Agregado
- **Valores de los ejes bajo el mouse** (estilo TradingView):
  - En la gráfica donde está el mouse aparece una línea horizontal y, en el eje derecho, una etiqueta azul con el valor exacto en esa altura (precio, MACD, RSI o puntaje cross-asset).
  - En todas las gráficas sincronizadas aparece, en el eje de tiempo, una etiqueta con el día y la hora ET de la barra más cercana.
  - El panel de 30 min ahora también sigue la línea vertical del cursor.
### Corregido
- El eje de tiempo ya no pone etiquetas dentro de los espacios vacíos entre días (salían horas que no existen, como 16:26).

## [v03.15] - 2026-10-16
### Agregado
- **Presets combinables:** ahora se pueden activar varios a la vez (por ejemplo **Open + Close**). Cada clic agrega o quita un preset; si quitas todos, vuelve la sesión completa.
  - Los rangos que se solapan se unen (Open + Morning = 9:30–12:00).
  - Entre rangos separados del mismo día queda un espacio más corto, sin línea divisoria. Entre días queda el espacio completo con la línea.
  - "Apply" con un rango propio reemplaza los presets. "Full view" quita todo.

## [v03.14] - 2026-10-16
### Corregido
- **Presets (Open, Morning, Lunch, Close, Power hour) y "Apply":** antes hacían zoom solo en el último día de la ventana y tomaban las horas en hora local (Denver), así que "Morning 9:30–12:00" mostraba en realidad 11:30–14:00 ET. Ahora:
  - Las horas son **ET** (hora del mercado).
  - El rango se aplica a **cada día** del frame (1D / 2D / 5D / 7D): por ejemplo, en 5D + Morning se ven las cinco mañanas seguidas.
  - El rango se mantiene al navegar con Prev / Next, Base date o al cambiar de vista.
  - "Full view" vuelve a la sesión completa.
### Agregado
- **Espacio vacío entre días** en las vistas de varios días (precio, MACD, RSI y panel de 30 min), con la línea divisoria en medio. Las líneas de indicadores se cortan en ese espacio.
### Cambiado
- Los ejes de tiempo y los tooltips ahora están en **hora ET** (antes en hora local), para que coincidan con los presets. El campo se llama "Time of day (ET)".

## [v03.13] - 2026-10-15
### Agregado
- Bandas **VWAP ±1σ** y **VWAP ±2σ**: desviación estándar del precio típico ponderada por volumen alrededor del VWAP de la sesión; se reinician cada día igual que el VWAP.
  - Cada nivel tiene su propio botón on/off.
  - ±1σ: amarillo claro con línea discontinua. ±2σ: ámbar con línea punteada.
  - En la gráfica de precio y en el panel de 30 min. No aplica a barras diarias.

## [v03.12] - 2026-10-15
### Agregado
- **Tres PMA** (promedio móvil aritmético / simple), independientes de las EMAs. Por defecto **40, 80 y 200**; periodos editables (2–500) en los campos **PMA** de la barra de controles.
  - Cada una tiene su propio botón on/off.
  - Se dibujan con línea punteada: PMA 1 blanca, PMA 2 turquesa, PMA 3 fucsia.
  - Están en la gráfica de precio y en el panel de 30 min, con calentamiento de días previos (completas desde la primera barra).

## [v03.11] - 2026-10-15
### Agregado
- **Base date** (campo de fecha en la barra de días): es el **primer día** del frame en cualquier vista (1D / 2D / 5D / 7D).
  - Al elegir una fecha, el frame empieza ese día. Si ese día no hay datos (fin de semana o feriado), empieza el siguiente día de operación.
  - Si no hay suficientes días después de esa fecha para llenar el frame, se corre hacia atrás y se avisa en la barra de estado.
  - Al cambiar entre 1D / 2D / 5D / 7D se mantiene el mismo primer día (antes se mantenía el último).
  - Prev / Next actualizan el campo.
  - El Breakout (MAX/MIN del primer día) usa ese mismo día.
### Cambiado
- **EMAs:** el botón único "EMA" (8 / 21 / 50) se reemplazó por **tres EMAs independientes**, cada una con su propio botón on/off y su periodo editable en los campos **EMA** de la barra de controles. Por defecto: **40, 80 y 200** (2–500).
  - Colores: EMA 1 cian, EMA 2 naranja, EMA 3 rosa.
  - Calentamiento: se toman días previos hasta tener 2× el periodo más largo, así la EMA 200 aparece completa desde la primera barra (excepto en los primeros días del archivo).
- Panel de 30 min: usa las mismas tres EMAs (antes 8 / 21 / 50 + 40 / 80), también con calentamiento de días previos.

## [v03.10] - 2026-10-15
### Agregado
- Botón **✕ Hide signals** (junto a All on / All off): con un clic oculta todas las señales de la gráfica de precio (triángulos BB Call/Put, líneas de Breakout y marcadores de spikes de EUR/USD y QQQ). Las bandas, VWAP, EMAs y demás indicadores no cambian.
- El botón cambia a **◉ Show signals** para volver a mostrarlas. Mientras están ocultas, siguen ocultas al navegar con Prev/Next.

## [v03.09] - 2026-10-15
### Corregido
- Flechas de navegación en **2D / 5D / 7D**: después de Prev/Next (o las teclas ← →) las gráficas de precio, MACD y RSI mostraban solo el último día de la ventana. Ahora muestran la ventana completa. Lo mismo para el botón "Full view".

## [v03.08] - 2026-10-15
### Cambiado
- La rueda del mouse ahora solo sube y baja la página; ya no hace zoom en ninguna gráfica (precio, MACD, RSI, 30 min, cross-asset).
- El zoom se hace con "Zoom to time" y los presets; arrastrar sigue moviendo la gráfica (pan). Se actualizaron las etiquetas de los paneles.

## [v03.07] - 2026-10-15
### Cambiado
- El panel **Cross-asset agreement** (con las alertas de spikes de EUR/USD y QQQ) se movió al final de la página, debajo del panel de 30 min. Antes estaba arriba, antes de la gráfica de precio.

## [v03.06] - 2026-10-15
### Agregado
- Indicador **Breakout** (botón en la fila de indicadores, junto a Signals): el MÁX y el MÍN del **primer día** del frame visible se proyectan como líneas horizontales hasta el final del frame. Verde lima = MAX, rojo = MIN, con etiqueta del valor.
  - 2D / 5D / 7D: el primer día de la ventana.
  - 1D: el rango del mismo día.
  - No aplica a barras diarias.

## [v03.05] - 2026-10-15
### Agregado
- Vistas **2D** y **5D** junto a 1D y 7D.
  - 2D: día anterior + día actual; Prev/Next avanzan 1 día (la ventana se desliza).
  - 5D: 5 días de operación; "← Prev 5D" / "Next 5D →" saltan 5 días, igual que 7D salta 7.
  - Separadores amarillos entre días y eje de tiempo con fecha en todas las vistas de varios días.
### Cambiado
- Los valores de los ejes (precio, MACD, RSI, horas, panel cross-asset) ahora son blancos en vez de gris oscuro (#3a4455).

## [v03.04] - 2026-10-15
### Corregido
- Vista **7D**: las flechas de navegación ya no desaparecen. "← Prev 7D" / "Next 7D →" (y las teclas ← →) mueven la ventana 7 días de operación a la vez. Se muestra el rango (ej. "502–508 / 515 days") y las flechas se desactivan al llegar al inicio o al final.

## [v03.03] - 2026-10-15
### Cambiado
- **Solo datos locales.** La gráfica ya no descarga nada de Polygon/Massive: se eliminaron el campo de API key (y la clave que venía escrita en el archivo), el botón "Load bars" y todas las llamadas a la API.
- Los datos vienen solo de los archivos guardados en `polygon/Used` (generados por `massive_capture.py`):
  - Gráfica principal: botón **Open data file** (o "Load data"). Ticker, fechas y TF se toman del archivo y ya no se editan a mano.
  - Panel cross-asset y alertas EUR/USD y QQQ: botón **Context folder** → elegir `Used/2026_macro`. Sin esa carpeta, muestran "pick Context folder".
- Context folder ignora las copias en carpetas que empiezan con `_` (`_backup_no_indicators`, `_replaced`).
- Encabezado: "Local data" en vez de "Polygon.io".

## [v03.02] - 2026-10-15
### Agregado
- Temporalidades **30 min** y **1 día** en el selector TF (también al pedir datos a la API: `1 day` usa `/range/1/day/`).
### Corregido
- Archivos de 30 min (ej. `polygon/Used/2026_macro/30min`): el selector TF y las etiquetas ahora dicen "30-min" en vez de "2-min".
- Bollinger, EMA 50, MACD y RSI en 30 min: el calentamiento toma tantos días previos como haga falta (mín. 60 barras), así que las bandas aparecen desde la primera barra del día. En 2 min no cambia nada (un día previo ya alcanza).
- Archivos diarios (`1day`): eje de fechas (mes/año), tooltip con fecha, sin navegación por día ni presets de hora (no aplican), panel de 30 min oculto y VWAP desactivado (el VWAP de sesión no tiene sentido en barras diarias).
- "Save data" con barras diarias guarda el archivo como `_1day_` en vez de `_1Dmin_`.

## [v03.01] - 2026-10-15
### Cambiado
- Nueva serie v03, creada a partir de v02.20 sin cambios de funcionalidad. Solo se actualizó la etiqueta de versión (título de la página y encabezado).

### Pendiente
- No incluye la herramienta de medición, la navegación por semana ni el salto a fecha, ni la vista de 2 días de la rama v02.31 (ver más abajo).

## [v02.20] - 2026-10-01
### Agregado
- Alerta **QQQ volume-spike FOLLOW** (`#qqq-spikes`): barra de 2 min de QQQ con volumen en el 3% superior para su franja horaria (≥ 3.67× la mediana de 20 días) y movimiento ≥ 2σ; SOXL tiende a seguir en la misma dirección y VIXY en la opuesta durante ~2 min.

## [v02.19] - 2026-10-01
### Agregado
- Alerta **EUR/USD volume-spike FADE** (`#eur-spikes`): volumen tick ≥ 1.83× la mediana de 20 días para la franja (3% superior) y movimiento ≥ 2σ en 2 min; operar en contra de la dirección del EUR/USD (VIXY: misma dirección), mantener 60 min. No probado: observar/paper-trade primero.

## [v02.18] - 2026-09-28
### Agregado
- Panel **Cross-asset agreement**: puntaje largo/corto según si EUR/USD, SOXX, VIXY y GLD están del lado de su propio VWAP que concuerda con la operación (signo de correlación diaria de 2 años). Incluye chips, valores de la última barra, gráfica de puntaje alineada con el eje de precio y extras por ticker.
- Botón **Context folder** para leer los datos de contexto desde los JSON capturados (ej. `Used/2026_macro`) en vez de la API.
### Corregido
- MACD y VWAP sin redondeo, y formato numérico que mantiene legibles valores pequeños (EUR/USD necesita 5+ decimales).

## [v02.17] - 2026-09-25
- Punto de partida de la rama de septiembre. Internamente el archivo dice **v02.10** (título y encabezado). No tiene la herramienta de medición ni la navegación por día/semana de v02.31.

---

## Rama de junio (archivada)

### [v02.31] - 2026-06-25
- Última versión de la rama de junio (`chart_v02_31.html`; original en `Downloads/chart_v02.31.html`).
- Incluye: herramienta de medición (`bindMeasureTool`), navegación por día/semana (`navStep`, `goWeek`), salto a fecha (`jump-date`), carga por rango de fechas (`fetchBarsRange`), vista de 2 días (`vt-2d`), barra de indicadores (`ind-bar`) y etiquetas de día (VIE / LUN / MAR …) sobre cada sesión.

### [v02.29] - 2026-06-23
- Copia en `Downloads/charting/chart_v02.29.html`.
