# Changelog de AiStudio

Todos los cambios relevantes de AiStudio, por versión. Cada versión lista las novedades para quienes usan la herramienta: funciones nuevas, mejoras visuales y errores corregidos.

---

## [2.1.0] - 2026-11-24

### Novedades

#### 🚨 Tareas que necesitan atención

**Nuevo**
- **Pausa automática de tareas con errores que no se resuelven solos**: si una tarea falla 3 veces seguidas por un problema que necesita tu intervención, AiStudio la pausa para que no siga fallando. Pasa cuando la autorización de la cuenta venció o fue revocada, cuando la cuenta no puede renovar su acceso, cuando faltan permisos, cuando la tarea no tiene una cuenta conectada o cuando no se encuentra la carpeta de Google Drive. Los errores pasajeros no pausan la tarea.
- **Aviso en el Dashboard**: indica cuántas tareas pausadas necesitan atención y, al desplegarlo, muestra el motivo de cada pausa y hace cuánto ocurrió.
- **Corregir y reanudar desde el aviso**: cada tarea tiene un botón para resolver el problema ("Reauthorize", "Assign credential", "Choose folder" o "Review") y otro para reanudarla.
- Las tareas que usan la misma cuenta se agrupan: al volver a autorizar la cuenta, se corrigen todas juntas.
- **Indicador en el selector de entidades** del encabezado: muestra cuántas tareas pausadas tiene cada entidad, para que no se te pase ninguna aunque estés trabajando en otra.
- Solo los administradores de la entidad pueden corregir y reanudar las tareas. El resto de los miembros ve el aviso.

---

#### 📊 Dashboard

**Nuevo**
- **Selector de período**: 7 días, 12 semanas, 12 meses o todo el historial.
- **Indicadores principales**: ejecuciones, créditos usados (con los créditos disponibles de la entidad), promedio de créditos por ejecución y tiempo promedio de procesamiento de la IA.
- **Gráfico de uso** que alterna entre créditos y ejecuciones.
- **Desglose de créditos** agrupado por tarea o por tipo de tarea.
- **Ejecuciones recientes** con filtros por tipo de tarea y por estado, paginación numerada y el tiempo de procesamiento de cada ejecución.
- Las ejecuciones hechas con **tu propia clave de IA** se marcan con la etiqueta "External" junto al modelo usado.

**Mejorado**
- Los estados de las ejecuciones ahora se muestran con su nombre correcto: filtrada, en proceso, procesada o fallida.
- Si los datos no cargan, se muestra un mensaje con un botón para reintentar, en lugar de una tarjeta vacía.

---

#### 📋 Tareas

**Nuevo**
- **Formulario de creación y edición rediseñado**, en secciones numeradas (datos básicos, origen, filtro, extracción y acción), con tarjetas para elegir el tipo de tarea, el proveedor y la acción.
- El formulario indica cuántos campos obligatorios faltan completar y marca los errores en cada campo.
- **Vista de resultados de una tarea rediseñada**: el nombre de la tarea como título, con su entidad, su tipo y su estado (en ejecución o pausada).
- Totales de la tarea: ejecuciones, procesadas, filtradas, fallidas y créditos.
- Los botones para ejecutar y editar, y un menú para pausar o reanudar, borrar los resultados o borrar la tarea, ahora están en el encabezado.
- **Detalle de cada resultado en un panel lateral**: resumen, resultado en JSON con botón para copiar y navegación al resultado anterior o siguiente.
- **Búsqueda y filtro por estado** en las ejecuciones de una tarea. La descarga de resultados respeta la búsqueda y el filtro.
- El resultado en JSON se muestra **coloreado**, para leerlo más fácil.
- **Enlace "← Tasks"** para volver a la lista de tareas.
- La configuración de la tarea muestra las plantillas asociadas, indicando si son de tipo Prompt o JSON.
- **Tareas de Google Drive**: la vista explica cómo funcionan (revisan la carpeta cada 5 minutos y procesan cada archivo nuevo una sola vez) y el botón "Check now" busca archivos nuevos en el momento.

**Mejorado**
- **Lista de tareas rediseñada**: filtros por tipo y estado con contadores, botón para limpiar filtros y paginación de 20 tareas por página.
- La columna "Results" pasa a llamarse "Executions".
- El detalle de una tarea solo muestra lo que aplica: los filtros y extracciones se ocultan si la tarea no tiene, y el asunto aparece solo en las tareas de correo.
- Al guardar una tarea, el estado se muestra en el mismo botón, sin bloquear toda la pantalla.

**Corregido**
- Al elegir una acción en el formulario de tareas, ya no se abre la ventana de la acción elegida anteriormente.
- Los estados "Filtered" y "Failed" ya no aparecen vacíos en la tabla de ejecuciones.
- Los mensajes de aviso ya no aparecen repetidos.
- Los nombres de los archivos adjuntos se muestran correctamente en el detalle de la tarea.

---

#### 🧾 Plantillas

**Nuevo**
- **Generar plantillas con IA en dos formatos**: al subir un archivo (PDF, TXT, audio o imagen) puedes elegir si generar una plantilla de tipo Prompt (una lista de campos, cada uno con su instrucción y tipo de dato) o una de tipo JSON (un esquema con propiedades tipadas). La plantilla generada se prueba automáticamente con el mismo archivo.
- Si ya existe una plantilla con el mismo nombre, la nueva se crea con un número al final, en lugar de dar error.

**Mejorado**
- **Vista de plantillas rediseñada**: las acciones secundarias (exportar, renombrar y borrar) están en un menú ⋮.
- En el editor de esquemas JSON se edita un campo a la vez, y los saltos de línea en las descripciones se muestran correctamente.
- Los mensajes de validación hablan de "instrucciones para la IA" en lugar de "prompts".

---

#### 🔑 API Keys y claves de IA

**Nuevo**
- **Guía rápida de la API** en la vista de API Keys: la dirección base para copiar y ejemplos listos para autenticarte, listar tus tareas y ejecutarlas.
- Al crear una API key, se pide confirmar que la guardaste en un lugar seguro antes de cerrar la ventana.

**Mejorado**
- **Vista de API Keys rediseñada**: la clave se muestra enmascarada (solo los últimos caracteres), con etiquetas de vencimiento y paginación, y las más nuevas primero.
- Las claves de IA externas muestran su plataforma, un interruptor para activarlas y mensajes claros si algo falla.
- Los campos con datos sensibles (secretos y claves) se ocultan y el navegador ya no los autocompleta.
- Enlaces actualizados a la documentación para configurar las credenciales de Google.

**Corregido**
- La clave enmascarada y las fechas de creación y actualización de las claves de IA vuelven a mostrarse.
- Al cerrar la ventana de credenciales de correo, los datos ingresados se borran.

---

#### 🏢 Entidades y créditos

**Mejorado**
- La configuración de alertas de créditos indica que los avisos se envían a todos los miembros, muestra el saldo actual y advierte si el saldo ya está por debajo del umbral.
- El selector de entidades solo aparece si tienes más de una.
- Ya no se muestra la opción de quitar al Owner de una entidad.
- **Calculadora de créditos rediseñada**: muestra el resultado aproximado y qué parte del saldo de la entidad representa, avisa si cambiaste los datos después de calcular, indica los formatos aceptados y el tamaño máximo, y explica cómo se calcula.

---

#### 📎 Archivos y correo

**Nuevo**
- **Tamaños máximos por tipo de archivo**: documentos (PDF y TXT) y audios hasta 25 MB, imágenes hasta 10 MB y correos completos (con adjuntos) hasta 25 MB. Aplican a todo lo que entra a AiStudio: archivos subidos, API, Google Drive y correo.
- Si un archivo supera el límite, el mensaje de error indica el nombre del archivo y el tamaño máximo permitido.

**Corregido**
- Las cuentas personales de Outlook (outlook.com y Hotmail) ya no renuevan su acceso en cada revisión del buzón.

---

#### 🌐 Interfaz

**Nuevo**
- **Versión de AiStudio** visible en el encabezado.

**Mejorado**
- Márgenes uniformes en todas las vistas.
- Si tu foto de perfil no carga, se muestran tus iniciales.
- Mejoras de accesibilidad en botones, menús y tablas.

### ⚠️ Antes y después de actualizar

- **Tareas pausadas automáticamente:** revisa el aviso del Dashboard después de actualizar. Corrige el motivo antes de reanudar una tarea: si lo reanudas sin corregirlo, vuelve a pausarse en unos 10 minutos.
- **Tamaño de archivos:** los archivos y correos que superen los nuevos límites no se procesan. Si trabajas con archivos grandes, revisa que estén dentro de los límites.
