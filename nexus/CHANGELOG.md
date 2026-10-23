# Changelog

Todos los cambios relevantes de Nexus, por versión. La versión más nueva va primero.

Cada versión tiene dos partes:

- **Novedades:** qué cambia para quien usa Nexus. Es el mismo contenido que el changelog para usuarios (documento CL-NX).
- **Detalles técnicos:** tickets, PRs, cambios de base de datos, variables de entorno y endpoints, para quien desarrolla o despliega.

---

## [2.0.0] - 2026-11-02

> En QA. Si algún ítem no pasa el QA, se quita de esta versión antes del release.

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

**Corregido**

- Al importar una aplicación, las pantallas conservan su configuración (fondo, ancho, padding, etc.), que antes se perdía.

**Mejorado**

- Al borrar una pantalla, su slug queda libre para usarlo en otra.
- Si no se puede borrar una pantalla, se muestra el motivo real, por ejemplo, que es la única pantalla de la aplicación.

#### 🔐 Inicio de sesión y contraseñas

**Nuevo**

- "¿Olvidaste tu contraseña?" en el login: recibís un email con un link para elegir una contraseña nueva. El link vence en 1 hora y sirve una sola vez.
- Administradores y owners pueden resetear la contraseña de otro usuario, enviándole el link por email o definiéndola a mano, desde Admin → Users, Makers & Owners y Usuarios de la aplicación.
- Botón para mostrar u ocultar la contraseña en el login y el registro.

**Mejorado**

- Al cambiar la contraseña, por cualquier camino, se cierran las sesiones abiertas del usuario y se invalidan sus links de recuperación pendientes.
- En el registro, el texto de ayuda indica qué caracteres especiales se aceptan (@$!%*?&).
- En el registro y en el restablecimiento de contraseña hay un botón **"← Back to login"** arriba del formulario para volver al inicio de sesión.

#### 🔌 Data Sources

**Nuevo**

- Nuevo data source AiStudio Rocketbot: conectá una aplicación a AiStudio y consultá sus tasks y resultados como tablas. Es de solo lectura.
- **Gateway On-Premises con SQL Server:** ahora te podés conectar con autenticación de Windows, sin usuario ni contraseña.

**Corregido**

- Los data sources de tipo **Rocketbot Orchestrator** vuelven a mostrar su ícono en el listado.
- **Gateway On-Premises con SQL Server:** las consultas con filtros, la paginación y las altas, modificaciones y borrados ahora funcionan. También se corrigieron las consultas con filtros en PostgreSQL. Requiere instalar la versión nueva del gateway.

**Mejorado**

- El formulario de data sources marca los campos obligatorios con un asterisco. Al guardar, señala el primer campo que falta con un mensaje de error, en lugar de dejar el botón deshabilitado.

#### 📊 Datos y tablas

**Corregido**

- En la lista de tablas, el badge de las tablas externas ahora dice solo **"Live"** y ya no recorta el nombre de la tabla. El nombre del data source aparece al pasar el mouse.
- Las **tablas con muchas columnas** se leen y se editan bien: cada columna mantiene un ancho mínimo, aparece scroll horizontal y la columna de acciones queda fija a la derecha.

#### ⚙️ Configuración de la aplicación

**Nuevo**

- Pantalla de inicio por usuario: en la sección Usuarios podés elegir con qué pantalla se abre la app para cada persona. Si esa pantalla se borra, el usuario vuelve a la pantalla de inicio general.

**Corregido**

- La vista de edición de una aplicación ahora carga correctamente las entidades.

**Mejorado**

- La sección Usuarios se simplificó: se quitaron el selector de rol y la leyenda de permisos, que no estaban en uso.
- Al navegar entre las secciones de una aplicación, el menú lateral y una barra en la parte superior indican que la sección está cargando. Query Manager y Functions ya no muestran "No queries yet" o "No JS functions yet" mientras cargan.

#### 🏢 Makers & Owners

**Nuevo**

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
- **Seguridad:** una API key solo puede acceder a las tablas, filas y queries de su propia aplicación.

#### 🔌 Integraciones internas

**Nuevo**

- Suite ahora puede consultar la información de un usuario de Nexus a partir de su email: sus entidades, el plan de cada una, las apps usadas y disponibles, si la entidad está activa o vencida, y las apps a las que tiene acceso.
- La consulta es solo entre servidores: se autentica con una clave interna (`SUITE_INTERNAL_API_KEY`) y no usa la sesión del usuario. Si la clave no está configurada en el entorno, la integración queda deshabilitada.
- No cambia nada para el usuario final dentro de Nexus.

### Detalles técnicos

#### Tickets de Jira (proyecto NEX)

| Ticket | Tema |
| --- | --- |
| NEX-4 | Botón para ver la contraseña en login y registro |
| NEX-40 | Mejora de componentes de screen |
| NEX-43 | Mejoras en la administración de usuarios |
| NEX-58 | Editor de screens: botones Undo/Redo |
| NEX-59 | Canvas: eliminar componente con la tecla Delete |
| NEX-61 | Live Ticker: propiedad "Loop Duration (sec)" |
| NEX-62 | Texto: detector de idioma y error falso en el editor JSON |
| NEX-64 | Edición de app: endpoint de entidades |
| NEX-75 | Date Range: validación y selector de "Min Date" / "Max Date" |
| NEX-78 | API externa: ejecutar queries por nombre además de por id |
| NEX-88 | Soft delete y hard delete de screens |
| NEX-90 | Métricas de logs |
| NEX-97 | Restaurar contraseña |
| NEX-98 | Clonar screen |
| NEX-101 | Opciones avanzadas de Table Data |
| NEX-103 | Gateway: SQL Server (T-SQL y Trusted Connection) y parámetros de PostgreSQL |
| NEX-104 | Pantalla de inicio por usuario |
| NEX-105 | Mover elementos entre contenedores y el canvas |
| NEX-116 | Fixes menores de screen |
| NEX-121 | Ícono del data source Rocketbot Orchestrator |
| NEX-124 | Queries por API externa vacías sobre data sources externos (Saturn) |
| NEX-128 | Indicador de carga al navegar las secciones de una app |
| NEX-131 | Botón "Back to login" en Register y Reset password |
| NEX-132 | Se quita el helper de tipo de usuario en Invite |
| NEX-133 | Badge "Live" que recortaba el nombre de la tabla |
| NEX-134 | Tablas con muchas columnas: celdas y campos de edición legibles |
| NEX-135 | Live preview de apps en una pestaña aparte |
| NEX-136 | Iframe bloqueado por la CSP `frame-src 'none'` |
| NEX-141 | Zona horaria por entidad |
| NEX-144 | MCP: permisos por key y mejoras de logs |

#### Pull requests (Bitbucket)

| Rama | PRs |
| --- | --- |
| `container-component-fixes` | #60, #65, #88 |
| `fix/entity-plans` | #61, #62, #63, #79 y merge directo a `dev` |
| `feature/screen-delete` | #64, #73, #93 |
| `feature/see-password-button/NEX-4` | #67 |
| `feature/delete-button-component/NEX-59` | #68 |
| `fix/live-ticker-time-settings/NEX-61` | #69 |
| `fix/text-component-markdown/NEX-62` | #70 |
| `fix/entities-api-call-in-app/NEX-64` | #71 |
| `fix/date-range-inputs/NEX-75` | #72, #89 |
| `fix/undo-redo-buttons` | #74 |
| `feature/clone-screen` | #75, #92 |
| `screen-small-fixes` | #76, #87 |
| `feature/reset-pasword` | #77, #94 |
| `fix/move-elements-between-containers` | #78, #90 |
| `feature/table` | #80, #91 |
| `feature/share-by-selected-home` | #81 |
| `feature/AiStudio` | #83 |
| `fix/login-show-password/NEX-4` | #86 |
| `fix/entity-expired` | #96 |
| `new/suite-api` | #97 |
| `feature/go-back-login` | #99 |
| `fix/remove-user-helper` | #100 |
| `fix/app-section-loading` | #101 |
| `fix/orch-icon` | #102 |
| `fix/live-badge-table-name` | #103 |
| `fix/table-edit-inputs-length` | #104 |
| `feature/preview-mode` | #105 |
| `feature/iframe-element` | #106 |
| `feature/logs-humans` | #107 |
| `fix/gateway-mssql` | PR pendiente |
| `fix/query-api` | PR pendiente (reemplaza a `fix/queryapi`, que se descartó) |

#### Base de datos

El proyecto no usa archivos de migración: los cambios de `backend/prisma/schema.prisma` se aplican con `prisma db push`. Todos los cambios de esta versión agregan columnas, índices o relaciones, con default o nullable. No borran datos.

| Modelo (tabla) | Cambio |
| --- | --- |
| `Plan` (`plans`) | `maxMakers` (`max_makers`), `Int`, default `5` |
| `AppUser` (`app_users`) | `homeScreenId` (`home_screen_id`), nullable, relación con `Screen` con `onDelete: SetNull`, e índice |
| `Screen` | Relación inversa `homeForAppUsers` |
| `Entity` (`entities`) | `timezone`, `VARCHAR(64)`, default `UTC` |
| `McpKey` (`mcp_keys`) | `permission`, `VARCHAR(20)`, default `FULL_ACCESS` (valores: `FULL_ACCESS`, `READ_ONLY`) |
| `ActivityLog` (`activity_logs`) | `entity_name`, `app_id`, `mcp_key_id`, `mcp_key_name` (todas nullable) e índice por `app_id` |

#### Variables de entorno (`backend`)

| Variable | Cambio |
| --- | --- |
| `SUITE_INTERNAL_API_KEY` | **Nueva, opcional.** Clave de al menos 32 caracteres para la integración con Suite (`POST /api/v1/internal/suite/user-info`). Si está vacía, la integración queda deshabilitada. Se genera con `openssl rand -hex 32`. |
| `IFRAME_ALLOWED_ORIGINS` | **Cambia su efecto.** Ahora también define la `frame-src` del HTML en `/app/*`, `/preview/*` y el editor. Si está vacía, se permite cualquier origen `https:`. Si tiene valores, solo esos orígenes (más `'self'`). |

#### Endpoints nuevos (`/api/v1`)

| Método y ruta | Para qué |
| --- | --- |
| `POST /auth/forgot-password` | Pedir el email de recuperación de contraseña |
| `POST /auth/reset-password` | Definir una contraseña nueva con el token del email |
| `POST /admin/users/:id/reset-password` | Reset de contraseña de un usuario (admin) |
| `POST /applications/:appId/users/:appUserId/reset-password` | Reset de contraseña de un usuario de la app |
| `POST /entities/:entityId/members/:userId/reset-password` | Reset de contraseña de un miembro de la entidad |
| `GET /entities/:entityId/members` y `POST`, `PATCH`, `DELETE` sobre `/entities/:entityId/members[/:userId]` | Gestión de Makers & Owners |
| `GET /entities/users/search` | Búsqueda de usuarios para agregar a la entidad |
| `GET /screens/:id/references` | Dónde se usa el slug de una pantalla |
| `DELETE /screens/:id/permanent` | Borrado permanente de una pantalla |
| `POST /datasources/aistudio-rocketbot/entities` | Entidades disponibles del data source AiStudio |
| `GET /admin/activity-logs/metrics` y `/export` | Métricas y export CSV de toda la plataforma |
| `GET /entities/:entityId/activity-logs`, `/metrics` y `/export` | Logs, métricas y export por entidad |
| `GET /applications/:appId/activity-logs/metrics` y `/export` | Métricas y export por app |
| `POST /internal/suite/user-info` | Integración con Suite (autenticada con `SUITE_INTERNAL_API_KEY`) |

#### Otros cambios técnicos

- **CSP:** en `/app/*`, `/preview/*` y el editor, el HTML sale con `frame-src 'self' https:` (o con `IFRAME_ALLOWED_ORIGINS`). El resto de la plataforma mantiene `frame-src 'none'`. `/preview/*` se agregó a las rutas con `'unsafe-inline'` en `script-src`, igual que `/app/*`.
- **Sandbox del Iframe:** el atributo `sandbox` siempre incluye `allow-scripts` y se normaliza a minúsculas, en backend (`iframeSandboxPolicy.ts`) y en `RIframe.vue`.
- **MCP:** con una key `READ_ONLY`, `createMcpServer` solo registra las herramientas de lectura de `READ_ONLY_TOOLS` y ningún prompt. `execute_query` solo acepta queries de tipo `READ`. Cada llamada a herramienta, resource o prompt, cada `initialize` y cada rechazo de autenticación (401) se registran en `activity_logs`.
- **Live preview:** las rutas `/preview/:id` y `/preview/:id/:screen` usan `RuntimeView` con `meta.preview`. Los cambios sin guardar viajan por `localStorage` (`nexus-preview-draft:<screenId>`, vencen a la hora). La preview no registra "app abierta" en los logs.
- **Navegación:** `useRouteLoading` expone `isNavigating` y `pendingPath` para la barra de progreso global y los spinners del menú lateral. El indicador aparece después de 150 ms.
- **Gateway (`query_builder.py`):** dialecto T-SQL para `mssql`: parámetros `?` (pyodbc), identificadores entre `[ ]`, `TOP n` cuando hay límite sin offset, `OFFSET n ROWS FETCH NEXT m ROWS ONLY` para paginar (con `ORDER BY (SELECT NULL)` si no hay orden) y `OUTPUT INSERTED.*` / `OUTPUT DELETED.*` en lugar de `RETURNING`. `postgres` pasa de `$N` a `%s` (psycopg2). MySQL no cambia.
- **Gateway (`mssql_adapter.py`, `config.py`):** si `database.user` está vacío se usa `Trusted_Connection=yes`, y `user` deja de ser obligatorio para `mssql`. Los cursores se cierran en un `finally`.
- **API externa (`external-api.routes.ts`):** `POST /external/queries/:queryId/execute` acepta id o nombre exacto (si el nombre está repetido en la app responde 400). Las tablas, filas y queries se validan contra la app de la API key: si no existen o son de otra app responden 404 (`GET /tables/:tableId` responde 403). `PUT` y `DELETE /rows/:rowId` aceptan `?tableId=` para filas de tablas virtuales. `DataEngineService` recibe `dataSourceRepository`, `adapterFactory` y `appVariableRepository`, que faltaban en esta ruta.
- **Compatibilidad de la API externa:** las llamadas a recursos de otra app, que antes funcionaban, ahora fallan, y los "no encontrado" pasan de 400 a 404.

#### Notas de despliegue

1. Ejecutar `prisma db push` antes de levantar el backend. Sin las columnas nuevas, fallan las lecturas de `activity_logs`, `entities` y `mcp_keys`.
2. Opcional: configurar `SUITE_INTERNAL_API_KEY` para habilitar la integración con Suite.
3. Opcional: configurar `IFRAME_ALLOWED_ORIGINS` si se quiere limitar qué sitios se pueden embeber con el componente Iframe.
4. Gateway On-Premises: generar y distribuir el ejecutable nuevo. Los clientes con SQL Server o PostgreSQL tienen que actualizar el gateway instalado para recibir el fix. En SQL Server, las tablas con triggers habilitados pueden fallar en update y delete por el uso de `OUTPUT` sin `INTO` (ver QA de NEX-103).

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

- Vulnerabilidad de seguridad (XSS) en el mapa: el contenido de los marcadores ahora se sanitiza antes de mostrarse.
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

#### Hotfix: Datasources de Saturn

Se corrige la integración de Saturn Studio como datasource: se agrega el adaptador `SaturnStudioAdapter` (usado únicamente para almacenamiento de archivos, sin soporte de consultas), se lo registra en `DataSourceAdapterFactory` con validación de `apiKey`, y se ajustan el ícono, la etiqueta y la descripción a "Saturn Studio File Storage" en el formulario y listado de datasources. Se oculta el botón "Probar conexión" para este tipo de datasource, ya que no aplica al no exponer tablas consultables.

### Detalles técnicos

#### Importación y exportación de aplicaciones (PR #19, #21)

PR #21 (`feat/fix-screen-import-handling`) termina lo que PR #19 (`fix/not-importing-footer-header`) dejó incompleto.

- `ExportApplicationModal` e `ImportApplicationModal`, con selección granular de header, footer y pantallas.
- Estrategia de conflictos por pantalla o recurso (`rename` u `overwrite`), vía `ImportApplicationDTO`.
- Validación de slugs duplicados (`ScreenSlugAlreadyExistsError`).
- Control de concurrencia (`ScreenHomeConflictError`) para que no queden dos pantallas marcadas como home.
- `IImportTransactionManager`: la importación corre en una transacción atómica, con rollback si falla un paso. Los repositorios Prisma (Screen, Table, Query, Row, DataSource, etc.) se adaptaron para operar dentro de esa transacción.

#### MCP: settings de pantalla, estilos universales y keys por entidad (rama `MCP_fix`)

- `create_screen` y `update_screen` aceptan `settings` (`size`, `padding`, `backgroundColor`, `showGridOverlay`, `confirmDeleteComponent`, `customCSS`), persistido en `Screen.settings`.
- Props universales `customClass` y `customStyle` para todo tipo de componente, documentados en `getUniversalComponentProps()` y expuestos en `list_component_types`, `get_component_schema` y `getComponentCatalogJson`.
- `create_function` / `update_function`: `parameters` pasa a un schema tipado (`functionParameterSchema`: `name`, `description?`).
- Tests nuevos en `backend/tests/unit/mcpToolSchemas.test.ts`.
- Fix: `backgroundColor` se aplicaba con `background-color` en vez de `background`, y los gradientes no se renderizaban (`EditorCanvas.vue`, `PreviewMode.vue`, `RuntimeView.vue`).
- Fix: se quitó una clase `bg-red` que había quedado en `RContainer.vue`.
- Fix: el store `frontend/src/stores/mcpKey.ts` pasó de un estado global a uno indexado por `entityId` (`mcpKeysByEntity`, `loadingByEntity`, `errorByEntity`). `revokeMcpKey` y `deleteMcpKey` reciben `entityId`.
- `McpKeysView.vue` lista las entidades en un acordeón y cada una carga sus keys al expandirse.

#### Gateway: BLOBs y límite de mensajes de Socket.IO (PR #27, `fix/gateway`)

- `blobSerializer.ts` (`backend/src/infrastructure/database/adapters/`): convierte valores `Buffer`/BLOB en data URIs base64 (`serializeRow` / `serializeRows`), detectando el MIME por la firma de bytes (PNG, JPEG, GIF, BMP, WEBP, SVG, PDF).
- Los BLOB de más de `MAX_BLOB_BYTES` (15 MB por defecto) se omiten (`[binary omitted size=...]`).
- Variable nueva `SOCKET_MAX_HTTP_BUFFER_SIZE` (default `20000000` bytes) para el `maxHttpBufferSize` de Socket.IO. El default de 1 MB no alcanzaba para resultados con BLOBs.
- Gateway (Python): opción `database.max_blob_bytes` (default 15 MB) y variable `RBNX_DATABASE_MAX_BLOB_BYTES`.
- Dependencias nuevas del gateway: `aiohttp>=3.8.0`, `async-timeout>=4.0.0` (Python < 3.11) y `typing-extensions>=4.0.0`.

#### Hotfixes posteriores (en `main`)

- `fix/saturn` (PR #66): adaptador de Saturn Studio, descripto arriba.
- `hotfix/openai-sdk-configurations` (PR #84, #85): `AI_MAX_TOKENS` y `AI_MAX_COMPLETION_TOKENS` pasan a ser opcionales en `env.ts`, para configurar el SDK de OpenAI con más flexibilidad.
