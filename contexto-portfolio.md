# Contexto — Portfolio de Product Design

> Documento de traspaso. Pégalo al inicio de una conversación nueva con Claude para no perder contexto.

## Quién soy

Product Designer en **Magnettu** (Barcelona, startup), desde 2023. Empecé como UI Designer, evolucioné a Product Designer. Antes hice un bootcamp intensivo de UX/UI en **Ironhack Barcelona** en 2022 (tiempo completo, 2 meses, proyectos de complejidad creciente cada semana).

Estoy construyendo un portfolio desde cero para buscar trabajo, posicionándome como **Product Designer con foco en AI prototyping / vibe coding**, sin dejar de lado research y hablar con clientes.

Día a día en Magnettu: prototipado con IA (Claude, Claude Code), mantenimiento del design system (tokens + librería de componentes), mantenimiento de Webflow, entrevistas con clientes, colaboración estrecha con un PM y el equipo de desarrollo. Herramientas: Figma, FigJam, Webflow, Datadog, Clarity, Claude Code.

Preferencias de estilo al escribir textos del portfolio: tono profesional pero no excesivamente formal, **sin guiones/em dashes, usar comas en su lugar**.

---

## Portfolio — estructura y archivos

Sitio HTML multi-página, ya construido parcialmente:

- `index.html` — home: hero animado, índice de proyectos, About corto (timeline), contacto
- `magnettu.html` — case study completo de Magnettu (ver detalle abajo)
- `about.html` — página extendida de "Sobre mí", en 3 capítulos con foto + texto + skills
- `rediseno.html` — placeholder, será el rediseño de Bumble (ver más abajo)
- `autonomos.html` — placeholder, herramienta de colaboración para autónomos (0→1, sin desarrollar aún, el concepto original no se recuerda bien y habrá que reconstruirlo)

### Sistema visual ("Plantilla A — Studio Canvas")

- Fondo: canvas claro con puntos sutiles (`radial-gradient` de puntos), sin dividers laterales
- Tipografías: **Space Grotesk** (títulos), **IBM Plex Sans** (cuerpo), **IBM Plex Mono** (labels, tags, mono detalles)
- Colores acento: índigo `#4A5FE8`, coral `#FF6B5C`, menta `#189873` (versiones "soft" en fondos de tags)
- Fondo general `#FAFAFC`, texto `#15161A`, texto secundario `#63636D`
- Hero con animación de entrada (texto revelado línea por línea) y foto con bloque de color detrás + "pines" tipo comentario de Figma
- Dark mode: pendiente de construir. Cuando se haga, usar la paleta de la "Plantilla B — Editorial" (fondo casi negro, degradado índigo→rosa), aplicada sobre la misma estructura de la plantilla A, no un layout distinto
- Timelines (usados en "evolución de versiones" y en el About corto) con marcador circular en el borde izquierdo, verde/azul si es normal, coral si representa un fracaso/aprendizaje

### Flujo de trabajo con Claude

- Se trabaja de forma iterativa: se define contenido en conversación, Claude genera HTML, se revisa en navegador
- Cambios de texto/contenido: preferible seguir pidiéndolos a Claude directamente (no Cursor), salvo que en el futuro quiera independencia total del código
- Los proyectos abren en páginas HTML separadas (no anclas en una sola página larga)
- Las imágenes las coloca ella misma en los `img-slot` (placeholders con borde discontinuo) que deja Claude

---

## Case study: Magnettu (`magnettu.html`) — ya bastante avanzado

**Título:** "De un modal confuso a un flujo guiado"

**Contexto:** Magnettu no tenía apartado para agencias. La empresa pivota hacia colaboración con agencias. Nace "Grupos y Miembros" (diseño de otra diseñadora del equipo), que mezclaba usuarios, perfiles y grupos sin distinción.

**El problema (secuencia real, ya corregida):**
1. Todo empezó mezclado en "Grupos y Miembros"
2. Se consolidó (no se separó aún) bajo un apartado llamado "Marcas Personales", que seguía mezclando perfiles personales (entonces llamados "marcas personales"), perfiles de empresa y grupos, solo que bajo un nombre y espacio común
3. Solo más adelante (en la V3 del flujo, ver abajo) se separó todo en secciones independientes

**Causa raíz de fondo:** Magnettu sirve tanto a **agencias** (colaboración con clientes) como a **departamentos de marketing con programas de employee advocacy**. Crear un perfil debía funcionar para ambos casos, pero sus necesidades chocaban: para una agencia, el email del propietario era imprescindible; para advocacy interno, pedirlo como obligatorio no tenía sentido. Intentar simplificar el flujo para servir a ambos casos generó fricción constante a medida que aparecían casos de uso nuevos.

**Evolución del flujo de creación de perfiles:**

- **V1** — 4 tabs: nombre del perfil, objetivos, conectar LinkedIn (opcional), invitar usuarios + permisos. Por qué no era suficiente: no se entendía cuándo había que meter el email del propietario; muchos decían "lo haré después" y se olvidaban.
- **V2** — Ajustes de UI: ahora se podían añadir marcas sin límite, y se podía especificar si una marca era de empresa o personal. Por qué no era suficiente: seguía sin resolverse el problema de fondo del email del propietario.
- **V3** — Todo en un solo modal (nombre del perfil, URL de LinkedIn obligatoria, cómo se conectaría, permisos), + reorganización de fondo: "marcas" pasó a llamarse "perfiles personales", los grupos se separaron en su propia sección, y perfiles personales/empresa quedaron cada uno en su propio apartado. Por qué falló: seguía sin entenderse por qué se pedía cierta información; algunos no querían añadir 50 marcas de golpe y, al ser la URL obligatoria, muchos managers acababan pidiendo al equipo que creara los perfiles por ellos.
- **V4 (actual, el rediseño de Tatiana)** — Flujo guiado en 3 pasos en vez de un modal único, con más contexto/explicación en cada paso. Cambio clave: nueva pregunta en el paso 2, **"¿quién va a conectar LinkedIn?"** con dos opciones ("la conecto yo" / "la conecta el propietario"). Si se elige "la conecta el propietario", éste recibe un email automático de invitación (antes era un proceso manual que se olvidaba). Lanzada hace ~1 semana (a fecha de esta conversación), en validación, revisión cada 2 semanas.

**Decisiones que tomamos (bloques con imagen + texto explicativo en la página):**
1. Por qué el flujo con 1 solo perfil incluye 2 pasos extra (Colaboradores, LinkedIn) que no aparecen si se crean varios perfiles a la vez — hipótesis pendiente de confirmar por Tatiana: con un perfil tiene sentido acompañar el onboarding completo en el momento; con varios perfiles, repetir esos pasos uno a uno sería tedioso, así que se deja para configurar después, perfil por perfil.

**Cómo se prototipó con IA:** Se partió de capturas estáticas de Figma, convertidas en prototipo interactivo con Claude (en vez de maquetar pantalla por pantalla). Brief detallado a Claude con contexto/objetivo/restricciones, iteración con testeo real de usuarios entre rondas.

**De Figma a código (modal de invitación por email):** Tatiana diseñó el modal en Figma, le pidió a Claude que lo convirtiera en HTML implementable casi tal cual (el developer solo añadió lógica). Para que el handoff funcionara, ella entró en el código real de la app de Magnettu con **Claude Code y Cursor**, para entender componentes reutilizables, estructura y roles de usuario — esto coincidió con una actualización en curso del design system de Magnettu, dándole valor doble.

**Prototipo interactivo insertado en la página:** un componente HTML/CSS/JS funcional que replica el flujo real de creación de perfiles de Magnettu (Perfiles → Acceso → Permisos → [si 1 perfil] Colaboradores → LinkedIn), con la lógica condicional real:
- Si se crea 1 perfil → 5 pasos completos
- Si se crean 2+ perfiles → el flujo termina en Permisos (3 pasos)
- El campo de email del "Propietario" en el paso Acceso solo es obligatorio si se elige "La conecta el propietario"
- El mensaje final del paso LinkedIn cambia según esa elección: si "la conecta el propietario", dice que no hace falta que el usuario la conecte él mismo (el propietario recibirá un email); si no, muestra el CTA normal de conectar LinkedIn ahora o más tarde
- Tiene un botón de "↺ Reiniciar" siempre visible (barra superior) para no quedarse atascada en ningún paso
- Nota debajo aclarando que es una representación del diseño, no una réplica exacta al 100%

**Pendiente de cerrar en este case study:**
- Sección "Aprendizajes" — aún sin rellenar, pendiente de que Tatiana decida qué aprendió (de producto, o de su proceso trabajando con IA)
- Colocar las imágenes reales en los `img-slot` (incluyendo las 2 capturas para el bloque de "Decisiones que tomamos")
- Confirmar la hipótesis de Claude sobre por qué el flujo se ramifica según el número de perfiles

---

## Página About (`about.html`)

Estructura en 3 capítulos (foto + texto + tags de habilidades alternando lados), inspirada en una referencia visual que Tatiana encontró:

1. **Empezando como diseñadora UX/UI** — Ironhack Barcelona, 2022. Tags: Design Thinking, UX Research, Usability Testing, Trabajo en equipo, Metodología ágil, Ideación, Wireframing & Prototyping, Comunicación
2. **De diseñadora UX/UI a Product Designer en una startup** — Magnettu. Tags: Product Ownership, SaaS Product Design, Iteración basada en datos, Design Systems, Hand-off técnico, AI for Design
3. **Mejorando como profesional** — foco actual en IA y prototipado avanzado. Tags: High-speed Delivery, Comunicación asertiva, Growth Mindset, Resiliencia & Adaptabilidad, Problem Solving

Pendiente: Tatiana debe indicar sus 8 hobbies reales (hay un bloque de iconos/grid para esto, actualmente con placeholders), y colocar sus fotos.

Pendiente técnico: falta enlazar "About me" desde la navegación de `index.html` y el resto de páginas (no se ha hecho aún, se esperaba confirmación del diseño de `about.html` primero).

---

## Proyecto 2: Rediseño de Bumble (`rediseno.html`) — EN CURSO, es el foco actual

### Cómo se llegó a este proyecto

Tatiana dudaba entre dos ideas para su segundo case study: una feature nueva para YouTube, o algo para Bumble. Hizo una entrevista de cada una:

**Entrevista YouTube (descartada):** persona bastante satisfecha (nota 9/10), sin pain real. Menciones: usa YouTube para cosas interesantes/productivas/documentales, ya usa historial y "me gusta" para volver a videos, los anuncios molestan pero no se va por lealtad a la app, no querría mensajes directos tipo red social, escucha música de sesiones de 3 horas (Spotify no tiene esa duración). Ideas sueltas: IA para recomendar según estado de ánimo, buscar videos antiguos por descripción/emoción en vez de nombre. **Se descartó** por falta de fricción real que justifique un rediseño con research sólido detrás.

**Entrevista Bumble (elegida):** aquí sí había un pain real. Notas textuales de la entrevista:
- Usa Bumble porque se siente solo/a
- Encuentra match "si tengo suerte, una vez al mes"
- Las citas están bien pero cuesta encontrar a alguien con quien haya "sentido de la vida" compartido
- Percepción de que es más difícil para los hombres, "las chicas no van detrás de cualquiera"
- Nota si hay conexión por cómo fluye la conversación; hay gente que no sigue si no siente conexión, y otra que insiste con menos intensidad igualmente
- El hombre suele proponer el plan de la cita (tomar algo, pasear, sitio público), motivado en parte por expectativa social, no porque le cueste esa tarea en sí; siente que no proponerlo le haría sentir "inútil según la sociedad"
- Después de una cita sin interés, se siente mal
- Se pregunta por qué a veces hay interés en el chat pero no en persona (lo atribuye a lo físico o a "cómo eres como persona")
- Usa también Bumble Friends (busca amistad, adapta el tipo de plan a lo que le apetece)
- Sobre decidir el like en un perfil: mira primero las imágenes, si es "femenina", y el texto de la bio; la bio "no se lee", solo se ve el físico; esto le hace sentir mal
- Descarta perfiles con contenido extremista/ideologías fuertes
- No sabe cómo mejorar sus fotos ni busca inspiración para ello
- Pregunta que se hizo Tatiana durante la entrevista: "¿qué hacemos con las personas que no encuentran el amor?"

### Ángulo elegido (validado por Claude y Tatiana juntas)

El problema no es "a nivel persona" sino un problema de producto real: **el formato actual del perfil y del match reduce la decisión casi por completo al aspecto físico** (nadie lee la bio), y **la responsabilidad de proponer y organizar la cita recae en una sola persona**. Esto dificulta que la conversación arranque con algo más sustancioso que "hola qué tal".

**Dirección de solución que se está explorando:** añadir un "plan" al perfil (qué tipo de cita/actividad le apetece a esa persona), para que:
- El match se base también en afinidad de planes compartidos, no solo en fotos/bio
- La organización de la cita sea algo compartido desde el principio, no una carga unilateral

**Se descartó explícitamente** la idea de "ayudar con IA a mejorar fotos/perfil", porque reforzaría el problema real (juzgar solo por el físico) en vez de resolverlo.

**Enunciado de problema propuesto:**
> "Los perfiles actuales reducen la decisión de dar like al aspecto físico, y una vez hay match, la responsabilidad de proponer y encontrar un plan recae por completo en una persona. ¿Cómo rediseñamos el perfil y el flujo post-match para que el match se base también en afinidad de planes, y la organización de la cita sea compartida?"

### Alcance decidido

**Completo**: perfil, match, chat y organización de la cita (no solo el perfil).

### Research — estado actual

- 1 entrevista ya hecha (la de arriba, con un hombre)
- Va a hacer **2 entrevistas más** antes de seguir avanzando, idealmente al menos una con una mujer, para contrastar si el problema del perfil reducido a la foto y la carga de organizar el plan se siente igual, distinto o invertido desde el otro lado
- Guion de preguntas ya preparado por Claude (abierto, sin mencionar la idea del "plan" para no sesgar), cubre: perfil/decisión de like, match/chat, organización de la cita, cierre con nota del 1-10

### Proceso a seguir (basado en uxtools.co/challenges, adaptado)

Fases "Understand" e "Ideate" y "Test" del framework (se descarta "Implement" por no ser un producto en producción real):

1. ~~User Interview~~ (1 hecha, 2 más en curso)
2. **Empathy Map** — juntando las 3 entrevistas (pendiente de tener las 2 nuevas)
3. **Competitive Analysis** — mirar Tinder y Hinge (Hinge es especialmente relevante porque su propuesta de valor es "diseñado para ser borrado", con perfiles más ricos que solo fotos). No hace falta crear cuentas nuevas necesariamente: sirven capturas de reviews de tiendas de apps, artículos comparativos, videos de reseñas. Esto se puede avanzar en paralelo a las entrevistas.
4. **Journey Map** — del recorrido actual (descubrir perfil → match → chat → decidir plan → cita), para señalar visualmente el punto de dolor exacto
5. **User Flow** — de cómo se conecta perfil + plan + match + chat + cita
6. **Wireframes** — boceto de baja fidelidad
7. **Prototipo de alta fidelidad** — posiblemente con un prototipo interactivo en HTML/JS, como se hizo en el case study de Magnettu
8. **Test de usabilidad** — con 2-3 personas, para validar si entienden el concepto del "plan" y si reduce la carga percibida de organizar la cita

### Siguiente paso inmediato

Tatiana va a completar las 2 entrevistas nuevas. Mientras tanto, se puede avanzar el Competitive Analysis (Tinder + Hinge) en paralelo sin depender de las entrevistas.

---

## Proyecto 3: Herramienta de colaboración para autónomos (`autonomos.html`)

Aún sin desarrollar. Concepto original: una herramienta de colaboración entre autónomos que funcionan como un mismo equipo pero manteniendo su condición de autónomos, ajustados a objetivos compartidos. Tatiana no recuerda los detalles exactos y habrá que reconstruir el concepto desde cero (problema, usuario, propuesta de valor) cuando llegue el momento. Por ahora, en la home hay solo un placeholder "próximamente".

---

## Recordatorio para quien retome esto

- No inventar datos que Tatiana no ha confirmado (fechas, motivos de decisiones, resultados). Si falta un dato real, dejar un placeholder marcado y preguntar, no asumir.
- Mantener el tono de las conversaciones: sin guiones, comas en su lugar.
- Cuando se generen archivos HTML nuevos, mantener el mismo sistema visual ya establecido (ver sección de arriba) para que todo el portfolio se sienta coherente.
