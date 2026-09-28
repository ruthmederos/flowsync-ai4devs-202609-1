# Prompts

## Prompt 1

**Modelo:** Opus 5.5 (claude-opus-5-5)
**Herramienta:** Claude Code

```
Antes de empezar con el proyecto, analiza el estado actual del repositorio.

Quiero entender el contexto que ya existe:
- Identifica las capabilities que ya están construidas y funcionando.
- Describe brevemente el modelo de datos actual y las entidades que ya existen.
- Distingue claramente lo que ya está implementado de cualquier cosa que solo esté preparada o mencionada.

Devuélveme un resumen breve que pueda utilizar como contexto para definir posteriormente el alcance del MVP.

No propongas todavía nuevas funcionalidades ni el alcance del MVP. No bajes a endpoints ni diseñes cambios técnicos. No modifiques ningún archivo.
```

## Prompt 2

**Modelo:** Opus 5.5 (claude-opus-5-5)
**Herramienta:** Claude Code

```
Antes de definir el alcance del MVP necesito que me ayudes a concretar el producto.

Hazme exactamente 5 preguntas, en una sola ronda, que consideres necesarias para aclarar el problema que queremos resolver, los usuarios a los que va dirigido y el alcance del MVP.

Pregunta antes de proponer soluciones. No entres todavía en endpoints, modelo de datos ni decisiones técnicas.
```

## Prompt 3

**Modelo:** Opus 5.5 (claude-opus-5-5)
**Herramienta:** Claude Code

```
Estas son las respuestas y hechos ya decididos del producto. Utilízalos para responder a las cinco preguntas anteriores. No inventes información adicional. Si alguna de tus preguntas no queda cubierta por estos hechos, toma una decisión razonable y márcala explícitamente como supuesto.

Al terminar, indícame claramente qué supuestos has tenido que hacer.

- Qué duele hoy: la daily de sincronización y el "¿en qué estás?" constante por Slack/chat. Nadie ve el estado del equipo sin interrumpir a alguien.
- Quién cobra el valor: los pares, no un lead. No hay reporte hacia arriba y a un manager le daría igual. Duele a los dos devs que descubren tarde que iban a lo mismo, y al que interrumpe a otro para preguntar.
- Episodio concreto: dos personas del equipo tocaron el mismo módulo la misma semana porque una empezó sin que la otra lo supiera. Dos días perdidos.
- Qué reunión desaparece (respuesta honesta, no la vendas de más): la daily NO desaparece entera. Desaparece la ronda de "¿en qué estás?", que hoy se come la mitad de los 15 minutos. La parte de bloqueos sigue, y este MVP no la resuelve.
- Usuarios / equipo: equipos remotos pequeños, 3–10 personas. Roles planos: en el MVP todos ven y editan lo mismo, sin jerarquía de permisos.
- Primer usuario concreto: equipo de 6 personas de producto SaaS, en 3 husos horarios, que hoy usa un gestor de tareas pesado y una daily de 15 minutos por videollamada. Es un CASO DE ESTUDIO, no un cliente real.
- Fronteras: un espacio único compartido, sin entidad "equipo". Varios equipos separados, o gente en más de uno, queda FUERA del MVP: se anota como supuesto en el PRD, no se construye.
- "Tiempo real" = ver los cambios de estado de las tareas sin refrescar ni preguntar. NO es chat, NO es videollamada, NO es colaboración simultánea sobre el mismo documento.
- Es frescura, no presencia: el estado es de la TAREA, no de la persona. Nada de "quién está conectado ahora" ni indicadores de actividad; eso es vigilancia y lo rechazamos a propósito.
- Forma de la señal: resumen que espera, no aviso que interrumpe. El caso es "llego por la mañana o vuelvo de una reunión y veo qué se ha movido". Sin notificaciones push.
- Qué decisión cambia: no empezar algo que otra persona ya está tocando, y elegir lo siguiente sabiendo qué está libre. Si la única respuesta fuera "sentirse informado", el tiempo real no valdría lo que cuesta.
- De dónde sale el estado: lo teclea la persona que hace la tarea, en segundos. Derivarlo de señales externas (Git/PRs, CI, calendario) está FUERA del MVP: es otro producto, con integraciones y OAuth de terceros.
- Por qué se sostiene: no porque sea más agradable, sino porque son dos clics sobre una lista ya abierta, sin campos obligatorios, sin decidir sprint ni estimación. Y quien lo escribe cobra en el momento: esa misma lista es su cola de trabajo, la mira para decidir qué coge, y de paso deja de recibir interrupciones preguntándole cómo va. Si el beneficio fuera solo para los demás, no lo escribiría.
- Si la información se queda vieja: el producto pierde el sentido, y lo asumo. Es el riesgo #1 a validar, no un detalle. La mitigación es que actualizar cueste dos clics, no obligar a nadie.
- Es donde se hace el trabajo, no donde se cuenta: sustituye al gestor de tareas, no convive con él. FlowSync crea las tareas, no lee las de otro sitio. Convivir exigiría doble actualización, que es como muere esta categoría.
- Renuncia explícita a sprints, estimaciones, épicas, backlog priorizado e informes. Un equipo que necesite eso no es nuestro usuario.
- "Menos rollo que Jira" = crear una tarea y cambiarle el estado en segundos, sin flujos de configuración ni campos obligatorios. Lo mínimo para saber quién está en qué.
- Qué necesita una tarea en el MVP: título, responsable, estado y fecha de vencimiento. La fecha, para ver de un vistazo qué se ha pasado de plazo.
- Cómo se consume la lista: filtrando por estado, para centrarse en lo pendiente.
- Éxito para el usuario: dejar de hacer la ronda de "¿en qué estás?" de la daily porque el estado del equipo se ve de un vistazo.
- Criterio a una semana de uso real: que el equipo cancele esa ronda y nadie pida que vuelva. Si la siguen haciendo igual, no funcionó.
- Cuánto construir: una vertical fina y usable de punta a punta, no el andamiaje amplio de un producto. Prefiero una capability terminada a tres a medias.
- Fuera del MVP: notificaciones push, integración con Slack, roles/permisos avanzados, analítica/reporting, comentarios en tareas.
```

## Prompt 4

**Modelo:** Opus 5.5 (claude-opus-5-5)
**Herramienta:** Claude Code

```
Con el contexto del repositorio, mis respuestas anteriores y los supuestos que has identificado, propón ahora el alcance del MVP.

Organízalo únicamente en estos cinco bloques:
1. Problema
2. Usuarios
3. Propuesta de valor
4. Alcance
5. NO-alcance

Quiero que seas concreto y que recortes lo no necesario. Incluye únicamente aquello que sea necesario para validar la hipótesis principal del producto: que un equipo remoto pequeño pueda saber en qué está trabajando cada persona sin tener que hacer la ronda de "¿en qué estás?" de la daily.

Para cada elemento del NO-alcance, justifica por qué queda fuera indicando qué hipótesis del producto no ayuda a validar.

No incluyas modelo de datos, endpoints, arquitectura, diagramas ni detalles de implementación.

Al final, indica:
- cuántas funcionalidades/capacidades consideraste candidatas a entrar en el MVP;
- cuáles propones finalmente mantener dentro;
- cuáles propones excluir.

No modifiques todavía ningún archivo.
```

## Prompt 5

**Modelo:** Opus 5.5 (claude-opus-5-5)
**Herramienta:** Claude Code

```
He revisado tu propuesta y quiero hacer los siguientes cambios:

- El acceso con cuenta no debe contarse dentro del alcance a construir del MVP, porque es un desarrollo  que ya existe en el proyecto. Debe mantenerse únicamente como parte del contexto existente.
- Mantengo la fecha de vencimiento y la marca de tarea vencida. Considero que aporta información útil para decidir qué trabajo requiere atención y además forma parte de los datos definidos para una tarea.
- Mantengo crear tareas, cambiar su estado, asignar o reasignar responsable, la lista compartida, el filtro por estado y ver los cambios sin refrescar.

Quiero cuestionar tu decisión de excluir la edición del título y la fecha. Tu propuesta indica que, ante un error, se cree otra tarea, pero al mismo tiempo propones que no se puedan borrar ni archivar tareas. Esto podría generar tareas erróneas y ruido en una lista que pretende ser sencilla.

Analiza esta posible incoherencia y discute si permitir editar título y fecha debería formar parte de la vertical mínima usable o seguir fuera del MVP.

No añadas mecanismos de trazabilidad, relaciones entre tareas, flags de error ni otras funcionalidades nuevas para resolverlo: evalúa únicamente si editar título y fecha es necesario para este MVP.

No modifiques todavía ningún archivo.
```

## Prompt 6

**Modelo:** Opus 5.5 (claude-opus-5-5)
**Herramienta:** Claude Code

```
Cierra ahora el ejercicio con las decisiones que hemos tomado.

Crea únicamente los dos archivos requeridos para la entrega:

1. docs/prd/alcance-mvp-RM.md
2. prompts.md

En docs/prd/alcance-mvp-RM.md incluye:
- Un resumen de 3-5 líneas del terreno existente.
- Problema.
- Usuarios.
- Propuesta de valor.
- Alcance definitivo del MVP.
- NO-alcance, justificando las exclusiones respecto a la hipótesis principal.
- Los supuestos relevantes que deban quedar explícitos.

Respeta nuestras decisiones finales:
- El acceso con cuenta es contexto existente y no forma parte del alcance a construir.
- La fecha de vencimiento y la marca de vencida permanecen.
- La edición de título y fecha permanece.
- Crear tareas, cambiar estado, asignar/reasignar responsable, lista compartida, filtro por estado y cambios visibles sin refrescar permanecen.
- No añadas trazabilidad entre tareas, flags ni funcionalidades adicionales.

Mantén el documento breve y centrado en producto. No incluyas endpoints, modelo de datos, arquitectura ni detalles de implementación.

En prompts.md guarda, en orden, todos los prompts que te he enviado durante este ejercicio desde el análisis inicial del repositorio hasta este prompt, literalmente y sin mejorarlos ni reescribirlos.

No hagas commit ni crees todavía el PR.
```

## Prompt 7

**Modelo:** Opus 5.5 (claude-opus-5-5)
**Herramienta:** Claude Code

```
Antes de cerrar la entrega haz dos correcciones finales:

1. Limpia prompts.md eliminando cualquier texto residual de la plantilla o del ejemplo. Deben quedar únicamente la cabecera necesaria y mis seis prompts reales, sin modificar el contenido de esos prompts.

2. Añade al final de docs/prd/alcance-mvp-RM.md una sección "Decisión de recorte" con:
- Número de capacidades que propuso inicialmente la IA para entrar en el MVP.
- Número de capacidades que quedaron finalmente en el alcance a construir después de mi revisión.
- La exclusión que más me costó fue: borrar o archivar tareas.
- La mantuve fuera porque no es necesaria para validar si una lista compartida y actualizada elimina la ronda de estado, y acepto ese riesgo durante la semana de prueba.
- La señal que me haría meterla en el MVP sería que las tareas creadas por error generen suficiente ruido como para que el equipo deje de confiar en la lista.

Calcula los dos números usando un criterio de conteo consistente entre la propuesta inicial y la final. No agrupes capacidades para alterar el recuento.

No hagas commit ni abras el PR.
```

## Prompt 8

**Modelo:** Opus 5.5 (claude-opus-5-5)
**Herramienta:** Claude Code

```
Añade a prompts.md el prompt de correcciones finales que faltaba y añade también este mensaje como último prompt del ejercicio. No modifiques el contenido de los prompts anteriores.

Después de actualizar prompts.md no realizaré más trabajo con el agente sobre el ejercicio.

No hagas commit ni abras el PR.
```
