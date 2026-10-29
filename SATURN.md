# Changelog

Todos los cambios relevantes de Saturn Studio, por versión. Cada versión lista las novedades para quienes usan la herramienta: funciones nuevas, mejoras visuales y errores corregidos.

## [2.1.0]


### Novedades

#### ✏️ Editor de flujos

**Nuevo**
- **Deshacer y rehacer**: botones en la barra de herramientas para deshacer o rehacer cambios en el canvas (agregar, borrar, conectar, mover y editar comandos). Si no hay nada para deshacer, aparece un aviso.
- **Copiar y pegar varios comandos a la vez**: Ctrl+C / Ctrl+V funciona con la selección completa, conserva las conexiones entre los comandos copiados y permite pegar en otro robot o en otra pestaña. Al pegar en otro robot, se avisa si faltan variables. Límite de 100 comandos o 5 MB por copia.
- **Pegar desde el menú del canvas**: clic derecho sobre un espacio vacío para pegar lo que copiaste.
- **Selección con Shift + clic** para agregar o quitar comandos de la selección.
- **Panel de atajos de teclado** desde un botón en la barra inferior.
- **La barra inferior muestra** cuántos comandos tienes seleccionados y cuánto pesa la selección.
- **Acciones rápidas al pasar el mouse** sobre un comando: ejecutar, editar, breakpoint, desactivar y "más opciones".
- **Ejecutar robot desde aquí**: ejecuta el flujo a partir del comando que elijas.
- **Insertar un comando entre dos comandos conectados**, sin tener que rehacer las conexiones.
- **Barra sobre las conexiones**: al pasar el mouse sobre una conexión puedes agregar un comando o borrar la conexión.
- **Título y descripción personalizados** para cada comando, visibles en el canvas.
- **Desactivar un comando** desde el menú contextual. Los comandos desactivados ahora se distinguen visualmente.
- **Indicador de breakpoint**: un punto rojo junto al comando muestra que el breakpoint está activo, sin tener que pasar el mouse.
- **Contador de vueltas** en los bucles For y While mientras el robot se ejecuta.
- **Nuevo indicador de comando en ejecución**, más visible.
- **Cambios sin guardar**: el botón Guardar y la barra inferior avisan cuando hay cambios pendientes.
- **Etiqueta "Robot activo"** en el interruptor de estado del encabezado.
- **Tour de bienvenida** guiado, con un robot de ejemplo y un enlace a la guía de introducción. Se puede volver a iniciar desde el menú de usuario.

**Mejorado**
- Encabezado del editor rediseñado: botones de acción más claros y "Logs" dentro del menú "Más".
- Barra de herramientas expandible con etiquetas en los botones, y el botón "Mostrar chat" integrado en la barra.
- Tooltips descriptivos en los botones del editor.
- Los comandos nuevos se ubican a continuación del último comando del flujo.
- Ajustes visuales para que el editor se vea mejor en distintos tamaños de pantalla.

**Corregido**
- Ocultar y mostrar las ramas de If, Try/Catch, While, For y Grupo funciona en todos los niveles anidados. Una rama que ocultaste sigue oculta al mostrar la rama que la contiene.
- El contador de vueltas se reinicia bien en los While anidados y su tooltip está traducido.
- Las columnas de reintento de la pestaña "Manejo de errores" quedan alineadas.
- Los menús contextuales ya no se salen del área visible del canvas.
- Ya no se puede borrar por error el comando de inicio.
- La confirmación de borrado indica si se borra una nota o un comando, y está traducida.
- Los comandos de lógica sin descripción muestran su nombre en el tooltip.
- Al ejecutar solo el comando "Iterar sobre elementos", la variable recibe el primer elemento de la lista.
- Los tooltips ya no tapan los íconos de los comandos.
- Al abrir un robot nuevo, el editor se muestra correctamente.

---

#### 🧩 Menú de comandos y edición de comandos

**Nuevo**
- **Vista agrupada por categorías**, con grupos que se pueden colapsar y un panel lateral que se puede ocultar.
- **Buscador de módulos renovado**, con un botón para limpiar la búsqueda.
- **Enlace "Documentación del comando"** en la ventana de edición, para los comandos que la tienen (por ejemplo, Google Sheets › Agregar fila).
- **Campos obligatorios marcados** en los formularios de los módulos.
- **Botón para quitar la variable seleccionada** desde el panel lateral.

**Mejorado**
- La búsqueda encuentra un módulo por su nombre en cualquier idioma y muestra todos sus comandos.
- La pestaña de configuración del comando pasa a llamarse "Manejo de errores".
- La descripción de un comando se limita a 100 caracteres.

---

#### 🔤 Variables

**Nuevo**
- **Variables resaltadas por color** en los campos de los comandos, según su origen: local, global, de sistema o no encontrada. Funciona también en los comandos de lógica (If, While, For, Switch) y de sistema.
- **Validación de rutas** en expresiones como `${{var}.campo}`: verde si la ruta existe, amarillo si puede fallar y rojo si la clave no existe.
- **Autocompletado dentro de variables**: sugiere los campos y posiciones de objetos y listas.
- **Tamaño de cada variable** visible en el selector y en la ventana de edición.
- **Validación del nombre** al crear una variable nueva.

**Mejorado**
- Ventana de variables con diseño renovado.
- El visor JSON resalta las variables también en la vista de texto plano.
- Mensaje de error más claro al exportar o importar variables demasiado grandes.

**Corregido**
- La tarjeta para crear una credencial nueva ya no queda cortada dentro de la ventana de variables.
- El autocompletado ya no interfiere al editar el valor de una variable.

---

#### 📝 Notas

**Nuevo**
- **Markdown completo en las notas**: tablas, listas, código y enlaces. Los enlaces sin `https://` se completan solos y se abren en otra pestaña.
- **Agregar nota** desde el menú contextual del canvas o junto a un comando.

**Mejorado**
- Las notas mantienen su tamaño y tienen scroll propio cuando el contenido es largo.
- Las notas nuevas aparecen en el centro de la vista y, si el lugar está ocupado, se acomodan al costado.

---

#### ⏰ Cronograma y activación de robots

**Nuevo**
- **Aviso al activar un robot sin cronograma**: si el robot necesita uno para ejecutarse periódicamente, se indica cómo configurarlo o a quién pedírselo.
- **Confirmación al apagar un robot**. Si el robot tenía un cronograma, se apaga junto con el robot.
- **Indicadores de cronograma**: el editor muestra si el cronograma tiene cambios sin guardar.

**Mejorado**
- Validación de cronogramas (intervalo, una vez, diario, semanal, mensual y expresión cron) y de la zona horaria antes de guardar.
- Mensajes del cronograma traducidos. En español, "Schedule" pasa a llamarse "Cronograma".

**Corregido**
- Un valor de cron inválido ya no afecta el funcionamiento del servicio.

---

#### 📜 Historial de ejecuciones y logs

**Nuevo**
- **Filtro por fecha** y paginación en los logs de ejecución.
- **Filtro "solo errores"** y **búsqueda por comando** dentro de los logs.
- **Detalle desplegable** de cada entrada del log, con etiqueta de nivel (info, advertencia, error).
- **Botón para actualizar** las ejecuciones sin cerrar la ventana.
- **Logs de las pruebas en el editor**: se guardan las ejecuciones de prueba para revisarlas después.

**Mejorado**
- El indicador de ejecuciones del robot muestra las últimas 7 ejecuciones (una barra por ejecución): verde si terminó bien y rojo si falló.
- Si un robot todavía no tiene ejecuciones, se muestra un mensaje en lugar de los filtros vacíos.
- La búsqueda por comando marca qué días tienen ejecuciones que coinciden. Los días con demasiadas ejecuciones para revisar aparecen como "No verificado".

**Corregido**
- Los miembros de una entidad pueden ver los logs de los robots que no son suyos.
- Se quitó el espacio sobrante entre mensajes en la ventana de logs.

---

#### 🏢 Entidades, robots compartidos y colaboración

**Nuevo**
- **Entidades**: espacios de trabajo compartidos a los que se invita a los miembros por correo. Las invitaciones se aceptan o rechazan desde Saturn.
- **Compartir robots y carpetas** con una entidad. Los miembros pueden editar los robots compartidos.
- **Delegar un robot** a una entidad: el robot pasa a pertenecer a la entidad y sigue usando tus credenciales. Al arrastrar un robot sobre una entidad puedes elegir entre compartir o delegar.
- **Dejar de compartir** carpetas y robots desde el árbol de carpetas o desde la lista, siempre con confirmación.
- **Robot personal**: los miembros de una entidad solo pueden activar y ejecutar los robots compartidos con la entidad.
- **Edición en vivo**: varios miembros pueden editar el mismo robot a la vez, ver quién está editando, ir a su cursor y usar autoguardado. Si alguien está editando un comando, los demás lo ven en modo solo lectura.
- **Editar y borrar carpetas** desde el árbol de carpetas.
- **Aviso al abrir el robot de otro miembro**: puedes editarlo y ejecutarlo, pero los cronogramas, los webhooks y la eliminación quedan a cargo de su dueño.
- En los robots compartidos, las credenciales de otro miembro indican de quién son.

**Mejorado**
- El panel de carpetas queda fijo al costado mientras bajas por la lista de robots, así puedes arrastrar cualquier robot a una carpeta.
- Al clonar un robot compartido, el robot se copia sin las credenciales del dueño.

**Corregido**
- Los usuarios de una entidad pueden probar los robots en desarrollo.
- Al editar el nombre o la descripción de un robot, ya no se abre el editor de flujo.
- Las invitaciones pendientes ya no aparecen duplicadas, y al rechazar una ya no queda una página en blanco.
- El contador de miembros se actualiza al quitar a un miembro.
- Si pierdes el acceso a un robot mientras lo editas, se ocultan las opciones de guardar notas y editar variables.

---

#### 🔗 Webhooks

**Nuevo**
- **Crear y editar webhooks** desde la vista de Webhooks, eligiendo el robot y el origen. La URL no cambia aunque cambies el robot.
- **Autenticación de webhooks**: además del webhook público, puedes exigir un secreto en el encabezado `X-Webhook-Secret` o limitar el acceso a usuarios de Saturn. El secreto se puede regenerar.
- **Íconos del servicio de origen** en la lista de webhooks.
- **Columnas de errores y última llamada**, más estadísticas en la vista de Webhooks.

**Mejorado**
- Las URLs de los webhooks se muestran enmascaradas en pantalla. Se pueden copiar completas.
- La vista de Webhooks tiene un diseño renovado.

---

#### 🔐 Credenciales y variables globales

**Nuevo**
- **Valores ocultos en variables globales**, con un botón para verlos por un momento.
- **Botón de documentación** en la credencial de WhatsApp Business.

**Mejorado**
- Los campos sensibles de las credenciales se muestran como contraseña.
- El botón "Guardar credencial" queda desactivado hasta que la credencial sea válida, también al editar.
- Mensajes de error más claros cuando una credencial es inválida (Notion, Odoo, Shopify y verificación de API Keys).

---

#### 🤖 Asistente MCP

**Nuevo**
- Herramientas para **crear y listar proyectos**.
- Herramienta para **leer el código de un robot**.
- La información del robot y del cronograma incluye si el robot está activo o inactivo.

**Mejorado**
- Todos tus robots están disponibles como herramientas MCP, sin tener que habilitarlos uno por uno y aunque estén inactivos.
- Los robots creados desde MCP se ordenan en el canvas de forma prolija.
- El asistente valida el cronograma antes de guardarlo.

**Corregido**
- La consulta de ejecuciones de un robot ya no devuelve error.

---

#### 🧰 Módulos e integraciones

**Nuevo**
- **Kapso** (módulo nuevo): listar mensajes, enviar mensajes de texto y obtener un mensaje por ID.
- **Mailchimp**: enviar, programar y armar el contenido de campañas, ver el reporte de una campaña, listar audiencias, agregar etiquetas a suscriptores y dar de baja miembros.
- **Salesforce**: actualizar, borrar y hacer upsert de registros, más operaciones masivas (insertar, actualizar, borrar y upsert).
- **Odoo**: actualizar y borrar registros y ejecutar métodos.
- **Claude AI**: listar modelos y uso de herramientas (tool use).
- **iLovePDF**: dividir un PDF.
- **Google Sheets**: opción "Traer solo registros nuevos" en el disparador, que devuelve solo las filas agregadas o actualizadas.
- **Orchestrator**: obtener el log de un robot.

**Mejorado**
- **Agentes de OpenAI**: compatibilidad con modelos de razonamiento (familia o1, o3, o4-mini y gpt-5), que antes fallaban por parámetros no soportados.
- **Google Sheets**: la lista de hojas de cálculo carga más rápido y sin duplicados.
- **Google Drive**: mejor manejo de los filtros avanzados en la búsqueda de archivos.
- Formularios de credenciales actualizados en varios módulos.

**Corregido**
- **Data Store**: se valida el nombre al crear o renombrar.

---

#### 🌐 Idiomas e interfaz

**Nuevo**
- **Selector de idioma** (inglés, español y portugués). Tu elección queda guardada.
- Todo el panel (robots, credenciales, webhooks, entidades, etc.) está disponible en español y portugués. Los textos y avisos del editor de flujos también están traducidos.
- **Enlace al Changelog** en el menú lateral.

**Mejorado**
- Vistas de Usuarios y Webhooks con nuevo diseño de encabezados, tablas y barras de herramientas.
- Los textos en español usan un tono neutro.

---

#### 🔒 Seguridad

**Mejorado**
- Más protección en las notas, los títulos de los comandos y la gestión de archivos ante contenido malicioso.
