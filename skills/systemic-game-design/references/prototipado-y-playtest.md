# Prototipado y playtest (cap. 12)

Leer cuando haya que validar una propuesta: encontrar la diversión rápido (cerrar el loop interactivo), qué es y qué no es un prototipo, una pregunta por prototipo, cuándo y con quién testear, guion, encuesta balanceada, métodos (observación, exploración dirigida, Mago de Oz, pensar en voz alta) y cómo leer el feedback (problemas, no soluciones).

Resumen parafraseado de Sellers, *Advanced Game Design: A Systems Approach* (2018). Entre corchetes va la sección del libro de donde sale cada bloque.

## Índice
- 1. Design-Build-Test (sección "Designing, Building, and Testing")
- 2. Finding the Fun Fast (sección "Finding the Fun Fast")
- 3. Effective Game Prototyping (sección homónima)
- 4. Effective Playtesting (sección homónima)
- 5. Heurísticas y errores comunes (resumen transversal)
- 6. Resumen mínimo de lo no central (pitch, producción, cierre)

---

## 1. Design-Build-Test (sección "Designing, Building, and Testing")

- **Design-build-test loop**: diseñar, construir y testear no son fases secuenciales sino actividades simultáneas durante todo el desarrollo. Cambia el énfasis: al inicio domina el diseño, después la implementación, al final testing/arreglo; pero siempre se hacen las tres.
- Apenas hay una idea del core loop se lo construye y se lo testea mientras el diseño sigue. Los cambios de diseño tardíos deben ser cada vez más acotados (detalle y balance, no estructura).
- Testear el gameplay durante todo el desarrollo, nunca dejarlo para el final.
- Implicancia: en una skill, todo análisis de diseño debería terminar en "qué se prototipa/testea para confirmarlo", no en una especificación cerrada.

## 2. Finding the Fun Fast (sección "Finding the Fun Fast")

- Primer gran objetivo: validar el concepto primario. No se puede postergar: si la idea no funciona o aparecen problemas técnicos, de interactividad o de gameplay invisibles en papel, hay que saberlo ya. Si funciona, da confianza para seguir.
- Cómo: **cerrar el interactive loop** entre jugador y juego. No importa que falte arte o gran parte del gameplay; lo que importa es que haya interactividad real.
- Distracciones tempranas (el autor las nombra): editor de mapas, iconografía, backstory del personaje. Importantes después, estorbo al principio.
- Regla fuerte: hasta que el loop interactivo esté cerrado y se confirme que hay algo atractivo, "no tenés un juego"; no tiene sentido invertir en otra cosa.
- Primer hito hacia el concepto = loop jugable, no contenido.

## 3. Effective Game Prototyping (sección homónima)

### Definición (game prototype)
- Prototipo = cualquier porción funcionante del juego que permita **al menos un interactive loop**.
- NO son prototipos: imagen no interactiva (es un **mockup**, aunque esté animada), video de gameplay (real o prefijado), simulación corriendo sin interacción (aunque a veces sirva como test técnico especializado). Regla práctica: si nadie puede jugarlo, no es prototipo de juego.
- Razón: sin interacción no se testea el juego; un programa no interactivo prueba un algoritmo o simulación, no un juego. Las excursiones fuera del juego son válidas pero cada prototipo debe acercar al juego final.
- El componente interactivo mínimo (analógico o digital) = el jugador forma una intención, la ejecuta con una acción, perturba el modelo interno del juego y el juego da feedback.

### Analógico vs digital
- Tabletop: cualquier cosa (papeles). Digitales: primeros prototipos suelen ser físicos (papel, dados, pizarra) con lo justo para un solo loop.
- Prototipo digital temprano = programa simple, standalone, para probar UNA parte, empezando por los core loops. Los posteriores incorporan más del juego.

### Mantener los prototipos separados (Keeping Prototypes Separate)
- Prototipos nunca son parte del producto; siempre se implementan aparte. Se puede reusar partes del juego como base de un prototipo, pero el código del prototipo NUNCA vuelve al juego.
- Deben poder ser rápidos, feos y sin optimizar. Señales de alarma: frenarse a "programarlo bien" o pensar en copiar/pegar al juego -> sos un híbrido que no es ni prototipo ni código viable.
- Mantra (**Move fast and throw it away**): moverse rápido y aceptar romper cosas. Se hace **refactor** (analizar qué funcionó y reescribir), no copia. El objetivo del prototipo es responder una pregunta de diseño, no producir código reutilizable.

### Cómo empezar (Getting Started with Prototyping)
- Se puede prototipar apenas hay idea y concepto. Empezar simple: no hace falta economía ni combate completos. Un movimiento básico o una acción simple alcanza.
- Arte y estilo de animación se prueban después; primero un loop interactivo y una meta simple del jugador (ej.: ir de aquí a allá) que tenga sentido en el juego.
- Agregar más decisiones y loops gradualmente, pero asegurando que los core loops sean atractivos. Si no lo son, "no hay maquillaje que los arregle": quedarán como partes flojas y frustrantes.

### Responder preguntas (Answering Questions)
- Un prototipo existe para hacer y responder preguntas. La primera y mayor: "¿Esto es divertido?" (sobre los core loops).
- La respuesta suele ser NO. Regla del autor: las primeras ideas suelen ser malas o, en el mejor caso, mediocres y derivativas; solo se ve al sacarlas de la cabeza. Descubrirlo con poca inversión es una ganancia (mejor que a los 6 meses).
- Si un prototipo falla: aprender, probar otro enfoque del mismo concepto (más rápido, más estratégico, núcleo emocional distinto). Un enfoque fallido no invalida el concepto.

### Metas y preguntas claras (Clear Goals and Questions)
- Todo prototipo lleva una pregunta/meta clara, no ambigua, cuya respuesta cambie significativamente el juego o cómo se desarrolla.
- Disparador: si el equipo discute o duda de dirección, es la situación ideal para un prototipo: dejar de discutir, formular la pregunta, construirlo, ver.
- Ejemplos de preguntas buenas: "¿Alcanza un recurso o hacen falta más?"; "¿Este estilo de combate se siente divertido?"
- Cuanto más precisa la pregunta y el prototipo, más se aprende; **mejor aún si se pueden probar varias opciones a la vez** (ajustando variables o modos distintos).
- Explicitar supuestos sobre el jugador para cada prototipo: qué sabe del juego, cuáles son sus metas, cuánto modelo mental armó. La meta del jugador puede ser simple ("ir de A a B") o compleja ("completar misión sin ser visto"); depende de la etapa.

### Audiencia del prototipo (Knowing the Intended Audience)
- Tipo 1, interno: rápidos y feos, solo para el equipo. Gastar lo mínimo en pulido; cuadrados o X de gráficos; o analógico con papel/marcadores/dados. Cuanto más rápido y feo, más eficaz para contestar la pregunta.
- Tipo 2, para terceros: **vertical slice** = corte que muestra todas las capas/sistemas funcionando juntos (UI pulida, interacción consistente, arte, exploración, combate balanceado, hasta la base de datos). La idea: lo demás sería solo "más niveles, armas, trajes".
- Crítica del autor al vertical slice: se confunde un sistema **complex** (con loops) con uno **complicated** (lineal). En juegos innovadores no se reduce a "ahora solo hacé más niveles". Un slice no garantiza que el resto sea lineal.
- Tensión con stakeholders: un prototipo feo pero atractivo (círculo esquivando cuadrados) puede hacerles perder confianza porque no ven la experiencia. Alternativa: un video demo NO interactivo de cómo se verá el juego; consume recursos pero sirve también para alinear la visión del equipo.

### Otros prototipos (Other Prototypes)
- Hay prototipos no interactivos o casi: probar un sistema interno del modelo del mundo, efectos gráficos, aspectos cualitativos de la UI (su **juiciness**, ej. animaciones breves en controles). Son válidos; si se puede, incluirlos en otro prototipo de juego; si no, mismo criterio: saber qué se prueba, qué pregunta se hace, cómo cambia el juego la respuesta, e iterar hasta que "se sienta bien".

## 4. Effective Playtesting (sección homónima)

### Por qué (The Importance of Playtesting)
- Testear la experiencia ya en prototipos, no solo en el juego terminado. Primero con el equipo; luego pronto con gente que no sabe nada del juego y, de preferencia, no te conoce. Es incómodo: lo claro para vos resulta opaco o frustrante. "Si esperás a sentirte listo, ya esperaste demasiado."
- Buscás ver cómo otros viven el juego: ¿engancha, es divertido, querrían seguir?
- No asumas qué pensarán los jugadores: probablemente te equivoques más de lo que acertás. Lo más valioso: descubrir lo que es obvio para vos y misterioso para ellos.
- **Jugadores dan problemas, no soluciones**: se busca ver dónde mejorar, no obtener soluciones. Si proponen una, mirar detrás para ver qué problema creen que hay; tu solución al problema de fondo puede ser muy distinta.

### Cuándo (When to Test)
- Lo antes posible, antes de que creas que está listo. Resistir el "todavía no está listo".
- Más tests cortos > pocos tests largos.
- Disparadores de playtest: (1) cambio significativo en el juego; (2) área donde dudás de la dirección; (3) pasaron unas semanas desde el último.
- Cadencia: al inicio ~cada 2 semanas; más adelante semanal o cada pocos días.

### Objetivos (Goals for Your Playtests)
- NO es buscar bugs de código (menos aún en prototipos feos). Es testear el diseño: ¿lo entienden, arman un modelo mental eficaz, lo encuentran atractivo y divertido?
- Temprano: validar conceptos básicos del diseño. A medida que crecen los sistemas: qué tan fácil se comprende y qué tan bien se arma el modelo mental.
- Buscar dónde "se desvían" los jugadores: modelo mental distinto de lo esperado y del modelo interno del juego; confusión, frustración, no saber qué hacer ahora.
- Tarde o temprano deriva en **usability testing**: ¿se entiende la UI, es fácil o engorrosa? No mide la experiencia global pero es parte de ella.

### Quién testea (Who Playtests Your Game?)
- No vos: sos el más sesgado y menos calificado. Tu experiencia no dice nada sobre lo divertido para otros.
- Equipo, amigos y familia: malos sujetos; inconscientemente se esfuerzan por ver el juego como entendible/atractivo aunque esté roto.
- Excepción: para prototipos tempranos y feos conviene mantenerlos cerca; unos pocos confidentes externos sirven si pueden ver más allá de los gráficos placeholder.
- **No se puede "des-saber"**: una persona que ya jugó no vuelve a ser naive. No reusar a la misma persona como novata para la misma parte. Repetidores sirven para comparar preferencias o si algo ahora tiene más sentido, pero no equivalen a un primerizo.
- A medida que el juego madura, ampliar y acercar el pool al público objetivo, sin acotarlo demasiado (se pierden jugadores inesperados o un mercado mal calibrado).
- Cuidado con los **hardcore gamers entusiastas**: útiles pero con opiniones firmes sobre qué es un "buen juego"; meten más ruido que señal.

### Preparación (Preparing Your Playtest)
- Tener claro el objetivo y cómo se conduce. Lugar: cualquier sitio tranquilo sin distracciones; incluso uno ruidoso funcionó (comedor universitario).
- Laboratorios con vidrio espejado o cámaras: útiles pero innecesarios; no frenar tests por falta de instalaciones. Hacer un prototipo y testearlo.
- Compensación: no siempre hace falta; ser justo. Pizza gratis para universitarios funcionó; tarjeta de regalo de poco valor; más compensación cuanto más largo el test y la encuesta.

### Guion (Writing a Script)
- Escribir un guion detallado de TODO (saludo, ejecución, preguntas post-test, despedida), hasta lo que se dice en cada paso. Evita decir de más o ponerse nervioso y asegura el **mismo contexto e instrucciones** para todos.
- Empezar con saludo y charla de calentamiento; datos mínimos del jugador (solo los necesarios: nombre/contacto, edad/género si acepta). Preguntar qué otros juegos juega: calibra experiencia y mete al jugador en modo test.
- Ética: avisar que se testea el juego, no a la persona, que lo que haga es válido; que puede parar y irse cuando quiera; que responder preguntas es voluntario. Idealmente declaración corta leída en voz alta y/o firmada/iniciales, o al menos reconocimiento verbal.
- Si el jugador quiere parar, se detiene el test sin insistir (insistir plantea problemas éticos); además el deseo de parar es información sobre tu juego.
- Registro: formularios de notas; opcional video de pantalla y cara con consentimiento. Advertencia: el video multiplica el tiempo de análisis y no necesariamente da más info, sobre todo temprano.

### Encuesta post-test (Creating a Survey)
- Diseñar encuestas requiere cierta pericia. Breve, pocas preguntas, todas ligadas al objetivo del test y a la experiencia (incluida comprensión y modelo mental). No preguntar por todo (gráficos, música, dificultad...) si no corresponde al objetivo actual: abruma y da datos que no vas a usar. Los comentarios espontáneos del jugador se anotan igual.
- **Preguntas balanceadas**: tantas respuestas/enunciados negativos como positivos, para no sesgar (evitar leading questions). Si es online, orden aleatorio de preguntas (reduce sesgo, facilita análisis).
- **Escala numérica** (5 a 7 opciones, de "muy en desacuerdo" a "muy de acuerdo" con neutral al medio). Los enunciados deben ser afirmaciones fuertes con las que se pueda concordar o discrepar. Ejemplos del libro:
  1. Fue fácil moverme en el juego.
  2. Entendí lo que pasaba en todo momento.
  3. Tenía metas claras que intentaba cumplir.
  4. Podría volver a jugarlo fácilmente sin repasar las reglas.
- **Lista de adjetivos marcables** (cuantificable pero abierta): Exciting, Fast, Confusing, Boring, Overwhelming, Thoughtful, Strategic, Broken, Engaging. Regla: igual cantidad de rasgos positivos, negativos y neutros, en orden no sesgado (no de mejor a peor).
- **Preguntas de comprensión / modelo mental** (mejor orales y grabadas, permiten respuesta libre): mostrar íconos/símbolos y pedir qué significan; preguntas de proceso ("¿qué pasos seguirías para saber cuántos soldados tenés disponibles?"); mostrar una captura de un momento típico y pedir qué harías a continuación señalando con el dedo.
- **Respuestas cortas** (oral o escrito) más una abierta final:
  - Explicá brevemente las reglas del juego como las entendés.
  - ¿Qué te sorprendió?
  - ¿Qué creíste que debías lograr?
  - ¿De qué juegos te acordó?
- "¿Cuánto pagarías?": sirve para calibrar experiencia positiva/negativa y valor vago, pero NO para fijar precio (lo dicho difiere de lo hecho).
- **Probar el guion antes** (mock playtest con alguien, aunque sea del equipo) para no tropezar con fallas del propio test.

### Conducir el test (Running a Playtest)
- Cortos: unos minutos, en general no más de 10-20.
- Informar lo mínimo del juego. Variantes por test: dar el nombre o la posible carátula; dar un resumen general o el elevator pitch para ver si afecta comprensión/disfrute; o no dar nada (avisándole al jugador que no vas a dar información). Seguir el guion para no decir más a unos que a otros. Después del lanzamiento no estarás para explicar, así que limitá la información previa.
- Durante el juego: fuera de la línea de visión, sin rondar, hablar lo mínimo. Responder las menos preguntas posibles y breve. **Hay que presenciar su confusión y frustración.** Alentar a seguir sin pistas.
- Prohibido: señalar algo en pantalla, "probá clic arriba a la izquierda", "volvé un menú atrás y leelo de nuevo", explicar el juego, defenderse de críticas. Explicar o defenderse arruina el test.
- Anotar qué hace, qué dice, dónde se confunde y SOBRE TODO reacciones emocionales (comprensión súbita, deleite, confusión, frustración).
- Si pide reassurance: "vas bien, seguí". Reacciones del observador, neutras y generales: los jugadores buscan señales (incluso inconscientes) de si pueden criticar.
- Fin del test: cuando completa lo buscado o se traba sin poder avanzar. Entonces preguntar qué intentaba y qué esperaba que pasara (revela modelo mental) y pasar al post-test.

### Cierre (Finishing Up the Playtest)
- Pedir impresiones generales. Prestar atención a lo PRIMERO que dicen (reacción top-of-mind) y a la estructura de lo que dicen: pueden empezar con algo amable para amortiguar la crítica real. Aceptar todo sin cerrar ni defender.
- Luego la encuesta del guion (sin sesgar), agradecer, pedir llenarla; si la rechaza, igual preguntar pensamientos finales; agradecer y despedir.

### Métodos de test (Testing Methods)
Según el objetivo y la confianza del facilitador:
1. **Observation**: mirar al jugador. Ver adónde va primero, qué opciones mira o ignora, si hace lo esperado en cada momento. Señales de engagement: mirar fijo la pantalla, labios apretados, parpadeo más lento. Reacciones emocionales: sorpresa, deleite, frustración. Anotar dónde se confunde, se traba o vuelve una y otra vez sobre el mismo contenido/UI (intenta y falla).
2. **Directed Experience and Exploration**: darle una meta concreta (en el guion, no para sacarlo de una confusión; útil sobre todo con quien ya probó el juego); o decirle que explore libremente y mirar qué ignora o evita.
3. **Wizard of Oz**: tests tempranos, analógicos; el diseñador hace de computadora ("el mago tras la cortina"). Baja fidelidad: no sirve para juzgar el comportamiento del juego digital futuro, pero revela expectativas y modelo mental.
4. **Thinking Aloud**: pedir que hable en voz alta todo el tiempo (intenciones, dudas). Difícil: se callan al razonar; recordar con "seguí hablando". Baja el rendimiento del jugador (sobre todo en juegos que exigen su **interactivity budget**). Útil cuando otros tests muestran confusión y no sabés por qué.
- Regla: usar solo métodos ligados al objetivo del test.

### Analizar feedback (Analyzing Feedback)
- Inmediatamente al terminar: anotar impresiones (reacciones vistas, bugs, ideas). Después separar tiempo de análisis: revisar notas de cada jugador buscando experiencias comunes, temas, qué fue más importante; revisar cuantitativos de encuesta por tendencias.
- No rechazar ni preocuparse por comentarios negativos: no son juicio sobre el diseñador, sino sobre cuánto el juego logra la experiencia buscada. Aprender de los negativos.
- **Outliers**: uno ama, otro no entiende nada: tienden a ser casos aislados; buscar lo COMÚN entre jugadores.
- No forzar patrones ni buscar significancia estadística (salvo equipo grande con decenas de jugadores por test). Buscar **directional experiences** que refinen el diseño y respondan preguntas.
- Direccionalidad también en el TIEMPO: comparar entre builds. ¿Las mismas partes enganchan consistentemente? ¿Zonas confusas ya se disfrutan? ¿Un cambio empeoró algo?
- Jugadores = punto de vista válido pero no diseñadores; leer su feedback como identificación de problemas, no soluciones.
- Casos del libro de feedback que cambió el diseño: (a) juego de piratas: la exploración se sentía relleno entre combates; el diseñador se enfocó solo en batallas navales y quedó más atractivo y más fácil de implementar; (b) The Sims: pensado como simulador de vida tipo Tamagotchi, pero los jugadores se interesaban por las interacciones y las historias emergentes; cambió el desarrollo y el marketing.

## 5. Heurísticas y errores comunes (resumen transversal)

Heurísticas
- Cerrar el loop interactivo antes que nada; pulir viene después.
- Una pregunta por prototipo; si hay debate del equipo, convertirlo en prototipo.
- Probar varias variantes/variables a la vez cuando sea posible.
- Prototipo: rápido, feo, descartable; refactor sí, copy-paste no.
- Muchos tests cortos; testear tras cada cambio significativo, duda de dirección o ~2 semanas sin test (luego semanal).
- Guion escrito y probado; mismo contexto para todos; observar callado.
- Buscar lo común y la dirección, no estadística; leer problemas, no soluciones.
- Fallar rápido de ideas es barato: celebrar el descarte temprano.

Errores comunes
- Esperar a que el juego "esté listo" para testear.
- Testearse a sí mismo o con amigos/familia/equipo y confiar en eso.
- Reusar un tester como novato; confundir repetidor con primerizo.
- Intervenir: señalar, explicar, defenderse, dar pistas.
- Encuestas sesgadas (solo enunciados positivos, orden fijo), demasiado largas o ajenas al objetivo.
- Tomar "cuánto pagarías" como precio real.
- Testear bugs en vez de diseño en prototipos.
- Meter código de prototipo en el juego; "híbrido horrible".
- Perder tiempo en editor de mapas, iconografía o lore antes de saber si hay diversión.
- Confundir sistema complex con complicated (creer que el slice basta y "solo falta más contenido").
- Maquillar un core loop flojo esperando que el pulido lo arregle.
- Hacer caso literal a las soluciones propuestas por jugadores.
- Hardcore gamers como único pool; pool demasiado estrecho.
- Análisis exagerado con video en etapas tempranas (cuesta mucho, aporta poco).

## 6. Resumen mínimo de lo no central (pitch, producción, cierre)

- **Pitch** (Making the Pitch): comunicar el juego para financiar, validar, reclutar o prensa; conocer objetivo, audiencia y material; elevator pitch (quién soy, qué hago, qué busco) vs reunión formal (<=10 slides, core loop gráfico, 5-10 min de preguntas); concept statement corto (idealmente <=140 caracteres, <=1 coma); orden de preferencia de evidencia (juego vendido > casi terminado > demo pulida > prototipo del core > trailer con sonido > mockups); call to action y follow-up; un "fast no" es mejor que "death by tea and crumpets". Útil de rescatar: comentarios tipo "es X cruzado con Y" indican que la persona armó un modelo mental; que no haya preguntas es mala señal.
- **Fases de producción** (Phases of Production): iterativo (no waterfall); **stage gating** con revisiones periódicas (cada ~2 semanas al inicio) y **concept bank** para ideas descartadas; sprints de 2-4 semanas; concept (1-3 meses, con gate: si el prototipo no funciona, no seguir invirtiendo), preproduction (2-3, hasta 6 meses; features, MVP, asset list, plan con horizonte decreciente), production (evitar scope creep: toda nueva feature pasa por mini concept y preproducción), alpha (todo jugable, testeado por externos; después solo bugs y balance de valores bajos), beta (balance, polish, juiciness UI, métricas de retención día 1/semana/mes en free-to-play), lanzamiento.
- **Production analytics**: medir estimado vs real por tarea; ratio personal como multiplicador (ej. 1.2x); mini postmortem por iteración; burndown charts.
- **Finishing**: terminar > perfeccionar; "anything finished is better than everything unfinished"; la liberación es el outermost designer's loop; el primer playtest grande del juego completo trae páginas de problemas y hay que seguir.
