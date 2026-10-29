# Changelog de Nexus

Todos los cambios relevantes de Nexus, por versión. La versión más nueva va primero.

---

## [2.0.0] - 2026-11-02

### Novedades

#### 🧩 Componentes de pantalla

**Nuevo**

- 11 componentes nuevos para tus pantallas: Toggle, Checkbox, Radio Group, Rango (slider), Área de texto, Fecha, Divisor, Avatar, Badge, Modal y Visor de JSON.
- Los modales se diseñan directamente en el editor y se pueden mostrar u ocultar desde las acciones de la pantalla.
- Los componentes ahora tienen opciones de tipografía en el panel de propiedades.
- El Embudo de ventas (Sales Funnel) suma un selector de tema con 4 variantes: Classic, Pyramid, Dark y Minimal.
- En el Live Ticker, "Loop Duration (sec)" ahora acepta cualquier valor: un número positivo define cuánto tarda una vuelta, 0 lo detiene y un número negativo lo hace desplazarse en sentido contrario.
- Tabla de datos (Table Data): nueva opción para ocultar el paginador.
- Tabla de datos: las columnas pueden mostrar su contenido como HTML.
- Tabla de datos en modo Live: podés elegir qué columnas mostrar, en qué orden y con qué título. Si no declarás ninguna, se ven todas como antes.

**Corregido**

- Live Ticker: la velocidad ahora responde a todo el rango de valores. Antes, entre 1 y 13 segundos, la cinta se movía siempre igual.
- Tabla de datos: un JSON inválido en las columnas o en los datos ya no rompe la página. La tabla queda vacía y el editor marca el error.
- El componente Texto ya no muestra un error de sintaxis falso cuando el contenido es Markdown válido.
- El link de ejemplo del componente Texto y el valor por defecto del QR ahora apuntan a una URL válida.
- Los textos del Stat Card con tema Glass y del Gauge con tema Gradient ahora se leen correctamente.
- El componente **Iframe** vuelve a mostrar sitios externos en la aplicación publicada, el editor y la vista previa. Antes quedaba en blanco con el mensaje "Este contenido está bloqueado".

**Mejorado**

- Los campos de fecha de Date, Date Range y Filter Bar ahora usan un selector de calendario, en lugar de texto libre con formato YYYY-MM-DD.
- En el Stat Card, el color de fondo del ícono se elige con un selector de color.
- Tabla de datos: más opciones por columna, como ancho en número o porcentaje, alineación del contenido y quitar el filtro de una columna.
- Tabla de datos: según el modo (Live o Static), el campo que no aplica queda bloqueado con una explicación, y "Columns (JSON)" muestra una ayuda con el formato esperado.

#### ✏️ Editor de pantallas

**Nuevo**

- **Live preview:** un botón nuevo en el editor abre la aplicación en otra pestaña tal como se ve en producción, sin publicarla e incluyendo los cambios que todavía no guardaste. Solo vos podés verla.
- Ahora podés mover un componente a otro contenedor, o sacarlo al canvas, con el nuevo ícono de mover (✥) que aparece al pasar el mouse.
- Podés borrar el componente seleccionado con la tecla Delete, con confirmación previa si la tenés activada.
- Atajos de teclado para deshacer (Ctrl/Cmd+Z) y rehacer (Ctrl/Cmd+Y o Ctrl/Cmd+Shift+Z). Dentro de un campo de texto, deshacen solo lo escrito en ese campo.
- Desde el árbol de componentes podés volver a mostrar un componente oculto.
- Controles de tamaño de los componentes en el panel de propiedades.
- La ventana Reference suma la pestaña $api, con las API Calls de la aplicación listas para copiar.
- Botón para copiar el slug de una pantalla desde su tarjeta.

**Corregido**

- Deshacer y rehacer ahora revierten cada acción completa: un arrastre, un redimensionado o una edición en el panel de propiedades cuentan como un solo paso, y no como muchos pasos intermedios.
- Al arrastrar sobre contenedores anidados, solo se resalta el contenedor donde va a caer el componente.
- Mientras carga una pantalla, se muestra un indicador de carga en lugar de "Empty Canvas", y no se pueden soltar componentes hasta que termine.
- Los campos numéricos del panel de propiedades ya no se borran al escribir un número negativo.

**Mejorado**

- En Events & Actions, una alerta avisa cuando una acción apunta a un componente que ya no existe en la pantalla.
- Los botones de copiar de la ventana Reference muestran el tooltip "Copy".

#### 📄 Gestión de pantallas

**Nuevo**

- Clonar pantalla: desde el nuevo menú ⋮ de cada tarjeta se crea una copia con el mismo contenido, configuración y acciones.
- Descargar una pantalla como archivo JSON, desde el mismo menú.
- Las pantallas borradas pasan a la sección "Deleted screens", desde donde se pueden restaurar.
- Borrado permanente desde "Deleted screens", con confirmación previa.
- **Exportar el historial** de versiones de una pantalla a un archivo JSON, desde el panel History.

**Corregido**

- Al importar una aplicación, las pantallas conservan su configuración (fondo, ancho, padding, etc.), que antes se perdía.

**Mejorado**

- Al borrar una pantalla, su slug queda libre para usarlo en otra.
- Si no se puede borrar una pantalla, se muestra el motivo real, por ejemplo, que es la única pantalla de la aplicación.
- El **historial de versiones** muestra el email de quien hizo cada cambio y el tipo de cambio (edición, IA, restauración, borrado o importación).
- El historial conserva las **últimas 100 versiones** de cada pantalla. Al superar ese número, las más antiguas se eliminan automáticamente.

#### 🔐 Inicio de sesión y contraseñas

**Nuevo**

- "¿Olvidaste tu contraseña?" en el login: recibís un email con un link para elegir una contraseña nueva. El link vence en 1 hora y sirve una sola vez.
- Administradores y owners pueden resetear la contraseña de otro usuario, enviándole el link por email o definiéndola a mano, desde Admin → Users, Makers & Owners y Usuarios de la aplicación.
- Botón para mostrar u ocultar la contraseña en el login y el registro.

**Mejorado**

- Al cambiar la contraseña, por cualquier camino, se cierran las sesiones abiertas del usuario y se invalidan sus links de recuperación pendientes.
- Las contraseñas aceptan **cualquier carácter especial** (por ejemplo `_ # - . +`), no solo `@ $ ! % * ? &`, y los textos de ayuda lo indican.
- En el registro y en el restablecimiento de contraseña hay un botón **"← Back to login"** arriba del formulario para volver al inicio de sesión.

#### 🔌 Data Sources

**Nuevo**

- Nuevo data source AiStudio Rocketbot: conectá una aplicación a AiStudio y consultá sus tasks y resultados como tablas. Es de solo lectura.
- **Gateway On-Premises con SQL Server:** ahora te podés conectar con autenticación de Windows, sin usuario ni contraseña.
- **Descargar el Gateway On-Premises desde Nexus:** en la sección Gateway de tu aplicación, el botón de descarga abre una ventana para elegir el sistema operativo (macOS con Apple Silicon o Windows), con los pasos para ponerlo en marcha y un `config.yaml` de ejemplo ya apuntado a tu servidor de Nexus.
- **Tokens del Gateway On-Premises compartidos por entidad:** los Owners y Makers ven y administran la misma lista de tokens desde la sección Gateway de cualquier aplicación de la entidad, sin importar quién creó cada uno. El estado de conexión de cada token también lo ven todos.

**Corregido**

- Los data sources de tipo **Rocketbot Orchestrator** vuelven a mostrar su ícono en el listado.
- **Gateway On-Premises con SQL Server:** las consultas con filtros, la paginación y las altas, modificaciones y borrados ahora funcionan. También se corrigieron las consultas con filtros en PostgreSQL. Requiere instalar la versión nueva del gateway.

**Mejorado**

- El formulario de data sources marca los campos obligatorios con un asterisco. Al guardar, señala el primer campo que falta con un mensaje de error, en lugar de dejar el botón deshabilitado.
- Al elegir el token de un data source Gateway, los tokens revocados aparecen deshabilitados con la marca "(Revoked)". Un data source Gateway solo puede usar un token activo de la misma entidad que la aplicación.

#### 📊 Datos y tablas

**Nuevo**

- **Exportar tablas:** un botón nuevo en la vista de una tabla descarga sus datos en Excel (.xlsx) o CSV. Se exportan las primeras 200 filas.
- **Re-importar tablas externas:** un botón nuevo vuelve a leer la tabla desde su data source y agrega las columnas que aparecieron en el origen. Las columnas y los datos que ya tenías no cambian.

**Corregido**

- En la lista de tablas, el badge de las tablas externas ahora dice solo **"Live"** y ya no recorta el nombre de la tabla. El nombre del data source aparece al pasar el mouse.
- Las **tablas con muchas columnas** se leen y se editan bien: cada columna mantiene un ancho mínimo, aparece scroll horizontal y la columna de acciones queda fija a la derecha.

**Mejorado**

- Cada tabla muestra el ícono de su tipo de data source junto al nombre, en la lista y en el título.
- El indicador de carga de una tabla queda centrado en la pantalla, aunque la tabla sea más ancha y tenga scroll horizontal.

#### ⚙️ Configuración de la aplicación

**Nuevo**

- Pantalla de inicio por usuario: en la sección Usuarios podés elegir con qué pantalla se abre la app para cada persona. Si esa pantalla se borra, el usuario vuelve a la pantalla de inicio general.
- Al quitar o reemplazar el logo del header o una imagen del footer, el archivo se elimina del almacenamiento.

**Corregido**

- La vista de edición de una aplicación ahora carga correctamente las entidades.
- Las imágenes subidas en Header y Footer usan **https** cuando la app se sirve por https. Antes quedaban en http y el navegador las bloqueaba.

**Mejorado**

- La sección Usuarios se simplificó: se quitaron el selector de rol y la leyenda de permisos, que no estaban en uso.
- Al navegar entre las secciones de una aplicación, el menú lateral y una barra en la parte superior indican que la sección está cargando. Query Manager y Functions ya no muestran "No queries yet" o "No JS functions yet" mientras cargan.
- Los editores de **Header, Footer y Theme** se rediseñaron y avisan si cerrás o recargás la página con cambios sin guardar.
- Cada pestaña de la configuración de la app tiene su propia URL: al recargar, la pestaña se mantiene.
- Si una aplicación no se puede abrir, se muestra el motivo en lugar de un mensaje genérico.

#### 🏢 Makers & Owners

**Nuevo**

- **Los Owners administran todas las aplicaciones de su entidad**, incluidas las creadas por sus Makers: pantallas, tablas, queries, API calls, funciones, variables, API keys, data sources y actividad.
- El Dashboard muestra a qué entidad pertenece cada aplicación: en la tarjeta, junto a la fecha, y en la nueva columna "Entity" de la vista de tabla.
- Ahora podés cambiar el rol de un miembro (Owner o Maker) directamente desde la tabla de miembros en Team.
- Filtro por rol en la tabla de miembros, con un contador de resultados.

**Mejorado**

- El único Owner de una entidad no se puede quitar ni pasar a Maker.
- En entidades inactivas o vencidas no se pueden cambiar roles ni quitar miembros. Los controles deshabilitados explican por qué.
- Un aviso advierte cuando un Owner está por quitarse a sí mismo de la entidad.
- El buscador de miembros ahora filtra solo por email y se quitó la columna "Platform Role".
- El badge del plan ahora es índigo, para no confundirlo con el badge rojo "Inactive".
- El botón Team del Dashboard ahora es un ícono, con el tooltip "Manage Makers & Owners".

#### 📈 Actividad y métricas

**Nuevo**

- Nueva pantalla **Activity Logs** en el menú de usuario, para los owners de entidad. Muestra la actividad de cada entidad y, para Super Admin, la de toda la plataforma.
- **Panel de métricas:** totales, errores, duración promedio, actividad por día de los últimos 14 días, usuarios más activos y cantidad por tipo de acción (apps abiertas, logins, queries, API calls, funciones y uso del MCP).
- Filtros por estado, método y rango de fechas, **exportación a CSV** (hasta 50.000 registros) y paginación. También están en la pestaña Activity de cada aplicación.
- Cada registro describe la acción en lenguaje claro, por ejemplo quién borró qué pantalla.
- Las **modificaciones de tablas**, filas y celdas quedan registradas, ya sea que se hagan desde la app, la API externa o el asistente MCP.
- **Zona horaria por entidad:** desde Admin → Entities se elige la zona horaria de cada entidad, y la actividad por día se calcula en esa hora local.

#### 🤖 Asistente MCP

**Nuevo**

- **Permisos en las MCP Keys:** al crear una key podés elegir **Full access** o **Read only**. Una key de solo lectura puede listar y consultar, pero no crear, modificar ni borrar nada. El permiso no se puede cambiar después, y las keys que ya existían quedan como Full access.

**Mejorado**

- Los registros de actividad del MCP muestran qué key se usó y sobre qué aplicación, e incluyen las conexiones y los intentos rechazados por una key inválida, vencida o revocada.

#### 🔗 API externa

**Nuevo**

- Las queries se pueden ejecutar por **nombre**, además de por id: `POST /api/v1/external/queries/<nombre>/execute`. Sirve para integraciones que no conocen el id o que trabajan con apps importadas en otro entorno.

**Corregido**

- Las queries ejecutadas por API sobre **data sources externos o tablas virtuales** ahora devuelven datos. Antes volvían vacías, por ejemplo al consultarlas desde Saturn. También se aplican las variables de la app.
- Cada API key accede solo a las tablas, filas y queries de su aplicación.

#### 🔌 Integraciones internas

**Nuevo**

- Suite ahora puede consultar la información de un usuario de Nexus a partir de su email: sus entidades, el plan de cada una, las apps usadas y disponibles, si la entidad está activa o vencida, y las apps a las que tiene acceso.
- La consulta es solo entre servidores, con una clave interna, y no usa la sesión del usuario.
- No cambia nada para el usuario final dentro de Nexus.

### ⚠️ Antes y después de actualizar

- **Gateway On-Premises:** si te conectás a SQL Server o PostgreSQL a través del gateway, descargá la versión nueva desde la sección Gateway de tu aplicación e instalala para recibir las correcciones.
- **Gateway On-Premises:** los tokens ahora pertenecen a la entidad. Revisá la lista en la sección Gateway: si falta algún token que usabas, contactá a soporte para asignarlo a tu entidad. Los gateways ya instalados siguen funcionando sin cambios.
- **Owners de entidad:** en el Dashboard vas a ver también las aplicaciones creadas por los Makers de tu entidad, y vas a poder editarlas.
- **Header y Footer:** si una imagen que subiste antes de esta versión no se ve, volvé a subirla desde el editor.
- **Header y Footer:** al subir un logo o una imagen nueva, el cambio se ve enseguida en la app publicada. Guardá siempre antes de salir del editor.
- **Historial de versiones:** cada pantalla conserva sus últimas 100 versiones. Las más antiguas se eliminan automáticamente y no se pueden recuperar.
- **API externa:** cada API key accede solo a las tablas, filas y queries de su aplicación, y cuando algo no existe la respuesta es 404 en lugar de 400. Revisá tus integraciones.
- **Live Ticker:** la velocidad ahora respeta "Loop Duration (sec)". Si usabas un valor menor a 12 o negativo, revisá la velocidad y el sentido.
- **Fechas:** los campos de fecha de Date, Date Range y Filter Bar ahora usan un selector de calendario. Revisá las pantallas que los usan.
- **Tablas externas:** si a una tabla importada le agregaste columnas en el origen y no aparecen en Nexus, usá el botón **Re-import** de la tabla.

---

## [1.0.0] - 2026-09-07

### Novedades

#### 📦 Importar y exportar aplicaciones

**Nuevo**

- Ahora podés **exportar tus aplicaciones** para respaldarlas o moverlas a otro entorno.
- Al **importar una aplicación**, podés elegir qué traer: encabezado, pie de página y/o pantallas específicas, en lugar de importar todo de una vez.
- Si una pantalla importada tiene el mismo nombre que una existente, podés elegir **renombrarla o sobrescribirla**.
- Nuevo componente de **HTML embebido** para pantallas, con un sandbox de seguridad que evita que el contenido externo acceda a datos de tu sesión o redirija la aplicación.

**Corregido**

- El encabezado y el pie de página ya no se pierden al importar una aplicación.
- Se corrigió un error que podía dejar dos pantallas marcadas como "principal" a la vez durante una importación.
- La importación ahora es más confiable: si algo falla a mitad de camino, los cambios se revierten automáticamente para no dejar la aplicación en un estado inconsistente.

#### 🤖 Asistente MCP y administración

**Nuevo**

- Panel de administración para configurar los límites de uso (rate limits) de inicio de sesión, registro, API y del asistente MCP, sin reiniciar el servidor.
- El asistente MCP ahora puede: ver dónde se usa el slug de una pantalla, consultar su historial de versiones y restaurar una versión anterior.
- El asistente MCP puede configurar el estilo completo de una pantalla (fondo, ancho, padding, CSS personalizado) al crearla o editarla.
- Los componentes ahora aceptan clase y estilo personalizados, para diseños no cubiertos por las opciones estándar.

**Corregido**

- El contenido de los marcadores del mapa ahora se sanitiza antes de mostrarse.
- Los fondos con degradé (gradiente) ya se ven correctamente en el editor, la vista previa y la app publicada.
- Se eliminó un color de fondo rojo que aparecía por error en algunos contenedores.
- En **MCP Keys**, las claves de distintas entidades ya no se mezclan ni se pisan entre sí.

**Mejorado**

- La vista de **MCP Keys** ahora agrupa las entidades en un menú desplegable, más ordenado cuando hay varias.

#### 👥 Compartir aplicaciones

**Corregido**

- Al compartir una aplicación, ya no se le asigna automáticamente la primera entidad del dueño de la app.

#### ✏️ Editor de código (JSON / funciones)

**Nuevo**

- Los editores de JSON y funciones ahora tienen un **modo de pantalla completa**, con formateo de código y mejor autocompletado (incluye funciones, queries, variables y componentes de la pantalla).
- El panel de propiedades y los paneles de resultado (API, funciones, queries) ahora se pueden **redimensionar**, con tamaños predefinidos rápidos.

#### 📊 Vista de tabla de la aplicación

**Corregido**

- Las fechas se muestran ahora en un formato consistente (fecha y hora), en lugar de depender del idioma/configuración del navegador.

#### Hotfix: Data source de Saturn Studio

- Saturn Studio funciona como data source de almacenamiento de archivos (no admite consultas). Se corrigieron su ícono, nombre y descripción ("Saturn Studio File Storage"), y se ocultó el botón "Probar conexión", que no aplica a este tipo de data source.
