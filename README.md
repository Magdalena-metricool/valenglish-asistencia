# Control de Asistencia — ValEnglish

Herramienta para calcular el % de asistencia de los estudiantes a partir de los exports de Zoom (Metricool) o del fichero Attendance Tracker. Incluye recordatorios automáticos en Slack.

---

## Puesta en marcha (una sola vez)

### 1. Crear el repositorio en GitHub

1. Ve a [github.com](https://github.com) e inicia sesión
2. Haz clic en **New repository**
3. Ponle nombre (ej. `valenglish-asistencia`), márcalo como **Private** si quieres
4. Sube los archivos de esta carpeta: `index.html`, `.github/workflows/recordatorios.yml` y este `README.md`

### 2. Activar GitHub Pages (para publicar la herramienta)

1. En el repo, ve a **Settings → Pages**
2. En *Source*, selecciona **Deploy from a branch**
3. Selecciona la rama `main` y la carpeta `/ (root)`
4. Guarda — en unos minutos la herramienta estará disponible en:
   `https://TU_USUARIO.github.io/valenglish-asistencia/`

### 3. Conseguir la Slack Webhook URL (pedir a IT)

Pide a alguien con permisos de Slack que cree una **Incoming Webhook** para el canal `#es5-people-metricool`:

1. Ir a [api.slack.com/apps](https://api.slack.com/apps) → **Create New App** → **From scratch**
2. Nombre: `ValEnglish Asistencia`, workspace: el de la empresa
3. En el menú lateral: **Incoming Webhooks** → activar → **Add New Webhook to Workspace**
4. Seleccionar el canal `#es5-people-metricool` → **Allow**
5. Copiar la URL que empieza por `https://hooks.slack.com/services/...`

### 4. Añadir la Webhook URL como secreto en GitHub

1. En el repo, ve a **Settings → Secrets and variables → Actions**
2. Haz clic en **New repository secret**
3. Nombre: `SLACK_WEBHOOK_URL`
4. Valor: pega la URL del paso anterior
5. Guarda

¡Listo! Los recordatorios se enviarán solos en las fechas programadas.

---

## Fechas de recordatorios automáticos

| Fecha | Descripción |
|-------|-------------|
| Lunes 2 de noviembre de 2026 | Revisión asistencia octubre |
| Lunes 7 de diciembre de 2026 | Revisión asistencia noviembre |
| Jueves 10 de diciembre de 2026 | Recordatorio cierre trimestre |
| Lunes 1 de febrero de 2027 | Revisión asistencia enero |
| Lunes 1 de marzo de 2027 | Revisión asistencia febrero |
| Lunes 5 de abril de 2027 | Revisión asistencia marzo |
| Lunes 3 de mayo de 2027 | Revisión asistencia abril |
| Lunes 7 de junio de 2027 | Revisión asistencia mayo |

---

## Cómo usar la herramienta

1. Abre la URL de GitHub Pages en el navegador
2. Arrastra o sube el Excel de reportes de Zoom (export de Metricool) o el Attendance Tracker
3. La herramienta calcula automáticamente el % de asistencia por grupo
4. Los estudiantes por debajo del **75%** aparecen marcados en rojo
5. Pulsa **Exportar resumen a Excel** para descargar el informe

### Enviar recordatorio manual a Slack

En la parte superior de la herramienta hay un campo para la **Slack Webhook URL**.
Pega la URL del webhook (la misma del paso 3) y pulsa el botón para enviar un aviso inmediato al canal.

> 💡 Si no quieres tener que introducirla cada vez, puedes pedirle a alguien técnico que la ponga directamente en el código del `index.html` (línea con `id="webhookUrl"`).

---

## Formatos de Excel compatibles

| Formato | Descripción |
|---------|-------------|
| Export de Zoom / Metricool | Ficheros con cabeceras `Topic / ID / Name...` — la herramienta los detecta automáticamente |
| Attendance Tracker | Ficheros con la cabecera `STUDENT ATTENDANCE TRACKER` y marcas P/U/E/T |
