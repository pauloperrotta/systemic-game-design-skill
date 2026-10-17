# Modelo sistémico del juego, visión y análisis (caps. 3, 5 y 6)

Leer para ANALIZAR un juego existente (checklist de 7 pasos todo → loops → partes), para entender el modelo sistémico de un juego (tokens y reglas, decisiones significativas, fuentes de oposición, tipos de metas, contenido vs sistemas, tema), las cinco cualidades de un buen sistema, y para trabajar la experiencia deseada y el documento de concepto (fantasía, key moments, One Question, público y motivaciones).

Resumen parafraseado de Sellers, *Advanced Game Design: A Systems Approach* (2018). Entre corchetes va la sección del libro de donde sale cada bloque.

## Índice
- 3. CAP. 3 - Fundamentos de juegos y diseño de juegos
- 4. CHECKLISTS DE DISEÑO / ANÁLISIS / BALANCE DERIVADAS
- 5. GLOSARIO RÁPIDO (inglés -> idea)
- CAPÍTULO 5 — Trabajar como diseñador sistémico
- 1. Cómo empezar ("How Do You Even Start?")
- 2. Conocé tus fortalezas, trabajá tus debilidades ("Know Your Strengths, Work to Your Weaknesses")
- 3. Cualidades de los sistemas de juego ("Qualities of Game Systems", Achterman 2011)
- 4. Juegos de mesa vs. digitales ("Tabletop and Digital Games")
- 5. Proceso de diseñar juegos como sistemas ("The Process of Designing Games as Systems")
- 6. MÉTODO: analizar juegos desde la visión sistémica ("Analyzing Games from a Systems View")
- 7. Prototipado y playtesting ("Prototyping and Playtesting")
- 8. Resumen del cap. 5
- CAPÍTULO 6 — Diseñar la experiencia total
- 9. La gran idea ("What's the Big Idea?")
- 10. La experiencia deseada ("The Desired Experience")
- 11. El documento de concepto ("The Concept Document")
- 12. Diseñar el sistema juego+jugador ("Designing the Game+Player System")
- 13. Preguntas a considerar sobre la visión de diseño ("Questions to Consider About Your Design Vision")
- 14. Resumen del cap. 6
- APÉNDICE: Listas de uso rápido (para diseñar / analizar / balancear)
- A. Checklist de diseño por niveles
- B. Señales de problema (detección)
- C. Ejemplos de juegos citados (una línea cada uno)
- D. Términos clave (EN) para búsqueda rápida

---

## 3. CAP. 3 - Fundamentos de juegos y diseño de juegos

### 3.1 Definiciones de "juego" [What's a Game?]
| Autor | Idea clave |
|---|---|
| Huizinga (Homo Ludens, 1938) | Jugar es absorbente, "no serio", fuera de la vida ordinaria, sin interés material, en límites propios de tiempo/espacio con reglas fijas -> **círculo mágico (magic circle)**. |
| Caillois (Man, Play, and Games, 1961) | Separado de la realidad, no obligatorio ni rentable, regido por reglas internas, con **incertidumbre** (el curso depende de elecciones). **Cuatro tipos:** **agon** (competencia), **alea** (azar), **mimicry** (juego de rol), **ilinx** (alteración de la percepción/vértigo). Espectro **ludus** (reglado, tipo deporte) <-> **paidia** (juego espontáneo, infantil). |
| Crawford (1984) | Cuatro factores: **representación, interacción, conflicto, seguridad**. Juego = sistema formal cerrado que representa subjetivamente un subconjunto de la realidad; reglas explícitas; el jugador "crea su historia" eligiendo; metas y obstáculos; conflicto y peligro sin consecuencias físicas. |
| Dewey | El juego conserva "libertad de subordinación a un fin impuesto por necesidad externa"; si se ata demasiado a una necesidad externa deja de vivirse como juego. |
| Sid Meier | "Una serie de elecciones interesantes" (útil por exigir decisiones significativas e informadas; ojo: educación o relaciones también lo son y no son juegos). |
| Costikyan (1994) | Forma de arte en que los participantes toman **decisiones para gestionar recursos mediante fichas (tokens) en pos de una meta**. No es puzzle (estático), ni juguete (sin meta), ni historia (lineal); el arte es pasivo, el juego exige participación activa. |
| McGonigal (2011) | Cuatro rasgos: **meta, reglas, sistema de feedback, participación voluntaria**. |
| Salen & Zimmerman (2003) | "Sistema en el que los jugadores participan en un conflicto artificial, definido por reglas, que da un resultado cuantificable." |
| Juul | Componente: **valorización del resultado** (algunos resultados son mejores que otros, codificado en reglas). |
| Wittgenstein | No busques una definición común a todos los juegos: hay una "red de parecidos" que se superponen (family resemblance). |

Elementos comunes (Summing Up Game Definitions):
- Experiencia en contexto propio, separado del resto (círculo mágico).
- Reglas propias (formales = ludus; tácitas/dinámicas = paidia).
- Interacción voluntaria y participativa (no solo observar).
- Metas, elecciones y conflicto significativos.
- Termina con un resultado reconocible (valorizado).
- Como producto de diseño: partes concretas implementadas en alguna tecnología, loops por interacción de comportamientos, y todos experienciales (dinámicos/dramáticos) al jugarlo con el jugador.
- Excepciones: póker por dinero real (círculo poroso); MMOs sin fin; no todos tienen conflicto. Son características típicas, no prescriptivas.

### 3.2 Frameworks de juegos [Game Frameworks]
**MDA (Mechanics-Dynamics-Aesthetics, Hunicke et al. 2004):**
- **Mechanics:** componentes del juego a nivel de datos y algoritmos.
- **Dynamics:** comportamiento en tiempo de ejecución de las mecánicas actuando sobre inputs y outputs mutuos en el tiempo.
- **Aesthetics:** respuestas emocionales deseadas en el jugador.
- Lectura: el **jugador** ve primero estética -> dinámica -> mecánica; el **diseñador** ve mecánica -> dinámica -> estética. Se busca que el diseñador piense primero en estética (en la práctica cada diseñador empieza por donde quiere).
- Punto clave: **solo las mecánicas están bajo control directo del diseñador**; las dinámicas se preparan indirectamente (esto anticipa el diseño de segundo orden).
- Críticas: "mechanics" se usa de forma elástica (desde "saltar"/"jugar carta" hasta loops como el blue shell: cuestión de "tamaño de chunk"); "aesthetics" se confunde con lo visual y distrae hacia el look & feel en vez de la experiencia total.

**FBS (Function-Behavior-Structure, Gero 1990):** Función (propósito/por qué se diseñó), Comportamiento (atributos y acciones derivadas de la estructura que logran la función; puede cambiar en el tiempo), Estructura (partes físicas y relaciones; topología/geometría/material; no cambia). **SBF** (Goel et al.) lo invierte, bottom-up: componentes y acciones -> estados y transiciones -> esquemas funcionales. Puente entre MDA y la visión sistémica; poco usado en juegos.
- Mensaje del autor: otros frameworks ad hoc son válidos si te sirven; el enfoque sistémico los complementa.

### 3.3 Modelo sistémico de juegos [A Systemic Model of Games] - EL MODELO CENTRAL
Descriptivo, no prescriptivo; "andamio, no camisa de fuerza".

**Nivel superior:** el juego-tal-como-se-juega = sistema **game + player(s)**, dos subsistemas (Fig. 3.1). Sin jugador humano el juego no tiene utilidad ni gameplay.

Tres niveles de componentes del subsistema juego (mapean directo a partes -> loops -> todo):
1. **Estructurales (Parts):** **tokens y reglas** = "sustantivos y verbos".
2. **Funcionales (Loops):** "frases" armadas con sustantivos y verbos; lo que se llama "los sistemas del juego"; modelo interno de la realidad, espacio de juego, incertidumbre, modelo mental, decisiones significativas, oposición, metas.
3. **Arquitectónicos y temáticos (Whole):** caras interna (desarrolladores) y externa (jugador) del mismo todo.

Gameplay = propósito y acción global del juego, comunicado como efecto emergente de los cuatro tipos de elementos (estructural, funcional, arquitectónico, temático).

**Jugador como parte del sistema mayor:** puede tener avatar explícito, avatar agregado (barco con capitán, tripulación, cañones) o ser invisible ("mano invisible" de una aldea/imperio). Punto: ambos (jugador y juego) se modelan mutuamente: el juego representa al jugador en su modelo; el jugador construye un modelo mental del juego (co-representación).

### 3.4 Partes estructurales: tokens [Structural Parts of a Game / Tokens]
- Tokens = objetos representativos que denotan aspectos del estado del juego; no tienen significado por sí mismos fuera del juego; comunican estado y cambios entre juego y jugador.
- Grados de representación: muy conceptuales (piedras de Go), semirrepresentativos (piezas de ajedrez de nobleza), detallados (armas/armaduras de RPG).
- Ningún juego representa el mundo completo: "un mapa a escala 1:1 no sirve"; la verosimilitud total saca del círculo mágico.
- Los tokens son los **sustantivos**: (1) representación del jugador; (2) unidades independientes que actúan solas o las usa el jugador; (3) el mundo (divisiones con estado: casillas del ajedrez, terreno); (4) recursos (dinero en Monopoly; trigo, oveja y madera en Catan); (5) objetos no materiales (el **turno**, cuántas cartas en mano, cuántos ítems se llevan, cuántos dados).
- **Regla:** todo lo que tiene estado y comportamiento en el juego debe estar representado por un token o agregado de tokens.
- Los tokens son simbólicos pero **precisos**: estado y comportamiento definidos siempre (la pieza está en una y solo una casilla). Cada concepto (¿vuela?, ¿hay montañas?) debe especificarse en tokens y reglas.

### 3.5 Partes estructurales: reglas [Rules]
- Reglas = especificación de procesos; **los verbos**: definen el comportamiento de los tokens.
- Funciones de las reglas (lista del autor):
  1. **Especificar acciones aceptables dentro del juego:** crean el espacio lúdico donde se actúa distinto (mentir en The Resistance, robar en EVE Online); aceptamos no ser eficientes (no agarrar el rey en ajedrez, no revisar el mazo).
  2. **Especificar cómo funciona el mundo:** estados permitidos, cómo cambian, cómo se progresa, obstáculos, resolución de conflictos, finales (ganar/perder), topología (cuadrícula, esfera, mundos imposibles como Monument Valley, Antichamber), estructura de piezas (cartas en mano, trabajadores iniciales), reglas universales ("caída infinita sin daño", "la gravedad cambia cada 30 s").
  3. **Preservar la agencia del jugador (player agency):** las reglas deben permitir distintos caminos/metas/estilos; si restringen demasiado, el espacio de decisión colapsa a pocas opciones o una y el jugador pasa de participante a observador.
- **Heurística de cantidad de reglas:** el mínimo de reglas que defina bien el espacio del juego. Pocas -> ambiguo, el jugador no puede construir/navegar un modelo mental. Demasiadas -> agencia constreñida, el compromiso se evapora.
- **Evitar excepciones a las reglas:** reglas arbitrarias o con excepciones sobrecargan el modelo mental (opuesto a la elegancia). Ejemplos: dado de 6 que normalmente es "buen resultado" salvo casos donde es malo; en digital, un click = saltar y doble click = tirar todo lo que llevás (acciones cognitiva y físicamente parecidas deberían tener resultados parecidos).
- **Mecánicas (game mechanics):** combinaciones **semánticamente viables** de tokens y reglas (frases cortas: "al pasar por Salida cobrás $200"); las complejas son combinaciones de simples. No se pretende definición precisa; el autor las ancla en términos sistémicos.

### 3.6 Juegos y metajuegos [Games and Metagames]
- El círculo mágico está definido por tokens y reglas; en general lo que pasa en una partida no pasa a la siguiente (Monopoly).
- **Metajuego (metagaming):** aplicar tokens o reglas a través de partidas: reglas de la casa (Free Parking), ventajas para novatos, juegos **legacy** (los hechos de una partida alteran la siguiente), tit-for-tat basado en partidas anteriores. Atraviesa el círculo mágico.
- Teoría de juegos (game theory) casi no tiene que ver con diseño; es economía/matemática. Los **juegos repetidos** (ej.: piedra-papel-tijera repetido) sí muestran que el metajuego puede quedar subsumido en el juego.

### 3.7 Aspectos funcionales [Functional Aspects of a Game]
- Son los ensamblajes con loops (economías, personajes, imperios). Criterio: cualquier cosa que complete la frase **"en este juego, el jugador es un..."** (pirata, piloto, florista, emperador) o que sea parte importante de lograr una meta.
- Todo debe reducirse a tokens y reglas, pero el diseñador pasa mucho tiempo organizando partes en **subsistemas operativos** que soportan la experiencia.
- **Crear posibilidades de juego:** economía/personaje/imperio no están codificados directamente, sino sus *posibilidades*; el juego debe ofrecer andamiaje para que esas estructuras emerjan y cambien durante el juego.
- **"Máquinas" anidadas (Ellenor):** un componente funcional es "una máquina que hace X" (clima, un mail al completar misión); máquinas simples dentro de otras más complejas, jerárquicamente hasta tokens y reglas; evita máquinas monolíticas.

**Modelo interno de realidad (internal model of reality):**
- Cada juego es un "universo de bolsillo" con leyes propias; abstracto (Ajedrez/Go) o detallado (RPG/estrategia). Koster: los juegos son abstractos e icónicos y excluyen detalles distractores.
- **Significado endógeno (endogenous meaning, Costikyan):** tokens y reglas significan algo solo por su función dentro del juego ($1.000 de Monopoly).
- **Advertencia:** más realismo/complejidad no hace mejor juego. Si el modelo es tan complejo, variable o impredecible que el jugador no puede formarse un modelo mental efectivo, es una simulación interesante pero no un juego divertido.

**Segundo orden de diseño (second-order design, Salen & Zimmerman):** dos significados:
1. Los tokens y reglas especifican un **espacio de estados (state-space)** con muchos caminos, no un camino único (primer orden = una experiencia igual para todos). Un solo camino = narración (libro/película); el jugador queda pasivo. El jugador sabe que había otros caminos aunque no todos sean igual de buenos.
2. Diseñar tokens y reglas para formar sistemas dinámicos es **habilitar emergencia**: las mecánicas se diseñan directamente; las dinámicas surgen al jugar. La experiencia del jugador no es mapeable a una parte o suma de partes, y puede ser impredecible para el diseñador.

**Dwarf Fortress - las muertes de gatos:** gatos mueren intoxicados: cazan ratas en la taberna, el vino derramado por enanos se les pega, se auto-limpian (solo gatos y pandas rojos), el efecto del alcohol escala según el tamaño del cuerpo -> mueren. Nadie lo diseñó; emerge de varios sistemas (beber, salpicar, tamaño, autolimpieza). Ilustra juego procedural, juego sistémico extremo y emergencia no planificada (y de paso que los sistemas interactúan sin que el diseñador lo prevea: hay que testear, no solo especificar).

**Incertidumbre y azar:** todo juego presenta incertidumbre; no todos usan aleatoriedad. Ajedrez/Go: la incertidumbre viene de no saber qué hará el otro. La mayoría tiene aleatoriedad, vista como contrapeso a la habilidad desarrollada. Tipos de aleatoriedad: uniforme (1-100 igual probabilidad) o ponderada (campana).
- **Regla:** cuanto más determinista el mundo, más se conoce de antemano; cuanto más se conoce, más colapsa el espacio a un solo camino y el jugador pierde decisiones. Ej.: aperturas memorizadas de ajedrez; el juego sigue interesante porque los jugadores recombinan "chunks" (subsistemas de piezas y posiciones) de formas nuevas.

**Modelo mental del jugador (player's mental model):**
- El jugador lo construye interactuando con tokens, reglas y elementos funcionales. No es parte del juego, pero el juego debe soportar su construcción.
- Más fácil de construir y más consistente con el modelo del diseñador -> más enganche. Reglas incompletas o inconsistentes -> el juego falla o exige muchos recursos cognitivos (limita la audiencia).
- "Fácil de construir" no es "simple": Tic-Tac-Toe tiene modelo simple pero cansa rápido (sin azar, profundidad sistémica, ni incertidumbre mutua). Go o Stellaris requieren esfuerzo, pero al ser sistémicos tienen pocas inconsistencias y recompensan con más capacidad cuando el modelo crece = **loop de refuerzo de exploración** (aprender -> poder -> más exploración).

### 3.8 Decisiones significativas, oposición y metas

**Decisiones significativas (meaningful decisions):**
- Requieren **incertidumbre** (en el modelo mental del jugador y normalmente en el mundo). Sin ella no hay decisión.
- Tres situaciones: **sin decisiones** (jugador pasivo, la experiencia de juego colapsa), **decisiones ineficaces/ilusorias** (dos puertas que llevan al mismo lugar = equivale a no elegir), y **decisiones que llevan a cambio**.
- Definición práctica: una decisión es significativa si afecta el estado del jugador o del mundo de forma discernible y **abre o cierra** oportunidades de exploración y decisiones posteriores. Para el jugador: si cree que el resultado lo acerca o aleja de lo que desea.

**Oposición y conflicto (opposition and conflict):** sin oposición se logra el objetivo sin esfuerzo (levantar el rey y decir "gané"). Cuatro fuentes de oposición:
1. **Las reglas** (límites de movimiento, de acciones por recursos, terreno infranqueable). Deben sentirse como parte natural del mundo; cuanto más arbitrarias, más piensa el jugador en cómo jugar en vez de jugar.
2. **Oponentes activos** (agentes con agencia: desde goblins anónimos hasta un némesis elaborado).
3. **Otros jugadores** (directa o indirectamente: ganar, puntaje).
4. **El propio jugador** (recursos limitados: tropas ahora vs mejorar cuarteles para después; trade-offs porque no se puede todo a la vez).

**Metas del jugador (player goals):** sin meta ninguna elección es mejor que otra: no hay intención ni significado; el jugador "deriva".
- **Explícitas (explicit goals):** provistas por el diseñador (ganar, "terminá el nivel"); responden a "¿cómo se gana?". Sirven como "ruedas de entrenamiento" (training wheels) para armar el modelo mental.
- **Implícitas (implicit goals):** creadas por el jugador cuando su modelo mental es suficiente ("terminar sin matar a nadie"). Combinables con logros opcionales (ej.: "pacifista") que incentivan metas propias y mejoran retención.
- **Juegos solo con metas explícitas:** menor longevidad y rejugabilidad; circunscriben las metas posibles; reducen espacio de estados, decisiones y compromiso (queda la ilusión de agencia hasta que se la ve).
- Las metas surgen del significado endógeno + modelo mental; sin ellos el jugador vaga.

**Tipos de metas (por duración/frecuencia y motivación):**
1. **Instantáneas (instant):** acciones de timing inmediato (saltar justo, tomar la soga, bloquear un tiro).
2. **Corto plazo (short term):** puzzle, matar un monstruo, usar una táctica, subir de nivel; cognitivas, incluyen varias instantáneas.
3. **Largo plazo (long term):** estratégicas (derrotar a un oponente fuerte, set completo, árbol de habilidades, imperio); columna vertebral del compromiso a largo plazo; contienen metas de corto plazo, que contienen instantáneas. Esa **jerarquía de metas** debería ser evidente y es fuente de satisfacción.
4. **Sociales (social):** relaciones con otros jugadores (inclusión, estatus, cooperación, competencia); se filtran fuera del juego (círculo poroso).
5. **Emocionales (emotional):** el diseñador suele no pensarlas explícitamente pero "deberían estar entre las primeras que se consideran"; resolución emocional (Gone Home, Road Not Taken, Undertale); son más importantes para el disfrute que las cognitivas aunque el jugador no las piense conscientemente.

### 3.9 Arquitectura y tema [Architecture and Thematic Elements]
Arquitectura y tema = dos caras del mismo todo: **arquitectura = hacia adentro (developers)**, **tema = hacia afuera (jugador)**.

Elementos **arquitectónicos:**
- Balance de contenido y sistemas.
- Componentes mecánicos/técnicos de la estructura narrativa.
- Organización de la interfaz (UX, lado técnico de cómo interactúa el jugador).
- Plataforma tecnológica (digital o de mesa).

Elementos **temáticos:**
- Cómo contenido y sistemas soportan la interactividad y metas del jugador, en particular las **autotélicas**.
- Contenido narrativo (si hay).
- Apariencia y sensación de la interfaz ("juiciness"): placer de verla/operarla en sí.

**Contenido vs sistemas [Content and Systems]:** todos los juegos tienen ambos; la pregunta es de cuál depende el gameplay principalmente. (Complicado = secuencia sin loops; complejo = loops.)

**Juegos dirigidos por contenido (content-driven games):**
- Contenido = ubicaciones, objetos y eventos que el diseñador desarrolla y ensambla (niveles/misiones con colocación y timing exactos).
- Juego lineal; metas explícitas, oposición clara en el camino, decisiones predeterminadas en oportunidad y resultado. Rejugar no cambia lo esencial (solo metas implícitas tipo "mejor tiempo").
- **Poca emergencia**: los diseñadores la evitan porque es impredecible, no testeable y riesgosa.
- **Content treadmill (cinta del contenido):** los jugadores consumen contenido más rápido de lo que se crea; cada pieza nueva es más cara; equipos enormes; riesgo de poca innovación. Pro: desarrollo más predecible.
- Si el contenido nuevo no cambia tokens/reglas (partes, estados, comportamientos posibles), el jugador nota que no hay nada nuevo que aprender o dominar y se aburre. Ejemplo: **reskins** (cambiar contexto/arte de medieval a sci-fi) entusiasman al principio y agotan rápido.

**Juegos sistémicos (systemic games):**
- Usan interacciones complejas (loops) entre partes para crear mundo, oposición, decisiones y metas; el diseñador no autora la experiencia sino las condiciones; el camino cambia en cada partida -> frescura y rejugabilidad.
- Ejemplo Daniel Cook, Steambirds: Survival: cuando no era enganchante agregaron **sistemas** (aviones derribados sueltan power-ups) en vez de escenarios con triggers: "¿voy por el heal o giro hacia el Dart a las 6?" es una decisión significativa impulsada por sistemas, no una "emoción barata autorada".
- Aunque haya meta explícita global (Civilization: conquistar el mundo; FTL: destruir la nave nodriza), el jugador crea su ruta; la incertidumbre y las combinaciones evitan que el espacio colapse en un camino óptimo único. No es todo aleatorio: es sistémico (desierto con cactus al azar, pero sin osos polares).
- **Balance:** no son excluyentes; juegos sistémicos necesitan algo de contenido y metas explícitas; los lineales tienen subsistemas (economía, combate) en un contexto lineal. El libro apuesta por diseñar juegos sistémicos usando elementos lineales cuando convenga. Tendencia: juegos cada vez más *complejos* y no solo más *complicados*.

**Experiencia autotélica (autotelic experience):** experiencia con propósito en sí misma, no dependiente de una meta o necesidad externa. El jugador crea metas implícitas por motivación propia y las acciones tienen valor intrínseco.
- El juego es separado, no consecuente y voluntario pero tiene que ser satisfactorio en sí mismo (Dewey).
- **"Gamification" fracasa** cuando la experiencia se subordina a un fin externo: parece juego pero no lo es.
- Metas explícitas sirven para aprender; encadenarlas indefinidamente produce **"the grind"** (misión tras misión por recompensa externa, como un trabajo; además depende de contenido caro y efímero y no de sistemas "evergreen").
- Juegos longevos (Ajedrez, Go, Civilization) permiten metas implícitas intrínsecas; el soporte son los elementos temáticos y sistémicos.

**Narrativa [Narrative]:** relato de individuos que viven una serie de eventos conectados con significado; ambos (eventos e individuos) importan. Puente entre arquitectura (cómo se arma desde lo funcional) y tema (cómo informa al jugador de qué trata).
- Puede ser el foco o solo la **premisa** (por qué el mundo es así y cuáles son las metas). También sirve como recompensa (cut-scenes expositivas).
- **Juegos story-driven:** más cuidado con contenido que con sistemas; oposición, metas y puntos de decisión definidos por el diseñador; poco rejugables. **Tensión central:** dirigir hacia la historia (estrecha el espacio hasta un camino único; jugador pasivo) vs. dejar libre (puede perderse la historia y el contenido caro, y no comunicar el tema).
- Ejemplo: Knights of the Old Republic (lado luminoso/oscuro; pocos finales porque múltiples finales son muy caros -> estrechamiento de caminos).
- **Juego sistémico con premisa:** el diseñador fija formas de oposición; las decisiones del jugador y el azar determinan cuándo/cómo se enfrentan; Terraria (premisa mínima), Pirates! de Sid Meier (narrativa básica, metas opcionales). La narrativa no está escrita, se vive.

**Tema, experiencia y significado [Theme, Experience, and Meaning]:**
- Tema = de qué trata el juego; lado del jugador del todo; contexto para su modelo mental, decisiones y metas. El jugador interpreta tokens y reglas a la luz del tema.
- Si todo (estructura, función, arquitectura, tema) se combina como sistema, juego + jugador crean **significado** (propiedad del sistema player+game).
- El tema no necesita ser profundo, sí **consistente** con estructura y función y que impulse al jugador (Minecraft: exploración y crafteo abiertos, suficiente).
- Ejemplos de falla:
  - **No Man's Sky:** mundo técnicamente profundo pero sin metas explícitas ni posibilidad de metas implícitas; sin tema -> sin decisiones significativas ni metas intrínsecas -> cae (falta causalidad descendente de diseño y no emerge un tema por causalidad ascendente).
  - **Splendor:** hermoso y de mecánicas atractivas, pero el tema (comerciante de gemas) apenas se conecta con los tokens y reglas abstractos; quien no se enamora de las mecánicas por sí mismas pierde el interés.
- Futuro: juegos con espacio de juego amplio y profundo, con narrativas fuertes que no dirijan demasiado ni dejen al jugador varado en un espacio sin tema.

### 3.10 Evolución del diseño [The Evolution of Game Design] (solo lo útil)
- Senet (~5.000 años). El diseño como disciplina reconocida desde ~1980s (Crawford, The Art of Computer Game Design, 1984; Journal of Computer Game Design; primera conferencia en 1988).
- Diseñadores históricamente venían de otros campos o eran jugadores; la mejor manera de aprender sigue siendo **diseñar, desarrollar, testear y lanzar** (aprendizaje por práctica); la teoría de diseño de juegos recién se acumula desde ~2010. **Teoría de juegos (game theory) ≠ teoría de diseño de juegos.**

### 3.11 Resumen cap. 3 (del autor)
- Los juegos ocurren en un contexto separado y sin consecuencias (círculo mágico) expresado por tokens y reglas; jugar es voluntario y requiere participación; dan mundo definido, decisiones significativas, oposición, interacción y distintos tipos de metas.
- Visión sistémica: **Estructuras** (tokens y reglas), **Elementos funcionales** (los loops/"frases" que dan el modelo del mundo de segundo orden, modelo mental, decisiones y metas), **Arquitectura y tema** (el todo: balance contenido/sistemas, narrativa, experiencia).


## 4. CHECKLISTS DE DISEÑO / ANÁLISIS / BALANCE DERIVADAS

### 4.1 Preguntas para analizar un juego o un sistema (derivadas de caps. 2-3)
Partes
- ¿Cuáles son las partes? Para cada una: ¿qué atributos/estado tiene (con valores "de planilla"), qué límites/qué interactúa con ella, qué comportamientos y qué recurso mueven?
- ¿Cada parte decide su propio estado (encapsulamiento) o hay "manos ajenas" modificándola?
- ¿Dónde están las fuentes, stocks, sumideros? ¿Qué topes tienen los stocks? ¿Qué convertidores/deciders hay?
Loops
- ¿Qué loops de refuerzo hay (¿cuál es el principal?) y qué loops de balance los contienen? Para cada refuerzo: ¿cuál es su condición limitante (curva S)?
- ¿Hay retardos entre acciones y consecuencias (posibles fixes that fail)?
- ¿Hay recursos compartidos con múltiples consumidores (tragedy of the commons)?
- ¿Hay snowball para el que va ganando? ¿Hay un mecanismo de catch-up (tipo blue shell)? ¿Cuál domina? ¿Hay riesgo de espiral de muerte (refuerzo negativo)?
- ¿Qué efectos son no lineales? ¿Se esperaría oscilación (predador-presa)?
- ¿Hay riesgo de resonancia (muchos pequeños eventos que se refuerzan)?
Emergencia y niveles
- ¿Qué emerge que no está en ninguna parte? Test: ¿no lo determina una parte? ¿no es suma lineal? ¿se describe mejor agregado?
- ¿Qué niveles de organización hay (partes que son subsistemas)? ¿Son auto-similares (andamio de aprendizaje)?
- ¿Hay causalidad descendente (el estado global afecta decisiones locales)?
Juego
- ¿Es contenido o sistemas lo que sostiene el gameplay? ¿Cuánto del valor de rejugar depende de contenido nuevo?
- ¿Hay espacio de estados con múltiples caminos (segundo orden) o un camino único?
- Para cada decisión: ¿hay incertidumbre? ¿abre/cierra opciones? ¿o es ilusoria?
- ¿Qué fuentes de oposición hay (reglas, oponentes, otros jugadores, el propio jugador/trade-offs)?
- ¿Qué metas hay por tipo (instantáneas, corto, largo, sociales, emocionales; explícitas e implícitas)? ¿Se anidan en jerarquía?
- ¿Se apoya en metas autotélicas o en grind con recompensa externa?
- ¿Tema coherente con estructura y función?

### 4.2 Señales de problemas (y cómo detectarlos)
- **Reglas con excepciones / arbitrarias** -> el jugador piensa en las reglas en vez de jugar; carga cognitiva alta. Detectar: tablas de "casos especiales", mismo input con significados distintos.
- **Demasiadas reglas** -> agencia constreñida. **Muy pocas** -> ambigüedad; no se arma modelo mental.
- **Decisiones ilusorias** (todas llevan al mismo resultado) -> equivalen a no elegir.
- **Un solo camino óptimo** (espacio de estados colapsado por determinismo conocido) -> sin decisiones.
- **Contenido nuevo que no cambia tokens/reglas** (reskin) -> burnout rápido.
- **Content treadmill:** el consumo supera la producción; el costo por hora de juego crece.
- **Inflación / acumulación** en economías de faucet/drain sin sumideros suficientes o sin topes en stocks.
- **Snowball sin catch-up** -> partidas decididas temprano; **catch-up excesivo** -> el esfuerzo no se premia (inferencia a partir del par refuerzo/balance).
- **Crecimiento lineal esperado** de algo que tiene condición limitante -> predicciones falsas.
- **Reward exploit** (cobra effect): los jugadores optimizan la métrica de recompensa de forma que rompe el objetivo.
- **Complejidad realista excesiva:** más simulación no es más diversión; si el jugador no puede modelar mentalmente, falla.
- **Tema desconectado de las mecánicas** (Splendor) o **sin metas** (No Man's Sky).
- **Gamification/grind:** metas externas que convierten el juego en trabajo.
- **Emergencia no testeada:** efectos como los gatos de Dwarf Fortress; la interacción de subsistemas produce situaciones imprevistas -> necesitás simulación/telemetría, no solo especificación.
- **Controlador central innecesario:** si algo "dirige" el sistema, probablemente se pierde emergencia.

### 4.3 Reglas prácticas / heurísticas (resumen de bolsillo)
1. Diseñá reglas y partes, no experiencias lineales (segundo orden): sólo las mecánicas controlás directamente; las dinámicas emergen.
2. Todo sistema tiene un refuerzo y un balance; si solo hay refuerzo, buscá cuándo explota; si solo hay balance, buscá por qué no avanza.
3. Para cada loop de refuerzo, diseñá explícitamente su límite (curva S) o prepará el colapso.
4. Para cada recurso: listá fuentes y sumideros y ponés topes. Revisá la inflación.
5. Prefiero parámetros que emerjan de estados internos (ataque vs defensa) en vez de perillas globales opacas; pero tocás fondo con valores de planilla.
6. Usá aleatoriedad como sustituto de lo que no modelás y para variabilidad, no como reemplazo de decisiones.
7. Mantené el modelo mental construible: pocos casos especiales, consistencia entre acciones similares.
8. Profundidad por jerarquía y auto-similitud (Go): pocas reglas, subsistemas que se parecen a los de arriba.
9. Metas: explícitas para enseñar; habilitá implícitas/autotélicas para longevidad; jerarquía instantáneo->corto->largo; no olvides las emocionales.
10. Contenido y sistemas se balancean: los sistemas dan rejugabilidad; el contenido da pulido; evitá depender solo de lo segundo.
11. Tema coherente y consecuente con la mecánica (aunque sea simple) para que se genere significado.
12. Probá el sistema operando: los sistemas se entienden experimentándolos (simular/jugar), no leyendo reglas.

---------------------------------------------------------------------
## 5. GLOSARIO RÁPIDO (inglés -> idea)
- Metacognition: pensar sobre el pensamiento.
- Phenomenological / reductionist / holistic / systemic thinking: cuatro modos de pensar.
- Greedy reductionism: creer que el todo es solo la suma de partes.
- Metastability: estable a un nivel, cambiante por dentro.
- Synergy: el todo no predecible desde las partes.
- Part = state + boundaries + behaviors.
- Spreadsheet-specific: nivel de detalle implementable.
- Encapsulation: cada parte controla su propio estado.
- Source / stock / sink / flow / resource / converter / decider.
- Faucet/drain economy.
- Simple collection / complicated process / complex system.
- Reinforcing (positive) vs balancing (negative) loop; snowball; vicious cycle.
- Nonlinearity; Lotka-Volterra; knobs.
- Random vs chaotic; resonance event.
- Fixes that fail / unintended consequences loop; limits to growth (S-curve); tragedy of the commons; trophic cascade; engine (build now vs invest).
- Emergence; upward / downward causality.
- Levels of organization / integrative levels; persistence; adaptability; homeostasis; structural coupling.
- Depth; self-similarity; elegance; Bushnell's Law.
- Game+player system; magic circle; ludus/paidia; agon/alea/mimicry/ilinx.
- MDA; FBS/SBF.
- Tokens (nouns) / rules (verbs) / mechanics (viable token+rule combos).
- Metagame; legacy game.
- Internal model of reality; endogenous meaning; second-order design; state-space.
- Mental model; meaningful decisions; opposition (rules, opponents, other players, self).
- Explicit vs implicit goals; instant/short/long/social/emotional goals.
- Architecture (inward) vs theme (outward); content-driven vs systemic; content treadmill; reskin.
- Autotelic experience; the grind; gamification.
- Narrative; story-driven games; premise.

---

# CAPÍTULO 5 — Trabajar como diseñador sistémico

## 1. Cómo empezar ("How Do You Even Start?")

- Empezar es difícil porque el problema parece sin asideros. Los diseñadores históricamente "se tiraron a la pileta". Fallar mucho es normal (ejemplo: Rovio hizo 51 intentos antes de Angry Birds). Ver el juego como sistema de sistemas reduce cantidad y duración de los fracasos.
- **Wholes to Parts or Parts to Wholes** ("De los todos a las partes o al revés"): no hay un único punto de partida correcto. Tres escuelas coexisten:
  - "Nouns and verbs" (sustantivos y verbos = las partes que forman los sistemas). Ej: Will Wright.
  - Experiencia deseada / sensación holística (el autor).
  - "A machine that does x" (Ellenor 2014): imaginar una máquina, deducir sus partes y ver qué juego emerge.
- Implicancia práctica: hay que llegar a tener definidos partes, lazos Y todo. Moverse con soltura entre niveles organizacionales; empezar por el que tenga sentido y rebotar. Diferencias de escuela generan malentendidos en el equipo (el autor tardó en entenderse con Wright).

## 2. Conocé tus fortalezas, trabajá tus debilidades ("Know Your Strengths, Work to Your Weaknesses")

Cada diseñador tiene un "hogar" (home place) al que vuelve cuando el diseño se pone difícil. Hay que identificarlo, no quedarse ahí, y saber trabajar con quienes parten de otro lado. Tres arquetipos:

| Arquetipo | Parte desde | Fortaleza | Trampa / riesgo | Qué debe desarrollar |
|---|---|---|---|---|
| **Storytellers** (narradores) | El todo: viaje y sentimientos del jugador, mundo | Pintar la experiencia, tema | "Los juegos no son historias"; contar el juego como relato no alcanza | Sistemas funcionales con tokens, reglas y elementos dinámicos; colaborar con quien estructure |
| **Inventors** (inventores) | Mecanismos complejos (relojes, simulaciones ecológicas/económicas). Ej: prototipos de Spore con simulación de formación de sistema estelar | Sistemas dinámicos fascinantes | Mecanismo en el centro, sin jugador humano ("watch it go"); al jugador le tiran migajas | Incluir al humano como parte integral; metas de largo plazo y razones para jugar (el todo) |
| **Toymakers** (fabricantes de juguetes) | Piezas/mecanismos atractivos aunque no "hagan" nada; o conocimiento de dominio (cadencia de un Sopwith Camel, espadas medievales, corales) | Prototipar rápido a partir de tokens/reglas | No piensan qué hace el jugador ni por qué es divertido | Construir sistemas interactivos y encontrar metas para el jugador |

- Regla: cada punto de partida es válido **mientras no sea donde terminás**. Equipos con estilos distintos son más difíciles de coordinar pero producen mejores juegos.
- "Find the fun" (encontrar la diversión) requiere las tres capas (partes, lazos, todo) **más** interactividad atractiva.
- Habilidad central: comunicar ideas, escuchar las de otros, trabajar con fortalezas distintas a las propias.

## 3. Cualidades de los sistemas de juego ("Qualities of Game Systems", Achterman 2011)

Cinco marcas de un sistema de juego efectivo:

1. **Comprehensible (comprensible)**: el diseñador debe entender el juego y sus sistemas internos, y el jugador debe poder armar un modelo mental. Por eso importan la documentación de diseño (para vos) y presentar el juego de modo que se pueda modelar mentalmente (para el jugador).
2. **Consistent (consistente)**: reglas y contenido funcionan igual en todas las áreas. Tentación: agregar una excepción/caso especial para arreglar un problema → baja la resiliencia del sistema (problemas futuros) y lo hace más difícil de aprender.
3. **Predictable (predecible)**: mismas entradas → salidas predecibles. Ayuda al modelo mental, y está algo en tensión con emergencia. No significa mecánico/aburrido; pero tampoco resultados muy distintos para entradas parecidas ni sistema frágil ante imprevistos. Mínimo: haber contemplado los casos borde que dañen la experiencia o dejen una grieta explotable.
4. **Extensible**: construir sistémicamente permite reusar contenido o generarlo proceduralmente en vez de depender de "set pieces" hechos a mano. Preferir **lazos (loops) a arcos**: cita de Daniel Cook, un arco es "un lazo roto que salís de inmediato". Un sistema general ("construcción de edificios") permite agregar una clase nueva de edificios sin hacerla a mano. Un sistema en lazos se puede reubicar como parte de otro juego. Partes mínimas necesarias + suficientes lazos entre ellas.
5. **Elegant (elegante)**: resume las anteriores y va más allá de la consistencia. Ejemplos de elegancia: espacio diverso explorable con pocas reglas (arquetipo: Go); reglas sistémicas con pocas excepciones, fáciles de aprender, con comportamiento predecible y emergente; sistema usable en múltiples contextos o con partes nuevas agregables.

Señales de problema derivadas: excepciones acumuladas; contenido hecho a mano que no se puede reusar; "arcos" de un solo uso; sistemas fracturados/separados.

## 4. Juegos de mesa vs. digitales ("Tabletop and Digital Games")

- Hay mucho en común entre ambos desde el diseño. Estudiar juegos de mesa enseña aunque nunca los diseñes: la única "potencia de cómputo" está en las cabezas, la interacción es solo con tokens físicos → expone la relación entre tokens/reglas, lazos y experiencia. Los digitales pueden esconder pereza de diseño detrás de gráficos y cinemáticas; los de mesa no.
- Analogía (Terrence Mann): "el cine te hace famoso, la TV rico, el teatro te hace bueno". La mesa es al digital lo que el teatro al cine: más cerca de la audiencia, menos donde esconderse.
- Por eso el libro usa muchos ejemplos de mesa. No es obligatorio diseñar de mesa, pero es buena práctica.

## 5. Proceso de diseñar juegos como sistemas ("The Process of Designing Games as Systems")

- Proceso **iterativo** entre partes, lazos y todo: primero en la cabeza/pizarra/papeles/documentos/hojas de cálculo; luego, ya con forma, ciclo prototipar + playtestear (cap. 12). Mejor prototipar rápido y testear temprano que esperar que la idea salga completa.
- **Game designer's loop** (Fig. 5.1 = Fig. 4.3): Diseñador → diseña Juego; Jugador ↔ Juego intercambian input/feedback; el diseñador recibe feedback del jugador/juego y retoca. El diseño es un lazo de retroalimentación diseñador-jugador-juego.
- Se puede empezar en cualquier nivel; lo importante es que luego los tres se soporten entre sí. El libro los recorre en orden todo → lazos → partes.

### 5.1 Nivel TODO: arquitectura temática ("The Whole Experience: Thematic Architecture")
Responde "¿cuál es el punto del juego (o de un sistema dentro)?". Se separa en **architectural** (aspectos técnicos de la experiencia: cómo se ve y se siente) y **thematic** (cualidades tácitas: de qué trata).
- Ejemplo: For Honor, Jason VandenBerghe: "el combate es una forma de arte" → combate cuerpo a cuerpo como danza letal. No alcanza solo, pero es una estrella guía de la que derivan interacciones y detalles.
- Error común: equipos que se lanzan a producir sin aclarar la "experiencia total"; la visión compartida y coherente es el mejor indicador de éxito del equipo (cap. 11).
- Aspectos de la visión a articular:
  - **World and History (mundo e historia)**: ¿cuál es el mundo y el punto de vista del jugador? (mismo mundo de espías: espía que asciende / jefe que mueve hilos / veterano en misión de venganza → tres diseños distintos). Historia: solo los eventos que aplican al jugador. Al inicio, una o dos páginas; no escribas 100 páginas de lore salvo que tengas tiempo, plata y experiencia. No escribas más de lo que el diseño necesita.
  - **Narrative, Progression, Key Moments**: la historia es el pasado; la narrativa es presente/futuro. Preguntas: ¿hay historia predefinida? ¿hay eventos mayores alrededor del jugador que dejan margen de decisión? ¿o el pasado es solo punto de partida? De ahí salen eventos mayores, metas, progresión y **key moments** (momentos clave: relatos cortos de puntos climáticos significativos).
  - **Art, Monetization and other whole-experience concerns**: estilo de arte (2D/3D, pictórico, cel-shaded, hiperrealista) y cómo refleja el corazón/tema; UI/UX; monetización (se decide en esta etapa).
- No importa si arrancás con visión de cielo azul o llegás después de definir partes y lazos: iterás entre ambos; antes de desarrollar tenés que tener el todo claramente articulado y compartido.

### 5.2 Nivel LAZOS: sistemas y espacio de juego ("Systemic Loops and Creating a Space for Play")
- Los lazos: modelo dinámico del mundo del juego, modelo mental del jugador e interacciones jugador-juego. Diseñarlos es el núcleo del "systems designer" (detalle en cap. 7).
- Objetivo: crear un **espacio** que el jugador explore y habite, no un camino único. Los sistemas deben apoyar el tema y la experiencia, y funcionar interactivamente entre juego y jugador. Hay que especificar (vía prototipo + playtest) los **core loops**, las metas explícitas y la progresión.
- Dificultad: es lo más difícil del diseño, porque la experiencia que producen no se ve bien de antemano. Ejemplo: recursos, crafting, producción de riqueza y combate tienen cada uno su funcionamiento y se interrelacionan entre sí y con el jugador. Requiere habilidad, paciencia y resiliencia ante intentos fallidos.
- **Balancing Game Systems (balancear sistemas)**: todas las partes definidas deben usarse y estar balanceadas entre sí, y todo sistema debe tener un propósito claro. Ejemplo: si agregás un sistema de misiones y los jugadores lo ignoran, entendé por qué y decidí si quitarlo o arreglarlo (detalle en cap. 9-10).

### 5.3 Nivel PARTES: tokens, valores y reglas ("The Structural Parts: Tokens, Values, and Rules")
- Antes de que sea un juego, hay que situar los lazos funcionales en el contexto del todo y crear las partes estructurales. Pasar de la descripción vaga ("hand-waving") a algo implementable es obligatorio.
- Esto es el **detailed design** o la parte "spreadsheet-specific": ¿la espada pesa 3 o 4? ¿cuesta 10 o 12? ¿cuántos tipos de tropas/caballos/pétalos y qué diferencia hacen? Es lo que vuelve real el juego y permite **balancear los tokens entre sí** para que los sistemas no se "vuelen" separados.
- Cómo pensar los tokens (objetos del juego: jugador, otras personas, naciones, criaturas, naves): dar a cada uno atributos, valores y comportamientos suficientes. **Pregunta guía**: ¿cuál es el menor número de atributos, estados y comportamientos que soporta los sistemas y la experiencia deseada?
- Hacer evidente al jugador qué son los tokens, qué hacen y cómo los afecta → alimenta UI/UX. La UI no se puede especificar hasta saber qué información es necesaria; preguntarse qué información necesita saber el jugador ayuda a clarificar la tokenización.
- Adelanto cap. 8: objetos complejos con pocos atributos generales que interactúan (subsistemas); comportamientos inter-objeto; cómo evitar tokens de "victoria fácil" o que rompan el juego.

### 5.4 Revisitar el proceso ("Revisiting the Systemic Design Process")
- El ciclo del diseñador: alternar entre ver el juego como todo, como sistemas/lazos y como partes individuales (Fig. 5.2), viéndolos a la vez y pudiendo bajar al detalle de cualquiera.
- **Heurística de desatasco**: si empujás un nivel sin efecto, cambiá de punto de vista. ¿No lográs la experiencia? Explorá los tokens y cómo informan la experiencia. ¿Tenés clara la experiencia pero no podés especificar tokens? Mirá qué dicen los sistemas sobre cómo deben funcionar.
- **Anti-patrón**: evitar tokenizar, asegurar interacciones interesantes o cohesión temática solo porque no es tu zona de confort. Los tres son necesarios.

## 6. MÉTODO: analizar juegos desde la visión sistémica ("Analyzing Games from a Systems View")

Se sigue la misma estructura que el diseño: todo → lazos → partes (y cómo construís tu modelo mental). Objetivo: entender qué hace funcionar (o fallar) a otros juegos, aprender decisiones del diseñador y mejorar los propios diseños.

**Paso a paso (checklist de análisis):**

1. **Tu propio modelo mental al empezar (primer contacto)**
   - ¿Entendés el escenario y el tema?
   - ¿Qué te sorprende?
   - ¿Qué conceptos fueron importantes, incompletos o difíciles de entender al aprender?
   - ¿Cómo podría el juego haber aumentado tu engagement al principio?
2. **El todo (experiencia)** — durante y después de jugar
   - ¿Qué experiencia y sentimientos intentó provocar el diseñador?
   - ¿Qué aspectos apoyaron o restaron a tu experiencia?
   - ¿Qué elementos visuales e interactivos sostienen el tema y la experiencia deseada?
   - ¿Qué podés inferir de la intención del diseñador a partir del estilo de arte y los aspectos interactivos?
3. **Sistemas** — identificar qué sistemas específicos existen
   - ¿Hay sistemas que operan independientemente del jugador, o todos dependen de que el jugador haga algo primero?
   - Ejemplo: Power Grid (mesa) tiene sistemas casi fuera de control del jugador; economía de oferta/demanda: cuanto más combustible compran los jugadores, más sube el precio hasta que se repone el suministro en el turno siguiente; el suministro se repone cada turno y baja precios si no se usa.
4. **Lazos de progreso**
   - ¿Cómo progresás? ¿Qué **reinforcing loops** (lazos de refuerzo) identificás?
   - ¿Qué **balancing loops** (lazos de balance) empujan contra el avance, o evitan que un jugador que se adelanta temprano simplemente gane?
5. **Interactividad**
   - ¿Cuáles son las formas primarias de interactividad?
   - ¿Cómo asigna el juego su **interactivity budget** (presupuesto de interactividad)? ¿Estrategia y socialización, o pensamiento rápido y acción?
   - ¿Las formas de interactuar ayudan a establecer el tema o van contra él?
6. **Partes: tokens y reglas** (las partes atómicas con valores y comportamientos)
   - ¿Apoyan la experiencia o la estorban?
   - Habiendo aprendido un sistema, ¿podés transferir eso a otra parte del juego, o hay muchas reglas con excepciones propias que obligan a pensar mucho cómo jugar? (test de consistencia/elegancia)
   - Mirar cómo el arte se expresa en los tokens, a veces de forma sorprendente. Ejemplo: Splendor (mesa, comerciante de gemas): las fichas pesan como fichas de póker; el peso suma sutilmente a la experiencia aunque no sea funcional.
7. **Comparar y sintetizar**: al analizar muchos juegos aparecen comunalidades y rasgos únicos; sirve para evitar errores ajenos, tomar buenas ideas y mantener fresco tu diseño.

## 7. Prototipado y playtesting ("Prototyping and Playtesting")

- El diseño es testear y refinar ideas repetidamente al servicio de una visión; casi todo cambia durante el desarrollo salvo la visión unificadora.
- Ejemplo: Ed Catmull (Pixar): "todas nuestras películas apestan al principio". Up empezó con un reino en el cielo, dos príncipes y un pájaro gigante llamado Kevin; al final solo quedaron el pájaro y la palabra "up".
- Reglas prácticas:
  - Estar dispuesto a muchas iteraciones y a **tirar trabajo** (dibujos, animaciones, código, documentos). No aferrarse a algo por el tiempo invertido: te quedás con lo "okay" o mediocre cuando con más trabajo sería grande.
  - **Prototipo**: versión temprana para jugar y testear la idea; puede ser dibujos en pizarra, papeles y monedas. Casi siempre feos o incompletos, convergen al producto pulido. El punto es sacar la idea del plano de las ideas y hacerla jugable **lo más rápido y seguido posible**.
  - **Playtesting**: validación de prototipos, o más a menudo, cómo descubrís dónde está roto el diseño. La intuición del diseñador nunca sustituye testear con jugadores que nunca lo vieron. Cita de Cook: sin implementación y playtest, un diseño es una "fantasía de papel ineficaz".
  - Testear temprano y a menudo; la idea brillante de tu cabeza no sobrevive al contacto con la realidad sin cambios (probablemente muchos).
  - Humildad y flexibilidad creativa para cambiar según lo que opinan otros.

## 8. Resumen del cap. 5
Al dividir el juego en partes, lazos y todo (no necesariamente en ese orden) se tiene un asidero para definirlo en cada nivel. Cap. 6 = el todo; cap. 7 = lazos; cap. 8 = partes.

---

# CAPÍTULO 6 — Diseñar la experiencia total

Propósito: llegar a la "gran idea" y registrarla en un **concept document** (documento de concepto) que es el todo unificado y la piedra de toque durante el desarrollo.

## 9. La gran idea ("What's the Big Idea?")

- Todo juego tiene una única idea impulsora (concepto / visión). Hay que aclararla **temprano** y poder explicarla de forma sucinta. Si se posterga, se deambula picando posibilidades sin hallar el corazón y nadie entiende qué hacés ni por qué vale la pena.
- Compartir una visión clara y convincente es la práctica que más correlaciona con juegos exitosos (cap. 11).
- La visión no tiene que ser grandiosa: cuanto más chica y enfocada, mejor. Ejemplos: Angry Birds (idea nada épica, disfrutada por millones); For Honor ("combate como danza": una frase evocadora comunica y entusiasma).

### 9.1 Blue-sky design ("Blue-Sky Design")
- **Ideation** = generar y comunicar ideas nuevas. **Blue-sky design** = forma muy abierta, sin límites, reglas ni realidades de negocio. Seductora, sobre todo para diseñadores jóvenes.
- **Métodos** ("Methods"): se puede solo, pero es mucho más efectivo con otros (rebotar ideas). Típicamente: sala con pizarras vacías y un equipo chico → "sean creativos, YA".
- **Brainstorming-ish** (con modificaciones):
  - Primero cantidad, no calidad: sacar ideas afuera.
  - Sembrar con un prompt o un chiste (Ron Gilbert: toda buena sesión empieza con 15 min sobre Star Trek). Aflojar mentalmente al grupo.
  - Mantener el flujo con mano ligera: la moderación pesada corta la creatividad. Turnos para que todos aporten; incluso juegos (la inicial de tu idea es la última de la idea anterior).
- **Getting Past the Easy Ideas (pasar las ideas fáciles)**: las primeras ideas casi siempre son estereotipos y clichés o calcos de algo reciente (lo que está en la superficie de la mente). No se pueden evitar, pero hay que no detenerse ahí, ni dejar que el ego ("qué listo soy") frene. Con otros, construir sobre lo que dijeron.
- **Twisting Ideas (retorcer ideas)**: tomar una idea sobre la mesa y subvertirla. Ejemplo: "guerrero que mata al dragón para salvar la aldea" → ¿y si salvás al dragón? ¿convencés a los aldeanos de aliarse con él? ¿sos el dragón?
  - **"Yes, and..."** (técnica de improvisación): en lugar de un "no" que mata el flujo, cada persona acepta y agrega su giro; la idea muta por adición. Saca el ego: importan las ideas, no quién las dijo.
- **Curation (curaduría)**:
  - Hay un límite a "no hay ideas malas". Pasado el flujo inicial hay que **abrir menos la canilla**: mirar las ideas escritas, ver cuáles tienen más pasión/creatividad (las que la gente sigue discutiendo sola) y descartar las "pozos secos".
  - No todas las populares sirven: algunas exceden los medios, requieren tecnología inexistente o no encajan con la dirección.
  - Analogía: director de museo que elige qué exhibir sin decir que lo demás carece de valor.
  - Suele decidir un perfil senior (director creativo, lead designer, a veces productor ejecutivo): desde circular ideas en pizarra hasta pedir desarrollo de pocos tratamientos escritos. Implica dejar atrás el resto.
  - Cita de Steve Jobs (parafraseada): foco es decir "no" a mil buenas ideas.
- **Limits to Blue-Sky Design (límites)**: sin límites suele llevar a ningún lado o a direcciones opuestas sin ganador. Muchos diseñadores se paralizan; o regresan a la seguridad de un juego conocido; sin límite de tiempo, retocan sin fin y no terminan.
- **Constraints Are Your Friend (las restricciones son tus amigas)**:
  - Casi siempre ya tenés restricciones: tiempo, dinero, plataforma, habilidad de programar y de hacer arte; licencias; tipo de juego requerido. Limitan el blue-sky pero no la creatividad dentro.
  - Conviene fijar además límites de **género** (tipo de gameplay) y de **experiencia** buscada. Incluso en la sesión, ground rules como "sin realidad virtual" o "sin matar". Eliminan millones de ideas, y ese es el punto.
- **Cautions (precauciones del brainstorming)**:
  1. **Voces dominantes**: quienes hablan primero o más se oyen más; extrovertidos y varones tienden a conducir y otras perspectivas se pierden.
  2. **Groupthink**: si todos acuerdan se asume que es bueno, pero un grupo homogéneo (todos varones, fans del mismo género, etc.) considera un rango estrecho y es el peor equipado para verlo (no vemos nuestros propios puntos ciegos). Traer gente diversa (género, etnia, experiencias de vida, intereses, nivel de experiencia).
  3. **Forzar la visión o feature en una sola sentada** (todo el día si hace falta): mala forma de crear; los callados quedan afuera y se agota rápido. Cuando baje el flujo, descansar: cada uno se va una hora o más con algunas ideas, y se vuelven a juntar a ver adónde llegó el pensamiento (no hace falta reiniciar ni retomar exacto).

## 10. La experiencia deseada ("The Desired Experience")

- Pregunta más importante de la ideación: **¿qué experiencia querés que tenga el jugador?** Es decir: qué hace, cómo progresa y, sobre todo, **qué siente**.
- Cuesta, sobre todo para inventores y toymakers, y puede parecer secundaria frente a tokens/reglas. Tarde o temprano hay que enfrentarla; no se resuelve sola. Diseñar sin diseñar intencionalmente la experiencia da un modelo mental más caótico, más difícil de aprender y de enganchar.
- Si sos storyteller: llegás rápido a la esencia emocional pero necesitás bajar a tierra con otros. Si ya hay narrativa: asegurate de diseñar un juego, no una película. Pregunta: ¿la experiencia deseada soporta **second-order design** (diseño de segundo orden: hay un espacio de juego para explorar, no solo un relato por el que caminar como espectador)?
- Decisiones específicas a tomar sobre la experiencia (lista):
  1. ¿Quiénes son tus jugadores? ¿Cuáles son sus motivaciones?
  2. ¿Cuál es el género (tipo de gameplay más usado)?
  3. Combinando ambas: ¿cuál es la **player's fantasy** (rol que da razón y espacio para explorar: héroe, pirata, emperador, escarabajo pelotero, niño…)?
  4. ¿Qué tipo de decisiones toma el jugador y cómo progresa?
  5. ¿En qué tipo de interactividad se apoya más? ¿Cómo gastás el **interactivity budget**: juego de reflejos, de planificación cuidadosa o de respuesta emocional? ¿Cuáles son las estéticas visuales y sonoras?

## 11. El documento de concepto ("The Concept Document")

- Articular la visión para comunicarla; saltearlo es tentador en equipos chicos, pero aclara el pensamiento, alinea al equipo y sirve para vender el diseño (nuevos miembros, financistas, ejecutivos).
- Es informativo **y** persuasivo: transmitir la idea rápido y claro y mostrar por qué vale hacerla. Es similar a la estructura del **pitch**, aunque difieren según audiencia (cap. 12). Plantilla en recursos online del libro.
- Formato: en papel, o mejor **online** (wiki/web): se mantiene vigente en vez de volverse obsoleto, y se agregan detalles de manera organizada sin engordar el documento.
- Reglas del documento:
  - Siempre a **alto nivel**; "la punta del iceberg"; nexo de toda la documentación de diseño; mantenerlo actualizado.
  - Breve, claro, resaltando la visión; cuantas más imágenes y diagramas, mejor.
  - Da descripciones conceptuales breves (estilo de arte, historia del mundo, progresión) y **apunta** a documentos específicos más detallados → permite que varios diseñadores trabajen partes distintas y se sumen documentos, manteniendo el concept doc como expresión global. Es la piedra de toque de la visión acordada y principio organizador activo.
- **Tres secciones principales**: (1) High-level concept, (2) Product description, (3) Detailed design.

### 11.1 Sección 1: High-level concept ("Capturing the Concept")
Subsecciones (lista completa): **Working title, Concept statement, Genre(s), Target audience, Unique selling points**.

- **Working Title (título de trabajo)**: el nombre-asa para hablar del juego. Evocativo del juego; algunos equipos buscan dominios y títulos competidores; otros eligen un nombre sin relación (codename, por confidencialidad). Ambos funcionan y probablemente da igual: el título final casi nunca es el inicial. Capturá el juego y seguí; la búsqueda de nombre es para después.
- **Concept Statement (declaración de concepto)**: una o dos frases que capturan todos los aspectos importantes, sobre todo la **experiencia del jugador**; responde "¿de qué trata tu juego?" y es la primera impresión. Debe ser breve, incisiva y comprensible; debe dar una idea exacta (no detallada) de los puntos principales, por qué no es como los miles de otros juegos y por qué es divertido. Truco: encajarlo en un tweet de 140 caracteres (pasarse un poco no importa; sirve para elegir cada palabra).
- **The One Question (La Pregunta Única, Booth 2011)**: una pregunta sobre el juego que sirve para **resolver cuestiones de diseño** (no es estrictamente parte del doc pero puede derivar del concept statement). Aplica literal o figurada a todo, de features chicas a UI.
  - Ejemplos: simulación histórica → "¿es auténtico?"; juego de ninjas → "¿es sigiloso?".
  - Guitar Hero: "¿Rockea?" Si un feature no contribuye a eso, afuera; entre dos features, el que más rockea. Aplicado a personajes: ¿crear tu propio personaje o elegir uno prearmado? → la que haga sentir más que sos el que rockea (de ahí la personalización hasta el delineador de ojos).
  - Rock Band: costó fijar la visión por amor a Guitar Hero; la pregunta pasó a ser "¿es una experiencia auténtica de estar en una banda de rock?". Al fijarla, muchas discusiones sobre features desaparecieron porque todos veían la línea divisoria entre ambos proyectos.
  - Uso: te da la visión concisa y evalúa ideas/features posteriores para ver si pertenecen.
- **Genre(s)**: etiqueta heurística (sin designaciones oficiales; mutan y se subdividen) basada en convenciones de gameplay, tipos de desafíos y decisiones, y a menudo estética/tecnología. Indica el tipo de interacciones prevalentes: acción rápida, estrategia reflexiva, emocional/narrativo, social, o combinación.
  - Ejemplo de shooter: subgénero de acción, mucha acción/feedback rápida y cognición de corto plazo en entorno de matar-o-morir; infinitos subtipos ("shooter espacial 2D top-down" como Gratuitous Space Battles; "shooter cooperativo masivo bullet-hell" como Realm of the Mad God). Portal: es shooter porque disparás, pero no matás nada y disparás para resolver puzzles → ejemplo de repensar supuestos tácitos.
  - **Peligro**: usar el nombre de género sin considerar qué aspectos de ese género incluís → diseño perezoso. ("Estrategia" ¿significa cámara top-down/isométrica, comandar muchas unidades u otra cosa?). **Mejor práctica**: decir qué aspectos de qué géneros querés (ej.: "control de múltiples unidades de estrategia + ritmo de acción + interacciones jugosas y fáciles de aprender de casual"). Eso informa a otros y te ayuda a ver si estás abarcando demasiados géneros.
  - Lista de géneros del libro con su perfil de interactividad (útil para análisis):
    - **Action**: lazos acción/feedback rápidos; historia como telón, poca narrativa en el gameplay.
    - **Adventure**: lazos rápidos de acción/feedback dentro de una historia de aventura que da metas de largo plazo.
    - **Casual**: fácil de aprender, pocos lazos y metas de corto plazo, sesiones cortas; interacciones "jugosas" (juicy): gráficos brillantes, acciones claras (botones grandes y coloridos), mucho feedback visual/sonoro; apunta a gente que no se considera "gamer" (puede jugar horas, pero como pasatiempo).
    - **Idle**: el jugador decide poco, el juego "se juega solo"; foco en acción/feedback (variante clicker), poca cognición de corto plazo y algo de planificación de largo plazo. Interactividad superficial = rasgo; baja carga cognitiva. Progresa aun ausente el jugador y le da feedback positivo de cuánto avanzó al volver. A Dark Room (Michael Townsend): público = gente a la que le gusta que "los números suban" + gente a la que le gusta explorar lo desconocido. Riesgo: cuando se desvanece la promesa, se ve que no hay más punto que ver subir números.
    - **MMO**: cientos/miles de jugadores; avatar y mundo persisten sin el jugador. Acción/feedback (combate), cognición corto y largo plazo (progresión del personaje); la interacción social es crucial (agrupar, comunidades informales).
    - **Platformer**: avatar que salta entre plataformas; acción/feedback rápida (saber cuándo y cómo saltar); fácil de agarrar, gratificante para dominar (viene de los arcades de los 80).
    - **Rhythm**: gameplay basado en sentido del ritmo/musicalidad/baile; replicar secuencias musicales/de baile con acción/feedback rápida dentro de una canción.
    - **Roguelike**: mapas generados proceduralmente, a menudo permadeath (si morís, empezás de nuevo); se espera morir seguido, y esa "precariedad mortal" (Pearson 2013) es parte del atractivo. Nombre por el juego Rogue. Como los niveles cambian, se rejuega sin repetición. Hoy se aplica también a exploración espacial, simulación, etc. Interactividad: mezcla de acción/feedback (combate en tiempo real) y cognición de largo plazo para mejorar el avatar (habilidades, equipo) y afrontar desafíos crecientes.
    - **Role-playing**: rol específico, usualmente aventuras heroicas; combate (acción/feedback), mejora de habilidades (cognición de corto plazo) y a veces crafteo (largo plazo).
    - **Sports and simulation**: simulan actividades reales con mayor o menor verosimilitud; deportes usan acción/feedback + cognición corto y largo plazo; simulaciones (granja, avión, ciudad) se apoyan sobre todo en cognición corto y largo plazo.
    - **Strategy**: casi exclusivamente interacción de corto y (sobre todo) largo plazo para planificar y comandar; puede verse aburrido visualmente porque se gasta el presupuesto cognitivo/interactivo en cognición de largo plazo.
    - **Tower defense**: proteger una base/objetos de oleadas crecientes mientras las defensas ("torres") se elaboran; se puede construir en cualquier lugar para "arriar" enemigos por un camino; hay un lazo de retroalimentación: ganás puntos/moneda por crear o mejorar torres según enemigos eliminados. Mezcla cognición de corto/largo plazo con algo de acción/feedback.
  - Hay combinaciones (ej. World of Tanks: acción-estrategia MMO).
  - **Heurísticas de género**: buscá juegos similares para definir el tuyo. Cuidado con: (a) encajar demasiado bien en un género establecido (por ejemplo, un 2D action platformer calcado de miles) → menos interesante y diseño perezoso que se apoya en la etiqueta; (b) mashups confusos o gimmicky ("bullet-hell narrativo con estrategia y shooter": difícil de que entiendan).
- **Target Audience (público objetivo)**: se describe con tres ejes: **psicografía, demografía y contexto tecnológico/ambiental**.
  - *Psychographics and Motivations*: forma fácil: "a quien le gusta el juego X, le gustará el mío". Forma más sofisticada: motivaciones primarias de gameplay.
    - **Modelo Quantic Foundry (Matsalla 2016; encuesta a ~300.000 gamers): 6 motivaciones**:
      1. Action: destrucción y gameplay excitante de ritmo rápido.
      2. Social: comunidad y competencia (no mutuamente excluyentes).
      3. Mastery: desafíos difíciles y estrategias de largo plazo.
      4. Achievement: completar misiones y volverse poderoso.
      5. Immersion: ser otro y vivir una historia elaborada.
      6. Creativity: expresarse por crafteo/personalización, tinkering y exploración.
    - **Tres clusters**: Action-social (excitación, competencia, destrucción → comunidad); Mastery-achievement (completar, estrategia, desafío → poder); Immersion-creativity (historia, personalización, diseño, fantasía → descubrimiento). "Power" y "Discovery" son motivaciones "puente" entre clusters. Ejes: cerebral vs kinético; acción "sobre el mundo" vs "sobre otros jugadores".
    - **Bartle (1996)**: ejes "actuar sobre" vs "interactuar con" y "jugadores" vs "mundo" → achievers (actúan sobre el mundo), explorers (interactúan con el mundo), socializers (interactúan con jugadores), killers (actúan sobre jugadores). No resiste el escrutinio cuantitativo pero conserva utilidad intuitiva (aforismo de Box: todos los modelos son erróneos, algunos útiles).
    - Los clusters correlacionan con el **Big Five / Five Factor Model**: neuroticismo, extraversión, amabilidad (agreeableness), responsabilidad (conscientiousness), apertura a la experiencia. Action-social ~ extraversión; mastery-achievement ~ responsabilidad; immersion-creativity ~ apertura. Los jugadores eligen juegos que coinciden con su personalidad: "no para ser quien no son sino más quien son" (Yee).
    - **Uso**: listar las motivaciones probables de tus jugadores según el gameplay y la interactividad; igual que con el interactivity budget, detectar combinaciones improbables (quien quiere inmersión emocional en una historia elegante probablemente no quiera pasar el rato haciendo explotar cosas).
  - *Demographics*: edad, género, contexto de vida. Algunos crean personas ("Lisa, divorciada de 45…"), útil para sacar el foco de uno mismo pero puede distraer de motivaciones reales; no te explayes salvo que el detalle importe al juego.
    - Tendencias relevantes (Yee 2017): la motivación "excitement" cae linealmente con la edad y se vuelve "anti-motivación" a los 50+ (explicaría por qué League of Legends es más popular entre jóvenes). "Competition" cae más rápido, alta en adolescencia y mínima hacia los 40; hombres más motivados que mujeres hasta ~45, luego la diferencia desaparece. "Completion" se mantiene estable por edad y está siempre entre las 3 motivaciones principales de hombres y mujeres.
  - *Environmental Context*: plataforma (consola, PC, móvil…), tiempo disponible/factores ambientales ("viajeros con 10 minutos en el bus" vs. "dedicados con un día entero"), nivel de sofisticación técnica o de juego, otros factores pertinentes.
  - *Summing up*: armar una declaración descriptiva corta (ej. jugadores de alta acción con competencia significativa apoyada por misiones predefinidas que satisfacen completitud; interrumpidos por la vida, valoran sesiones de 10 min y rampa de aprendizaje fácil, con capacidad de mostrar habilidades y misiones completadas). Debe ser clara pero no restrictiva, ni excesivamente amplia ni estrecha.
  - **Regla dura**: si la respuesta a "¿quién es tu jugador objetivo?" es "todos", no pensaste suficiente en el concepto ni en su atractivo. Ningún juego es universalmente atractivo; dentro del atractivo general hay un público "bull's-eye". Definirlo ayuda a decidir.
- **Unique Selling Points (USPs)**: lista corta (**3 a 5**) de declaraciones breves y significativas de qué hace único/atractivo el juego. Si cuesta escribir USPs significativos, probablemente haya que **rehacer el concepto**.
  - Pregunta test: ¿por qué alguien dejaría un juego que ya sabe que le gusta para jugar el tuyo?
  - **Trampas**: creer que como a vos te parece genial a todos les parecerá; creer que porque fue difícil de hacer tiene que ser bueno / que la pasión del equipo se nota (nunca pasa). Los jugadores no se preocupan por tu amor o esfuerzo; primero hay que capturar la atención visual y de gameplay.
  - Se puede conformar con "fresco": no 100% nuevo, pero no visto una y otra vez, con giro nuevo. Ej.: zombis; cambios triviales ("zombis rápidos", "zombis violetas") no alcanzan; algo como rescatar zombis y reinfectarlos para volverlos humanos sí podría.
  - También se puede **subvertir un género** (Portal con shooters; Undertale con RPG): tomar el tropo dominante ("en shooters todo es destruir") y cambiarlo ("disparás para navegar y resolver puzzles"). Más difícil que usar aspectos del género y llevarlo a nuevas direcciones (ej. juego narrativo con elementos de acción; juego idle que escape del clic sin sentido).
  - Equilibrio: lo nuevo y único diferencia, pero el juego tiene que seguir siendo **reconocible**; si no, lo descartan por ininteligible tan rápido como por convencional.
  - Pensar en USPs es otra razón para diseñar el concepto con calma: si te quedás con la primera idea, probablemente no sea única de manera significativa. Necesitás algo más que "me suena copado".
  - **X-statements**: dos definiciones. (1) el "x-factor": qué lo hace especial/distinto/atractivo (≈ lista de USPs). (2) estructura "A x B" ("A cruzado con B" / "A meets B"): ej. "The Division x Overwatch", "GTA meets Undertale": mezcla de juegos existentes para una versión fresca.
  - **Caveats (cuidados)**: usar USPs/x-statements como muleta de diseño perezoso (combinar USPs de otros juegos esperando un híbrido maravilloso "casi nunca funciona"). Los USPs deben apoyar una **visión coherente**, no formar una aglomeración monstruosa de puntos sin relación. A pesar de "selling", sirven sobre todo para entender y comunicar el concepto: el énfasis va en lo que lo hace atractivo y envolvente de maneras nuevas, no en lo que venderá. Diseñar un buen juego que venda, no un juego que venda "y ojalá sea bueno".

### 11.2 Sección 2: Product description ("Product Description")
Subsecciones (lista completa): **Player experience, Visual and audio style, Game world fiction, Monetization, Technology/tools/platform, Scope**. Con punteros (links) a documentos de detalle (cap. 7 y 8).

- **Player Experience (experiencia del jugador)**: pocos párrafos cortos; incluye la fantasía del jugador, **key moments** como ejemplos de gameplay y una breve discusión de lo que el juego llega a significar para el jugador. Debe reflejar (y verse reflejada en) concept statement y USPs. Salida principal del proceso de blue-sky.
  - **What Is the Fantasy? (fantasía)**: dejar claro el punto de vista del jugador y qué fantasía da (caballero heroico, ladrón sigiloso, capitán estelar, madre soltera que mantiene a su familia, organismo unicelular, líder incorpóreo de un imperio galáctico). Cada una = experiencia distinta.
    - Las fantasías suelen ser **aspiracionales** (capitán, alcalde, luchador valiente, mago sabio); a veces es estar en una situación difícil y sacar lo mejor (The Last of Us); a veces ponerse en los zapatos de otro (Gone Home: una chica que investiga qué pasó en su casa; The Sims: una familia de tu invención).
    - Cada juego crea su **magic circle** (círculo mágico): experiencia novedosa, separada y sin consecuencias dentro de sus límites.
    - **Entrance (entrada, Daniel Cook, Spry Fox)**: el jugador debe entender al empezar qué hace y por qué es interesante. Test de validación: dar a un jugador potencial el concept statement y pedirle que cuente cómo imagina el juego: qué haría, dónde empezaría, cómo terminaría, si valdría la pena. Si no puede armar un modelo mental que pueda relatarte, o no coincide con tu concepto, hay mucho trabajo. Si entiende de inmediato la fantasía y la lleva en la misma dirección que tu diseño, buen comienzo. Mantenerlo informal: es una prueba del concepto, no una forma de que los jugadores diseñen por vos.
    - Se llega a la fantasía desde storyteller (experiencia total primero) o toymaker (unificar mecánicas bajo una experiencia).
  - **Key Moments (momentos clave)**: contar pocas anécdotas breves: cuándo ocurren, cómo mantienen al jugador, cómo lo hacen sentir. Ilustran la experiencia en distintas etapas: **aprendiendo, siendo habitual, habiendo dominado**; y desde puntos de vista de jugadores con distintas motivaciones.
    - Crear **personas** (arquetipos): el jugador experimentado, el apurado, el inseguro, etc. (depende del juego). Para cada una, identificar situaciones importantes: primera victoria y primera derrota; cómo el juego se abre de una manera nueva (nivel 50, segundo castillo, primera moto); qué pasa cuando juegan online con otro; etc.
    - No descuidar la **apertura**: muchos creen que los **primeros 300 segundos (5 minutos)** deciden si el jugador se engancha. No hace falta mapearlos todos, sino los momentos clave que creés (y vas a testear) que enganchan y motivan a seguir.
    - Narrar en texto y dibujos rápidos. Sirven para entender el concepto desde distintos jugadores, recordar por qué se tomaron decisiones, y **testear opciones nuevas contra las personas y key moments**.
    - Poner pocos en el concept doc y apuntar a un documento aparte con más.
  - **Emotions and Meaning (emociones y significado)**: la experiencia total es cómo lo hace sentir. Si no genera respuesta emocional, no engancha. No requiere tocar fibras ni cambiar la visión del mundo, pero debés poder identificar un componente emocional global: logro, escapar sin aire de un desastre, o (como en Tetris) "morí pero mejor que la última vez" / "peor pero sé que puedo mejorar".
    - Algunos juegos buscan emociones sutiles (pérdida, esperanza, gratitud, inclusión, repulsión…). Si dependés de interactividad emocional, hay que diseñar con cuidado experiencia, key moments y sistemas que la soporten: no ocurre solo; creás el espacio y el jugador, si quiere, se acerca.
    - **Meaning (significado)**: ¿deja el juego un significado duradero? Hasta Monopoly enseña un modelo de cómo enriquecerse y qué es el éxito. ¿Qué enseña un shooter sobre la guerra vs. This War of Mine? ¿Qué significado sobre relaciones transmiten Firewatch, Gone Home, The Sims? Se puede elegir un juego liviano sin significado (Candy Crush), pero conviene decidirlo. Ejemplo (Will Wright): el "significado" original de The Sims era que el tiempo es el único recurso no renovable: cuantas más cosas comprás, más tiempo dedican los Sims a arreglarlas → "poseídos por sus cosas".
- **Visual and Audio Style**: describir la intención del arte y cómo apoya el concepto y la experiencia. Cualitativo en palabras ("liviano, aireado, colores brillantes poco saturados"; "tono oscuro, grises y sombras duras en escenas low-poly") **acompañado de imágenes** de concept art o **reference art** (arte de otras fuentes no usado en el juego; uso aceptable como referencia, nunca incluir material ajeno en el juego sin permiso). **Mood boards**: paneles públicos con arte de referencia/concepto para que el equipo capte tono y ánimo.
  - El audio (música y efectos) es al menos tan importante como lo visual: complementa y unifica. Se describe cualitativamente ("tema simple y evocador en violín solo"; "temas de distorsión electrónica en todo el juego, que encajan con el tono visual oscuro y crean atmósfera ominosa"); usar audio de referencia y links en docs online.
  - El detalle va en la **style guide**, no en el concept doc (pero se referencia); puede completarse casi al entrar en producción.
- **Game World Fiction**: breve descripción de la historia de fondo y del mundo; no páginas de detalles, sino una idea del mundo contemplado ("sos una ameba que busca su casa"; "piloto estelar varado en un mundo donde la magia funciona y la tecnología no"). Pocas oraciones sobre qué pasó hasta el comienzo, posiblemente mapa del territorio y breve descripción de NPCs principales. Base para el diseño detallado.
- **Monetization (monetización)**: todo juego comercial debe recuperar costos más ganancia. Pensar al menos en uno de estos modelos:
  - **Premium pricing**: precio único al adquirir; modelo clásico, hoy sin garantía (jugadores reacios a pagar incluso $1); pocos juegos con este modelo recuperan costos fuera de grandes presupuestos (decenas de millones).
  - **Free to play (F2P)**: dominante hoy, sobre todo en móvil; gratis para siempre pero diseñado para incentivar compras (algunos agresivamente); a veces ver un video publicitario reemplaza la compra. **Debe integrarse al diseño desde el principio; no se agrega a último momento.**
  - **Limited-play pricing**: jugar gratis hasta cierto punto (primeros niveles) y comprar para continuar; menos común desde F2P.
  - **DLC**: contenido adicional pago; pregunta clave: ¿podía haberse incluido en el juego original o los jugadores sienten que se lo retuvo para cobrarlo después?
  - **Ad supported**: gratis con anuncios; atractivo por no tener que diseñar F2P, pero los ingresos son magros salvo millones de jugadores regulares.
  - Hay otros modelos (incluso no inventados); si el juego es por encargo/subvención y no hay monetización, anotarlo en el doc para evitar preguntas.
- **Technology, Tools, and Platforms** (lista de qué definir): hardware y sistema operativo (Windows/Mac, móvil iOS/Android, VR/AR/mixta: consecuencias grandes); herramientas de desarrollo (Unity, Unreal u otras: ahorran trabajo pero requieren saberlas y tienen costos y desventajas); servidor y red (aunque sea single player, definirlo de entrada); monetización y publicidad (integración con servidores de ads/pagos; al menos saber si es parte del producto); **localización** (decidir desde el comienzo: es muy difícil retrofitearla una vez avanzado el desarrollo). Si no sabés todas las respuestas, respondé la mayoría y listá el resto como preguntas a resolver rápido.
- **Scope (alcance)**: del concepto y producto se deduce cuántas personas, qué habilidades y cuánto tiempo. Más arte/contenido, más sistemas a crear y balancear, más ítems de monetización y localización → mayor alcance. **Regla**: limitar el alcance de cualquier proyecto, especialmente el primero; hasta productores de equipos de 100+ lo intentan; si hay límite de tiempo/dinero, ser implacable en la priorización.

### 11.3 Sección 3: Detailed design ("Detailed Design")
Es una predicción (aún no está construido): estará algo equivocada, pero es importante. Subsecciones (lista completa): **Core loops; Objectives and progression; Narrative and main systems; Interactivity**.

- **Core Loops**: qué actividades hará el jugador, sobre todo las más repetidas momento a momento (combate, construcción, juntar pétalos…) y **por qué ese conjunto de lazos es enganchador y apoya los objetivos y metas**.
- **Objectives and Progression (objetivos y progresión)**:
  - Viaje del jugador de tutorial a maestría y recorrido espacial (si existe, ej. atravesar un mapa).
  - **Progression vectors**: dimensiones en las que crece el jugador (dinero, habilidad, reputación, poder mágico, provincias, tamaño de tripulación…).
  - Construir **metas inmediatas, de corto plazo y de largo plazo**, soportadas por core loops, narrativa y sistemas principales.
  - Las metas deben apoyar la fantasía y la experiencia del concepto (ej.: juego de asesino → criar erizos es mal objetivo; juego de construir un imperio → describir qué hace el jugador momento a momento para mantener el interés).
  - Si el juego soporta metas **implícitas** del jugador (además de las explícitas), anotar cómo (ej.: poder ser maestro artesano en un juego centrado en combate).
- **Narrative and Main Systems**: narrativa (lo que ocurre durante el juego, en lo que el jugador participa o le ocurre; distinta de la historia de fondo, que mira al pasado) en breve y con puntero a un documento detallado. Describir los **sistemas principales** (combate físico/mágico, economía, ecología, sistemas políticos…), a menudo relacionados con los core loops; indicar cuáles toca el jugador directamente y cuáles viven solo en el modelo del mundo (ej. maquinaciones políticas de fondo que el jugador no puede afectar).
- **Interactivity**: formas de interacción primarias: solo mouse, teclado+mouse, control, touch, mirada, etc. Comentar cómo gasta el juego su **interactivity budget** (acción/feedback rápida o "jugosa"; cognición de corto o largo plazo; emocional, social, cultural) y cómo lo logra visual y sonoramente. No es la UI detallada, pero sí cómo los métodos primarios apoyan la experiencia y dan **suficientes verbos y feedback** para que las acciones afecten los sistemas. Incluir al menos un mockup de pantalla y una lista de interacciones no visibles (tipeadas, gestos, mouse).

## 12. Diseñar el sistema juego+jugador ("Designing the Game+Player System")

- Todo este proceso es el diseño del sistema mayor del que juego y jugador son partes: el **game+player system**. Solo existe si el jugador sigue jugando → el juego debe ser comprensible, disfrutable, y la experiencia envolvente y divertida.
- A nivel conceptual: la idea tiene que ser clara y consistente; si otros no entienden la visión, se vuelve confusa también para los jugadores (si llegás a desarrollarla).

### 12.1 Mantenerse en el tema ("Keeping to the Theme")
- Visión/concepto = marco, restricción y "tejido conectivo". Los elementos temáticos (el "todo") **deben tocar todo el juego**.
- **Regla de poda**: si un sistema o token no deriva su sentido del tema o no lo apoya, se **elimina o se altera** para que encaje. Tema consistente en todo → partes, lazos y todo alineados y unificados → sistema juego+jugador engañoso en el buen sentido (engagement).

### 12.2 Elegancia, profundidad y amplitud ("Elegance, Depth, and Breadth")
- **Elegance (elegancia)**: visión clara y consistente que recorre sistemas, tokens y reglas (del todo a lazos y partes), con pocas excepciones y casos especiales. Cumple la **Ley de Bushnell** (fácil de aprender, difícil de dominar): el jugador arma un buen modelo mental temprano que le sirve sin grandes reajustes; aprender es casi sin esfuerzo subjetivo, cada cosa aprendida suma a la progresión y sensación de maestría, y nunca debe salirse mentalmente del juego para recordar una excepción o regla contradictoria.
- **Depth (profundidad sistémica)**: cuánto tarda el dominio depende de la profundidad sistémica y la amplitud de features. Con elegancia, hay típicamente **sistemas dentro de sistemas**, organizados para que el aprendizaje temprano se aplique al dominio posterior (no se deshaga). Incluso con pocos sistemas simples, el espacio navegable puede ser enorme → se percibe como gran profundidad. Jugadores motivados por explorar reglas y maestría seguirán mientras puedan expandir su modelo mental dentro de su presupuesto de cognición, emoción e interacciones.
- **Breadth (amplitud)**: más features = más formas de interactuar con el mismo contenido/sistemas. A veces **sustituye** a la profundidad sistémica (montañas de contenido para retener al jugador en lugar de sistemas profundos que no requieren tanto contenido) — señal de alerta. Otras veces el alcance requiere una paleta amplia (múltiples clases, vehículos, sistemas de combate, sistemas de recursos/economía/política/combate que interactúan; típico de los "grand strategy").
- Juegos amplios también pueden ser profundos y conservar algo de elegancia, pero sumar amplitud y profundidad casi siempre agrega excepciones y reglas especiales que dificultan el aprendizaje; solo la cantidad de features a atender complica el modelo mental. Eso limita la elegancia en juegos grandes, amplios y profundos, lo cual **no es necesariamente un defecto**: depende de la experiencia deseada y del público (quien busca eso no pide elegancia sin esfuerzo).

## 13. Preguntas a considerar sobre la visión de diseño ("Questions to Consider About Your Design Vision")

Usarlas para chequear que el concepto sea claro y completo antes de definir lazos y partes, y **volver a ellas seguido** para que el diseño no derive. Lista completa (parafraseada):

1. ¿Cuál es tu concept statement en una o dos frases? ¿Captura todos los elementos importantes? ¿Tenés un test de "One Question" para features basado en el concepto?
2. ¿Para quién es tu juego? ¿Qué motivaciones tiene la audiencia? ¿Qué otros juegos disfruta quien juega el tuyo? ¿Hay factores externos/ambientales que afecten cómo se juega (por ejemplo, durante el trayecto al trabajo, o requiere reservar un día entero)?
3. ¿Qué rasgos o aspectos de gameplay lo distinguen de todos los demás? ¿Por qué un jugador objetivo (que ya disfruta este tipo de juego) dejaría uno existente para jugar el tuyo? ¿Qué atraerá el interés inicial y qué del diseño lo mantendrá enganchado a lo largo del tiempo?
4. ¿Cuáles son los sellos de la experiencia de jugarlo? ¿Cómo la caracterizás en motivaciones y emociones?
5. ¿La experiencia parece intencional al jugador? ¿Es un todo cohesivo o un parche mal combinado de conceptos y sistemas?
6. ¿Los jugadores llegan a sentir maestría, o al menos mayor competencia? ¿Cómo saben que progresan en su habilidad?
7. ¿Cómo apoyan el concepto y el gameplay el arte (visual y sonoro)? ¿El arte diferencia al juego de otros similares?
8. ¿Qué sistemas del juego apoyan directamente el concepto y la experiencia?
9. ¿Qué formas de interactividad apoyan la experiencia? ¿Hay interacciones superfluas u oscuras que gravan los recursos cognitivos del jugador?
10. ¿El juego significa algo para el jugador? ¿Tiene corazón, genera emociones? No todo juego necesita significado profundo, pero conviene considerarlo y **preguntarlo en playtests** para ver si el significado percibido coincide con el intencionado.

## 14. Resumen del cap. 6
Crear el concepto del juego e idear un todo intencional, consistente y claro: blue-sky → visión refinada de la experiencia → concept doc con tres secciones, como puntero a diseño detallado y fuerza unificadora. No es obligatorio empezar por el concepto, pero no se puede diseñar ni desarrollar sin él; si sos inventor o toymaker y no te sale natural, hacelo igual antes de desarrollar. Sin entender el marco de lo que construís, se deambula.

---

# APÉNDICE: Listas de uso rápido (para diseñar / analizar / balancear)

## A. Checklist de diseño por niveles
- **Todo**: concept statement, One Question, fantasía, key moments (aprender/habitual/maestría), emoción y significado, estilo de arte/audio, mundo, restricciones. Verificar que cada sistema/token derive del tema; si no, podar.
- **Lazos**: core loops, metas inmediatas/corto/largo plazo, vectores de progresión, lazos de refuerzo y de balance, presupuesto de interactividad, sistemas que operan con y sin el jugador.
- **Partes**: tokens con el mínimo de atributos/estados/comportamientos; valores concretos (hoja de cálculo); balance entre tokens; qué info necesita el jugador (→ UI).
- Rebotar: si atascás en un nivel, cambiá de nivel.

## B. Señales de problema (detección)
- Sistema que los jugadores ignoran (ej. misiones) → entender por qué; quitar o arreglar.
- Excepciones y casos especiales acumulados → pérdida de consistencia/resiliencia.
- Contenido de arco único o hecho a mano que no se reusa; amplitud usada para tapar falta de profundidad.
- Sistemas fracturados que "vuelan separados" por falta de balance entre tokens.
- Mecanismo sin lugar para el humano (inventor); relato sin espacio de juego (storyteller); piezas sin objetivo (toymaker).
- Jugador que no puede describir el juego a partir del concept statement (falla de "entrada").
- Público objetivo "todos"; USPs imposibles de redactar; USPs que son suma de ideas ajenas; género usado como etiqueta vaga o mashup confuso.
- Combinaciones de motivaciones incompatibles en el mismo diseño (inmersión narrativa fina + solo explosiones).
- Interacciones superfluas u oscuras que gastan carga cognitiva.
- Monetización, localización o alcance pensados al final.
- Apego a trabajo hecho por el tiempo invertido; no testear con jugadores nuevos.
- Brainstorm dominado por voces fuertes, grupo homogéneo, sesión maratónica única.

## C. Ejemplos de juegos citados (una línea cada uno)
- Angry Birds: 51 intentos de Rovio; idea simple y enfocada que gusta a millones.
- For Honor: visión de una frase ("combate como danza/arte").
- Spore: prototipos con simulaciones fascinantes (formación estelar) → ejemplo de "inventor".
- Power Grid: sistema de oferta/demanda que opera fuera del control directo del jugador.
- Splendor: fichas pesadas como arte no funcional que refuerza la experiencia.
- Go: pocas reglas, espacio enorme (arquetipo de elegancia).
- Up (Pixar): película que cambió casi todo salvo el pájaro y "up" → iteración.
- Guitar Hero / Rock Band: la "One Question" ("¿rockea?" / "¿experiencia auténtica de estar en una banda?").
- Portal: shooter que no mata y dispara para resolver puzzles → subversión de género.
- Undertale: subvierte el RPG.
- Gratuitous Space Battles / Realm of the Mad God: subgéneros de shooter (espacial 2D top-down / bullet-hell cooperativo masivo).
- World of Tanks: acción-estrategia MMO (género combinado).
- A Dark Room: idle con elementos narrativos; "números que suben" + explorar lo desconocido.
- Rogue: origen del roguelike (niveles procedurales, permadeath).
- League of Legends: ejemplo de excitación/competencia que atrae más a jóvenes.
- The Last of Us: fantasía de hacer lo mejor en una situación difícil.
- Gone Home / The Sims: fantasía de ponerse en zapatos de otro; Firewatch, This War of Mine: significado.
- Tetris: emoción de "morí pero mejor que antes".
- Monopoly: enseña un modelo de cómo hacerse rico (significado incluso en un juego liviano).
- Candy Crush: juego casi sin significado más allá del placer sensorial/puzzle.
- The Sims (Wright): significado "el tiempo es el único recurso no renovable"; más posesiones → más tiempo arreglándolas.
- The Division x Overwatch, GTA meets Undertale: ejemplos de x-statement.

## D. Términos clave (EN) para búsqueda rápida
Qualities of Game Systems (comprehensible, consistent, predictable, extensible, elegant) · game designer's loop · storytellers/inventors/toymakers · thematic architecture · detailed design / spreadsheet-specific · interactivity budget · blue-sky design / ideation · yes, and... · curation · groupthink · concept document (high-level concept, product description, detailed design) · working title · concept statement · The One Question · genre · target audience (psychographics, demographics, environmental context) · Quantic Foundry motivations · Bartle · Big Five · unique selling points · x-statement · player fantasy · entrance · key moments · personas · magic circle · mood board / reference art · style guide · monetization models · scope · core loops · progression vectors · game+player system · Bushnell's Law · elegance/depth/breadth.
