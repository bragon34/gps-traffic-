# 📍 GPS Track – Clientes + Mi ubicación GPS

Página web para ubicar clientes en un mapa, medir la distancia desde tu posición GPS, calcular rutas y actualizar las coordenadas de cada cliente en Google Sheets.

---

## V1.16 — Serpentina + Google Sheets (versión unificada)

**Archivos:** `index_V1.16.html` + `Codigo.gs` (**nuevo**: hay que actualizarlo y publicar "Nueva versión"; la URL no cambia)

Toma como base la **V1.15** (serpentina, trazos, recorrido a pie/carro) y le suma todo lo de la V1.11 a la V1.14.

**Rutas y lista**
- 📋 Botón **Copiar lat, lon** junto a la precisión GPS.
- 🔢 **ID #1, #2…** en la lista, el marcador y las paradas. El buscador acepta `#ID` y ese filtro también aplica a serpentina y ruta óptima.
- ⛶ Botón **Ampliar mapa** movido a la parte **superior** del mapa.
- 🧭 **Ruta óptima**: con más de 40 clientes pregunta cuántos de los más cercanos incluir. Excluye los visitados y respeta el modo a pie/carro.
- 🐞 La primera parada ya no sale como "Parada 2".
- 🐞 Visitado, Deshacer y "siguiente parada" usan el ID, así no se confunden clientes con el mismo nombre.
- 🐞 Orden correcto de la lista cuando la ruta óptima incluye solo una parte de los clientes.

**Google Sheets**
- 🔎 Selector **Buscar por: Código (C) / Nombre (D)**. Muestra fila, código, nombre, datos de A y B y el GPS actual de AA.
- 📱 Botón **Abrir en app Sheets**: en Android abre la app nativa de Google Sheets (si no está instalada, abre el navegador); en PC abre una pestaña nueva. La app abre el archivo; la hoja y la fila se indican junto al botón.
- 🔒 Credenciales protegidas como en la V1.14: Mostrar (1 vez), campos vacíos al conectar, Cambiar conexión, Desconectar y olvidar, Recordar.

**Protección del Sheet (Codigo.gs)**
- ✍️ Solo escribe en **AA de la fila elegida**, como texto. Nunca inserta, borra, ordena ni crea hojas.
- 🚫 No escribe si AA tiene una **fórmula**.
- 🔁 Relee la celda después de guardar para confirmar que **no se truncó**.
- 🛡️ Bloqueo contra escrituras simultáneas y verificación de que la fila siga teniendo el mismo código.

---

## V1.15 — Rutas serpentina y trazos (rama paralela)

**Archivo:** `index_V1.15.html`

> Esta versión se desarrolló en paralelo a la V1.11–V1.14 (que partieron de la V1.10). La V1.16 las une.

- 🐍 **Rutas serpentina**: agrupa clientes por cercanía (distancia máx. entre vecinos, mínimo de puntos por ruta) y los recorre en franjas, en un solo sentido y sin devolverse. Los puntos aislados van en una ruta aparte.
- 🚶 **Recorrido a pie o en carro** (a pie incluye peatonales, escaleras y senderos).
- 🗂️ Resumen de rutas: Ocultar/Mostrar, Solo esta, Ver, Trazar recorrido, Serpentina para estos, Google Maps.
- 📋 Lista agrupada por ruta, con colores, número de parada y flechas en el mapa. Botón **Quitar rutas**.
- ✏️ **Mis trazos**: dibujar a mano, ordenar según trazos (con tolerancia), asignar un cliente a un trazo, guardar, exportar e importar KML.
- ⛶ Botón **Ampliar mapa** (abajo) que oculta cabecera y lista.

---

## V1.14 — Credenciales visibles solo una vez

**Archivo:** `index_V1.14.html` (usa el mismo `Codigo.gs`)

- 👁 El botón **Mostrar (1 vez)** deja ver la URL y la clave **una sola vez** mientras las escribes (15 segundos o hasta pulsar *Ocultar*).
- 🔁 Para poder verlas otra vez hay que **borrar ambos campos y escribir todo de nuevo**.
- 🧹 Al conectar, los campos **se vacían**: la URL y la clave ya no se pueden ver desde la página.
- ⚙️ **Cambiar conexión** abre los campos **vacíos**. La conexión actual sigue funcionando hasta que la nueva conecte bien, y **✖ Cancelar** vuelve atrás.
- 🔌 Al abrir la página se reconecta sola con los datos guardados, sin mostrarlos.

---

## V1.13 — Ocultar URL y clave de conexión

**Archivo:** `index_V1.13.html` (usa el mismo `Codigo.gs` de la V1.12)

- 🙈 La URL y la clave se escriben en campos **ocultos** (como contraseña). El botón **👁 Mostrar** las deja ver 15 segundos para revisar errores de tipeo.
- 🔒 Al conectar, **se esconde toda la configuración**. Solo se ve "🟢 Conectado".
- ⚙️ Botón **Cambiar conexión** para volver a ver o editar la configuración.
- 🚪 Botón **Desconectar y olvidar**: borra la URL y la clave del dispositivo.
- ☑️ Casilla **Recordar en este dispositivo**. Si la desmarcas, hay que escribir los datos cada vez que se abre la página.
- ⚠️ `SHEET_URL_FIJA` y `SHEET_CLAVE_FIJA` deben quedar **vacías** si la página está publicada, porque el código fuente de una página publicada es visible para cualquiera.

---

## V1.12 — Conexión directa con Google Sheets

**Archivos:** `index_V1.12.html` + `Codigo.gs`

- ❌ Se quitó la opción de subir y descargar el archivo `.xlsx` (V1.11).
- ✅ La página se conecta **directo al Google Sheet en línea** mediante un Apps Script (`Codigo.gs`) publicado como *Aplicación web*.
- 🔎 Busca el cliente por **código en la columna C** (filas 2 a 9999) directamente en el Sheet.
- 📍 Escribe el GPS (`lat, lon`) en la **columna AA** de esa fila. El cambio queda en el Sheet al instante.
- 📑 Permite elegir la **hoja** si el archivo tiene varias.
- 👥 Si el código está **repetido**, muestra todas las filas (con datos de A, B y D) para elegir la correcta.
- ⚠️ Pide confirmación si la celda AA ya tenía un GPS.
- 🛡️ Antes de escribir, verifica que la fila siga teniendo el mismo código (por si alguien movió filas).
- 🔑 Protegido con una **clave**. La URL y la clave se recuerdan en el teléfono y la página se reconecta sola.

**Instalación (una vez):**
1. Google Sheet → **Extensiones → Apps Script** → pegar `Codigo.gs` y cambiar `CLAVE`.
2. **Implementar → Nueva implementación → Aplicación web** (Ejecutar como: *Yo* · Acceso: *Cualquier usuario*).
3. Copiar la URL `/exec` y pegarla en la página junto con la clave → **Conectar**.

---

## V1.11 — Mejoras de uso y Excel local

**Archivo:** `index_V1.11.html`

- 📋 Botón **Copiar lat, lon** junto a la precisión GPS.
- 🔢 **ID consecutivo** (#1, #2, #3…) para cada cliente según el orden del CSV. Se ve en la lista y en el mapa, y el buscador acepta `#ID`.
- ⛶ Botón **Ampliar mapa** en la parte **superior** del mapa (pantalla completa; se cierra con *Reducir mapa* o `Esc`).
- 🧭 **Ruta óptima:** si hay más de 40 clientes, pregunta cuántos de los **más cercanos** incluir (sugiere 20, máximo 40). Ya no incluye clientes visitados.
- 🐞 Corregido: la primera parada aparecía como "Parada 2".
- 🐞 Los clientes se identifican por ID interno (antes por nombre), para evitar confusiones con nombres repetidos.
- 📗 Panel para cargar un `.xlsx`, buscar el código en la columna C, escribir el GPS en AA y descargar el archivo actualizado. *(Reemplazado en V1.12 por la conexión con Google Sheets.)*

---

## V1.10 — Versión base

**Archivo:** `index_V1.10.html`

- 📂 Carga de clientes desde **CSV** (`Nombre, lat, lon`).
- 📡 **GPS en tiempo real** con marcador, círculo de precisión y líneas hacia cada cliente.
- 📋 Lista de clientes **ordenada por distancia** y buscador por nombre.
- ✅ Botón **Visitado** (copia tu ubicación y pasa al siguiente cliente) y **Deshacer**.
- 🗺️ Carga de **barrios en KML/KMZ** con colores por barrio.
- 🛰️ Mapa de **calles o satélite**.
- 🧭 **Ruta óptima** con OSRM (máximo ~40 clientes).
- 🔋 **Pausa automática del GPS** tras 5 minutos sin movimiento, y botón para pausar o reanudar.
