# Interactividad, engagement y diversión (cap. 4)

Leer cuando el problema es que el juego no engancha, aburre, abruma o 'no se siente bien': modelo mental del jugador, carga cognitiva y distancias articulatoria/semántica, los seis loops interactivos y sus escalas de tiempo, flow, arousal, presupuesto de interactividad ('lo rápido expulsa a lo lento'), emociones y motivaciones, y la definición operativa de diversión. Termina con un checklist de diagnóstico.

Resumen parafraseado de Sellers, *Advanced Game Design: A Systems Approach* (2018). Entre corchetes va la sección del libro de donde sale cada bloque.

## Índice
- 1. El jugador como parte del sistema (sec. "The Player's Part of the Game as a System")
- 2. Enfoque sistémico de la interactividad (sec. "A Systemic Approach to Interactivity")
- 3. Modelos mentales, arousal y engagement (sec. "Mental Models, Arousal, and Engagement")
- 4. Interactive loops: seis tipos (sec. "Interactive Loops")
- 5. Flow (sec. "Flow in Interactive Loops")
- 6. Vista de escalas de tiempo: loops apilados (sec. "A Time-Scale View of Interactive Loops")
- 7. Carga mental y presupuesto de interactividad (sec. "Mental Load and the Interactivity Budget")
- 8. Reconocer, definir y crear "diversión" (sec. "Recognizing, Defining, and Creating 'Fun'")
- 9. Checklist de diagnóstico y diseño (síntesis de las heurísticas del capítulo)

---

---
## 1. El jugador como parte del sistema (sec. "The Player's Part of the Game as a System")

- **Game+player system**: la experiencia de juego solo existe cuando se juntan juego y jugador; cada uno es un subsistema con partes (estructura), bucles (función) y todo (tema).
- **Mental model (modelo mental del jugador)**: reflejo que el jugador construye del **internal model** del juego (el que define el diseñador). Todo el capítulo es "cómo se construye ese modelo y qué lo mantiene vivo".
- El bucle mutuo (el jugador actúa, el juego cambia y devuelve feedback, el jugador actualiza su modelo) es el núcleo de interactividad, gameplay, engagement y diversión.

## 2. Enfoque sistémico de la interactividad (sec. "A Systemic Approach to Interactivity")

### Definición
- Interactivo = dos o más agentes que se afectan mutuamente/recíprocamente (Webster). Rafaeli: serie de intercambios donde cada mensaje se relaciona con los previos. **Crawford (1984)**: ciclo en que cada agente alternadamente *escucha, piensa y habla* (una "conversación").
- Debate académico: algunos ubican la interactividad solo en el individuo, solo en el medio, o solo en humano-humano. Sellers: es propiedad del **sistema** formado por los agentes.

### Partes (structure)
- Al menos un humano en el bucle. Un juego que "se juega solo" sirve para testeo, pero pierde la experiencia significativa.
- Cada parte tiene **estado, límites y comportamientos**. Los comportamientos **afectan pero no determinan del todo** el estado del otro.
- **Estado interno del jugador** = su modelo mental. Incluye su comprensión de:
  1. Variables actuales del juego (vida, riqueza, población, inventario...).
  2. El estado del juego, sobre todo cómo cambió su comprensión según el feedback de su última acción.
  3. Metas inmediatas, de corto y largo plazo, incluyendo predicciones de qué pasará según sus acciones.
  4. Efectos de decisiones pasadas y lo que aprendió de ellas.
- **Estado interno del juego** = el diseño hecho funcionamiento (variables, reglas, event loop, cuándo acepta input).

### Comportamientos
- Las acciones son las que el diseñador habilita; el juego puede inhabilitarlas (ej: cooldown). Habilidades y límites extraordinarios son parte del **magic circle**.
- Comportamiento del jugador: empieza como meta mental y debe volverse físico (mover pieza, click, tap, swipe, incluso mirada). Esa transición es la frontera modelo mental/conducta.

### Cognitive load y las dos "distancias" (Norman & Draper 1986; Sweller 1988)
- **Cognitive load**: recursos mentales que consume pensar/atender. Menos carga para *cómo* jugar = más recursos para *qué* hacer = más engagement y diversión.
- **Articulatory distance** (distancia articulatoria): cuán directa es la acción física. Señalar con el dedo < cursor de mouse < tipear coordenadas (x,y). Menos distancia = menos carga.
- **Semantic distance** (distancia semántica): cuán fácil es interpretar el resultado/feedback. Se reduce con feedback abundante, oportuno y fácil de interpretar.
  - Ejemplos del autor: ícono de espada < letra "w" < palabra "sword"; animación de edificio construyéndose < barra de progreso < texto "563/989 ladrillos".
- Regla: menos casos especiales en las reglas = menos que recordar = distancia semántica menor. **Go** como caso extremo (casi cero distancia, toda la cognición va al espacio de juego). Conecta con *elegance* (cap. 2).
- Heurística de diseño: cada vez que agregues una excepción, un modo o un ícono críptico, estás gastando presupuesto cognitivo del jugador.

### Comportamientos del juego y feedback
- El juego da feedback (gráficos, texto, animación, sonido) para que el jugador actualice su modelo.
- El feedback debe ser **perceptible** (un color que no se ve o sonido que no se oye = sin feedback), pero **no tiene que ser completo**: el estado oculto es ingrediente clave. **Koster**: la parte "caja negra" que el jugador infiere. **Ellenor**: los sistemas internos como "una máquina que hace X" que el jugador solo conoce por su conducta.
- **Todo lo que el jugador sabe del juego viene de su comportamiento y feedback.** Cuidado con asumir conocimiento previo (mouse, tocar pantalla, dados): si el juego no lo enseña y hace falta, el jugador no puede jugar.
- Las zonas del modelo mental que el jugador siente sólidas le sirven para predecir las zonas inciertas; ahí vive mucho del gameplay (probar acciones con resultado predicho y ajustar el modelo).

### Elección intencional
El jugador debe poder entender qué acciones: (a) son válidas en el contexto actual, (b) tienen la información necesaria para decidir, (c) lo acercan a su meta según el resultado que predice, (d) pueden decidirse y ejecutarse en un tiempo razonable. Si falla alguna, la acción es azarosa, no una elección.

### Interactive loop (Figs. 4.2, 4.3)
- Jugador da **input** → el juego procesa y devuelve **feedback** → cambia el estado interno del jugador. Es el origen del **core loop** (se afina más abajo y en cap. 7). Ambos tienen además bucles internos propios.
- **Designer's loop** (cuarto bucle): el diseñador está fuera del sistema; da input (ideas/prototipos) y recibe feedback (qué funciona). Es el proceso de diseño iterativo.
- Cuatro bucles en total mencionados: mental interno del jugador, interno del juego, interactivo jugador-juego, del diseñador.

### El todo
- El significado del juego (tema, moraleja, lo que queda después) es **emergente** del sistema interactivo, no está solo en el jugador ni solo en el juego (Newhagen 2004). Esos símbolos de nivel superior forman el modelo mental.

---
## 3. Modelos mentales, arousal y engagement (sec. "Mental Models, Arousal, and Engagement")

### Construcción del modelo mental
- El jugador prueba su comprensión con acciones. Feedback positivo ("hice algo bien") = sensación de logro y el concepto se agrega al modelo; feedback negativo = revisar y corregir.
- Modelo mental = atención + planes + metas + emociones. Incluye sistemas (combate, economía, ecología) y **navegación** de espacios geográficos o lógicos.
  - Ejemplos: saber ir de Ashenvale a Stormwind en *WoW* (modelo del mundo); entender el árbol de habilidades de *The Witcher 3* (p. ej. por qué elegir Muscle Memory sobre Lightning Reflexes).
- Si el jugador no logra un modelo coherente con el del diseñador, o las interacciones son tediosas/aburridas/abrumadoras, **deja de jugar**. Término psicológico: **behavior extinction**; en juegos, *burnout*.
- **Bushnell's Law**: fácil de aprender, difícil de dominar. En términos de modelo mental: fácil construir y validar el modelo (sin ambigüedades ni excepciones que trabu al nuevo), con información básica clara y familiar que invite a explorar.
- Buen juego = amplio espacio mental para explorar: se rejuega sin sentir que se dominó rápido. **Una vez que el jugador vio todo el contenido y exploró todas las interacciones, no hay nada que aprender y el juego deja de enganchar.** Go como arquetipo.

### Interactive loop detallado (Fig. 4.4)
Secuencia: el jugador **forma intenciones y metas** → **realiza acciones** en el juego → el juego **procesa input y cambia estado** (también cambia solo por su diseño) → el juego **da feedback con información extra, habilidades nuevas y call to action** → el jugador **ajusta su modelo mental**. Repetir.
- **Call to action / hook**: lo que impulsa a empezar o seguir (desde la splash screen). Similar pero no igual a *affordance* (Norman 1988: pista perceptible de cómo opera algo; "las placas son para empujar..."). El call to action necesita *affordance* (obvio cómo actuar) **más motivación** (querer actuar). Metáfora del autor: no solo una taza con asa, sino una taza atractiva con cacao caliente.
- El juego debe sostener el loop con **nueva información/habilidades y nuevas oportunidades** para que el modelo siga creciendo.

### Arousal y atención
- Para jugar, el jugador tiene que estar interesado y **aroused** (alerta, listo para participar). Aburrido o abrumado/ansioso = no invierte energía.
- Señales de problema:
  - **Aburrimiento**: no ve controles usables o no entiende qué se muestra.
  - **Abrumamiento**: tanto pasa en pantalla (sobre todo visualmente) que no sabe qué hacer ni por dónde empezar.
- Nadie está obligado a jugar: es responsabilidad del diseñador que el juego parezca lo bastante interesante para atraer y retener.

### Yerkes-Dodson Law (1908)
- Curva en U invertida: a más arousal, más rendimiento hasta un punto; después ansiedad, pérdida de foco, pánico y caída de rendimiento. Zonas del gráfico: sueño → aburrimiento (bajo) → alerta leve (óptimo) → estrés → ansiedad → pánico.
- Variaciones: en **tareas simples** el rendimiento cae menos con arousal alto; en **tareas complejas** el óptimo se alcanza antes. **Expert effect**: a más habilidad/práctica, se tolera más arousal sin perder rendimiento (piloto, cirujano, conductor).
- Zona óptima/ligeramente pasada el pico: ahí ocurren aprendizaje y mejora de habilidad ("surfear el borde"). Deslizarse por la derecha = demasiado input/carga cognitiva.
- **Psychological engagement** = estar en la zona media: alerta, atento a la tarea, capaz de ignorar lo irrelevante, rindiendo bien y consciente de ello.

### Engagement (definición)
- Estado interno del individuo ante el mundo (Gambetti & Graffigna 2010). **Schaufeli et al. (2002)**: combinación de **vigor** (energía, resiliencia, esfuerzo, persistencia ante dificultades), **dedication** (significado, entusiasmo, inspiración, orgullo, desafío) y **absorption** (concentración total, el tiempo pasa rápido, cuesta desengancharse).
- Son las cualidades de los jugadores que describen una experiencia satisfactoria. El jugador logra un modelo que calza con el del juego, se plantea hipótesis, actúa y recibe feedback satisfactorio; el ciclo sigue.
- **Fun (esbozo)**: actividad que engancha, placentera, voluntaria, separada y sin consecuencias (magic circle) → "estar divirtiéndose".
- "Player engagement" se usa como métrica comercial sin definirse; esta definición lo ancla.

### Engagement neuroquímico (cuidado: no reducir diversión a química)
| Neuroquímico | Qué señala | Implicancia de diseño |
|---|---|---|
| **Dopamina** | "Recompensa": alerta, motivación; novedad (no demasiado rara), exploración, meta alcanzada. Ver puntos subiendo = dopamina. Si la recompensa esperada no llega, baja la dopamina y la conducta se valora menos. | **Habituación**: valoramos lo nuevo más que lo esperado; lo conocido pierde atractivo hasta el aburrimiento. Gran parte del diseño es dar recompensas/formas nuevas de engancharse. |
| **Serotonina** | Contrapeso de dopamina: seguridad, logro, estatus social, completar logros, ganar habilidad ("harm avoidance"). Dopamina empuja a buscar lo nuevo/impulsividad; serotonina a seguir con lo conocido. | Subir de nivel satisface en parte por serotonina. Los efectos audiovisuales de celebración ("Ding!" en MMOs) condicionan la asociación; no subestimarlos. |
| **Oxitocina / vasopresina** | Vínculos sociales, apoyo, pertenencia a pareja/familia/equipo/comunidad. | Base de la participación social en juegos. |
| **Norepinefrina / endorfinas** | "Estrés": vigilancia a corto plazo, reacción rápida, aprendizaje rápido (NE); enmascarar dolor, sensación de energía extra (endorfinas). Menos relevantes en juegos sedentarios pero ayudan a concentrar la atención bajo estrés. | Útil en juegos de acción/tensión. |

- **Cinco sensaciones de engagement** (no todas a la vez): alerta/buscando novedad o esperando recompensa; seguro en la recompensa o en el lugar en la jerarquía social; conectado a otros por lazos sociales; vigilante ante estrés; "empujando" exitosamente a pesar del esfuerzo.
- **Ritmo**: un nivel difícil o clímax se sigue de un momento tranquilo para bajar la vigilancia, descansar y consolidar logros y conexión social. Manipular estas sensaciones es parte de sostener el engagement.
- Contexto consecuente (trabajo) → "realizador"; contexto separado, voluntario y sin consecuencias (magic circle) → "divertido".
- Los tipos de engagement que siguen van de reflexivo a ejecutivo a reflexivo-reflexivo, bajo más control individual y escalas de tiempo más largas. Corresponden a los tipos de **metas del jugador** del cap. 3: cada loop da la oportunidad de formar una intención, desde reflejo instantáneo hasta meta lejana. Las motivaciones se tratan en cap. 6.

---
## 4. Interactive loops: seis tipos (sec. "Interactive Loops")

Todos son el mismo loop (intención → acción → cambio de estado → feedback). Difieren en **recursos mentales requeridos, escala de tiempo y experiencia resultante**. **Ocurren a la vez, anidados** (muchos loops rápidos dentro de uno cognitivo largo).

Orden del más rápido/menos cognitivo al más lento/más reflexivo (Fig. 4.6):
1. Action/feedback
2. Short-term cognitive
3. Long-term cognitive
4. Social
5. Emotional
6. Cultural

### 4.1 Action/Feedback (A/F)
- Escala: < 1 s hasta 2-3 s. Acción física del jugador, feedback sensorial del juego, casi sin pensar.
- **Latencia**: se percibe como instantáneo con **< 100 ms** entre acción y feedback; para conservar sensación de conexión inmediata, **máximo ~250 ms** (Card et al. 1983). Más allá, el jugador no asocia feedback con acción salvo que sea simbólico a un modelo cognitivo más largo, y aun así se siente lento.
- **Present tense**: test para saber qué loop domina. Si el jugador describe lo que hace en verbos presentes (caminando, corriendo, disparando, saltando), su atención está en A/F. Si lo describe en metas futuras ("completo esta misión", "armo ejército para ayudar a mi amigo"), A/F existe pero dentro de un loop cognitivo/emocional/social mayor.
- **Reflexive (exogenous) attention**: atención guiada por eventos externos (Mayer 2004). El cerebro está en alerta a estímulos nuevos: amenazas, objetos brillantes, coloridos, de aparición rápida, sobre todo periféricos (Yantis & Jonides 1990). *Whack-a-Mole* y FPS avanzados la usan como gameplay principal; los jugadores reportan excitación y tensión positiva (Yee 2016b).
- **Juiciness**: feedback rápido, colorido, animado y ruidoso (Gabler 2005, Juul & Begy 2016). Mientras se mantenga el loop "juicy", el jugador sigue alerta, enfocado y aprende a reaccionar rápido.
- **Game feel** (Swink 2009): sensación táctil/kinestésica de manipular un objeto virtual; sensación de control. Placentero por sí mismo.
- **Fitts' Law** (Fitts & Peterson 1964): el tiempo para llegar a un blanco varía inversamente con su tamaño (y es más lento si su posición no se conoce antes). Blancos grandes = fáciles; chicos = más estrés motor. Acertar libera dopamina y norepinefrina ("una más"). Aporta además algo de *ilinx* de Caillois (placer de moverse rápido, preciso y bien, aun solo en los dedos).
- **Juegos deterministas arcade** (ej: *Pac-Man*, fantasmas siempre igual): el jugador aprende un patrón fijo; con práctica se ejecuta por **procedural memory/"muscle memory"** sin cognición significativa, hasta que la velocidad supera su capacidad de respuesta.
- **Endless runners** (*Temple Run*): el loop A/F se acorta y el juego acelera; es divertido hasta que se vuelve injugable. Esa injugabilidad genera el **"just one more try"** (meta-juego del loop exterior): cerebro listo para el siguiente logro, quiero llegar un poco más lejos. El modelo mental mejora a nivel perceptual-motor por repetición.
- Aun juegos con cognición encima usan A/F: acciones con timing preciso (mover, tocar, saltar, disparar) o feedback juicy. **Peggle** ejemplo de recompensa perceptual desmedida: cámara en zoom y slow-motion en el tiro clave, redoble, fuegos artificiales, texto "EXTREME FEVER", coro de *Ode to Joy*, arcoíris y puntaje enorme = refuerzo positivo perceptual y neuroquímico.
- **Moment-to-moment gameplay**: pregunta clave del diseñador: **"¿qué está haciendo el jugador en cada momento que juega?"** y qué feedback recibe, cómo le sirve para su modelo y qué acciones puede tomar. Juegos sin feedback y oportunidades de acción regulares aburren al jugador salvo que tengan otro loop que lo sostenga. El loop A/F es una **"onda portadora"** de los otros tipos.

### 4.2 Cognitive (short-term y long-term)
- Corto plazo = **puzzles / tácticas**; largo plazo = **metas / estrategia**. Ambos requieren **endogenous/executive attention** (pensar para planear). "Corto" y "largo" son relativos (un Sudoku fácil dura segundos; la estrategia, de minutos a horas).
- Clave: racionalidad y **aprendizaje consciente**; incremento de skill y conocimiento (**mastery**). Fuerte motivador para jugadores orientados a logro/progreso (aprender una habilidad libera dopamina). Ej: crucigramas, Sudoku.
- **Cómo crear cognitive interaction**: dar metas planificables y alcanzables, simples al principio (matar este monstruo, construir este edificio, ir a este punto) y que con el modelo crezcan en **pasos (complicadas)** y en **bucles/construcción sobre resultados (complejas)**. Requiere que el jugador pueda predecir resultados a corto y largo plazo.
- **El juego necesita profundidad en su modelo interno** para sostener profundidad en el mental. Sin jerarquía sistémica no hay metas profundas que formar.
  - *Content-driven* (nivel tras nivel): solo pensamiento de corto plazo; algunos lo compensan con personalización de largo plazo (skill trees), pero al agotarse las opciones no queda nada.
  - *Systemic* (ej: dónde construir el castillo por valor defensivo y futuro mercado): soluciones tan variadas como permitan los sistemas, espacio de juego amplio, mejor y más larga permanencia.
- **Blending**: la cognición pura casi no existe. Ajedrez y Go son lo más puro, pero igual se manipulan piezas y se habla de "partida hermosa". **Chunking**: con la experticia la táctica de bajo nivel se agrupa en jerarquías, se vuelve tácita (casi tan poca carga como tomar una piedra) y libera recursos para estrategia; el modelo se vuelve más profundo y jerárquico.
- Combinaciones comunes: sensorial rico + puzzle corto (*Candy Crush*); estrategia con visuales "juicy" no operativos pero que mejoran la experiencia.
- Ejemplo de apilado en un RPG: click (A/F) para atacar → matar monstruo (corto plazo) → subir nivel (largo plazo) → unirse a un gremio (social).

### 4.3 Social
- Implica planificación y atención ejecutiva más un componente reflexivo-emocional (inclusión, exclusión, estatus, estima). Base neuroquímica: serotonina y oxitocina. **Tarda más**: una conversación breve, pero resolver un loop social lleva horas, días o semanas; sentirse parte de una comunidad lleva mucho.
- Puede existir en single-player: *Firewatch* (diálogo por walkie-talkie con Delilah; la relación depende de las elecciones sociales).
- **Game-mediated social interaction**: en multijugador el juego (su modelo interno) media entre jugadores; cada uno tiene su propio loop con el juego y los efectos se propagan a otros. Solo el chat de texto/voz es social directo. Observación del autor (corrió MMOs): muchos jugadores se quedaban por la comunidad aun después de agotar el contenido (juego *content-driven* sostenido por lo social).
- **Técnicas para fomentar interacción social** (cuando los jugadores se necesitan o se benefician mutuamente):
  1. **Social referents** (referentes sociales externos): objetos con los que varios jugadores pueden interactuar (la pelota). Lección de los chats gráficos 3D de los 90, que perdían enganche con solo chatear. Objetos "juguetones" catalizan lo social.
  2. **Competition**: ganadores/perdedores, rankings, leaderboards; FPS y MOBA, ligas profesionales; los equipos agregan efecto grupo propio/ajeno. Fuerte motivador para muchos, **desmotivante para otros** y el que más se desvanece con la edad (Yee 2016a).
  3. **Grouping**: alianzas, gremios, parties, corporaciones; un jugador funda y administra (membresía, privilegios, traspaso de liderazgo). Alternativa ad hoc: *Realm of the Mad God* da XP compartida por cercanía (baja fricción, pero sin estructura de grupo duradera, el vínculo social queda corto). Con estructuras formales (gremios/alianzas como clubes), el engagement social dura mucho más.
  4. **Complementary roles**: nadie puede hacer todo (tanque, DPS, soporte/buff). Los jugadores logran juntos lo que nadie logra solo. Subsume dopamina, serotonina, oxitocina más A/F y cognición corta: mecanismo muy potente de engagement.
  5. **Social reciprocity**: devolver favores (*Game of War: Fire Age*: ayudar a construir/reparar más rápido a un aliado; regalos a la alianza cuando alguien compra, lo que impulsa a replicar). Mismo gameplay "mundano" que otros juegos pero casi 2 millones USD/día de microtransacciones durante meses (cifra del autor): el valor del loop social.
- **Falsos sociales**: *FarmVille* es casi no social (visitas asincrónicas, jugadores "fantasmas en dimensiones paralelas"); no satisface motivaciones sociales reales, solo orgullo de mostrar la granja.

### 4.4 Emotional
- Pasa de atención ejecutiva a reflexiva. Los juegos han explorado sobre todo **emociones primarias/básicas** (Damasio 2003, Ekman 1992): ira, miedo, tensión, sorpresa, logro, deleite; biológicas, rápidas, reflejas, exógenas.
- Emociones más matizadas (temor/dread, culpa, pérdida, anhelo, plenitud, amor, complicidad, gratitud, honor) han empezado a explorarse hace poco; tardan **minutos a horas** en surgir y a veces perduran mucho más.
- Diferencia con libro/película: en el juego hay loop; si siento vergüenza puedo actuar para cambiarlo; si siento ternura puedo sorprenderme de que el juego no lo acompañe.
- **Ejemplos**: *Papers, Please* (decidir destinos ajenos como oficial de migraciones), *This War of Mine* (civiles en guerra), *The Grizzled* (soldados de la 1ª Guerra), decisiones sin respuesta correcta; *Journey* (asombro); *Knights of the Old Republic* (arco romántico interactivo); *Burgle Bros* (golpe cooperativo al borde del desastre); *Fugitive* (tensión "casi se escapa").  La emoción es parte del juego y condiciona decisiones, no un agregado "pegado".
- **No hay teoría consolidada**; modelos citados: Lazzaro (2004), Bura (2008), Cook (2011a). Mucha literatura trata al juego como novela/película (camino único con puntos emocionales predefinidos, sin agencia): evitarlo.
- **Modelo de dos ejes (Russell)**: **valence** (displacer→placer, horizontal) × **arousal** (baja→alta energía, vertical) = 4 cuadrantes: alta energía/feliz; baja energía/feliz; baja energía/infeliz; alta energía/infeliz (≈ humores sanguíneo, flemático, melancólico, colérico). Variantes: circumplex de Russell (1980) y circumplex multicapa de Sellers (2013). Sirve para ubicar emociones objetivo (ira, alegría, miedo, contento, codicia, celos, compasión, deleite, resignación).
- **Emociones = compañeras de las motivaciones** ("cómo nos sentimos sobre lo que queremos o no queremos"). Mapeo con **Maslow** (escala temporal coincide con la de los loops):

| Nivel Maslow | Motivaciones ejemplo | Emociones ejemplo |
|---|---|---|
| Contribution (autorrealización) | Mirar más allá de uno, liderar y servir al grupo | Compasión, unidad, ira justa (wrath), asombro, alegría, desesperación, resignación, humildad |
| Skill and attainment (estima/habilidad) | Habilidad, valor profesional, logro | Victoria, honor, culpa, coraje, plenitud, orgullo, remordimiento, piedad |
| Social (pertenencia) | Amigos, familia, inclusión, grupo, identidad | Simpatía, vergüenza, celos, amistad, odio, desprecio, aceptación |
| Security and objects (seguridad) | Adquisición, preparación, refugio, protección | Deleite, esperanza, envidia, decepción, juguetón, asentado, inestable |
| Physical (fisiológico) | Comida, agua, contacto humano, novedad, evitar dolor/daño | Atracción, placer, asco, ira, miedo, sorpresa, fatiga |

- Uso: elegí las emociones que querés, buscá la motivación que las genera y creá situaciones/sistemas que la sostengan; o al revés, mirá qué motivaciones domina tu juego y predecí las emociones. Motivaciones in-game ≠ motivaciones fuera del juego (cap. 6).
- Ejemplo: personaje bajo oleadas de muertos vivos = motivaciones físicas/seguridad → miedo, asco, sorpresa, esperanza/decepción; no amistad, compasión o venganza, salvo que sumes un componente social (alguien a quien rescatar) o de habilidad (victoria, coraje).
- **Técnicas**:
  1. **Context**: crear atmósfera (colores, luz, ángulos de cámara, música, ambientación) que prepara emociones. Ejemplo: parque de diversiones soleado visto desde arriba vs. de noche en tormenta, luz baja y cámara desde el suelo.
  2. **Situation and goals**: dar metas con significado que el jugador quiera alcanzar, conservar o evitar, ligadas a los niveles de Maslow; poner en riesgo vida, posesiones, amigos, estima o grupo. Lograr/evitar el fin genera emoción (victoria, decepción, soledad, inclusión). **El jugador tiene que importarse de verdad por la meta**; la magnitud de la emoción iguala la importancia asignada.
  3. Recordar el magic circle: las emociones suelen quedar dentro, pero cuanto más "real" se vuelve el juego, más se filtran afuera (como la muerte de un personaje querido).
- **Desafío**: crear sistemas que produzcan la experiencia emocional **sin reducir el juego a un único camino con set pieces lineales**. Compromiso: cut-scenes/contenido lineal = **precisión emocional y fiabilidad** (rol de autor); sistemas emergentes = menos precisión pero experiencia más interactiva, personal y auténtica (rol de diseñador de condiciones).
- **Cautelas**: el jugador puede perderse la oportunidad o no invertir significado (emoción no ocurre); puede reaccionar más fuerte de lo previsto; puede sentir otras motivaciones/emociones que las planeadas; lleva tiempo construir los sistemas y que el jugador los viva y resuelva (horas a semanas). Cuanto más alto en Maslow, más tarda en generarse y resolverse pero más dura.

### 4.5 Cultural
- Escala de años (conversaciones sobre valores, identidad, historia, derechos). Los juegos no duran tanto pero pueden capturar corrientes y generar reflexión sobre temas de toda una vida.
- **Train** (Brenda Romero): peones amarillos en vagones; el destino se revela tarde (campos de concentración nazis); señales sutiles (vidrios rotos bajo el tablero). Reglas con "huecos procedimentales" que obligan al jugador a decidir y ser cómplice; pregunta final: ¿hasta dónde seguimos reglas sin preguntar "¿para qué?". Reacciones: repulsión, llanto, o completar todo, o subvertir.
- Posible solo en juegos: el jugador habita la historia/cultura vía sistemas modelo. **Borra los bordes del magic circle**: la conversación sigue fuera (¿es moral jugar *Train*?).
- Loops culturales extra-juego: fandom, cosplay, foros, crítica. Ej: *Bioshock* y el Objetivismo generó conversaciones. Son un bucle más grande diseñado y desprendido del juego; área naciente.

---
## 5. Flow (sec. "Flow in Interactive Loops")

- **Flow (Csikszentmihalyi 1990)**: "estar en la zona". Parecido a engagement: tarea desafiante con incertidumbre (no memorizada), metas comprensibles, feedback claro, atención enfocada sin estrés, tiempo distorsionado pero consciencia no intrusiva de rendir bien; absorción sin autoconsciencia; la tarea se vuelve significativa por sí misma.
- **Autotelic experience**: mantener el estado de flow pasa a ser una meta en sí.
- **Flow channel (Fig. 4.8)**, ejes challenge (vertical) × skill (horizontal):
  - Poco challenge y poco skill: **apathy**.
  - Reto pequeño acorde a skill de principiante: **interest** → entrada al flow.
  - El canal sube en diagonal a medida que crecen ambos.
  - Reto levemente mayor que el skill: **arousal**; si sigue creciendo: **anxiety** (se cae por la derecha de Yerkes-Dodson).
  - Skill mayor que el reto: **relaxation** → **boredom**.
  - El jugador oscila (sinusoide) entre arousal y relaxation sin salir del canal = zona Goldilocks: engaged, aprendiendo, rindiendo bien.
- **Habituación** impulsa progreso: lo que deleitó antes ya no alcanza → empuja a aprender más y tomar mayores desafíos ("surfear" en el borde superior derecho). Puede caer a relajación sin romper el flow gracias al apilado de ciclos.
- **Autotelic goals**: cuando el jugador progresó lo bastante, empieza a fijarse metas propias y ya no necesita presión externa. No todos los juegos lo necesitan (*Tetris*, match-3 logran flow con A/F y cognición corta). Los modelos internos lo bastante profundos para metas autotélicas son los que se juegan más tiempo y se aman más.

---
## 6. Vista de escalas de tiempo: loops apilados (sec. "A Time-Scale View of Interactive Loops")

- Los loops se apilan en distintas escalas; los rápidos se perciben **menos significativos**; la profundidad de significado exige loops largos (social, emocional, cultural).
- Ejemplos: match-3 = A/F + cognitivo corto (y un cognitivo corto recurrente más largo al resolver puzzles), sin estrategia ni emoción/social/cultural. Wargame online = A/F + táctico, estratégico y social.
- **Juegos "ligeros" (rápidos)**: fáciles de agarrar y soltar, menor valor duradero. **"Pesados" (largo plazo, social, emocional, cultural)**: enganchan por más tiempo y fidelizan por años. Dato: en mobile, solo **38%** de los jugadores sigue jugando un mes después de empezar (Dmytryshyn 2014).
- **Halo / Jaime Griesemer — "30 seconds of fun"**: "un loop de 3 segundos dentro de uno de 30 s dentro de uno de 3 minutos que siempre es distinto" → experiencia única cada vez. Loops cortos = momento a momento (dónde pararse, cuándo disparar, cuándo esquivar granada); largos = más tácticos/cognitivos. Apilar loops, construir engagement en cada escala y variar lo que da cada una.

### Core loop (Fig. 4.9)
- Definición operativa: lo que el jugador hace la mayor parte del tiempo. Ciclo: **intención del jugador → acción (input) → cambio interno del juego → feedback al jugador → progresión y recompensa (o call to action) → nueva intención**.
- El juego define cuál tipo de interacción es la principal (casi siempre incluye A/F, pero no siempre es el más significativo): puede ser moverse/saltar/disparar, o solo un medio para construir edificios, descubrir tecnologías, administrar un imperio o construir relaciones. Detalle en cap. 7.

### Cycles of engagement
- Apilar loops de distinta duración crea **ciclos naturales de alta y baja tensión**: desafío/tensión y luego relajación/consolidación. Previene la **attentional fatigue** (el jugador no da abasto y caen engagement y rendimiento).
- Metáfora: olas pequeñas (A/F, siempre presentes) sobre grandes rolling swells (cognitivo largo, social, emocional, cultural) (Fig. 4.10).
- **Rhythm and ritual** (Chelsea Howe 2017): ciclos que marcan paso del tiempo: nuevos contenidos (misiones/recompensas diarias), puntos naturales de inicio/fin de sesión, momentos de batalla o reparación, subida y descarga de tensión en arcos dramáticos, ritmos sociales o celebratorios (estaciones, subir de nivel).

### Narrativa vs. interacción
- **Cook (2012)**: la narrativa forma **arcos, no loops**: entrega "payload de información preprocesada"; no es interactiva, el jugador queda como espectador pasivo durante la narración.
- Narrativa como **bookends** (presenta la misión, se juega, se narra el cierre): puede dar apariencia de narrativa interactiva, pero si el jugador intuye que inicio y fin están fijados, sus decisiones pierden sentido y aparece la futilidad. **"Gilligan's Island problem"**: pase lo que pase se vuelve al punto de partida (limita crecimiento/cambio).
- Encadenar loops con arcos no interactivos puede enganchar pero **baja la rejugabilidad**. Usada con mesura como contexto y andamiaje de juego sistémico, la narrativa acelera el modelo mental del jugador.

---
## 7. Carga mental y presupuesto de interactividad (sec. "Mental Load and the Interactivity Budget")

- **Mental load**: versión ampliada de cognitive load (atencional, perceptual, cognitiva, emocional, social, cultural). Hay un tope de cuántos enemigos, explosiones, conversaciones o partes de puzzle se pueden seguir.
- **Prioridad de atención: lo rápido expulsa a lo lento ("the fast drives out the slow")**. Orden: reflexiva/involuntaria/exógena > ejecutiva > reflexiva-lenta. Si hay que esquivar proyectiles o vigilar la periferia, se suprimen la táctica, la estrategia y la reflexión emocional. Excepción: concentración ejecutiva tan intensa que se ignoran señales del entorno.
- **Quantic Foundry** (casi 300.000 jugadores encuestados): eje *excitement* (acción rápida, sorpresa, emoción) vs. eje *strategy* (pensar por adelantado, decisiones complejas).
  - Arriba-izquierda (alta excitación, baja estrategia): *Counter-Strike*, *League of Legends*. Abajo-derecha (baja excitación, alta estrategia): *Europa Universalis*.
  - **La esquina superior derecha está vacía**: ningún juego alto en ambos; sería demasiada carga mental. Hay un **umbral cognitivo** (Fig. 4.11).
  - Mientras más lejos sobre cualquier eje, más "hardcore" (más recursos para aprender y modelar); la esquina inferior izquierda = "casual", **"easy fun"**. Bandas: **easy fun, balanced fun, hard fun** (Fig. 4.12). Dentro de cada banda el género varía pero la dificultad relativa de aprender y tener éxito es parecida.

### Interactivity budget
- Cuánta carga mental total está dispuesto a gastar un jugador en un momento dado, y qué tipos de interacción gasta. Jugadores dispuestos van a juegos más a lo largo de los ejes o a mucha interacción emocional (*Gone Home*, *Papers, Please*); quien quiere algo liviano, a *Candy Crush* (poco cognitivo corto + A/F suave y juicy). Menos requisitos = más casual, se entra y sale a gusto.
- **Los loops cortos (reflexivos) consumen primero el presupuesto**: A/F puede ahogar al cognitivo corto, que ahoga al largo, etc.
- **Reglas de diseño derivadas**:
  1. Juego de alta acción (A/F + cognitivo corto): no pidas a la vez cognitivo largo, emocional o social. Si los incluís, **separalos en el tiempo** del tramo rápido.
     - RPGs: personalización de largo plazo **entre** tramos tácticos de misiones y combates.
     - *League of Legends*: social en el lobby, separado de partidas de alta intensidad.
  2. Juego pensante/largo: evitá mucho A/F o cognitivo corto bajo presión. Ej: *Stellaris* (estrategia galáctica; las batallas no las dirige el jugador, se pueden mirar sin esfuerzo; visual atractivo sin presión temporal).
  3. Juego de impacto emocional (*Papers, Please*, *Train*): presentación austera y poco A/F, poco cognitivo corto/largo para dejar energía a lo emocional.
- Estado de la ciencia: **no sabemos medir** el presupuesto ni cuánto feedback sensorial hace falta para sostener atención, salvo encuestas; es práctica y exploración futura.

---
## 8. Reconocer, definir y crear "diversión" (sec. "Recognizing, Defining, and Creating 'Fun'")

### Intentos previos de definir
- Caillois & Barash: *agon, alea, ilinx, mimicry*. Koster (2004): "fun is just another word for learning". Otros proponen 8 (Hunicke et al. 2004), 14 (Garneau 2001) o hasta 21 (Winter 2010) tipos de diversión.

### Características de la diversión (sec. "Characteristics of Fun")
- Experiencia agradable/emocionalmente positiva con **duración** (más que una descarga rápida) y que se querría repetir. Schaufeli: "estado afectivo-cognitivo generalizado".
- **Voluntaria y típicamente sin consecuencias** (magic circle). Si se quita la posibilidad de abandonar, desaparece la diversión.
- Atractiva (no se evita ni es meramente informativa), **valencia positiva**, aunque la superficie sea triste o aterradora (película dramática, casa embrujada) si es voluntaria y sin consecuencia real.
- Muchos sabores: sensorial (fuegos artificiales, vértigo/ilinx), neuroquímico, recompensa material, inclusión social, logro, completitud (completar sets).
- **Puede incluir aprendizaje pero no lo exige**; puede ser puramente sensorial o emocional; no requiere racionalidad (pero puzzles mentales pueden dar victoria "astuta").
- Implica **satisfacción y sensación de equilibrio**: demasiado aburrido, estresante, caótico o arbitrario deja de ser divertido. Fun y flow están profundamente relacionados.

### Definición (sec. "Defining Fun")
- No hay una definición única, pero hay regularidades. Consistente con los tipos de engagement.
- **Voluntario primero**: si la participación se fuerza (coerción, adicción, pérdida de agencia), se va la diversión. Con consecuencia real de pérdida, también (salvo apuesta: ahí el riesgo voluntario y la anticipación de recompensa/dopamina mantienen el "fun").
- Por tipo: sensorial/físico (ilinx, montaña rusa, espectáculo de luces); cognitivo (puzzles a estrategias, aprendizaje: construir un modelo mental puede ser divertido; ojo con el aprendizaje de memoria o bajo demasiado estrés, no es divertido); social y emocional (bailes, juegos de fiesta, conversación); cultural (museos para algunos).
- Todo debe estar dentro del **presupuesto de interactividad subjetivo**, que varía por persona y momento; si está fuera del canal de flow, no es divertido en ese momento.

**Resumen formal (cuatro atributos de la diversión):**
1. Voluntaria y (típicamente) sin consecuencias.
2. Valencia emocional positiva (a veces bajo una superficie negativa) y con cierta duración, no un "jolt".
3. Elementos de uno o más compromisos: sensorial, cognitivo, social, emocional, cultural.
4. Calza con el nivel actual de deseo de interactividad (interactivity budget), que varía por persona y momento.

- Frase clave: **no todo lo engaging es divertido, pero toda experiencia divertida es engaging.**

### Definición operativa para diseño: un juego exitoso necesita ser
1. Una actividad **voluntaria** que el jugador elige por sí mismo.
2. **Perceptualmente atractivo**, con call to action obvio que inicie los loops.
3. **Interactivamente engaging** en una o más formas de este capítulo: oportunidades de decisión del jugador en un amplio play-space, que invite a "vigor, dedicación y absorción".
4. **No demasiado exigente** para su capacidad mental/presupuesto de interactividad.

- No se "diseñan" estas cualidades y se tildan: son **emergentes** del conjunto.
- **Preguntas que el diseñador debe repetir** durante diseño, construcción y test: ¿Estoy sumando o restando a estas cualidades con cada decisión? ¿El diseño da suficientes oportunidades de engagement, incluyendo decisiones significativas? ¿Lo hace sin desbordar el presupuesto mental?

### ¿Los juegos tienen que ser divertidos?
- No estrictamente. Un juego puede usar su naturaleza atractiva/interactiva de modo "subversivo" (*Train*) para llevar a experiencias valiosas que no se buscarían.
- Birk et al. (2015): los juegos producen todo el rango emocional. Juegos construidos sobre **frustración** enorme: *Super Meat Boy*, *Dark Souls*, *Dwarf Fortress*; con contextos emocionales negativos: *The Last of Us*, *That Dragon, Cancer*. Siguen siendo voluntarios, engaging y compelling aunque no sean "divertidos".
- Conclusión: la mayoría son divertidos, pero no necesariamente; deben ser **muy interactivos y engaging**.

### Profundidad y elegancia revisitadas
- **Systemic depth**: jerarquía de sistemas dentro de sistemas; si el jugador puede subir y bajar entre niveles e interactuar en cada uno, aumenta el engagement y aparece un "asombro cognitivo" (como fractales/sistemas autosimilares).
- **Elegance**: profundidad sin excepciones ni casos especiales que rompan la simetría; cumple Bushnell's Law (reutilizar estructuras aprendidas en una zona al abordar otra, sin colapsar el play-space).
- Reglas con excepciones o dos sistemas que operan de modo contradictorio **consumen el presupuesto de interactividad** y reducen engagement: el jugador trabaja más para llegar al punto de preocuparse menos por *cómo* jugar y simplemente disfrutar. Menos reglas, **menos excepciones**, espacio de juego grande y muchos niveles de organización = más elegante, enganchante y disfrutable.

---
## 9. Checklist de diagnóstico y diseño (síntesis de las heurísticas del capítulo)

**Señales de que un juego no engancha (y causa probable):**
- Nadie entiende qué hacer al empezar → falta affordance/call to action (controles no visibles, pantalla ilegible). [Arousal bajo/aburrimiento]
- Pantalla con demasiado ruido visual o demasiadas cosas a la vez → sobrecarga, ansiedad (derecha de Yerkes-Dodson). 
- El jugador necesita leer texto/números para interpretar resultados → semantic distance alta.
- Entradas poco directas o con muchos modos/excepciones → articulatory distance y reglas con excepciones comen presupuesto.
- Feedback tarde (> ~250 ms) o inexistente → pierde la asociación acción-resultado; sensación de lag.
- Todo el contenido visto y los sistemas agotados → nada nuevo que aprender; falta profundidad sistémica/metas autotélicas (content-driven vs. systemic).
- Recompensas esperadas y repetidas → habituación; necesita novedad, nuevas formas de engagement.
- Tensión continua sin descanso → fatiga atencional; faltan ciclos de tensión/relajación.
- Pedirle a la vez reflejos + estrategia profunda + emoción/social → rompe el interactivity budget ("lo rápido expulsa a lo lento").
- Inicio y fin preestablecidos con decisiones que no cambian nada → "Gilligan's Island problem", sentido de futilidad.
- Juego "social" sin necesidad mutua real (asincrónico, sin referentes ni roles) → no satisface lo social (FarmVille).
- Dificultad desalineada con el skill → fuera del flow channel (aburrimiento o ansiedad).

**Qué mirar al diseñar un loop o feature:**
1. ¿Qué hace el jugador cada momento (moment-to-moment)? ¿Qué feedback recibe y qué acciones puede tomar?
2. ¿En qué escalas hay loops (3 s / 30 s / 3 min / sesión / meta / social / emocional)? ¿Cada una aporta algo distinto (Halo)?
3. ¿Qué loop(s) son el core loop? ¿Cuál consume el presupuesto de interactividad?
4. ¿Hay ciclos de alta/baja tensión? ¿Ritmo y ritual?
5. ¿El jugador puede formar intenciones válidas, con información, predecibles y a tiempo?
6. ¿Facilito aprender (pocas reglas, sin excepciones) y dejo profundidad para dominar (Bushnell)?
7. ¿Qué emociones quiero y qué motivación (Maslow) las genera? ¿El jugador se importa de verdad?
8. ¿Qué es voluntario? ¿Qué consecuencia real puede matar la diversión?
9. ¿El call to action tiene affordance y motivación?
10. ¿Hay estado oculto útil para que el jugador infiera y haga predicciones (caja negra)?
11. ¿El feedback es juicy y con buen game feel cuando el loop principal es A/F? ¿El blanco/tolerancia respeta Fitts?
12. Medición: el autor reconoce que el presupuesto de interactividad se mide hoy sólo por encuesta; usar playtest, no fórmula.

**Números del capítulo:** <100 ms = instantáneo; <=250 ms máximo para sentir conexión inmediata (Card et al. 1983); A/F: <1 s a 2-3 s; Halo: loops de 3 s / 30 s / 3 min; mobile: 38% retiene al mes; Quantic Foundry: ~300.000 encuestados; Game of War: ~2 M USD/día en microtransacciones; tipos de diversión: 8 / 14 / 21 según autor; emociones: 2 ejes = 4 cuadrantes; Maslow: 5 niveles; loops: 6 tipos.
