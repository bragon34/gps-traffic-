# 📍 GPS Track – Clientes + Mi ubicación GPS

Página web para ubicar clientes en un mapa, medir la distancia desde tu posición GPS, calcular rutas y actualizar las coordenadas de cada cliente en Google Sheets.

---

## V1.13 — Ocultar URL y contra de conexión

**Archivo:** `index_V1.13.html`

- 🙈 La URL y la clave se escriben en campos **ocultos**  El botón **👁 Mostrar** las deja ver 15 segundos para revisar errores de tipeo.
- 🔒 Al conectar, **se esconde toda la configuración**. Solo se ve "🟢 Conectado".
- ⚙️ Botón **Cambiar conexión** para volver a ver o editar la configuración.
- 🚪 Botón **Desconectar y olvidar**: borra la URL y la clave del dispositivo.
- ☑️ Casilla **Recordar en este dispositivo**. Si la desmarcas, hay que escribir los datos cada vez que se abre la página.


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
