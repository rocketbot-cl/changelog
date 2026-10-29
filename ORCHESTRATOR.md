# Changelog de Orchestrator

Todos los cambios relevantes de Rocketbot Orchestrator, por versión. La versión más nueva va primero.

---

## [2026] - 2026-11-16

### Novedades

#### 📊 Consola de procesos

**Nuevo**

- La sección **Processes** ahora es una consola de operación: muestra el estado de todos los procesos de la empresa en una sola pantalla, con tarjetas de resumen (en ejecución, en cola, sin respuesta y completados) y una tabla con el estado de cada proceso.
- Cada proceso muestra su última ejecución, su duración, las instancias vinculadas, los pendientes en cola y la próxima ejecución programada.
- Los crones se muestran en lenguaje claro (por ejemplo, "todos los días a las 9:00") junto con la fecha de la próxima ejecución.
- Filtros por proyecto, estado, tipo de robot y búsqueda por nombre, con ordenamiento y paginación.
- La consola se actualiza sola mientras está abierta, sin recargar la página.
- Dentro de un proyecto, las tarjetas de resumen muestran solo los procesos de ese proyecto.

**Mejorado**

- Las ejecuciones que quedaron colgadas porque una instancia se cayó sin avisar ya no se cuentan como "en ejecución": se muestran aparte como **sin respuesta**, para que los números reflejen lo que realmente está corriendo.

#### ⚙️ Procesos

**Nuevo**

- **Duplicar un proceso:** se crea una copia con su robot y podés elegir qué más traer: crones, instancias, miembros, assets, Process Control, formulario Xperience y Launchbot. Se pueden crear hasta 25 copias de una vez.
- En las copias, los crones llegan **desactivados**, para que el proceso nuevo no empiece a ejecutarse solo. Las colas de tareas no se copian: cada copia arranca vacía.
- Al duplicar, podés avisar por email a los destinatarios de Process Control de las copias.
- **Ejecutar en otra instancia:** podés correr el robot de un proceso en una instancia que no está vinculada. La instancia se vincula de forma provisoria y se desvincula sola al terminar la ejecución o al detenerla a mano. Las instancias provisorias no se usan en las ejecuciones programadas por cron.
- **Procesos privados:** los procesos privados solo los ven sus miembros. El nuevo permiso extra **Ver procesos privados** permite verlos todos, y ese acceso queda registrado en la auditoría.

**Mejorado**

- Los listados de procesos y robots cargan más rápido, sobre todo en empresas con muchos procesos.

#### 🛡️ Análisis de código de robots

**Nuevo**

- Al desplegar un robot de tipo **zip** o **script**, el Orchestrator analiza su código en busca de problemas de seguridad y errores.
- El resultado se muestra como un nivel de riesgo (**Seguro**, **Advertencia** o **Peligroso**) con un puntaje de 0 a 100 y el detalle de los problemas encontrados.

#### 🗂️ Tasks

**Nuevo**

- Nueva sección **Tasks** en el menú lateral. Los sets de tareas pasan a ser de la empresa y no de un proceso: cualquier proceso puede usarlos.
- Cada set tiene un nombre y una clave única dentro de la empresa.
- Las tareas se pueden cargar a mano o subiendo un archivo **CSV o Excel (XLS/XLSX)**, indicando si la primera fila tiene los encabezados. Al terminar, se informa cuántas filas se cargaron y cuáles fallaron.
- Un proceso puede configurarse para arrancar solo cuando su set de tareas tiene transacciones pendientes. Varios procesos pueden compartir el mismo set.

**Mejorado**

- Cuando un robot toma una transacción, queda bloqueada para los demás: dos robots ya no procesan la misma transacción.

#### 📝 Form Xperience

**Nuevo**

- Nuevo tipo de campo **JSON** en los formularios. El valor se valida al enviar y se guarda como objeto o lista, no como texto. Tamaño máximo: 50 MB.
- Se pueden **eliminar registros de las colas**. Los registros eliminados dejan de verse y no se procesan.

**Mejorado**

- Si la empresa alcanzó su límite de almacenamiento, los formularios rechazan nuevos envíos con el mensaje "Storage limit reached. Please contact your administrator.". Aplica al formulario publicado, al envío por API y a la carga de archivos.
- El uso de almacenamiento que muestra el panel ahora incluye los archivos adjuntos de los formularios, y coincide con el límite que se aplica.

#### 🔔 Notificaciones

**Nuevo**

- Nueva sección **Notifications**, con **Events** y **Channels**.
- Canales disponibles: **Slack, Microsoft Teams, PagerDuty, Twilio y Webhook**.
- Eventos a los que te podés suscribir: instancia desconectada, timeout de un proceso, licencia por vencer y notificaciones externas. La severidad se define en cada suscripción.
- **Webhook:** podés tener varios por empresa, cada uno con su propio destino. El cuerpo del mensaje se arma con una plantilla JSON con variables como `{{title}}`, `{{body}}`, `{{severity}}`, `{{timestamp}}` y `{{meta.*}}`, y los headers son libres (por ejemplo, para autenticación).
- Al editar un canal, los datos sensibles (URLs de webhook, tokens y headers) se muestran enmascarados. Si no los cambiás, se conservan los que ya estaban guardados.

#### 👥 Usuarios, roles y permisos

**Nuevo**

- Nuevos permisos extra para **Process Control**: uno para ver los destinatarios y otro para modificarlos.

**Corregido**

- Cada usuario recibe la API key de la empresa en la que está trabajando, también si pertenece a varias empresas.
- Al deshabilitar a un usuario en una empresa, su API key de esa empresa deja de funcionar.
- La lista de usuarios de una empresa incluye a los miembros que pertenecen a varias empresas.
- Consultar los logs de un proceso que todavía no tiene ejecuciones ya no se muestra como error.

**Mejorado**

- Mensajes de error más claros al crear o editar usuarios (nombre, email, teléfono y contraseña), en lugar de un mensaje genérico.
- Si se vence el tiempo para elegir la empresa al iniciar sesión, el mensaje lo explica y pide volver a ingresar.

#### 🏃 Clientes Runner

**Nuevo**

- Desde **Clients**, un administrador de la plataforma puede marcar un cliente como **Runner**.

#### 🧭 Menú lateral

**Mejorado**

- El menú lateral se reorganizó y suma las secciones **Tasks** y **Notifications**.

#### 🤖 Asistente MCP

**Nuevo**

- El Orchestrator expone un **servidor MCP** para conectar asistentes de IA (como Claude). El asistente se autentica con el token del usuario y respeta sus permisos y su empresa.
- Desde el asistente podés:
  - Consultar el resumen de la cuenta, el estado de la licencia y el estado de instancias y procesos, incluido el uso de CPU, RAM y disco de cada instancia.
  - Listar, crear, editar y eliminar proyectos y procesos.
  - Ejecutar y detener robots, y consultar el estado y los logs de la última ejecución.
  - Configurar crones, trigger, formulario Xperience, Process Control, emails de alerta e instancia de respaldo de un proceso.
  - Vincular, desvincular y crear instancias.
  - Listar, crear y editar formularios Xperience: campos, CSS, JavaScript y assets.
- Las acciones que modifican datos quedan registradas en los logs de usuario con la marca **[MCP]**.
- Si los datos enviados no son válidos, el asistente recibe el motivo del error para poder corregirlos.

### ⚠️ Antes y después de actualizar

- **Process Control:** ver y modificar los destinatarios ahora requiere los nuevos permisos extra. Los administradores los tienen por defecto; para los demás roles, asignalos desde **Roles**.
- **Procesos privados:** si un usuario necesita ver procesos privados de los que no es miembro, asignale el permiso extra **Ver procesos privados** desde **Roles**.
- **Tasks:** la carga de tareas se movió de la ficha del proceso a la nueva sección **Tasks**. Los robots que usan tareas tienen que actualizar el módulo de Rocketbot Studio para trabajar con la nueva versión.
- **Tasks:** la opción de ejecutar un proceso cuando tiene tareas pendientes se reemplazó por el set de tareas que lo activa. Revisá la configuración de los procesos que la usaban.
- **Duplicar procesos:** las copias nacen con los crones desactivados. Activalos cuando la copia esté lista para correr.
- **Almacenamiento:** el panel de uso ahora suma los archivos adjuntos de los formularios, así que el valor puede ser mayor que antes. Si una empresa ya supera su límite, sus formularios dejan de aceptar envíos.
