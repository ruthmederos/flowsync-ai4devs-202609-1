# Alcance del MVP de FlowSync

> **Hipótesis principal:** un equipo remoto pequeño puede saber en qué está trabajando cada persona sin hacer la ronda de "¿en qué estás?" de la daily.
>
> Hipótesis de apoyo:
> - **H2, frescura (riesgo nº 1):** la gente mantiene el estado al día porque actualizarlo cuesta dos clics sobre la lista que ya usa como cola de trabajo.
> - **H3, solapamiento:** viendo quién tiene cada tarea y qué está libre, nadie empieza algo que otra persona ya está tocando.

## Terreno existente

Hoy FlowSync es una base técnica sin funcionalidad de producto. Lo que ya funciona es la cuenta de usuario: registro, inicio de sesión, perfil y cierre de sesión, con las pantallas protegidas según haya sesión o no. El usuario es la única entidad del producto; no hay tareas, estados, responsables ni equipos. Tampoco hay actualización en vivo ni tests. El acceso con cuenta es **contexto existente** y no forma parte de lo que hay que construir.

## Problema

En un equipo remoto pequeño, saber en qué está cada persona exige interrumpir a alguien: por Slack o chat, o en la ronda de estado de la daily, que ocupa la mitad de sus 15 minutos. Cuando nadie pregunta, el trabajo se duplica: dos personas tocaron el mismo módulo la misma semana porque una empezó sin que la otra lo supiera, y se perdieron dos días. El gestor de tareas actual no lo resuelve porque es pesado de actualizar y nadie lo mira para decidir qué coger.

La parte de bloqueos de la daily sigue existiendo y este MVP no la resuelve.

## Usuarios

- **Quiénes:** equipos remotos pequeños (3 a 10 personas), en varios husos horarios y con roles planos. Todos ven y editan lo mismo.
- **Primer usuario (caso de estudio, no un cliente real):** un equipo de producto SaaS de 6 personas en 3 husos horarios, que hoy usa un gestor de tareas pesado y una daily de 15 minutos por videollamada.
- **Quién sale ganando:** los propios compañeros, no un responsable. Por un lado, quien estaba a punto de duplicar trabajo o de interrumpir a alguien para preguntar. Por otro, quien actualiza su tarea, porque deja de recibir preguntas y usa la lista como su cola de trabajo.
- **Para quién no es:** managers que buscan informes, y equipos que necesitan sprints, estimaciones o backlog priorizado.

## Propuesta de valor

Una única lista compartida de tareas donde cada persona ve, sin preguntar y sin recargar, quién está con qué, qué está libre y qué se ha pasado de plazo. Actualizarla cuesta dos clics, y quien lo hace lo hace por interés propio porque es su cola de trabajo. FlowSync es donde se hace el trabajo, no donde se cuenta: sustituye al gestor de tareas, no convive con él.

**Criterio de éxito:** tras una semana de uso real, el equipo cancela la ronda de "¿en qué estás?" y nadie pide recuperarla. Si la siguen haciendo igual, no ha funcionado.

## Alcance

Es una sola funcionalidad fina, usable de principio a fin:

1. **Crear una tarea en segundos.** Solo el título es obligatorio. El responsable y la fecha de vencimiento son opcionales.
2. **Cambiar el estado** entre tres estados fijos: *pendiente*, *en curso* y *hecha*.
3. **Asignar o reasignar el responsable**, incluido asignarse una tarea libre.
4. **Fecha de vencimiento con la marca de tarea vencida**, para ver de un vistazo qué requiere atención.
5. **Editar el título y la fecha** de una tarea ya creada. Sin esto, un título equivocado o un plazo que se mueve dejan información falsa o vieja en la lista, que es justo el riesgo nº 1.
6. **Lista única compartida**, con el título, el responsable (o que está libre), el estado, la fecha y la marca de vencida de cada tarea.
7. **Filtrar la lista por estado**, para centrarse en lo pendiente.
8. **Ver los cambios de los demás sin recargar la página.** Lo que se ve es el estado actual de la lista.

## NO-alcance

| Queda fuera | Por qué no ayuda a validar la hipótesis |
|---|---|
| Borrar o archivar tareas | No ayuda a saber quién está en qué. Una tarea *hecha* deja de molestar gracias al filtro por estado, y un error se corrige editando la tarea, no duplicándola. |
| Filtrar por responsable o vista "mis tareas" | La hipótesis necesita ver a todo el equipo, no a una persona. El filtro por estado ya sirve para centrarse en lo pendiente. |
| Historial o "novedades desde tu última visita" | Para validar la hipótesis basta el estado actual. El historial cuenta lo que pasó, no quién está en qué ahora. |
| Presencia, "quién está conectado" o indicadores de actividad | El estado es de la tarea, no de la persona. Además es vigilancia, y se rechaza a propósito. |
| Notificaciones push o avisos | La señal es un resumen que espera, no un aviso que interrumpe. Interrumpir es justo el problema que se quiere eliminar. |
| Integración con Slack | Añade otro sitio donde leer y escribir, en contra de H2 (un único sitio donde se trabaja). |
| Estado derivado de Git, PRs, CI o calendario | Pone a prueba otra hipótesis (que el estado se pueda deducir solo), no la actualización manual. Es otro producto, con conexiones a terceros. |
| Importar tareas o convivir con el gestor actual | Actualizar en dos sitios rompe H2: así es como muere esta categoría de producto. |
| Varios equipos o espacios, personas en más de uno, invitaciones | El caso de estudio es un solo equipo, y la hipótesis se valida con un único espacio. |
| Roles y permisos | Con roles planos todos editan lo mismo. Los permisos no cambian si se hace o no la ronda de estado. |
| Estados configurables o flujos de trabajo | Van contra "menos rollo que Jira" y suben el coste de actualizar (H2). |
| Varios responsables por tarea | "¿De quién es esto?" tiene que tener una respuesta clara (H3). Varios responsables la vuelven ambigua. |
| Descripción u otros campos adicionales | Cada campo más hace más lenta la creación (H2) y no ayuda a saber quién está en qué. |
| Comentarios en las tareas | Son conversación, no estado. Abren la puerta a convertir la herramienta en un chat. |
| Chat, videollamada o edición simultánea | Aquí "tiempo real" significa que el estado esté al día, no colaborar en directo. |
| Sprints, estimaciones, épicas y backlog priorizado | Son planificación, no visibilidad. Un equipo que los necesita no es nuestro usuario. |
| Informes y analítica | Nadie los consume: no hay informes hacia arriba y el valor es para los compañeros. |
| Medir el uso dentro del producto | El criterio de éxito se observa en el equipo: si cancela la ronda de estado. No hace falta instrumentar nada. |
| Gestión de bloqueos | Es la parte de la daily que sigue existiendo, y queda explícitamente fuera. |

## Supuestos

1. **Un único espacio compartido, sin la entidad "equipo".** No se contemplan varios equipos ni personas en más de uno.
2. **Cómo se entra al espacio:** cualquier usuario registrado accede al único espacio, sin invitaciones ni aprobaciones.
3. **Estados:** hay tres fijos (*pendiente*, *en curso*, *hecha*) y no se pueden configurar.
4. **Campos obligatorios:** solo el título. Una tarea sin responsable es una tarea libre.
5. **Responsables:** una tarea tiene uno como máximo.
6. **Quién puede editar:** con roles planos, cualquiera puede cambiar cualquier tarea (estado, responsable, título y fecha).
7. **Qué es "ver qué se ha movido":** es el estado actual de la lista, actualizado sin recargar. No incluye historial ni marcas de novedad.
8. **Riesgo residual que hay que observar en la semana de prueba:** una tarea creada por error y que no corresponde a nada no se puede borrar. Solo puede reutilizarse editándola o marcarse como hecha.
9. **Riesgo nº 1:** que la información se quede vieja. La mitigación es que actualizar cueste dos clics, no obligar a nadie a hacerlo.

## Decisión de recorte

**Cómo se cuenta:** cada capacidad es una acción o una vista que el usuario distingue por sí misma, y se ha contado igual en la propuesta inicial y en la final. La fecha de vencimiento con su marca de vencida cuenta como una capacidad propia en los dos recuentos.

- **Capacidades que la IA propuso inicialmente para el MVP: 8.**
  1. Acceso con cuenta.
  2. Crear una tarea.
  3. Cambiar el estado.
  4. Asignar o reasignar el responsable.
  5. Fecha de vencimiento con la marca de vencida.
  6. Lista compartida.
  7. Filtrar por estado.
  8. Ver los cambios sin recargar.
- **Capacidades que quedan en el alcance a construir tras la revisión: 8.** Sale el acceso con cuenta, porque ya existe y pasa a ser contexto. Entra editar título y fecha.
- **La exclusión que más me costó:** borrar o archivar tareas.
- **Por qué la mantengo fuera:** no hace falta para validar si una lista compartida y al día elimina la ronda de estado. Acepto ese riesgo durante la semana de prueba.
- **Qué me haría meterla en el MVP:** que las tareas creadas por error metan tanto ruido que el equipo deje de confiar en la lista.
