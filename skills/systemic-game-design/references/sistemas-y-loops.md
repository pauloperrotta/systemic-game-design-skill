# Sistemas y loops (caps. 2 y 7)

Leer para DISEÑAR o ANALIZAR la estructura dinámica de un juego: partes (estado, límites, comportamientos), fuentes/stocks/sumideros, loops de refuerzo y de balance, patrones (fixes that fail, límites del crecimiento, tragedia de los comunes), emergencia, jerarquía, los cuatro loops principales, core loops, y los tres tipos de loops de gameplay (motores, economías, ecologías) con sus fallas típicas y cómo corregirlas. Incluye la plantilla de documento de sistema y las preguntas para revisar tus loops.

Resumen parafraseado de Sellers, *Advanced Game Design: A Systems Approach* (2018). Entre corchetes va la sección del libro de donde sale cada bloque.

## Índice
- 2. CAP. 2 - Definir sistemas
- 1. Repaso de loops [A Brief Review of Loops]
- 2. Los cuatro loops principales [The Four Principal Loops]
- 3. Los tres tipos de loops de gameplay [Three Kinds of Gameplay Loops]
- 4. Ejemplos de sistemas de juego [Examples of Game Systems]
- 5. Cómo definir los loops y metas de un sistema [Defining a System's Loops--And Goals]
- 6. Herramientas para diseñar sistemas [Tools for Designing Game Systems]
- 7. Cómo documentar los sistemas [Documenting Your System Designs]
- 8. Preguntas para considerar sobre tus loops [Questions to Consider About Your Game Loops]
- 9. Catálogo de fallas y diagnóstico (síntesis operativa para analizar/balancear)
- 10. Heurísticas y reglas prácticas (lista plana)
- 11. Índice de ejemplos de juegos (una línea cada uno)
- 12. Términos clave (glosario rápido ES -> EN)

---

## 2. CAP. 2 - Definir sistemas

### 2.1 Definición breve y expandida [What We Mean by Systems / A Brief Definition]
Definición corta: **conjunto de partes que juntas forman loops de interacción para crear un "todo" persistente; el todo tiene propiedades y comportamientos propios que no pertenecen a ninguna parte individual.**

Definición expandida (lista del autor):
1. Los sistemas se hacen de **partes**. Cada parte tiene **estado interno** y **límites (boundaries)** externos. Interactúan por **comportamientos (behaviors)** que envían información o (más a menudo) recursos a otras partes para alterar su estado interno.
2. Los comportamientos forman **loops**: locales (A->B) y transitivos (A->B->C->A).
3. Los sistemas se organizan en **niveles integrativos jerárquicos** que surgen de propiedades emergentes de sus estructuras con loops. Cada nivel muestra estado y comportamiento organizados = ser una parte de un sistema mayor.
4. En cada nivel hay **persistencia y adaptabilidad**: no se desarma rápido (se auto-refuerza) y tolera/se adapta a condiciones externas.
5. Comportamiento **organizado, descentralizado pero coordinado**: sin controlador central. El todo es a su vez parte de uno mayor.
Corolario: arriba-abajo y abajo-arriba son equivalentes; el diseñador necesita poder ver el juego bottom-up, top-down o intermedio.
Frase-chiste del autor: "Esta oración es un sistema" (letras y palabras generan significado emergente).

### 2.2 Partes: estado, límites, comportamientos [Defining Parts]

**Estado (state):** combinación de atributos, cada uno con un valor en cada instante. Estado de la parte = agregado de valores actuales; cambia solo si otras partes la afectan.
- En el mundo real el estado emerge de subsistemas más abajo; en un juego a veces igual (el "salud del bosque" = agregado de árboles), pero **en algún punto hay que "tocar fondo"** con pares atributo/valor simples (enteros, strings). Ejemplos: ficha de ajedrez = tipo + posición; monstruo = 10 HP, llamado Steve.
- **"Spreadsheet specific"** (nivel de especificidad de planilla): no podés construir un juego hasta bajar todo lo vago a valores/atributos de planilla. Pero ese piso NO es un techo: podés construir **diseño de segundo orden** agrupando partes simples en subsistemas más ricos para no depender de costosa creación de contenido. Heurística: buscá oportunidades de agrupar partes simples en todos sistémicos mayores.

**Límites (boundaries):**
- El límite es **emergente**, definido por la vecindad de interacción de las subpartes: lo muy interconectado (con loops) forma un subsistema = parte de nivel superior. No hay "piel" explícita (salvo casos como la membrana celular); es difuso.
- **Regla práctica adentro/afuera:** si algo puede cambiar el comportamiento global del sistema, está adentro; si se comunica con una parte pero no puede alterar el comportamiento del sistema, está afuera.
- El límite es una forma de **modularidad** (emergente o impuesta en software): hace partes comprensibles y reusables y evita la tentación del control centralizado ("small pieces loosely joined", Weinberger: la Web; si una página cae el resto funciona).

**Comportamientos (behaviors):**
- Lo que hace una parte: típicamente crear, cambiar o destruir un recurso del sistema, comunicando un cambio de valor a otras partes. Puede afectarse a sí misma (monstruo que se cura solo; interés compuesto).
- **Encapsulamiento:** una parte puede perturbar a otra, pero cada parte decide sola cómo cambia su estado y si ignora el mensaje. Nadie "mete mano" en el estado ajeno. (Implicancia de diseño/arquitectura: eventos/mensajes, no escritura directa.)

### 2.3 Fuentes, stocks y sumideros; flujos; recursos [Sources, Stocks, and Sinks]
(No hay notación canónica; el autor usa términos utilitarios.)
- **Fuente (source):** parte que incrementa el estado de otra. Típicamente supuesta inagotable. Su estado interno = tasa de generación (ej.: 2 unidades/seg). No guarda nada; genera y pasa.
- **Stock:** acumula un recurso; su estado = cantidad en un instante. Puede tener tope (la bañera). Ejemplos: bañera, cuenta bancaria, HP, provincias de un imperio.
- **Sumidero (sink):** la salida del stock; pasa una cantidad por unidad de tiempo; si el stock está vacío no puede pasar nada (a diferencia de la fuente).
- **Flujo (flow):** el conector entre partes; transporta mensajes o, más comúnmente, un recurso.
- **Recurso (resource):** cualquier cosa contable, almacenable o intercambiable, aunque no sea física (HP, provincias).
- **Convertidores (converters):** transforman un recurso en otro/proceso. **Deciders (deciders):** miden y deciden (¿muy lento? ¿muy rápido?) y retroalimentan para acelerar/frenar. Fuente->proceso->sumidero + deciders = el regulador centrífugo; es lo que vuelve el esquema "sistémico" (cierra un loop).
- Hay que **trazar los límites del diseño**: lo de afuera se modela como fuente/sumidero ilimitado (ej.: asumir agua y electricidad externas). En juegos, hay que especificar todas las fuentes (faucets) y sumideros (drains) y cómo afectan al juego.

**Economía faucet/drain (Ultima Online, Fig. 2.3):** MMO temprano modelado como faucet (spawns, NPCs que compran, pago en oro) -> stocks (recursos naturales, materias primas, bienes, inventario, vendedores) -> drain (decay, degradación, venta a NPC, manufactura fallida).
- Problemas: (a) los stocks de jugadores son ilimitados y la salida no está garantizada (un jugador acumuló 10.000+ camisas; cada objeto hay que rastrearlo); (b) **inflación**: el oro se crea ex nihilo cada vez que se mata un monstruo o se vende a un NPC; si la masa de oro crece más rápido que lo que drena, cada unidad vale menos para el jugador.
- Heurística de balance: para cada recurso listá faucets y drains con su tasa; si faucets > drains en el estado estable, hay inflación/acumulación; hay que poner drains o topes a los stocks.

### 2.4 Complicado vs complejo [Complicated Versus Complex]
- **Colección simple (simple collection):** partes sin comportamientos que afecten el estado de las otras (bolsa de ladrillos, frutero). No es sistema.
- **Proceso complicado (complicated process):** muchas partes e interacciones, pero conectadas en **secuencia lineal sin loops**. Predecible y repetible; cuando falla suele poder rastrearse a una causa y reemplazar la pieza (se puede aplicar pensamiento reduccionista). Ejemplos: péndulo simple, línea de montaje, cohete a la Luna (fases sin efecto hacia atrás).
- **Sistema complejo (complex system):** las partes forman **loops**; el comportamiento de una parte vuelve a alterar su propio estado futuro (A->B->C->A, con retardo). No se puede "desenrollar" el loop sin destruir su naturaleza. Ejemplos: cuerpo humano, economía, huracanes, termiteros, péndulo doble, muchos juegos.
- **Implicancia para juegos:** juegos de niveles secuenciales son más complicados que complejos: lo que pasa en el nivel 10 no afecta al nivel 2; el nivel jugado pierde valor y exige crear más contenido. (Ver 3.8 contenido vs sistemas.)
- Señal de diagnóstico: si cuando algo falla podés rastrear una única causa -> complicado. Si el problema es distribuido/circular -> complejo, hay que analizar el sistema entero.

### 2.5 Loops [Loops]
Los loops son "las estructuras más importantes de los sistemas y de los juegos". Dos tipos básicos:

**Loop de refuerzo (reinforcing loop, feedback positivo):** cada parte aumenta la salida de la siguiente. Si un sistema no tiene al menos un loop de refuerzo primario, tiende a extinguirse (excepción: estabilidad por oposición mutua, como contrafuertes). En juegos: premia a los que van ganando, magnifica el éxito temprano, **desestabiliza**, puede producir ganador desbocado si alguien lo capitaliza apenas mejor. Nombres: "snowball", "rich get richer", "vicious cycle" (si todo va para abajo es igual refuerzo, no balance).
- Ejemplos: interés bancario (saldo -> interés -> saldo); **Monopoly** (más efectivo -> más propiedades -> más renta -> más efectivo).

**Loop de balance (balancing loop, feedback negativo):** cada parte reduce la actividad de la siguiente; mantiene o restaura equilibrio. En juegos: **perdona al que va atrás, estabiliza y prolonga la partida**, evita que el que va primero se despegue para siempre.
- Ejemplos: termostato de horno; **XP en RPG** (cada nivel nuevo sube el XP necesario para el siguiente -> reduce la velocidad de subir niveles); **blue shell / spiny shell de Mario Kart** (item aleatorio para quien no es primero que ataca específicamente al primero y lo voltea).

Notación: en diagramas causales, flecha con "+" = más del origen -> más del destino; "-" = más del origen -> menos del destino. Los nodos son stocks.

**Todo sistema tiene ambos tipos.** Regulador centrífugo: reacciona en ambos sentidos. Pero el output casi siempre es **no lineal** respecto del input, y eso lo hace interesante.

### 2.6 No linealidad: depredador-presa [Combined, Linear, and Nonlinear Effects]
Ejemplo lince-liebre (lynx-hare): liebres se reproducen (refuerzo, lazo chico) y los linces las comen (balance, lazo grande). Resultado emergente: **oscilación no lineal desfasada** (picos de presas, luego de predadores, luego caen las presas, luego los predadores...). Los predadores nunca son tan numerosos como las presas.
- Razón de la no linealidad: matar una presa quita también toda su descendencia futura (efecto multiplicativo, no aditivo).
- Regla: **no extrapoles linealmente** una cantidad creciente; "si seguimos así..." casi nunca se cumple.
- No toda no linealidad es periódica; puede ser caótica (péndulo doble).

**Ecuaciones de Lotka-Volterra (modelo matemático):**
- Presas: dx/dt = a*x - b*x*y (crecen a*x; mueren b*x*y, proporcional a encuentros presa-predador).
- Predadores: dy/dt = d*x*y - g*y (ganan d*x*y según comida disponible y eficiencia de conversión; mueren g*y).
- Parámetros: a (alfa, natalidad presa), b (beta, tasa de predación exitosa), d (delta, eficiencia de convertir comida en cría), g (gamma, mortalidad predador).
- Datos reales (MacLulich 1937, Canadá) muestran oscilaciones parecidas pero más ruidosas.

**Matemático vs sistémico (Mathematical Versus Systemic Modeling):**
- El modelo matemático es conciso pero opaco: trata las partes como símbolos agregados y los parámetros como **knobs** (perillas) de una caja negra, con efectos no obvios.
- En diseño sistémico, esos parámetros agregados deberían **emerger** de interacciones de estados internos de las partes (ej.: la tasa de predación sale de ataque del lince vs defensa de la liebre), con lo cual el modelo es más comprensible y matizado.
- Aun así, hay que decidir el nivel más bajo de detalle y ahí poner parámetros (incluyendo valores aleatorios) como representación de lo que está debajo.
- Todo modelo es una aproximación (maqueta vs barco real): su valor es ser útil, no exacto. En juegos, "estás haciendo un modelo de una parte del mundo".

### 2.7 Azar vs caos [Chaos and Randomness]
- **Efecto aleatorio (random):** valor impredecible dentro de un rango (ej.: 1-10 con 10% cada uno); el estado futuro no se deduce del actual. En juegos sirve para **simular sistemas de bajo nivel que no se modelan** (daño variable en vez de simular 1.000 factores) y para dar variabilidad al sistema superior para que no sea predecible y aburrido.
- **Efecto caótico (chaotic):** **determinista** (en principio predecible si conocés todo el estado) pero hipersensible a condiciones iniciales (péndulo doble). No se puede analizar desarmándolo; hay que analizar el todo (subpartes + relaciones, o matemática).
- **Eventos de resonancia (resonance events):** muchos pequeños eventos caóticos se combinan en un loop de refuerzo y producen un resultado no lineal enorme.
  - Puente Tacoma Narrows (1940): el viento hace oscilar el puente, la oscilación aumenta la captura de viento -> colapso (loop de refuerzo dominante).
  - Puente Albert (Londres): cartel pidiendo romper el paso a las tropas (pasos sincronizados -> resonancia).
  - Luciérnagas sincronizadas: cada una adelanta un poco su destello al ver otro; sin director, la población pasa de caos a resonancia (parches -> olas -> unísono). También células nerviosas del corazón. Lección: orden sincronizado emergente desde una sola regla local.

### 2.8 Patrones de loops (arquetipos) [Examples of Loop Structures]

**a) Fixes that fail / consecuencias no intencionadas (unintended consequences loop):**
- Cobra effect: problema "demasiadas cobras" -> solución "recompensa por cabezas" (loop de balance interno) -> pero un loop externo de refuerzo **con retardo** ("¡criemos cobras!") trae el problema de vuelta empeorado (al cancelar la recompensa se soltaron más cobras que antes).
- Rasgos para detectar: una solución rápida que funciona al principio; un segundo loop lento y oculto (delay marcado con "\\" en el diagrama) que revierte el efecto; el problema termina peor y se gastó tiempo/energía en una solución ilusoria. Ejemplos: no mantener el auto para ahorrar; el gerente que hace arreglos rápidos y es ascendido.
- En juegos: el jugador de estrategia que hace ejército grande rápido pierde contra quien invierte en mejorar tropas; la elección **"build fast now" vs "invest for the future"** es una estructura llamada **engine** (se ve en el cap. 7). Para el diseñador: cuidado con reglas/recompensas que los jugadores pueden explotar con un loop que vos no previste (el equivalente a "criar cobras"); y con parches de balance que traen efecto rebote retardado.

**b) Límites del crecimiento (limits to growth) y colapsos posteriores:**
- Dos loops enlazados: uno de refuerzo (acciones -> resultados -> más acciones) y uno de balance fuente de una **condición limitante** (recurso necesario que el crecimiento consume: mercado saturado, mineral del suelo, capacidad de pago).
- Resultado: **curva en S** (sube lento, rápido, y se aplana). Ejemplo: rendimientos de trigo que se aplanan desde los 90s. Regla: para todo crecimiento alimentado por refuerzo hay un balance alimentado por una condición limitante; **buscala siempre**.
- A veces el límite aparece **abruptamente** y se dispara un refuerzo en sentido inverso ("vicious cycle"): crack de 1929 (compra a crédito "on margin", 10-20% de reserva; al caer los precios hay que vender más para cubrir, lo que baja más los precios). Ejemplo actual (2017): préstamos subprime; concentración de riqueza empuja inversores a riesgo y prestatarios a más deuda; dos refuerzos no sostenibles.
- Para juegos: toda mecánica de crecimiento exponencial (economía, poder del personaje) necesita su condición limitante diseñada; si el límite es abrupto, el colapso puede ser una espiral de muerte.

**c) Tragedia de los comunes (tragedy of the commons):**
- Cada actor tiene su propio loop de refuerzo (más ganado -> más valor); todos consumen un recurso compartido con límite; el uso total forma un loop externo de balance que agota el recurso para todos. Nadie lo quiere ni se siente responsable (basura, contaminación).
- Lección: **responsabilidad sistémica = responsabilidad distribuida**; no hay "villano" ni causa raíz única.
- En juegos: cualquier recurso limitado que varios quieren maximizar (mina de oro, animales). Ejemplo: jugadores cazan conejos para comer -> colapsa la población -> sin conejos se mueren los linces -> se pierde la plaga que controlaban.

**d) Cascada trófica (trophic cascade)** (Yellowstone): serie de loops de refuerzo y balance en cadena; el lobo reduce al alce (balance) y por lo tanto aumenta indirectamente árboles, osos, etc. (refuerzo transitivo). Método para desenredar: identificar stocks/recursos y las relaciones de comportamiento (flechas) entre ellos.

### 2.9 Emergencia [Emergence]
- Cuando loops de refuerzo y balance están en equilibrio dinámico, hay **metaestabilidad** y aparecen comportamientos organizados que no están en ninguna parte (bandada, molécula, luciérnagas sincronizadas).
- **Efecto emergente:** propiedades cualitativamente distintas de las partes, no suma simple.
- **Ejemplo del cardumen (school of fish):** el peso total del cardumen NO es emergente (suma); la **forma** (baitball) SÍ: no está en ningún pez, no hay un pez a cargo.
- **Test de emergencia** (tres condiciones; si se cumplen, hay una "nueva cosa"): (1) no la determina ninguna parte individual; (2) no es la suma lineal de atributos de las partes; (3) se describe más fácilmente por la agregación que por el detalle de partes y relaciones.
- No hay un "controlador central" ("no fish in charge"): hasta científicos asumieron "células fundadoras/marcapasos" en mohos que se agregan; hubo que aprender a ver el control distribuido. Vale para diseño: resistir la tentación de poner un director/controlador omnisciente cuando basta una regla local.
- **Causalidad ascendente (upward causality):** las interacciones de las partes causan el fenómeno agregado (compras individuales -> mercado sube).
- **Causalidad descendente (downward causality):** el agregado afecta a las partes (el mercado en caída hace que cada uno venda más; el tamaño/forma del cardumen condiciona a cada pez). Explica burbujas/crashes "irracionales". Al desarmar un sistema ves la causalidad ascendente pero perdés la descendente (solo existe con el sistema funcionando) -> el análisis reduccionista no basta.
- Nota de diseño del autor (cap. 3): la falta de tema/meta intrínseca = ausencia de causalidad descendente de diseño (ver No Man's Sky).

### 2.10 Jerarquía y niveles de organización [Hierarchy and Levels of Organization]
- Un sistema metaestable crea una "cosa nueva" de **nivel superior**; sus propiedades (estado, límites, comportamientos) emergen de las interacciones de los niveles inferiores. Quark -> protón -> átomo -> molécula -> ... planeta -> galaxia.
- Todo sistema es parte de uno mayor, interactúa con pares y contiene sistemas menores. **En juegos podés elegir los niveles de abstracción**; hacerlos más profundos que superficiales tiene recompensas.
- Los niveles son emergentes, no absolutos.
- **Persistencia** = "límite a través del tiempo": el sistema se autorrefuerza dentro de sus límites. **Adaptabilidad:** tolera señales/inputs cambiantes. En seres vivos: **homeostasis** (mantener condiciones internas en rango estrecho pese a cambios externos).
- **Acoplamiento estructural (structural coupling, Maturana):** dos sistemas que interactúan recurrentemente se moldean mutuamente hasta formar un sistema superior integrado (jinete-caballo, auto-conductor, flor-insecto). **Juego + jugador** forman un acoplamiento estructural: si el juego tiene un espacio de estados amplio y diverso (diseño de segundo orden), se adapta al jugador mientras el jugador se adapta a él; esto genera enganche (cuesta salir de los loops).

### 2.11 Profundidad y elegancia [Systemic Depth and Elegance]
**Profundidad (depth):** el sistema tiene partes en múltiples niveles de organización (partes que son subsistemas). Auto-similitud (self-similarity, fractales/romanesco) = manifestación visual de la profundidad.
Beneficios de juegos con profundidad:
- El jugador construye modelos mentales multinivel y es recompensado por aprender cada subsistema ("abrir un regalo y encontrar otro adentro").
- Gran variabilidad explorable porque el diseñador definió un espacio amplio (diseño sistémico) y no un camino estrecho de contenido.
- Pueden tener **pocas reglas** (Go: tablero + piedras alternadas + capturar/rodear + territorio) y ser muy profundos. **Ley de Bushnell (Bushnell's Law):** fácil de aprender, difícil de dominar: pocas reglas iniciales, cada una se abre en subsistemas a medida que se aprende.

**Elegancia (elegance)** - cuando se combinan:
1. Uniformidad **metaestable**, no estática: el juego cambia en cada partida pero conserva una familiaridad global (tema/experiencia).
2. Sistemas de alto nivel **simples de definir pero con gran profundidad jerárquica**: el jugador descubre la profundidad gradualmente y construye modelo mental; da lugar a comportamientos complejos que a su vez revelan sistemas y tema.
3. **Simetría / auto-similitud:** cada sistema inferior refleja la estructura del superior; no deben ser idénticos, pero lo bastante parecidos para que el nivel de arriba sirva de **andamio (scaffolding)** de aprendizaje -> sensación de "casi ya lo sé".
4. **Pocos cabos sueltos:** pocas excepciones y casos especiales (rompen la simetría mental y suben la carga cognitiva).
5. El jugador, tras aprenderlo, puede reflexionar (metacognición) y apreciar la profundidad y simetría; el juego se disfruta también al pensarlo.
- Es raro; requiere que el diseñador vea todo a la vez y también linealmente como lo vive el jugador.

### 2.12 El todo del diseño [Wholes]
- El todo que el diseñador persigue **no es el juego solo, sino el sistema game+player** (juego-tal-como-se-experimenta + jugador actuando). El juego es el medio.

### 2.13 Resumen operativo cap. 2 (definición final)
Sistema = todo integrado de partes independientes e interactuantes, con estado interno, límites y comportamientos; el todo persiste, se adapta a condiciones externas, tiene comportamientos coordinados emergentes, contiene sistemas de nivel inferior y es parte de uno superior. Las cosas y los sistemas son lo mismo (un matrimonio, una universidad, una conversación son "cosas" reales y metaestables).



- Un sistema es más que la suma de las partes cuando las partes se conectan en **loops** (bucles); de ahí sale el comportamiento emergente y el gameplay interesante. [More Than the Sum of the Parts]
- "Systems design" (diseñar sistemas) = construir loops efectivos a partir de partes que interactúan para obtener la experiencia total deseada. No es solo "hacer el sistema de combate": es todo el andamiaje que genera la experiencia.
- Jerarquía de trabajo del diseñador: **partes -> loops -> todo**. Hay que oscilar entre los tres niveles todo el tiempo.
- Un juego es casi siempre una combinación de sistemas en distintos niveles jerárquicos; cada sistema es una parte de un sistema mayor (sistemas de sistemas, loops dentro de loops).
- Qué hace el diseñador con esto: (1) identificar, (2) analizar, (3) crear sistemas, descomponiéndolos en sus loops constitutivos. [Summary]

---

## 1. Repaso de loops [A Brief Review of Loops]

### 1.1 Tipos de colección de partes (cap. 2)
- Simple: partes que no se afectan (fruta en un bowl).
- Complicado: conexión lineal (proceso).
- Complejo: partes con interacciones que **vuelven sobre sí mismas** (loops). Solo los loops dan emergencia.

### 1.2 Reinforcing vs Balancing loops
- **Reinforcing loop (loop de refuerzo / "feedback positivo")**: la interacción refuerza el estado de las partes. "Positivo" no significa bueno: refuerza la cualidad que sea (interés compuesto = bueno; contagio de enfermedad = malo). Ejemplos: interés bancario, epidemia, Monopoly.
- **Balancing loop (loop de balance / "feedback negativo")**: el efecto de una parte sobre otra empuja todo hacia un punto de equilibrio. Ejemplos: termostato/horno (a menor brecha de temperatura, menos calor), depredador-presa, aumento de XP requerida por nivel en RPGs (equilibra el tiempo para subir).
- Casi todo balance en juegos es **dinámico, no estático** (dynamic balance). Ejemplo físico: el regulador centrífugo (governor): acelerador abierto -> motor más rápido -> pesas se abren -> acelerador cierra -> motor más lento -> pesas bajan -> acelerador abre... oscila dentro de un rango aceptable.

### 1.3 Usos en diseño
- **Reinforcing = recompensa a los ganadores / runaway / "rich get richer"**. Ejemplo: Monopoly (más plata -> más propiedades -> más plata). Falla de compromiso: el que gana atiende cada vez menos para seguir ganando; el que pierde tiene cada vez menos opciones. El espacio de decisión colapsa en ambos -> el juego deja de ser psicológicamente enganchante.
- **Balancing = reduce diferencias entre jugadores** ("perdonar al que pierde, castigar al que gana", o ambas). Ejemplos: turnos con ventaja al que anotó (posesión en fútbol americano/básquet); Power Grid (el jugador mejor posicionado juega último: balancing loop permanente contra los loops de refuerzo de plata/plantas/ciudades).
- Regla práctica: en la mayoría de los juegos predominan los reinforcing loops (progresión: el avatar se vuelve más poderoso); los balancing loops sirven de freno/regulación. [Three Kinds of Gameplay Loops]

### 1.4 Partes como componentes de loop (vocabulario base)
(Detalle de partes en cap. 8; aquí lo mínimo para armar loops.)
- **Resources (recursos)**: objetos que se pasan entre partes del loop. Todo lo *contable* en el juego (oro, maná, agua en una bañera, madera, tropas), sobre todo si se crea, destruye, almacena o intercambia.
  - **Simple resources**: elementales y fungibles (oro, madera, maná): una unidad vale como otra.
  - **Complex resources**: se ensamblan de otros y tienen propiedades asignadas por el juego (una espada hecha de madera + metal; un ejército = conscriptos + espadas + armaduras).
  - **Production chains (cadenas de producción)**: madera + metal -> espadas/armaduras -> + reclutas -> ejército. Ej.: Terraria, Banished: profundidad sistémica por largas cadenas de combinación.
- **Currencies (monedas)**: tipo de recurso que se **intercambia pero no se consume** (el oro pagado a un vendedor no "se vuelve" el arma; el vendedor lo reutiliza). Diferencia clave con recursos normales (que se consumen en la conversión). En simulación se asume que se gasta en otra cosa fuera del sistema; en muchos juegos el oro directamente desaparece en un sink.
- **Sources (fuentes / "faucets")**: de dónde vienen los recursos; pueden ser un lugar (mina de oro) o conceptuales (matar monstruos da XP). Suelen crear recursos *ex nihilo*; modelar el oro enterrado agrega carga cognitiva sin diversión salvo que ese sea el punto del juego.
- **Stocks (reservas / "pools")**: contenedores de recursos. Estado = cantidad actual; comportamiento = tasa de flujo hacia otra parte. Los recursos fluyen de la fuente (u otro stock) al stock a cierta tasa hasta un límite. Ejemplos: plata en el banco, HP, población de un pueblo. Algunos tienen máximo (bañera), otros no (cuenta bancaria).
- **Converters (conversores)**: transforman un recurso en otro (el original desaparece, se crea el nuevo). Son el "verbo" básico de cómo algo pasa a ser otra cosa. Pueden ser una caja mágica (hierro -> acero) o un proceso con múltiples entradas/salidas (metal + madera + herramientas + habilidad + tiempo -> espada + desechos como escoria/calor). Decisión de diseño: más detalle de conversión da más gameplay (¿cómo manejo la acumulación de desechos?) o es carga mental inútil.
- **Deciders (decisores / puntos de decisión)**: ramas lógicas donde el flujo va por un camino u otro según lógica interna, cantidad de un recurso o condiciones externas. **Regla**: mantener las condiciones del decider lo más *locales* posible (a su mismo nivel de organización; como máximo un nivel arriba o abajo). Mayor distancia jerárquica = sistema más **brittle** (frágil).
- **Sinks (sumideros / "drains")**: opuesto de la fuente; los recursos fluyen hacia afuera. No importa a dónde van: lo de más allá del sink está fuera del sistema (simplificación válida para diseñar).

### 1.5 Iconografía (adoptada de Joris Dormans / Machinations; no universal) [Iconography]
- Triángulo hacia arriba = source.
- Círculo = stock (cantidad: fichas individuales, sombreado de cuán lleno está, etc.).
- Triángulo con una línea = converter.
- Rombo = decider.
- Triángulo hacia abajo = sink.
- Flechas = flujo entre ellos. Los diagramas de loops se dibujan con estos símbolos; no hace falta dominar todo Machinations para usar los conceptos.

---

## 2. Los cuatro loops principales [The Four Principal Loops]

Lista completa (los cuatro que el diseñador debe tener en mente):
1. **Game's model loop** (loop del modelo del juego).
2. **Player's mental loop** (loop mental del jugador).
3. **Interactive loop** (loop interactivo juego-jugador).
4. **Designer's loop** (loop del diseñador).

### 2.1 The Game's Model Loop
- El juego tiene un modelo interno del mundo, **dinámico y en loop** (si fuera estático o lineal no habría interactividad ni gameplay).
- Ese modelo crea el mundo que ve el jugador y el espacio de gameplay. Pocos caminos viables = **probability space** angosto = pocas decisiones significativas = sin gameplay, sin engagement, sin diversión.
- Diseñar el modelo vía *second-order design* crea el espacio de exploración del jugador.
- El modelo = combinación de todos los sistemas del juego; tipos: **engines, economies, ecologies**. De ahí salen sistemas conocidos: progresión, combate, inventario, skills, misiones, etc.

### 2.2 The Player's Mental Loop
- El modelo mental del jugador también es dinámico y en loop. Se construye mientras juega (y hay que mantenerlo enganchado mientras lo construye) y debe **coincidir de cerca** con el modelo interno.
- Si las acciones tienen efectos inesperados o, peor, aleatorios, el jugador no puede construir ni verificar su modelo -> experiencia sin sentido, no enganchante.
- Incluye las metas **explícitas** (que el juego pone) y las **implícitas** (que el jugador se pone). La sensación de progreso al lograrlas suele venir de uno o más sistemas de progresión.

### 2.3 The Interactive Loop
- Ciclo juego<->jugador: el jugador actúa, el juego da feedback, el jugador aprende. Subsume tanto el modelo del juego como el modelo mental (cada uno es subsistema de este loop).
- Acciones del jugador = input al loop del juego; el cambio de estado se comunica de vuelta = input al modelo del jugador.
- **Hasta que este loop existe, el juego no existe funcionalmente.** Los sistemas solos no crean la experiencia. "Cerrar el loop" (que el jugador pueda decidir, actuar y recibir feedback del modelo interno) es el primer indicio de que la experiencia buscada podría existir.
- Se extiende a multijugador: cada jugador debe predecir al juego *y* a los otros jugadores; el juego es el árbitro del círculo mágico. El juego muestra cómo se expresan los planes de otros vía sus estructuras, no los planes mismos.

### 2.4 Core Loops (loops núcleo) [Core Loops]
- **Core loop** = interacciones juego-jugador que forman el foco principal / atención central del jugador. Secuencia: forma una intención -> la ejecuta -> cambia el modelo interno -> feedback (a menudo más habilidad o información) -> aprendizaje (modelo mental actualizado) -> nueva intención.
- Mínimo **un** core loop; puede haber varios en **distintas escalas de tiempo** (ver los tipos de interactividad del cap. 4: Action/Feedback, Short-Term Cognitive, Long-Term Cognitive, Social, Emotional, Cultural; Fig. 7.2). Ej.: RPG con combate rápido (action/feedback + short-term cognitive) como loop primario y adquisición de skills a largo plazo como loop externo. Cambia el core loop cuando cambia la atención (de combate a elegir skills).
- **Inner / outer loops**: internos = cortos y rápidos; externos = largos. "Core" no significa el más rápido o más interno, sino **el más importante para la experiencia del jugador en ese momento** (a veces: donde pasa más tiempo, o el que el diseñador cree que da más valor; el uso del término no es consistente).
- Estrategia: el jugador alterna construir edificios -> hacer unidades -> pelear -> investigar; ese core loop está hecho de core loops más cortos.

**Ejemplos de core loops (una línea cada uno):**
- *Clash of Clans*: tres loops - collect (clic en fuentes, guardar en stocks hasta un límite), battle (alta tensión, decidir cuándo/dónde desplegar tropas; vuelve con oro/elixir/ranking), build & train (baja tensión, gasta oro/elixir en edificios que son fuentes - minas, recolectores -, productores de unidades o stocks). Límites: tasa de las fuentes, capacidad de almacenes, cupos de entrenamiento; mejorar edificios limitado por el nivel del Town Hall. **Palanca F2P**: construir y entrenar toma tiempo; las gemas (ganadas o compradas con dinero real) aceleran o compran recursos = "plata por tiempo". Metas anidadas: "mejoro el almacén para poder mejorar el Town Hall para mejorar los cuarteles...". Capa social externa: clanes. Cada decisión de gasto es parte de un reinforcing loop (más/mejores unidades) y de un balancing loop (gastar bloquea otras decisiones) -> decisiones significativas.
- *Marvel War of Heroes*: dos reinforcing loops elegibles, PvE (misiones) y PvP (oponentes), con balanceadores internos distintos (stamina en PvE, attack power en PvP) que limitan cuántas vueltas se dan sin descansar o pagar recarga. Loop externo: combinar/mejorar héroes (feedback instantáneo vistoso + trade-offs estratégicos a largo plazo) -> mejor desempeño -> más recompensas -> más mejoras; es la principal oportunidad comercial.
- *Boomshine*: un solo clic por nivel y ver el resultado; juego corto, pero el jugador crea su propio outer loop (rejugar para mejorar su modelo/habilidad).
- Patrón recurrente: **loop de acción/tensión alta** (batalla, puzzle) + **loop de construcción/crafteo/comercio de baja tensión**. El primero usa action/feedback y short-term cognitive; el segundo long-term cognitive, emocional, social. (Analogía biológica del autor: sistema simpático "lucha o huye" vs. parasimpático "descansar y digerir".)
- El mismo diagrama de loops puede dibujarse más abstracto o más detallado: **el nivel de detalle debe elegirse según qué es más informativo para la audiencia** (devs, negocio, jugadores).

**Resumen**: si los core loops cubren varias duraciones de interactividad, el juego engancha de inmediato y por mucho tiempo. Juegos simples = un core loop, experiencia corta.

### 2.5 Game Mechanics (mecánicas) [Game Mechanics]
- Definición sistémica: una **mecánica** es un loop interactivo identificable entre jugador(es) y juego, en general independiente del contexto del juego (robar carta, control de territorio, saltar en plataformas, push your luck, tirar dados, gestión de recursos). Puede ser rápida y simple sin subsistemas, o larga y compuesta.
- Sin esta definición las mecánicas quedan como "trozos difusos de gameplay".
- **Core mechanic / core gameplay**: la mecánica que el jugador encuentra repetidamente (incorpora el chunk significativo + la idea de core loop).
- Los **géneros** se forman cuando muchos juegos repiten mecánicas parecidas (plataformas: saltar + doble salto, plataformas móviles, wall jump; RPG: combate, loot, ganar poder). La familiaridad ayuda al jugador a armar su modelo mental.
- El autor no hace lista de mecánicas; prefiere ver los tres tipos de loops (engines, economies, ecologies) y combinarlos.
- Listas de patrones existentes citadas: Bjork & Holopainen (2004), Adams & Dormans (2012). Muchos diseñadores las encuentran de poca utilidad y prefieren patrones generales como bloques jerárquicos.

### 2.6 The Designer's Loop [The Designer's Loop]
- Es el loop más externo. El diseñador ve **game + player como un sistema unificado desde afuera**; ambos son subsistemas necesarios.
- Es un **balancing loop**: diseño -> experimentado por el jugador -> feedback -> brecha entre intención del diseñador y experiencia del jugador -> el diseñador cambia el diseño para reducir la brecha -> repetir.
- Creer, testear y ajustar el modelo interno es la esencia del diseño. **Hasta que se ve a jugadores interactuando con el juego, el juego "no existe"**: un conjunto de reglas no es un juego; ni siquiera una simulación (modelo que corre solo) lo es. Recién con el sistema game+player operando existe el designer's loop (se detalla en el cap. 12: prototipos y playtests).

### 2.7 Niveles y jerarquía [Levels and Hierarchy]
- Los sistemas contienen sistemas. Interactive loop tiene como partes al juego y al jugador; el interactive loop es parte del designer's loop (junto con los planes y metas del diseñador).
- Habilidad crítica: construir sistemas de sistemas **sabiendo en qué nivel estás trabajando sin perder de vista la experiencia total**.
- **Ejemplo ciervos/lobos (Fig. 7.6 y 7.7):**
  - Nivel bajo (Fig. 7.6): sistema de ciervos con loop principalmente reinforcing (más ciervos adultos -> más nacimientos) con componente balancing (más ciervos -> menos comida -> menos nacimientos). La comida entra como source externa; la muerte es sink. Los bordes del sistema se marcan con círculo punteado.
  - Nivel alto (Fig. 7.7): el sistema de ciervos entero pasa a ser **un stock** dentro de un sistema mayor con lobos y plantas. Más ciervos -> más lobos (a costa de ciervos: mini balancing loop); ciervos vs. plantas (otro balancing); ciervos y lobos muertos -> suelo -> plantas (**reinforcing loop ciervo-suelo-planta**, que podría desbocarse, pero lo frenan los ciervos comiendo plantas y los lobos comiendo ciervos). Las **tasas de crecimiento distintas** de plantas, ciervos y lobos son lo que balancea el conjunto. El sistema de ciervos tenía source y sink externos; en el nivel alto se vuelven stocks que pueden ser sistemas por sí mismos.
  - Lección: lo que era "externo" (source/sink simple) en un nivel pasa a ser parte del sistema en el nivel de arriba. Un diagrama a nivel más abstracto encapsula al anterior.

---

## 3. Los tres tipos de loops de gameplay [Three Kinds of Gameplay Loops]

Cada sistema es "una máquina que hace X" ("quiero una máquina que haga ciervos", "una ecología ciervo-lobo"). Hace algo porque sus partes (a menudo sistemas) interactúan en estructuras de loops.

Los sistemas mezclan reinforcing y balancing según su propósito. En la mayoría de juegos **predominan los reinforcing** (permiten la ganancia/progresión del jugador). El comportamiento de las partes suele ser aumentar, disminuir, fluir, convertir o intercambiar recursos entre partes; el loop puede usar el mismo recurso o convertir/intercambiar uno por otro.
- Reinforcing = "ganar" (recursos crecen con el tiempo); balancing = "mantener" (recursos bajan a un nivel predeterminado o a un balance dinámico).

**Taxonomía (dos ejes: reinforcing/balancing x mismo recurso/recursos intercambiados):**
| Tipo | Naturaleza |
|---|---|
| **Engines** | Reinforcing o balancing con el **mismo** recurso |
| **Economies** | Reinforcing **intercambiando** recursos |
| **Ecologies** | Balancing **intercambiando** recursos |

### 3.1 ENGINES

Dos variantes: **boosting** (refuerza; agrega recursos al juego) y **braking** (balancea; los drena).

#### 3.1.1 Boosting engine (motor de impulso)
- **Qué es**: sistema que agrega recursos al juego y deja al jugador elegir entre **usarlos ahora para actuar** o **invertirlos para tener más flujo en el futuro**. (Adams & Dormans lo llaman *dynamic engine*; una source simple = *static engine*.)
- **Piezas**: source -> recurso fluye -> decider (jugador: ¿construyo engine o uso el recurso?) -> rama A: "aumentar el flujo de la source" (inversión; cierra el reinforcing loop) / rama B: "actuar en el juego" (termina en sink, con recompensa de corto plazo y recurso gastado). Fig. 7.8.
- **Decisión núcleo**: cuándo invertir vs. cuándo actuar. Tiende a long-term cognitive (estratégico) cuando es core loop. Si no se juega estratégicamente se pierde; si se invierte demasiado y se actúa poco, también se puede perder.
- **Ejemplos**:
  - *Monopoly*: $1500 iniciales, $200 de la banca por vuelta (source); inviertes en propiedades que generan más plata; engine secundario: casas/hoteles con monopolio de color. Razones para no invertir: esperar una propiedad mejor, tener cash para pagar renta/costos.
  - *Dominion, Power Grid, Splendor*: engine building de mesa. Splendor: las cartas compradas con gemas dan gemas "gratis" cada turno (más flujo) y además puntos de victoria; la decisión es gastar solo para capacidad futura o gastar más para también sumar puntos.
  - Estrategia en PC: gastar en unidades de combate vs. en facilidades que fabriquen mejores unidades; loop externo: mandar unidades a recolectar recursos con riesgo de perderlas.
  - *Star Realms*: core loop individual = engine building; el combate entre jugadores es el freno.
- **Cómo falla (problemas del boosting engine)**:
  1. **Runaway (rich-get-richer)**: al ser reinforcing, sin balancing loops se desboca. Ej.: *Rampart* (1990) - tras cada ronda se reconstruye castillo con más muros y cañones según el desempeño; quien empezaba a ganar no podía ser alcanzado; el único balanceador era meter monedas en el arcade (en consolas sin monedas el defecto se hizo evidente).
  2. **Estancamiento por recursos insuficientes (stall)**: Monopoly con $500 iniciales: pocos activos y riesgo de bancarrota rápida. Fantasía donde el único oro viene de un monstruo que solo muere con un arma mágica comprada con ese oro = **deadlock** (el loop termina antes de empezar porque el recurso ganado al recorrerlo es necesario para iniciarlo).
  3. **Descompensación de costos**: si las unidades son baratas y no mueren, el jugador acumula suficientes y destina todo a inversión -> runaway o escalada rápida de todos. La escalada puede ser emocionante si los jugadores se balancean entre sí (típico en estrategia mobile), pero termina en **content starvation** (se acabaron las unidades/contenido). Corregir con costos exponencialmente crecientes (balancing) **solo retrasa, no evita** el agotamiento de contenido (curvas de progresión en cap. 10).
  4. **Estrategia dominante (dominant strategy)**: al afinar demasiado el balance entre invertir y actuar, los jugadores optimizan y se colapsa el espacio de caminos a una sola estrategia óptima (siempre preferible, mayor probabilidad de ganar). Ej.: una combinación arma+armadura que supera a todas; una unidad que vence a todas. Consecuencia: sin decisiones significativas; los jugadores o se apuran hacia la receta o la descubren y se frustran porque otros ya la conocían -> se evapora la diversión.
- **Cómo se corrige / se mantiene sano**: balancing loops explícitos (tasa de producción, cuánto puede crecer el flujo, cuánto debe gastar el jugador en actuar en vez de invertir, otros contrapesos), catch-up o frenos, costos crecientes, y cuidar que no haya una única opción óptima.

#### 3.1.2 Braking engine (motor de freno / "friction structure")
- **Qué es**: predominan los balancing loops; una source genera recurso pero la acción del loop **lo reduce** y a veces reduce la frecuencia/cantidad de ganancia futura. Analogía: frenos del coche, regulador centrífugo. Adams & Dormans: *friction structures*.
- Se ven como **partes dentro de otros loops**, rara vez solos. Función: regulador/freno del progreso del jugador.
- **Ejemplos**: stamina y attack power en *Marvel War of Heroes* (sin ellos se juega sin restricción); la carta "make repairs" de Chance en Monopoly (paga según casas/hoteles -> drena recursos y además hace *rubberbanding*, porque afecta mucho más al que tiene muchas propiedades que al rezagado). Otras formas de fricción: condiciones a las que el jugador debe atender y que desvían recursos de la progresión (mantenimiento, reparaciones).
- **Cómo falla - "slowing to a stop"**: si la regulación es demasiado severa y supera al reinforcing loop principal (de un boosting engine o economía), el jugador queda sin recursos para actuar y el juego se detiene. Es como un auto con frenos arrastrando: se saca demasiada energía del sistema. Ej.: la carta de reparaciones más frecuente o más cara en Monopoly dejaría sin acción al jugador.
- **Cómo se corrige**: calibrar la fricción para que sea menor que el motor reinforcing; que sea proporcional (castigue al líder más que al rezagado).

### 3.2 ECONOMIES

- **Definición operativa**: sistema dominado por un reinforcing loop donde el aumento de recursos o valor viene **no de invertir internamente** un recurso (eso es boosting engine) sino de **intercambiar o convertir un recurso por otro con ganancia de valor no lineal**. Cita de Brian Giaime (2015): economía de juego = intercambio dinámico de recursos, tiempo y poder entre sistemas y entidades, intercambiados porque los jugadores perciben ganancia de valor.
- **Diferencia clave engine vs. economy**: engine = mismo recurso, inversión; economy = recursos distintos, intercambio/conversión. En una economía el jugador usa un recurso para una acción o lo intercambia por otro que le da más capacidad.

**Ejemplo de la madera (Fig. 7.9):**
- Un trabajador necesita 1 pan para cortar 1 madera. Si 1 madera se cambia por 2 panes, el jugador gana capacidad de cortar 2 maderas más (tras una demora, p. ej. el turno siguiente) = núcleo del loop económico reinforcing. La demora evita el runaway instantáneo.
- Outer investment loop: construir un **aserradero** (sawmill): 1 madera -> 1 tablón (lumber), y 1 tablón = 4 panes. Aumento fuertemente **no lineal** en capacidad y valor.
- **Costos del salto** (decisiones de timing e inversión = el corazón del gameplay económico): (1) acumular madera para construir el aserradero (inversión tipo boosting engine); (2) dedicar un trabajador (recurso escaso) al aserradero -> se corta menos madera; (3) tiempo extra de conversión; (4) repagar la inversión de tiempo y madera que podría haberse intercambiado directo por pan.

**Unfolding Complexity (complejidad que se despliega):**
- Se pueden introducir objetos, recursos y monedas nuevos a medida que avanza el juego: primero solo pan y madera; cuando se domina, aparece el aserradero y el tablón -> nuevo loop, modelo mental ampliado, más decisiones (cuándo construirlo, cuántos trabajadores).
- **Production chains** introducidas con el tiempo (Fig. 7.10): mina de mineral -> mineral -> fundición (smelter) + chimenea -> hierro -> herrería (smithy) -> acero -> armas; cada paso requiere edificio, trabajadores y a veces conocimiento (una academia para convertir trabajadores en herreros). Ej.: empezar vendiendo mineral, luego refinar a hierro y ver que paga lo suficiente para justificar los pasos extra, hasta múltiples rutas de producción.
- Beneficios: exploración, maestría y logro a medida que el modelo mental crece; múltiples loops entrelazados = amplio espacio de juego y compromiso a largo plazo. Para quien disfruta construir/gestionar cadenas.
- Rol especializado entre jugadores: cada uno produce algunos recursos y comercia otros (otro jugador o NPC).

**Currencies en economías [Currencies]:**
- Actúan como recurso catalítico: permiten el intercambio sin consumirse (como un catalizador químico). Plata que usan tanto el leñador como el panadero.
- En muchas economías de juego las monedas se destruyen igual vía sinks al gastarse.
- Propiedad extra: **uso casi universal** (a diferencia de recursos con pocos usos). 1000 monedas -> entrenamiento, armas, información o ahorrar: muchas opciones + sensación de recompensa valiosa.
- Riesgo: inflación y estancamiento. **El jugador tiene que percibir que la moneda tiene valor de cambio**, si no es una molestia. Equilibrar para que conserve valor sin volverse demasiado preciosa es un problema difícil, a ver **a nivel de toda la economía** y no por una sola parte; requiere mucho ajuste iterativo (tasas de creación de recursos, precios, etc.) para llegar a una economía estable pero dinámica.

**Economías con engines [Economies with Engines]:** es común que una economía tenga engines como subloops (vender madera por pan vs. invertirla en el aserradero). Tener fuentes cuyo recurso sirve para inversión interna o intercambio rentable es el núcleo de muchos juegos buenos: trade-offs corto plazo vs. ganancia a largo plazo.

**Ejemplos de economías [Examples of Economies]:**
- **RPG típico**: "mato monstruo, obtengo loot, compro cosas". El jugador intercambia **tiempo** y **salud del personaje** (y desgaste de armas/armaduras) por loot (XP, habilidades, mejores armas/armaduras, oro para comprar o reparar). Cada encuentro no asegura recompensa -> **variable schedule** de recompensa (cronograma variable): recompensa en momentos impredecibles; produce más enganche (conducta persistente y enfocada) y picos de dopamina por cada recompensa que un cronograma regular; útil sobre todo en interactividad action/feedback; explica por qué persistimos en juegos, apuestas, bolsa. El **combate** es una ecología subsistema de la economía mayor.
- **Economías de comercio tradicionales**: trueque o con monedas; todo recurso debe tener valor para el comprador. En una economía sana los compradores satisfacen necesidades o crean valor (el herrero convierte lingotes en armas). **Ese aumento de valor es lo que impulsa cualquier economía** y mantiene el loop reinforcing.
- **Multi-recurso, múltiples compradores y vendedores** (humanos o NPC): los recursos tienen valor relativo distinto según necesidades y presupuesto. Con muchas transacciones los precios se asientan en un rango estrecho; con pocas transacciones fluctúan mucho (falta de historia/precedente).
- **Oferta y demanda**: más interés o menos disponibilidad (con interés persistente) -> sube el precio; si es fácil de conseguir -> baja. La economía ocurre cuando vendedores y compradores acuerdan. (El autor se detiene en el borde de la microeconomía: complemento analítico recomendado.)
- **Crítica a prácticas comunes**:
  - **Precios fijados centralmente**: dan experiencia consistente (los cueros de lagarto no se vuelven de golpe inútiles) pero sacan la "vida" y las decisiones (no hace falta buscar dónde vender mejor). Reduce la economía a ejercicio mecánico. Puede estar bien según el juego. **Regla**: si quieres decisiones económicas, permite variabilidad de precios; si lo importante es solo poder vender sin pensar, la variabilidad solo suma carga mental y consume el "interactivity budget".
  - **Vendedores con efectivo, stock y apetito infinitos**: compran las siguientes 10, 100, 1000 unidades al mismo precio; consistente pero sin vida ni decisiones.
  - **Economías jugador-a-jugador**: mucho más dinámicas porque los jugadores fijan precios; mucho gameplay económico, pero con problemas significativos (runaway, inflación, ver abajo).

**Problemas de las economías [Economic Issues]:**
1. **Runaway / rich-get-richer**: un jugador aprovecha el reinforcing loop y se adelanta; gana forzando a otros a perder, a veces a costa de su disfrute o de su presencia. Monopoly y Risk son *zero-sum* con eliminación de jugadores (todo el valor se concentra en uno). Salvo que busques un juego hipercompetitivo, no crea un diseño sano.
   - **Soluciones**: **rubberbanding** (balancing loops que frenan al líder o ayudan al rezagado; "forgive losers and punish winners"). Pueden ser correcciones puntuales y bruscas: *blue shell* de Mario Kart (el que va último golpea al primero y lo detiene unos segundos); el ladrón (thief) en Catan (se pone sobre el terreno de los líderes para bloquear su producción hasta que lo muevan); efectos integrados como el orden de turno de Power Grid.
2. **Inflation (inflación)** - "más faucets que drains": el reinforcing loop es demasiado fuerte o el intercambio/conversión demasiado fácil/rentable; el jugador acumula demasiado y no tiene dónde gastarlo de forma significativa.
   - Puede usarse a favor un tiempo: pasar de dos monedas a comprar castillos da sensación de poder; **solo mientras las cantidades sigan siendo significativas** (se pueden usar en algo).
   - *Adventure Capitalist* (idle game): de limonada a estudios de cine, bancos y petróleo, con cifras de 10^300 (novemnonagintillion). Pocos jugadores llegan: el gameplay se vuelve repetitivo antes. Solución parcial: **prestige loop** - boosting engine externo: acumulas un recurso de prestigio (inversores ángeles); cuando el ritmo actual ya no da beneficios, reinicias y mantienes solo el prestigio, que funciona como **multiplicador** de la tasa del recurso principal -> pasas rápido los niveles bajos ya aburridos y llegas más lejos; sigues acumulando prestigio, hay incentivo para repetir. Convierte la inflación en parte del gameplay y alarga la vida del juego.
   - *Diablo II*: cada monstruo suelta oro y objetos; oro de sobra con pocos usos (más faucets que drains) -> inútil entre jugadores. Los jugadores adoptaron gemas como moneda no oficial -> también se devaluaron (cantidad de loot + "dupes" = duplicación tramposa de objetos). Luego el *Stone of Jordan* (SOJ: pequeño, caro, útil) -> también se devaluó. Finalmente *high runes* (pequeñas, caras, útiles, con estadísticas distintas = **denominaciones** de valor distinto, como billetes). Causa: reinforcing loop demasiado fuerte vertiendo moneda + falta de contenido para sostener decisiones y metas significativas. Todo juego con economía enfrenta esto; cada vez es más difícil agregar contenido de gama alta sin repetir.
3. **Stagnation (estancamiento)** - menos común: oferta de recursos/moneda demasiado restringida, o costos de mantenerse en el juego demasiado altos. Los jugadores atesoran por miedo a arrepentirse de gastar, o deben pagar mantenimiento (un braking engine) hasta quedar sin fondos. Es raro porque los jugadores simplemente abandonan cuando deja de ser divertido, y la economía se apaga.
   - Causa típica: diseñadores tan obsesionados con balancear que no dejan que el reinforcing loop crezca. Reducir el loop principal evita la inflación pero también elimina el **gradiente económico**: si nadie siente que un intercambio le conviene, no hay intercambios y no hay economía. Sin interacción de intercambio/conversión entre dos recursos no hay sistema; si es un core loop, no hay juego.

### 3.3 ECOLOGIES

- **Definición**: sistema con loop(s) **balancing** predominantes en el que los recursos se intercambian (como en una economía) pero de modo que cada parte termine balanceando, no reforzando, a las otras. Dentro de las partes suele haber reinforcing loops como subsistemas, pero no son el motor principal (Fig. 7.6 y 7.7).
- Meta = balance, no crecimiento sin freno, pero **no significa estancamiento**: una ecología sana está en **metastability** (equilibrio interno / dynamic balance). Las partes cambian constantemente, el todo se mantiene balanceado. Ejemplos: ciervo/lobo; liebre/lince (Fig. 2.10); cascada trófica de la reintroducción de lobos en Yellowstone (Fig. 2.22).
- Cada parte intenta maximizar su crecimiento, pero en conjunto son **braking engines unos de otros**: ciervos frenan plantas, lobos frenan ciervos. El lobo (*apex predator*) no está limitado por depredadores sino por escasez de comida (poca población por su metabolismo y crecimiento lento).

**Tipos de ecologías en juegos [Different Kinds of Ecologies]** (no son solo biológicas: cualquier sistema balanceante con intercambio de recursos):
- **Inventario** (RPG): más cosas = menos espacio; "cosas" y "espacio" se balancean. *Diablo II* lo lleva al extremo: cada pieza compite por una configuración de espacio, no solo por cantidad.
- **Combate**: dos o más lados que se "balancean" (intentan matarse). Si el jugador gana, las recompensas alimentan el loop económico mayor.
- **Ecologías sociales**: *Dark Age of Camelot* - Realm vs. Realm con **tres** facciones (Albion, Hibernia, Midgard): si una domina, las otras dos se alían temporalmente contra la líder -> balance metaestable constante. Con **solo dos** facciones, el balancing loop es superado por un reinforcing (todos se pasan al ganador): runaway. Es lo que pasó en servidores PvP tempranos de *World of Warcraft* (Alliance dominaba por ser más atractiva, entre otras causas); hicieron falta cambios de clases e incentivos y nunca alcanzó un balance orgánico como Camelot.
- Regla de diseño derivada: **tres o más facciones** producen auto-balanceo por alianzas cambiantes; dos facciones tienden al runaway.

**Desequilibrios ecológicos [Ecological Imbalances]:** los dos fallos principales:
1. **Balance demasiado estático -> aburrido** (y, paradójicamente, frágil).
2. **Balance que se sale de control -> destruye el sistema.**

- **Resilient vs. brittle (resiliente vs. frágil)**: dentro de cierto rango el ecosistema se rebalancea; pasado un **punto de no retorno** ya no puede. Analogía **homeostasis**: el cuerpo mantiene temperatura en un rango estrecho; si el stress excede la capacidad, pasa de resiliente a frágil y se apaga.
- **Dificultad práctica**: es difícil saber cuándo un sistema pasó a ser frágil. Una caída fuerte en liebres puede ser parte normal del ciclo. Con datos históricos se pueden hacer modelos: **statistical process control** - si un recurso se aleja **más de 3 desvíos estándar de su media histórica**, el proceso está "fuera de control" y hay peligro severo de fragilidad. Problemas: en sistemas dinámicos puede detectarse tarde, y en juegos casi nunca hay datos históricos suficientes.
- **Peligro de controlar de más**:
  - **Oversteer** (sobrecorrección) -> otra falla frágil.
  - **Estatismo forzado**: clavar todo para asegurar experiencia consistente -> aburrido (sin modelo mental que construir ni decisiones), y además frágil porque el sistema no se auto-balancea y se rompe ante cualquier influencia externa. Analogía: si la temperatura corporal estuviera clavada en 37 °C, una brisa fría o un rayo de sol agotaría la energía y el sistema fallaría.
- **Dominant strategy en ecologías de combate** (ej. una unidad demasiado fuerte para su costo): se vuelve especie invasora; todos construyen solo esa; colapsa el espacio de decisiones.
  - **Anti-patrón "contra-unidad"**: crear una unidad para contrarrestar la dominante; si esa es OP (overpowered) se vuelve la nueva única; la tentación de sumar otra contra-unidad es alta y el juego se parece a la canción de la vieja que se tragó una mosca. Es una solución no sistémica a un problema sistémico (el autor cita el caso del DDT en Vietnam: matar gatos -> ratas -> cosechas). **Corregir el costo/balance en el origen, no apilar contramedidas.**

### 3.4 Combinar loops [Combining Loops Together]
- Engines, economies y ecologies son tipos primarios; muchas mecánicas se construyen combinándolos. Raro que un juego tenga un solo sistema.
- **Ejemplo RPG (Fig. 7.11)**: economía de refuerzo central = progresión del personaje (intercambia tiempo y HP por XP y loot -> más HP, skills, mejores herramientas). Dentro:
  - **Skill engine**: el jugador decide cuándo y cómo invertir puntos (nota: casi nadie permite *gastar* XP/puntos de skill en una acción en vez de invertirlos; AD&D 3.5 lo hace con algunos conjuros; Deadlands y Torg se acercan. Idea de diseño: verlo como engine revela esa posibilidad).
  - **Item economy**: crafteo/comercio.
  - **Inventory ecology**: espacio vs. cosas.
  - **Role economy**: roles de party que se refuerzan (tanque absorbe, a distancia daña, sanador mantiene al tanque).
  - **Combat ecology** dentro de la economía mayor.
  - **Braking engines** (stamina/energía que regenera con el tiempo, típico F2P) que evitan progresar demasiado rápido.
- Efecto neto: los subsistemas se refuerzan mutuamente (más skills/items/party -> vencer más monstruos -> más XP/loot). Combate e inventario frenan y obligan a decidir qué tirar, pero **el efecto sistémico predominante es reforzar el poder del personaje**.
- **Beneficios de jerarquía de sistemas ("Bringing All the Systems Together")**:
  - El core loop cambia según el jugador cambie de foco entre subsistemas o al nivel más alto.
  - Sistemas en paralelo = más cosas que hacer = **breadth** (amplitud).
  - Sistemas anidados con zoom in/zoom out mental = **depth** (profundidad) con complejidad comprensible (Fig. 7.6, 7.7, 7.11).
  - Así el second-order design crea espacio de juego: metas y decisiones en cada sistema y subsistema.
  - **Revelar la complejidad de a poco** ayuda a construir el modelo mental: cada sistema nuevo trae conocimiento, decisiones, formas de actuar y sensación de logro.

---

## 4. Ejemplos de sistemas de juego [Examples of Game Systems]
(No lista exhaustiva; se ve el loop primario, subsistemas internos y relación con otros.)

### 4.1 Progression Systems (sistemas de progresión)
- Casi todos los juegos dan alguna progresión (habilidad, poder, recursos, **conocimiento**). El conocimiento del jugador es un recurso del juego: más conocimiento -> hace más y mejor. Aumentar la variedad de cosas que se pueden hacer (más sistemas paralelos y jerarquía más profunda) introduce conceptos de a poco y da sensación creciente de maestría.
- Muy comunes y recompensantes -> suelen ser el **core loop**. Mapean al interactive loop (acción -> feedback positivo -> nuevas decisiones). "¿Qué hace el jugador?" suele reducirse a "¿cómo progresa?". Son economías o engines, a menudo con subsistemas de ambos tipos.
- **De juguete a juego**: un *toy* (sin metas explícitas) es "lindo, pero ¿qué hace el jugador con él?". Agregar metas explícitas + progresión convierte un toy en game y sostiene el engagement. Típico error de "toymakers" (cap. 5).
- Se piensan como **recompensa/ganancia de recurso por unidad de tiempo**. Para cada dimensión de progreso (salud, magia, conocimiento, objetos, XP, tropas...) hay que especificar una **tasa de aumento** (tokenizing, cap. 10). A veces es poco cuantificable (modelo mental y herramientas cognitivas).
- **La tasa misma debe aumentar con el tiempo** (no solo la cantidad) para mantener lo aspiracional y evitar la **habituación / hedonic fatigue (hedonic adaptation, satiation)**.

**Habituation y Utility [Habituation and Utility]:**
- **Wanting > having** impulsa atención y conducta. Una meta alta, aun ridículamente lejana, mantiene el engagement. Si el jugador siente que logró todo (mató al jefe mayor, obtuvo el mejor tesoro), el engagement cae rápido.
- **Hedonic fatigue**: nos acostumbramos a cualquier recompensa; lo evaluamos de forma relativa, no objetiva. En economía: **marginal utility** (utilidad marginal decreciente): el primer bocado de helado es genial, el tercero normal, el vigésimo no se quiere; puede incluso volverse negativa. 20 bocados no valen 20 veces uno.
  - Nota (**network effects**): a veces la utilidad marginal sube (teléfonos, bloques de construcción, computadoras en red), hasta saturar.
- Consecuencia: si el jugador no se siente significativamente recompensado, cae del "aburrimiento" del borde inferior del flow channel (Fig. 4.11). **Las recompensas tienden a crecer en el tiempo -> curva exponencial** de recompensa.
- **Efecto secundario fatal**: si la tasa sube con el tiempo, entran más recursos al juego. **Si los sinks no crecen igual que las sources -> inflación.**
- **Tácticas contra habituación/inflación** (lista completa):
  1. **Limiting sources (limitar fuentes)**: menos fuentes, menor tasa de producción por fuente, o mayor costo/dificultad de obtener el recurso. Ej. RPG: dificultad de conseguir un arma mejor, la última pieza de un set con beneficio no lineal, la XP del siguiente nivel con curva no lineal (cap. 9 y 10).
  2. **Limiting stock (limitar reserva)**: tope al inventario (WoW, Diablo) -> ecología "lo que cargo vs. espacio que me queda"; posterga pero no elimina la inflación; además da otra vía de progreso (aprender a cargar más).
  3. **Increasing sinks (aumentar sumideros)**: sacar recursos del juego. Ej. *Zelda: Breath of the Wild* (y otros): las armas se rompen y salen del juego -> el jugador nunca ve una buena espada como inútil (conserva utilidad marginal) porque sabe que otras se romperán.
- La inflación y la habituación son difíciles de evitar del todo; motivo para el enfoque sistémico con jerarquías de sistemas. **Los juegos basados solo en contenido y progresión terminan**: el contenido se vuelve cada vez más exagerado para sostener curvas exponenciales de desafío y recompensa y se vuelve más caro de crear y mantener. Los juegos con fuerte componente **ecológico/balanceante** (ej. Realm vs. Realm) pueden durar mucho más sin límite claro de engagement.

### 4.2 Combat Systems (sistemas de combate)
- Típicamente **ecologías**: dos o más oponentes que buscan balancearse y eliminarse. Tiempo/interactividad: action/feedback + short-term cognitive. Parte importante del core loop, pero casi siempre acompañado de **reinforcing loops (progresión)** para dar metas a largo plazo y compensar la naturaleza balanceante del combate.
- **Advertencia**: algunos juegos (sobre todo móviles) tienen combate sin decisiones del jugador; el reinforcing loop externo mantiene jugando pero la pérdida del action/feedback rápido reduce engagement y longevidad. **Aun con un core loop sólido, las decisiones momento a momento y la interactividad siguen siendo vitales.**
- Combate como **sistema balanceante que interactúa con otros**: *Star Realms* - el core loop individual es engine building; el combate entre jugadores frena/balancea el progreso del rival, elevando la presión sobre las decisiones del engine (construir naves para ganancia inmediata o inversión a largo plazo sabiendo que el rival te desafiará).

### 4.3 Construction Systems (sistemas de construcción)
- Crafteo, cultivo, cría, construcción/modificación de vehículos, edificios o del personaje (RPG). Típicamente **engines + economías** (con largas cadenas de producción), según el énfasis: reinvertir (engine; ej. deck-building como core loop) o intercambiar para ganar valor (economía).
- Interactividad: short-term y long-term cognitive; los muy detallados añaden action/feedback.
- A menudo son **subsistemas de apoyo dentro de un loop de progresión mayor**: en RPG se construyen skills, armas, armadura, conocimiento del mundo y red social (party, gremio); en estrategia: investigar -> edificios -> unidades más fuertes -> fama y botín (engines y economías anidadas).

### 4.4 Skill and Technological Systems (skills y tecnología)
- Metas de largo plazo de descubrir skills/tecnologías: abilidades nuevas para personaje/imperio. Son **engines reinforcing limitados**. Suelen organizarse en **árboles** (una skill lleva a 2-3 más); el jugador navega para personalizar personaje o civilización.
- El jugador gana puntos de experiencia/investigación y los **invierte** en una skill. Raramente se pueden usar los puntos en una acción no inversora: área abierta a exploración de diseño.

### 4.5 Social and Political Systems
- Son **ecologías sociales**: cliques, bandas rivales, partidos políticos, facciones; cada uno balancea al otro mientras busca su propio dominio reinforcing. Interactividad social y a largo plazo.
- Falla igual que cualquier ecología: si un lado llega a una posición autoreforzada que ya no se puede desafiar, el sistema colapsa y no queda gameplay.

---

## 5. Cómo definir los loops y metas de un sistema [Defining a System's Loops--And Goals]

### 5.1 Punto de partida: metas de diseño del sistema
Pregunta madre: **¿qué propósito tiene el sistema dentro de tu juego?** Para responderla:
1. Construir la **forma de loop** del sistema para sostener el gameplay y la experiencia del jugador deseados.
2. Considerar consciente y cuidadosamente las **interacciones, metas y conductas del jugador** que habilita.
3. Definir con claridad las **partes y sus interacciones** con las que se cuenta, y los otros sistemas con los que este interactuará.

Las metas se expresan en niveles jerárquicos:
- **Arriba**: el sistema de nivel superior del que forma parte; el más alto es la **experiencia del jugador** (surge de game+player): cómo interactúa (rápido/lento; perceptual, cognitivo, emocional, social) y cómo su modelo mental se corresponde con el modelo sistémico.
- **Abajo / contexto**: si el sistema vive dentro de otro (como Fig. 7.6/7.7), mirarlo en su contexto: qué sistema mayor refuerza o balancea y cómo interactúa con **pares** (otras partes del mismo sistema superior).

### 5.2 Definir la estructura de loop [Defining the Looping Structure]
Preguntas a resolver:
- ¿Qué estructura necesita? Opciones: loop reinforcing simple, loop balancing simple, **engine**, **economy**, **ecology**, o un híbrido.
- ¿Tiene subsistemas internos?
- **Proceso**: esbozar los loops primarios (ver Herramientas). Da comprensión rápida del comportamiento dinámico, cómo sostiene la experiencia, qué subsistemas/recursos forman el loop, dónde encaja el sistema y por qué es necesario. **Hacerlo varias veces**, redefiniendo estructura y relaciones: ayuda a precisar el sistema, la experiencia total y a empezar a definir los **objetos del juego que serán las partes**.
- **Poda**: puede resultar que el sistema no hace falta (aporta poco). No dejar un sistema que no encaja con el resto, **aunque te guste o hayas trabajado duro en él** (ej. un sistema de crafteo en un juego de relaciones sociales). Ponerlo de lado: quizá sirva después u en otro juego.
- Además, evaluar cómo las partes y sus interacciones sostienen las metas del sistema -> lleva a **balance** y a si el sistema permite decisiones significativas (partes: cap. 8; balance: caps. 9-10).
- Trabajar en **partes, loops y todo a la vez** (o alternando el foco) para articular las metas como *máquinas dinámicas* que crean el espacio de acción, no como contenido estático.

### 5.3 Vincular experiencia del jugador y diseño del sistema [Linking the Player Experience and System Design]
- Todo sistema se piensa en función de cómo apoya la experiencia. **Ejemplo combate**: ¿batalla de ejércitos a gran escala donde ves los efectos de tus órdenes desarrollarse en minutos, o combate personal intenso con control sub-segundo de cada movimiento? Ambos son ecologías de combate, pero la interacción del jugador y las partes necesarias difieren por completo. Definir las metas en términos de interacciones/experiencia del jugador, y de las partes, atributos y comportamientos que las soportan, clarifica la estructura.
- **Ejemplo progresión - ritmo**:
  - ¿Cuán rápido debe progresar? ¿Cómo dar sensación de maestría temprana en un loop rápido para generar engagement pero sostener interés a largo plazo?
  - Sin feedback positivo temprano el jugador no arma su modelo mental ni se engancha. **Crear una "experiencia de éxito" ("¡lo lograste!") en un core loop dentro del primer minuto** ayuda a engancharlo.
  - Pero hedonic fatigue aparece si das la misma recompensa a la misma tasa.
  - Recompensar demasiado/progresar muy rápido -> el juego termina o se aburre rápido.
  - Progresar muy lento o con progresión intrínsecamente no recompensante -> **grind**: el jugador persiste solo si cree que hay suficiente recompensa más adelante; si no, abandona.
  - (Nota al pie: el grind/leveling treadmill es aceptado en RPG/MMO, pero un enfoque sistémico puede apuntar a **maestría sistémica** en vez de repetición mecánica.)

---

## 6. Herramientas para diseñar sistemas [Tools for Designing Game Systems]

- No hacen falta herramientas exóticas: papel, pizarra. El trabajo es **muy iterativo**: se redibujan los loops una y otra vez. Intentar dibujar un diagrama de loops ya obliga a enfocar y clarificar el pensamiento y muestra cómo funciona como parte del juego.
- Cuando las estructuras y diagramas se solidifican -> **hacer prototipos** para ver si el diseño funciona y cumple las metas.

**Lista de herramientas:**
- **Whiteboards (pizarra)**: analógica; dibujar/borrar/redibujar con colores; mucho tiempo frente a ella. Límite: tu cerebro es la computadora y los humanos son pésimos manteniendo una comprensión precisa del comportamiento de un sistema dinámico.
- **Loopy** (Nicky Case, 2017): gratis online, dibuja loops reinforcing/balancing y los ves en acción; funcionalidad limitada, estética limpia; no admite subsistemas.
- **Machinations** (Joris Dormans): mucho más detallada; diagramas de loops funcionales e incluso juegos completos (sin presentación, solo sistemas puros); incluye operadores con input de usuario; envejeciendo y sin mantenimiento aparente; subsistemas no modulares utilizablemente.
- **NetLogo** (Wilensky 1999): pensada para simulación; más potente, puede crear sistemas completos de juegos simples; curva de aprendizaje larga y menos rápida para iterar.
- **Lenguajes/entornos de prototipado rápido**: JavaScript, Python, Unity, etc. Prototipos **rápidos y feos** (el énfasis no es el arte). Clave: usarlos como medio para pasar de diagramas conceptuales a prototipos funcionales lo más rápido posible.
- **Spreadsheets (hojas de cálculo)**: pilar del diseño de sistemas; Excel el más popular (también Google Sheets, OpenOffice). Hay que dominarlas para ingresar, visualizar y comparar datos que definen las partes de más bajo nivel y hacen funcionar los loops (cap. 8 y 10).

**Desafíos de las herramientas (dos ejes):** cuán complejo/completo puede ser el sistema interactivo vs. cuánto cuesta aprender y usar la herramienta. Pizarra: fácil pero sin ejecución; Loopy/Machinations: fáciles de aprender; NetLogo: más potente, más lento; lenguaje general: expresividad vs. velocidad según estilo y disposición a aprender. No hay mejor herramienta única: "la correcta para el trabajo".

---

## 7. Cómo documentar los sistemas [Documenting Your System Designs]

Quien trabaje en el juego (**incluido vos mismo meses después**) debe entender:
- **Por qué** los sistemas están diseñados así.
- **Cómo** apoyan el concepto del juego y la experiencia de jugador deseada.
- **Cómo** están encarnados por los objetos del juego como partes del sistema.

La documentación se mantiene **viva**: se actualiza y consulta con cada iteración, no es "escribir y olvidar". No documentar lleva a malas decisiones futuras al perder el hilo de por qué se decidió algo; los sistemas tienen **decisiones sutiles con efectos no obvios** que la documentación debe hacer explícitos para no perder la esencia.

### 7.1 System Design Document (documento de diseño de sistema)
Contenido (lista completa):
1. Nombre del sistema y descripción de alto nivel.
2. **Metas del sistema en términos de experiencia del jugador**: cómo ayuda a crear el gameplay; suele ser cualitativo y centrado en lo experiencial; es válido usar palabras sobre cómo se siente el jugador.
3. **Depiction gráfica** del sistema: subsistemas importantes, partes internas y comportamientos; típicamente los diagramas de loops de este libro (uno de alto nivel se parecería a la Fig. 7.11).
4. Interacciones del jugador habilitadas o requeridas por el sistema.
5. Lista (idealmente links vivos) a las descripciones de subsistemas, sistemas pares y el sistema contenedor (el más alto es game+player).
6. Cualquier otro detalle necesario para entender el propósito e implementación.
- **Un documento breve por sistema**, claro y conciso; **no un "design bible" gigante** que envejece rápido. Documentos separados pero linkeados (web, Google Docs, wiki) para editar cada uno sin tocar el resto.
- Un *deliverable* es todo lo que se entrega a un stakeholder (puede ser tu yo futuro).

### 7.2 System Technical Design Document
- Se enfoca en **cómo se implementa** (no el porqué). El design doc es para diseñadores; el technical doc para programadores. Deben mantenerse **en sincronía**. Útil separarlos aun si diseñador y programador son la misma persona (dos puntos de vista).
- Contenido: descripciones implementables de atributos y comportamientos (definiciones tipo código); a medida que se asienta: **atributos por tipo** (string, integer, etc.), **rangos válidos**, **fórmulas** de cómo los comportamientos alteran atributos para producir los efectos descritos, **descripción de tests y resultados** para verificar que el sistema funciona; formato y links a archivos de datos (hojas de cálculo); eventualmente elementos de arquitectura de software (clases) según el nivel de detalle necesario (más en equipos grandes/proyectos largos).

### 7.3 Mockups y prototipos
- Ayudan a comunicar propósito y comportamiento del sistema y a asegurar que tú y otros lo entiendan. Dan ejemplos de cómo funciona y qué experiencia crea. **No** ejemplifican la implementación técnica (se toman muchos atajos que no son apropiados en el juego final).
- **Mockup**: diagrama no funcional + texto de apoyo; dibujos orientados al jugador/storyboards/descripciones narrativas ("más diagramas y menos texto es mejor"). Ej. mockup de combate: las elecciones del jugador como en la UI y una descripción diagramática/narrativa de cómo transcurre un combate, mostrando efecto de las elecciones sobre el funcionamiento interno.
- **Prototype**: en juegos digitales tiene funcionalidad real, aunque limitada, y deja afuera lo no relacionado con la función del sistema. Arte de reemplazo lo más simple posible. **"Fast and ugly" como cualidad positiva.** Cualquier herramienta, de hoja de cálculo a entorno de programación completo.
- **Regla estricta**: el prototipo está **prohibido para transferir al juego final** (solo ideas). Se reescribe todo en producción; la tentación de copiar-pegar "un poquito" cuesta más tiempo y dolores que resistirla.
- Tener un prototipo funcional referenciado en la doc da más certeza de que el diseño cumple las metas y facilita entender la **función** (no solo la estructura).
- No hay que prototipar cada sistema, pero **cuanto más importante (core loops), más prototipar temprano**, cuando es rápido y barato. Descubrir en producción que el core loop o un sistema mayor no funciona causa retrasos mucho más costosos.

---

## 8. Preguntas para considerar sobre tus loops [Questions to Consider About Your Game Loops]
(Completas, parafraseadas)
1. ¿El propósito del sistema es claro, sobre todo para gente que no lo diseñó (equipo primero, jugadores después)? (Requiere prototipo funcional y playtesting.)
2. ¿Los recursos internos, monedas y/o subsistemas son evidentes y bien entendidos?
3. ¿Está claro dónde vive el sistema dentro del juego completo? ¿Es parte de un sistema de nivel superior? ¿Tiene sistemas pares dentro de ese sistema superior? ¿Forma uno de los core loops del jugador?
4. ¿Tiene un loop primario propio fácilmente definible? ¿Hay suficiente interacción y feedback entre las partes (atómicas o subsistemas)? ¿Ese loop actúa reforzando o balanceando los recursos de modo que sostiene el gameplay buscado?
5. ¿El sistema es resiliente a cambios internos y externos? ¿Entendés (y podés predecir) en qué situaciones se vuelve frágil y falla? ¿Hay partes que anulan el efecto de todas las demás o **cuellos de botella (choke points)** donde, si falla una parte o subsistema, falla todo?
6. ¿Ofrece e incluso exige decisiones significativas? ¿Fuerza una estrategia dominante, o no da interacciones con frecuencia apropiada (según el tipo de interactividad buscado)? ¿O, al contrario, exige tantas decisiones que abruma?
7. ¿Da suficiente feedback sobre su funcionamiento interno para que el jugador arme un modelo mental efectivo?
8. ¿Puede **desplegarse progresivamente** a medida que crece la comprensión del jugador (versión simple o de alto nivel a la que se añade detalle e interacción conforme aprende)?
9. ¿Crea gameplay **emergente**? ¿Las partes y subsistemas se combinan en efectos nuevos que no residen en ninguno y que sorprenden y deleitan?
10. ¿Podés mostrar cómo funciona con un prototipo en vez de solo hablar de él?
11. ¿Está documentado adecuadamente, tanto metas de diseño como elementos específicos de implementación?

---

## 9. Catálogo de fallas y diagnóstico (síntesis operativa para analizar/balancear)

| Falla | Dónde ocurre | Causa estructural | Señales | Corrección |
|---|---|---|---|---|
| **Runaway / rich-get-richer** | Boosting engine, economía, ecología social con 2 bandos | Reinforcing loop sin balancing loop; sin catch-up | El líder gana con cada vez menos atención; el rezagado pierde opciones; brecha creciente; pocas decisiones | Rubberbanding (blue shell, thief de Catan, turnos inversos de Power Grid); fricción proporcional (make repairs); 3+ facciones |
| **Deadlock** | Boosting engine / economía | El recurso ganado en el loop es necesario para entrar al loop | Jugador no puede progresar desde el inicio | Dar fuente inicial independiente del loop |
| **Stall por recursos insuficientes** | Boosting engine (Monopoly con $500) | Arranque pobre; costos altos | Bancarrota/eliminación rápida | Subir stock/flujo inicial |
| **Content starvation / agotamiento** | Boosting engine con unidades baratas y duraderas; progresión exponencial | Inversión sin gasto que consuma; costos crecientes solo retrasan | Jugadores sin nada nuevo que desbloquear | Más sinks, prestige loop, sistemas ecológicos que no dependan de contenido |
| **Dominant strategy** | Engines, ecologías de combate | Balance demasiado fino o una opción mal costeada | Todos construyen/usan lo mismo; "receta óptima" conocida | Arreglar costo en origen; evitar la espiral de contra-unidades |
| **Slowing to a stop** | Braking engine | Fricción mayor que el reinforcing loop | Jugador sin recursos para actuar | Reducir freno; hacerlo proporcional |
| **Inflation** | Economía / progresión | Más faucets que drains; tasa de ganancia creciente sin sinks proporcionales | Moneda sin uso, devaluada; jugadores cambian de moneda (Diablo II) | Limitar fuentes, limitar stock, aumentar sinks (armas que se rompen), prestige loop, denominaciones |
| **Stagnation** | Economía | Oferta de recursos muy restringida o costos de mantenimiento altos | Atesoramiento; nadie siente que un intercambio le conviene; abandono silencioso | Dejar crecer el reinforcing loop; restituir gradiente económico |
| **Habituación (hedonic fatigue)** | Progresión | Recompensa constante | Disminuye engagement al caer al "boring bottom" del flow channel | Tasa de recompensa creciente + sinks proporcionales; metas aspiracionales |
| **Grind** | Progresión | Progreso muy lento o no intrínsecamente recompensante | Persisten solo por promesa futura | Progresión intrínsecamente gratificante; maestría sistémica |
| **Brittleness (fragilidad)** | Ecologías | Pasar el punto de no retorno; o estatismo forzado | Valores >3 desvíos de la media histórica; sistema no se rebalancea | No oversteer; dejar balance dinámico; vigilar con datos históricos |
| **Oversteer / contra-unidad** | Ecologías de combate | Solución no sistémica | Cadena de unidades OP que se contrarrestan | Corregir en origen |
| **Estatismo** | Ecologías | Clavar valores para consistencia | Sin modelo mental que construir ni decisiones | Permitir variabilidad |
| **Sistema huérfano** | Cualquier | Sistema que no encaja | No aporta a la experiencia | Sacarlo (aunque cueste) |

---

## 10. Heurísticas y reglas prácticas (lista plana)

- Dibujar el sistema como diagrama de loops antes de balancear; rehacer el diagrama varias veces.
- Identificar para cada recurso: source, stock (y si tiene límite), converter, decider, sink. Contar faucets vs. drains.
- Cada vez que aumenta la tasa de recompensa, aumentar los sinks en proporción.
- Un reinforcing loop necesita un balancing loop en algún lado (límite, costo, fricción, rubberband, demora).
- Una **demora** entre intercambio y beneficio evita el runaway instantáneo en economías (ej. el pan que alimenta al leñador llega al turno siguiente).
- Los inputs de un decider deben ser locales (mismo nivel de la jerarquía, a lo sumo un nivel de distancia) para no volver frágil el sistema.
- No dejes vendedores/precios totalmente fijos si quieres decisiones económicas; si no te interesa la decisión económica, la variabilidad es carga mental inútil.
- Mantener el balance dinámico: ni demasiado estático (aburrido/frágil) ni libre (colapsa).
- Para mantener un balance a largo plazo entre bandos, preferir **tres** o más (alianzas cambiantes) a dos.
- Monedas: que conserven valor sin ser demasiado preciosas; revisar a nivel de toda la economía, iterativamente.
- Al corregir un problema, sospechar de los parches no sistémicos (contra-unidad, contra-contra-unidad).
- Dar un "éxito" temprano (primer minuto) para iniciar el modelo mental; después regular el ritmo de recompensas.
- Combates sin decisiones significativas debilitan la longevidad aunque el loop exterior de progresión funcione.
- Loop de alta tensión (acción) + loop de baja tensión (construcción) es un patrón probado.
- Metas visibles de largo alcance mantienen el *wanting*; si todo está logrado, el engagement se cae.
- Inflación bien manejada puede ser parte del gameplay (sentirse poderoso) mientras los números sean significativos; si no, agregar prestige loop o reiniciar.
- Prototipar primero los core loops; el prototipo se tira (no se copia al código final).
- Una doc de sistema por sistema, corta, con links; separar el *por qué* (design) del *cómo* (technical).
- Si el sistema no aporta a la experiencia, sacarlo.
- Antes de decidir que un ecosistema está roto, compararlo con su variabilidad histórica (3 desvíos estándar como regla de control estadístico), aunque en juegos suele faltar historia -> usar simulación/playtests para generarla.

---

## 11. Índice de ejemplos de juegos (una línea cada uno)

- Monopoly: boosting engine ($200 por vuelta + inversión en propiedades/casas), runaway, stall con poco capital, braking con la carta de reparaciones (+ rubberbanding).
- Power Grid: orden de turno inverso al líder = balancing loop permanente.
- Clash of Clans: collect/battle/build & train; gemas intercambian dinero por tiempo (F2P).
- Marvel War of Heroes: PvE/PvP con stamina/attack power como frenos; outer loop de mejorar héroes.
- Boomshine: core loop de un solo clic; rejugar como outer loop propio del jugador.
- Terraria, Banished: cadenas de producción profundas.
- Rampart (1990): engine de reconstrucción sin catch-up -> runaway.
- Dominion, Splendor: engine building de mesa (Splendor: cartas dan gemas gratis + puntos).
- Star Realms: engine building con combate como freno entre jugadores.
- Mario Kart (blue shell), Settlers of Catan (thief): correctivos puntuales de rubberbanding.
- Risk: zero-sum con eliminación.
- Adventure Capitalist: inflación extrema y prestige loop.
- Diablo II: inflación de oro -> gemas -> SOJ -> high runes; inventario como ecología espacial.
- WoW / Diablo: tope de inventario como freno a la inflación; WoW PvP temprano con 2 facciones = runaway.
- Dark Age of Camelot: Realm vs. Realm de 3 facciones = metastability.
- Zelda: Breath of the Wild: armas que se rompen = sink que preserva el valor de lo que tenés.
- AD&D 3.5, Deadlands, Torg: casos donde se gasta XP en lugar de invertirla (engine de skill con "uso" alternativo).
- Deer/wolf/plants: ecología jerárquica de ejemplo (Fig. 7.6/7.7). Lynx/hare y lobos de Yellowstone (cap. 2) referidos.

---

## 12. Términos clave (glosario rápido ES -> EN)

Loop reinforcing / balancing; core loop, inner/outer loop; game's model loop; player's mental loop; interactive loop; designer's loop; game mechanic / core mechanic; engine (boosting / braking, dynamic engine, friction structure); economy; ecology; resource (simple/complex); production chain; currency; source / faucet; sink / drain; stock / pool; converter; decider; dynamic balance / metastability / homeostasis; resilient vs. brittle; point of no return; statistical process control (3 sigma); rubberbanding; runaway / rich-get-richer; deadlock; dominant strategy; inflation (more faucets than drains); stagnation; prestige loop; variable schedule; habituation / hedonic fatigue / marginal utility; network effects; progression system; grind / leveling treadmill; toy vs. game; unfolding complexity; breadth vs. depth; system design document / technical design document; mockup / prototype ("fast and ugly").
## Anexo: formas de pensar y ejemplos de loops del mundo real (cap. 1)

### 1.1 Formas de pensar [Ways of Seeing and Thinking]
Metacognición (metacognition): pensar sobre cómo se piensa. El diseñador debe entender cómo piensa el jugador y cómo piensa él mismo.

Cuatro modos de pensar, y cuál usar:
1. **Fenomenológico (phenomenological thinking):** el mundo como eventos aislados sin principio unificador. Consecuencia: no ves los sistemas que te afectan (ej.: el mar se retira rápido -> no ves el tsunami; hipotecas fáciles -> no ves la crisis). Para diseño: es el diseñador/jugador que ve "pasó X" sin ver el loop que lo produjo.
2. **Reduccionista (reductionist thinking):** desarmar en partes hasta que la solución es obvia; asume determinismo y causa raíz única. Útil para procesos complicados (lineales), peligroso en sistemas con loops. Fallas típicas:
   - Confundir correlación con causalidad (helados/ahogamientos; luz de noche/miopía; deuda/crecimiento con causalidad invertida).
   - "Reduccionismo codicioso" (greedy reductionism, Dennett): creer que el todo es solo la suma de químicos/partes.
   - Esperar efectos lineales: el "cobra effect" (ver 2.7).
   - Péndulo simple = predecible (complicado); **péndulo doble = caótico** (complejo): un cambio mínimo (una articulación) hace impredecible la trayectoria.
3. **Holista (holistic thinking):** ver el todo; sintetizar. Ventaja: ves macro-tendencias y evitás el reduccionismo codicioso. Riesgo: si todo está conectado no hallás causas; falsos positivos (correlaciones espurias).
4. **Sistémico (systemic thinking):** el punto medio "Ricitos de Oro": analizar las partes Y entender cómo funcionan juntas en su contexto operativo; encontrar los loops (A afecta B, B afecta C, C afecta A). Es "both-and": reduccionista + holista. Es la habilidad central del diseñador.

Test de los peces de Michigan (Michigan Fish Test, Nisbett/Masuda): occidentales ven los peces grandes (partes), orientales ven la escena y relaciones. Moraleja: tendemos a ver las partes y no las relaciones.

Ejemplos de loops físicos:
- Horno con termostato: la brecha entre temperatura deseada y actual determina el calor aplicado; el calor reduce la brecha (loop de balance).
- Regulador centrífugo (centrifugal governor): válvula abre -> motor acelera -> pesos se abren -> palanca cierra la válvula -> motor frena -> pesos bajan -> válvula abre. Se autorregula. Lección: para sintonizar un sistema hay que entender qué interacciones dominan; fricción/juego ("play") en las uniones suaviza oscilaciones (equivalente a damping/delay en un loop de juego).
- Conejos en Australia (24 conejos, sin predación, explosión): una pequeña introducción puede desestabilizar un ecosistema entero.
- Lobos en Yellowstone (14 lobos + 52 más, 1995): **cascada trófica (trophic cascade)**: un cambio en un nodo de alto nivel se propaga hacia abajo por todo el ecosistema (los lobos asustan a los alces, vuelven árboles, osos, aves, peces, castores, ríos cambian de curso). Diagrama con +/- en flechas; los efectos se invierten transitivamente (reducir lo que reduce = aumentar).

### 1.2 Sistemas como proceso del mundo [Systems as the Process of the World]
- Los sistemas hay que **experimentarlos** (operando, en contexto); no se entienden leyendo reglas estáticas. Ejemplo: **boids de Reynolds** (3 reglas: no chocar, igualar dirección/velocidad con vecinos, ir al centro de masa visible) - leerlas no te da el flock; hay que correrlo.
- Tesis del autor: **diseñar y modificar juegos es la mejor forma de aprender a ver sistemas**. Ejemplo: el hijo del autor entendió el pricing de la casa por la Casa de Subastas de WoW (un sistema económico del juego se generalizó al mundo real).
- Interconexión creciente: un incendio en una planta (Sumitomo, 1993) disparó el precio de memoria de $33 a $95 por MB; sistemas acoplados propagan shocks lejos.
- Habilidad para programadores/diseñadores: pensar en el sistema entero (cómo mi cambio afecta a lo demás, qué comportamiento esperado de los usuarios, qué impacto final).

### 1.3 Qué es una "cosa" [A Strange Systemic Journey]
- Barco de Teseo (Theseus' ship): ¿sigue siendo el mismo barco si cambiás todas las piezas? Respuesta sistémica: la identidad está en las **relaciones** entre las partes, no en las partes. Si reemplazás tablas sin romper la estructura relacional, el sistema persiste; Helen construye otro con las piezas viejas = otro sistema.
- Las "cosas" (átomos, moléculas, protones) son estructuras de relaciones y energía; las partes no están "dentro", **son** el todo visto en más detalle. Frase del autor: las cosas son "menos como una mesa, más como un tornado".
- **Metaestabilidad (metastability):** estable en el tiempo pero siempre cambiando a un nivel inferior (proton, bandada, huracán, corriente de agua). Es la propiedad básica de un sistema.
- **Sinergia (synergy, Buckminster Fuller):** comportamiento del todo no predecible por las partes por separado.
- **El "tercer elemento" (the "third thing", D.H. Lawrence) / "cualidad sin nombre" (quality without a name, Alexander) / "causa" de Aristóteles:** lo que hace que el agua sea agua o una casa más que un montón de ladrillos = el todo que surge de las relaciones. Poincaré: hechos acumulados no son ciencia como ladrillos apilados no son casa.
- Alexander (A Pattern Language): ningún patrón existe aislado; existe en la medida que lo sostienen patrones más grandes, del mismo tamaño y más chicos. Aplicación: al construir una cosa hay que "reparar" el mundo alrededor y adentro. Donde él dice "patrón", Sellers dice "sistema".
- Para el diseñador de juegos: ver "el tornado en la mesa quieta": el diseño estático (tablas, árboles de habilidades) es un sistema dinámico; ver a la vez la experiencia total (game as played, camino único de cada jugador) y poder "hacer zoom" en cada pieza sin colapsarla a un solo camino por el espacio de estados.

