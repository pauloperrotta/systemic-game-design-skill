# Partes, atributos y comportamientos (cap. 8)

Leer para bajar un diseño al nivel 'de planilla': elegir los atributos mínimos, órdenes de atributo (monto/tasa/tasa de la tasa), rangos, comportamientos locales y genéricos que generan emergencia, reglas de feedback (100-250 ms, consistente, sin ruido), cerrar loops entre partes, y documentar en texto + planillas data-driven.

Resumen parafraseado de Sellers, *Advanced Game Design: A Systems Approach* (2018). Entre corchetes va la sección del libro de donde sale cada bloque.

## Índice
- 1. Getting Down to Parts (intro)
- 2. Defining Parts
- 3. Determining Attributes (reglas para elegir atributos)
- 4. Attribute Ranges (rangos de atributos)
- 5. A Nautical Example (ejemplo: batallas navales era de la vela)
- 6. Specifying Behaviors for Parts
- 7. Back to the Nautical Example (behaviors del barco)
- 8. Creating Looping Systems (loops a partir de partes)
- 9. Don't Get Lost in the Weeds or the Clouds
- 10. Documenting Your Detailed Design
- 11. Spreadsheet Details (estructura de las planillas)
- 12. Questions to Consider About Your Detailed Design (completas, parafraseadas)
- 13. Resumen del autor (Summary)
- 14. Checklists operativos extraidos (para diseñar / analizar / balancear)
- 15. Referencias de ejemplos citadas (indice rapido)

---

---

## 1. Getting Down to Parts (intro)

- **Parts (partes)**: los componentes de un sistema; crean loops por sus acciones. En juegos es donde se definen numeros y funciones logicas que hacen que el juego funcione.
- Una parte puede ser **subsistema** de otro nivel. En algun punto hay que llegar a partes **atomicas/simples (simple/atomic parts)**: indivisibles; ahi se deja el pensamiento en loops y se pasa a estructuras y comportamientos internos.
- **Nouns y verbs del juego**:
  - Atributos (attributes) = sustantivos = determinan el **estado (state)**; tienen valores y definen **recursos**.
  - Comportamientos (behaviors) = verbos = definen la **funcion**; especifican interacciones con otras partes y flujos de recursos. Los behaviors son lo que permite crear loops -> sistemas.
- Las partes especifican las interacciones y sus efectos, incluido el **feedback al jugador**, que permite decisiones significativas. Del loop jugador-juego sale la experiencia.
- Implicacion: hay que poder cambiar de foco entre parte atomica, loop sistemico y experiencia global.

## 2. Defining Parts

- Meta: cada parte "spreadsheet specific": estado interno especificado sin ambiguedad. Toda parte termina descompuesta en **tokens estructurales (structural tokens)** (cap. 3 y 7, "Parts as Loop Components") + behaviors que actuan sobre ellos.

### Types of Parts (tipos de partes)
Tres familias; todas tienen estado y comportamiento via atributos y valores:
1. **Fisicas**: personaje, ejercito, arbol.
2. **No fisicas (conceptos)**: area de control, emocion, tiempo.
3. **Representacionales / de reglas**: maximo de cartas en mano, displays/controles de UI, orden de turnos actual.
- **Partes decorativas de fondo** (decoracion de UI) sin estado ni comportamiento: van a la lista de arte/UI, NO son partes de sistema.

### Your Game's Parts (como encontrarlas)
- Partir de los loops ya esbozados (modelo interno + loop interactivo): ahi aparecen recursos, monedas y valores = partes nucleo.
- Pocas partes concentran la atencion del jugador y estan en los core loops: RPG = personajes y oponentes; estrategia = ejercitos y area controlada.
- Cada parte primaria arrastra otras contenidas jerarquicamente (personaje -> armas, armadura, hechizos, botin, mascota/caballo; ejercito -> tipos de unidad; area -> adyacencia, produccion de recursos).
- Listar todo para ver cantidad y jerarquia; los sistemas definidos en loops indican cuales son atomicas y cuales necesitan mas especificacion.
- Considerar fisicas, no fisicas y representacionales: cualquier cosa con datos internos de estado, con comportamientos que afectan otras partes, o con la que el jugador interactua (ej. personaje -> armas -> UI del inventario).
- **La lista de partes es un proxy del alcance (scope)**: cuanto trabajo de arte, animacion y programacion. Se alarga rapido.
- Separar por tipo, tipicamente en **hojas distintas** de la planilla, agrupando las que comparten atributos (no mezclar objetos de entorno con NPCs enemigos ni con objetos de UI como las cartas en mano). Sirve para detectar partes faltantes; las del mismo tipo comparten muchos atributos/behaviors.

### Internal State (estado interno)
- Estado de una parte = valor actual de cada atributo/variable (hitPoints = 5, gold = 10, class = Ranger, secretName = "Steve"). Incluye numeros, tipos, strings, cualquier rasgo con nombre y valor.
- Los atributos son **estand-ins de sistemas reales**: en vez de modelar metabolismo, un atributo "5 hit points".
- **Name-value pairs** (attribute-value / key-value): estructura clasica de programacion y bases de datos. Si el dato es numerico de cierto tipo (unidades, dolares) = un **stock** en terminos de sistemas.
- Mapeo a programacion: una parte = instancia de clase (miembros de dato = atributos; metodos = behaviors). OOP y component-based encajan bien.

## 3. Determining Attributes (reglas para elegir atributos)

Reglas practicas, en orden:
1. **Tan pocos como sea posible**: cada atributo suma complejidad a reglas y codigo y es **una nueva forma de desbalancear** el juego. Empezar con pocos y agregar por iteracion.
2. **Combinar atributos similares entre partes**: no crear dos atributos para dos partes si uno sirve.
3. **Priorizar atributos con los que el jugador interactua mas o que dan mas decisiones significativas.**
4. **Prueba de comunicacion**: si no podes comunicar rapido al jugador como difieren dos atributos y por que ambos importan, quitar uno o fusionarlos. Ejemplo: ataque slash vs pierce; salvo que el juego trate del combate cuerpo a cuerpo fino, un solo atributo de ataque alcanza (se agrega un segundo despues si hace falta).
5. **Amplia aplicabilidad**: evitar atributos usados por 1 o 2 partes. Ej: "visibility" en una parte camuflable: ¿otras partes pueden ocultarse? Si es la unica, ¿vale la pena o se generaliza? Muchos atributos de un solo uso complican sin enganchar mas y dificultan programar behaviors.
   - **Excepcion**: la representacion del jugador (personaje, nacion) puede tener varios atributos unicos por su relacion especial con el resto del juego.
6. **Considerar cantidad (amount) y tasa (rate) de un recurso**: ej. cuenta con gold = 100 (monto) y atributos income = 10, debt = 3 (tasa) -> +7 por periodo. El periodo puede ser un atributo de la cuenta o, mas probable, uno global del juego (por turno, por minuto).

### Orden de los atributos (first/second/third-order attributes)
- **First-order**: describen un monto (gold, XP actuales).
- **Second-order**: afectan la tasa de cambio del recurso (income, rate de XP en idle games).
- **Third-order y mas**: la tasa misma cambia (income que crece lentamente; XP necesaria para el proximo nivel y la nueva tasa en ese nivel: ambas son de tercer orden).
- **Decision de diseño**: ¿atributo o funcion? Si el proposito se representa simple con un numero -> atributo numerico. Si requiere logica para determinarse -> es salida de un behavior (y la parte pasa de simple a sistema propio).

## 4. Attribute Ranges (rangos de atributos)

Para cada atributo numerico definir el rango valido. Requisitos del rango:
- Que vos lo entiendas intuitivamente **y** puedas comunicarlo al jugador.
- Que funcione bien en todas las partes que usan el atributo.
- Que de **suficiente discriminacion** entre valores (¿se nota la diferencia entre 5 y 6? ¿hace falta un 5.5?).
- Que no sea tan grande que se pierda el "feel" (556 vs 557 no se distingue).

Reglas/heuristicas:
- Ejemplo: ataque 0-10; si 5 vs 6 no se distingue o falta granularidad, pasar a 0-100; 0-1000 casi siempre es excesivo.
- Rangos de bytes (0-128, 0-255) son utiles para programar pero se transponen a 0-100 o 0-10 para el jugador (la gente no piensa en binario/hex).
- Por defecto **enteros**: faciles de entender y mas rapidos que floats.
- Para probabilidades combinadas se usa 0.0-1.0 (matematica mas facil) pero la gente distingue mal 0.5 de 0.05. Truco: definir un rango entero grande (0-10,000) y dividir al operar (**normalization**, normalizacion a 0.0-1.0).
- Al jugador se le puede mostrar el numero como mejor convenga: entero, o **etiquetas de texto** mapeadas al numero ("terrible" ... "awesome").
- **Forma del rango (linear vs differential probability)**: percentil 1-100 = cada valor igual de probable (99 tan probable como 37 o 2). Dos d6 sumados: rango 2-12 pero no equiprobable (2 y 12 ~3% c/u; 6 ~17% porque se obtiene de 5 formas: 5+1, 4+2, 3+3, 2+4, 1+5). Un 10 en escala lineal 1-10 significa algo muy distinto que un 10 en campana 2-12. Hay que entender como se determina el atributo, no solo su rango. (Se desarrolla en cap. 9, Fig. 9.1.)

## 5. A Nautical Example (ejemplo: batallas navales era de la vela)

Ejemplo extendido de como encontrar partes y atributos; resumido:
- **Concepto**: combate naval de barcos de linea, mas estrategico/tactico que accion rapida (hay tiempos muertos). Define como se gasta el **interactivity budget** (presupuesto de interactividad). Se descarta meter elfos marinos/dragones (control de scope). Jugador construye su armada y pelea contra una flota enemiga controlada por el juego.
- **Sistemas derivados**: progresion primaria con **loop economico** (defender puertos/comercio -> dinero para construir/reparar barcos y contratar tripulacion); subsistema economico de comercio mercante dentro del modelo (el jugador no lo toca directamente pero hay que pensar sus partes).
- **Riesgo detectado: rich-get-richer / snowball**: si el enemigo hunde mercantes o toma un puerto, el jugador pierde fondos y no puede recuperarse. Solucion sugerida: **balancing loop** (ej. suma unica del rey para retomar el puerto).
- **Core loop**: el jugador dirige batallas entre su flota y la enemiga. **Outer loop**: usa ingresos para construir/reparar y contratar (quiza inteligencia).
- **Partes nucleo**: barcos (primarios, en core loop y progresion). Hace falta sistema de navegacion (incluye orientacion respecto al viento) y de combate (ecologia de loop balanceador entre varios barcos). Cada barco necesita saber a que armada pertenece (para no disparar a aliados).
- **Decision de granularidad**: ¿tripulacion = un par nombre-valor ("crew = 100") o subsistema (entrenamiento, moral)? No hay respuesta unica: depende de la experiencia, el interactivity budget y la cantidad de unidades. Con 2-3 barcos el detalle es bienvenido; con 200 es una carga. Mas detalle = mas decisiones, pero es facil pasarse. Disenar inicial -> playtestear.
- **Atributos definidos**: crewNumber, crewTraining, crewMorale (enteros, entradas de los behaviors del barco; pueden volverse subsistema despues); shipNation, shipName (no numericos, identificadores); maxSpeed, velocidad de giro, maximo de velas, velas desplegadas actuales (enteros, cada uno podria volverse subsistema); cantidad de cañones operativos (determina fuerza de ataque; velocidad y calidad de disparo dependen de la tripulacion).
- **Captain como parte propia**: se separa del crew para dar textura (heroes como Nelson, Cochrane, Aubrey); algunos navegan/pelean mejor -> eleccion significativa de a quien asignar a cada barco. El barco tiene un atributo "captain" que es una parte con sus atributos y behaviors.
- **Huecos detectados al revisar**: falta el **viento** (atributos: direccion, intensidad, quiza frecuencia de cambio; puede ser parte compleja con subsistema que interactua con el barco). Tripulacion mejor entrenada deberia navegar mas rapido: como "training" ya existe como atributo, agregarlo cuesta poco.

### The Detail Design Process (proceso)
- Hay que definir **cada parte y cada atributo**; algunas atomicas, otras con sistemas propios; todas tienen behaviors y casi todas aportan a decisiones del jugador.
- **Limitar** atributos/partes/sistemas que existen solo para el loop interno y casi no interactuan con el jugador (ej. el sistema de comercio que da la recompensa por proteger mercantes). Tiene que haber pocos; hacerlos lo mas simples posible: si no genera interaccion ni decisiones, no gastar esfuerzo (balancearlos es complejo e iterativo, cap. 9-10).
- **Proceso iterativo (parte del designer's loop)**, en orden:
  1. Definir partes y atributos claramente necesarios para core loops y la experiencia deseada.
  2. Definir behaviors de las partes para enlazarlos en loops.
  3. Iterar con mockups y prototipos (cap. 12). Un prototipo feo con core loop completo ya dice mucho sobre si el juego vale la pena.
- Definir recursivamente (partes dentro de partes); no hace falta completar todo de una vez.

## 6. Specifying Behaviors for Parts

- Behaviors = complemento funcional de los atributos: por ellos las partes forman loops (engines, economies, escapements, ecologies) y le dan feedback al jugador.
- Preguntas base: ¿que recursos crea, consume o intercambia cada parte? Recursos fisicos (salud, dinero, mineral) y no fisicos (movimiento, tiempo, experiencia, cordura, combos).
- El jugador tambien acumula unos recursos y minimiza otros; algunas partes lo ayudan y otras le ponen oposicion ("push back" contra sus metas). El jugador decide en su loop mental -> interactua.
- **Regla**: por cada cambio de un recurso o interaccion entre dos partes o jugador-juego tiene que existir un behavior.
- Cada behavior termina siendo una **formula o logica** iterable = las reglas del juego (humanas en tabletop, codigo en digital).

### Principios de creacion de behaviors

**a) Local action (accion local)**
- Un behavior interactua con partes de **nivel de organizacion similar** y **mismo contexto operacional**. Cañones afectan tripulacion (cansancio) y otros barcos (daño): ok. Cañones afectando el comercio de un puerto: **no local** (otro nivel, sin conexion operacional razonable).
- La parte que actua **aporta un efecto** (cambio de recurso) pero **no decide como responde la otra**. "20 de daño" al otro barco; el barco receptor decide si pierde crew, cañones, velas o se hunde. En lenguaje de sistemas: una parte puede **perturbar (perturb)** el estado de otra pero no **determinarlo**. En OOP: **encapsulation** (no se "mete la mano" para setear atributos de otro objeto).

**b) Generic, modular behaviors (genericos, modulares, libres de contexto)**
- Lo mas simples posible, sin mas contexto del necesario, lo bastante genericos para muchas situaciones. Cañones disparan -> infligen daño; no saben si el blanco es enemigo ni cuanto daño ya tiene (eso lo decide otro behavior: jugador o capitan NPC decidiendo disparar).
- Error comun: el contexto se cuela en scripts elaborados -> menos reuso. Ejemplo: NPC con "open the door" generico (no sabe por que va a otra sala, ni destrabar o forzar; "unlock door" solo destraba). Contra-ejemplo: "mover al NPC de su cuarto a la sala de comando" = complejo, contextual, sirve una sola vez, sin emergencia.
- Señal de problema: escenas/behaviors scriptados angostos y **fragiles (brittle)**, no aplicables a la funcion general del NPC.

**c) Creating Emergence (emergencia)**
- Behaviors locales + de un nivel + modulares/genericos = fuente de efectos emergentes: variedad infinita, atencion y engagement prolongado con **menos contenido y menor costo** que el scripting muy contextual.
- Ejemplos de emergencia (una linea c/u):
  - **Flocking (boids)**: 3 reglas locales por pajaro (misma direccion/velocidad que los vecinos; no chocar; tender al centro de masa cercano) -> bandadas dinamicas e impredecibles.
  - **Conway's Game of Life** (Gardner 1970): celdas on/off con 4 reglas segun los 8 vecinos (menos de 2 vecinos on -> off; on con 2-3 -> sigue on; mas de 3 -> off; off con exactamente 3 -> on). Solo contexto local, solo afectan a la propia celda -> patrones fascinantes.
  - **Parable of the Polygons** (Nicky Case 2014, basado en Schelling 1969): triangulos y cuadrados con atributo "happiness" segun vecinos iguales (feliz si exactamente 2 vecinos iguales; "meh" si todos son iguales; infeliz si solo 1; solo los infelices pueden moverse; el movimiento lo hace el jugador, no los poligonos). Resultado emergente: segregacion aunque nadie la quiera.
  - **Slime Rancher** (2016): los slimes se apilan al estar cerca (sin proposito): permite que escapen de un corral para llegar a comida (apilar + buscar comida); los **tabby slimes** mueven comida que no pueden comer hacia donde ya hay comida: se percibe como robo o regalo, redistribuye comida y dispara cascadas imprevistas que deleitan.

**d) Providing Feedback (feedback al jugador)**
- Cierra el **loop interactivo**: el jugador perturba el estado; el juego actua con behaviors y responde. **Todo verbo del juego debe dar feedback al jugador.** Si una parte no tiene behavior o el behavior no tiene feedback, cuestionar con rigor si hace falta.
- El feedback construye el **modelo mental**: aprender, confirmar o recrear predicciones, ver que funciona, evaluar la propia mejora. Mantiene el engagement.

**Feedback and Player Expectations (tres casos)**
1. Feedback coincide con la expectativa -> experiencia positiva, refuerza el modelo.
2. Feedback sorprendente pero el jugador ajusta el modelo rapido -> aprendizaje valido, tambien positivo.
3. Feedback ausente, distorsionado o incompatible con el modelo y no se puede reconciliar rapido -> negativo, baja el engagement.
- Informa efectos de acciones recientes y procesos en curso (analogia: encender la hornalla = saber de inmediato que calienta; el agua hirviendo = feedback gradual de temperatura).

**Kinds of Feedback (tipos)**
- Mayormente **visual y auditivo**, mas texto/simbolos. Visual: cambios de color, tamaño, animacion, efectos especiales (brillo, fuegos artificiales). Auditivo: tonos, notas, cambios de musica, SFX. Se usa mas lo visual (dice cual parte cambio mejor que el sonido), pero el sonido se subutiliza y con poca imaginacion.
- **Todo cambio de estado, toda accion de un behavior, debe tener feedback.** Si un cambio no merece feedback, examinar si es necesario en el juego: ¿el jugador necesita saber ese estado para mejorar su modelo?
- Intensidad proporcional: cambio sutil = barra de termometro que se llena lento; **cambio de estado completo** (edificio terminado y utilizable) = notificacion enfatica. Si el jugador se pierde "ejercito listo" o "agua hirviendo", se frustra y pasa a vigilar la UI en vez de jugar.

**Amount, Timing, and Comprehension (cantidad, tiempo, comprension)**
- **Cantidad**: relacionar con el interactivity budget. Accion rapida con solo interactividad accion/feedback puede bombardear los sentidos (es parte del atractivo). Estrategia, relaciones, socializacion: si hay caos visual/auditivo, **reducir partes y behaviors** para dejar el foco donde corresponde.
- **Timing**: feedback **inmediato** = no mas de **100 a 250 ms** del cambio (cap. 4). Entre ~0.25 y ~1 s se siente con lag molesto. Mas de ~1 s: el jugador puede no asociarlo al cambio.
- **Comprension instantanea**: la conexion con el estado debe ser obvia, sin razonar simbolos oscuros. Ejemplo malo: llama azul arriba a la izquierda = agua hirviendo (azul=agua + llama=calor). El jugador juega el juego, no la UI ni las reglas.
- Basta con que el feedback diga "el estado de esta parte cambio" y sea reconocible como tal.
- **Texto = mal medio**: "la gente no lee" (exageracion util). Aun numeros flotantes de daño: importa mas color y movimiento que la cifra. Para feedback que exige razonar: seccionarlo (dialogo/ventana aparte) y **pausar el juego** si es posible hasta que se absorba.
- **Evitar feedback enganoso o sin sentido**: los fuegos artificiales deben significar algo; no dispararlos al azar ni para estados distintos segun la situacion. Cualquier cosa es valida si es obvia, inmediata y **consistente**.
- Animaciones/sonidos "de ambiente" sin atar a un cambio de estado (aunque trivial) son riesgo: el jugador interpreta casi todo feedback como significativo y lo mete en su modelo; si no significa nada, es **ruido** que distrae y baja el engagement.

## 7. Back to the Nautical Example (behaviors del barco)

- Barcos: moverse, atacar, recibir daño del enemigo; hacerse la pregunta ¿falta algo que el barco deba hacer? Decidirlo en el diseño inicial y revisarlo en playtest.
- Capitan y tripulacion contribuyen a navegar y pelear: base de sus behaviors (funciones de interaccion con el barco = sistemas de navegacion y combate).
- **Attack del barco** = atributo de cañones operativos modificado por la tripulacion. El capitan NO modifica el ataque directamente (para interbloquear sistemas y mantener local el behavior del capitan): su behavior suma un bonus (o malus) a la **moral** del crew segun su atributo **Leadership**.
- Behavior "fight" dentro del crew: combina numero de tripulantes, moral (afectada por el capitan) y entrenamiento (afectado por dinero que gasto el jugador) para producir un **modificador** del ataque del barco (Fig. 8.2: Captain.Leadership -> Crew.Morale; Crew.Number/Training -> "Fight!" -> Ship.Attack con Cannon; -> barcos enemigos; conexion tentativa de retorno para mejorar Leadership).
- **Funcion de peso ponderada**: pocos tripulantes con muchos cañones = ataque bajo (sin crew no disparan); mucho crew con moral/entrenamiento malos = bajo; gran capitan + buen crew + pocos cañones = bajo; capitan fuerte + crew numeroso + muchos cañones = alto. Esto sugiere una formula/logica que determine el efecto de cada factor, como interactua el jugador con cada uno y el rango de valores posibles del modificador de ataque.
- Puede generar **atributos subsidiarios**: coeficientes de ponderacion (cuanto pesan cañones, crew, capitan) que se ajustan iterando en playtest (balance, cap. 9).
- Sailing similar, pero con la variable externa **viento** (direccion/intensidad): ¿alcanza ese detalle? Depende de la experiencia de juego.
- Tokenizar el concepto; testear y ajustar en prototipos lo antes posible: no se acierta de entrada con partes, atributos ni behaviors. Documentar el diseño de partes.

## 8. Creating Looping Systems (loops a partir de partes)

- Los behaviors deben ser locales, genericos, con mucho feedback **y formar loops de retroalimentacion**, no solo cadenas lineales. **Cada parte debe afectar y ser afectada** por otras.
- Ejemplo: barcos que pelean: ataque depende de cañones operativos, calidad/cantidad de crew y liderazgo. Al recibir daño pierden crew y/o cañones, y la moral baja -> menor capacidad de contraatacar. Los dos barcos forman un **loop balanceador ecologico** (intercambio del recurso "daño", cada uno reduce su propio crew y cañones).
- La contribucion del capitan es **conexion de una sola via**: funciona pero no crea sistema dinamico. Para cerrarla: que el crew afecte al capitan de vuelta. Opciones:
  - **Loop economico reforzador** corto: si la moral queda alta al terminar el combate, el capitan gana Leadership (se intercambia Morale por Leadership).
  - **Loop de progresion** largo: el capitan gana Leadership solo tras ganar cierto numero de batallas; el exito mejora el liderazgo que mejora el exito.
- Hay que asegurar que las partes se afecten entre si formando loops **y** que formen loops interactivos con el jugador. Las partes clave deben conducir los core loops con sus interacciones.
- Decisiones del jugador que alimentan los loops: momento a momento en batalla (efecto inmediato en capitan, crew, barco) y decisiones de largo plazo (que capitan en cada barco, cuanta tripulacion, cuanto gastar en cañones y mantenimiento).
- **Chequeo**: revisar la lista de partes y confirmar que cada una afecta a algunas y es afectada por otras. NO hace falta que cada parte afecte a todas (el modelo mental seria imposible); basta con que afecte a unas pocas, localmente y a niveles de organizacion parecidos.
- Usar las plantillas del cap. 7 (engines, economies, ecologies) para mapear los loops. Cada parte puede ser atomica o tener loops internos: asi se construye jerarquia y profundidad (= mas engagement).

## 9. Don't Get Lost in the Weeds or the Clouds

- Tipos de diseñador (**storytellers, inventors, toymakers**) se sienten comodos en etapas distintas; hay que moverse por todos los niveles de organizacion sin perder la vision global.
- Storyteller de alto nivel: bajar a atributos/behaviors puede sentirse tedioso, pero es la unica forma de que el diseño sea real. Diseñador de detalle: el concepto puede sentirse nebuloso, pero hay que dejar la precision y verificar que los detalles sumen algo disfrutable.
- **Señal de problema**: un juego que es "un monton de partes tiradas esperando que sean divertidas" (sin concepto cohesivo). Tampoco hace falta realismo total ni gran variedad: una clase de catapulta en un juego de estrategia puede bastar, no cinco; tres tipos de flores/peinados/estandartes pueden bastar. Si disfrutas definiendo partes, no abusar como via a una experiencia coherente.
- Todo juego necesita partes/atributos/behaviors totalmente definidos, pero **existen para construir loops y soportar la interactividad perceptual, cognitiva, social, emocional y cultural** que genera la experiencia. El juego no es las partes: emerge de sus interacciones entre si y con el jugador. Tener las partes no alcanza.
- Ver el todo y las partes a la vez; subir y bajar de abstraccion: concepto claro, sistemas que lo soportan, partes que habilitan interacciones y progresion significativas.

## 10. Documenting Your Detailed Design

- En el diseño detallado la especificidad es critica: define que es el juego, por que y como se implementa.

### Getting Started and Overall Structure
- Al principio: pizarron o doc de texto. Luego pasar a **documentos de diseño textuales + planillas**.
- **Textos**: preservan la intencion de cada parte con precision implementable (codigo o reglas analogicas).
- **Planillas (spreadsheets)**: hogar de toda la informacion especifica, sobre todo numerica (atributos y valores). Ademas permiten testear e iterar rapido.

### Detailed Design Documents (contenido)
- Un conjunto de documentos que especifique todo: **design rationale** (por que cada parte importa) + **descripcion de comportamiento especifica** convertible a codigo o a reglas de juego.
- Usar imagenes, diagramas, flow models, mockups; enlazar a mockups y prototipos externos.

### Being Assertive and Precise (reglas de redaccion)
- Tratarlos como **planos de un edificio**.
- Tiempo **presente** ("el juego se comporta asi", no "se comportara"); sin palabras evasivas ("podria").
- Evitar cualitativos salvo en alto nivel: no "este enemigo se mueve rapido", "gran explosion", "esta torreta gira izquierda y derecha". Preguntar: ¿cuan rapido? ¿cuan grande? ¿hasta donde?
- Donde haya cantidad (numero de skills/niveles, daño): dar un **numero, un rango definido o una referencia a una ecuacion/factor** en el doc o la planilla. Si la decision aun no esta tomada, **decirlo y marcarlo como asunto abierto (issue to resolve)**.
- Ser preciso obliga a eliminar la vaguedad del diseño en la cabeza; es mas facil encontrar huecos en una propuesta que en una idea.

### Avoiding Overdoing It
- Documentar de mas daña tanto como documentar de menos.
- Si sabes el detalle: documentarlo (diagramas, mockups, texto). Si no: documentar lo que buscas, tus mejores ideas y **caminos descartados**, y **prototipar** (papel o electronico). No documentar ni discutir muchas opciones: **ubicar la zona de incertidumbre y prototiparla**; una vez claro el camino, documentar eso y por que.
- Documentos online, compartibles, enlazables, comentables, editables con **control de cambios** (quien, cuando, rollback). Linkeados entre si y a los docs de sistemas y concepto.
- Diagramas de una pagina, grandes y visibles, por sistema, para que el equipo los internalice.
- Evitar la **"design bible" monolitica e impenetrable**; preferir referencias chicas y comprensibles para artistas, programadores, etc.

### Keeping Your Documentation Up-to-Date
- Documentos "vivos": planear desde el inicio actualizarlos. Si se descuida, el juego implementado se aleja del diseñado y la doc queda desactualizada, enganosa y "peor que inutil".

## 11. Spreadsheet Details (estructura de las planillas)

- **Estructura base**: una **fila por parte**, una **columna por atributo**. El estado de la parte = valores en su fila.
- Ejemplo (Fig. 8.3, armas cuerpo a cuerpo): columnas Name / Attack / Damage / Speed; filas: Dagger, Short sword, Cutlass, Broad sword, Rapier, Long sword, Great sword (valores tipo Attack 0-5, Damage 2-6, Speed 1-5; el texto extraido tiene la tabla desalineada, no confiar en los numeros exactos).
- Partes de tipos muy distintos (armas, flores, autos, equipos) -> **grupos o, mas comun, hojas separadas**; partes del mismo tipo juntas. Armas a distancia o hechizos pueden ir en la misma hoja si comparten casi todos los atributos; si no, hoja propia con sus atributos.
- Pueden haber celdas con el **efecto de cada behavior en forma matematica** (formulas).
- Incluir **punteros** a descripciones externas (texto y diagramas) de partes, atributos y behaviors.

### Beyond Attributes and Values
- **Nombres**: una parte puede tener nombre en pantalla, nombre interno de referencia y nombre de archivo/directorio de contenido (arte, sonido). Listar todos en la planilla: ayuda a **localizacion** (reemplazar el nombre en pantalla por el equivalente en otro idioma) y a mantener el esquema de nombres de archivos que el programa lee.
- Un **unico estandar de nomenclatura** de archivos, seguido a rajatabla y reflejado en la planilla, ahorra "inmensos dolores de cabeza"; dejar que cada uno nombre a su gusto es receta de desastre (no se puede reconstruir por que un archivo se llama asi). No hace falta resolverlo desde el dia 1.
- **Formato por color** para legibilidad: distinguir nombres de partes, **coeficientes globales**, numeros que no deben cambiar, etc.
- **Comentarios en celdas**: registrar el por que de un nombre o valor, y si es **temporal/en prueba** o **testeado a fondo y no debe cambiar**. Mantenerlos al dia o se vuelven enganosos.

### Data-Driven Design
- Lo mas valioso de la planilla: usar los datos **directo en el juego** (si es digital). Vale la pena automatizar la **exportacion a CSV, JSON o XML** que el juego lea.
- Los objetos del codigo tienen **valores por defecto de inicializacion** que el archivo de datos sobreescribe -> datos y estructuras de codigo separados.
- Si planilla/docs coinciden con partes y atributos del codigo, los diseñadores prueban valores nuevos **sin tocar codigo** -> mucha mayor velocidad de iteracion.
- Paso extra recomendado: que el juego mire el **timestamp** del archivo exportado y lo **recargue si cambio**, permitiendo cambiar datos **con el juego corriendo** (hot reload) y probar muchos mas valores de atributos, acortando todavia mas el ciclo diseñar-testear.
- Nota al pie: en juegos analogicos sirve igual: prepoblar valores de cartas e importarlos a un programa de layout reduce mucho el tiempo de test e iteracion.

## 12. Questions to Consider About Your Detailed Design (completas, parafraseadas)

1. ¿Hay suficientes partes definidas para armar el core loop? ¿Cada una tiene atributos, valores, rangos de valores y behaviors?
2. ¿Todas las partes tienen interacciones significativas entre si y con el jugador? ¿Todas afectan a otras y a la vez son afectadas?
3. ¿Definiste distintos tipos de partes: fisicas, no fisicas y representacionales del juego?
4. ¿Cual es el menor numero de estados y behaviors con que se pueden construir los loops y lograr los efectos buscados? ¿Soportan las interacciones y caminos de progresion deseados?
5. ¿Las partes principales estan especificadas lo bastante como para implementarlas ("spreadsheet specific")?
6. ¿Los behaviors dan suficiente feedback para que el jugador entienda cuando hay cambios de estado y arme su modelo mental?
7. ¿El jugador tiene suficiente interaccion? ¿Las partes habilitan decisiones significativas y suficientes "knobs and dials" para perturbar el modelo interno del juego?
8. ¿Los efectos de los behaviors son locales en alcance y generales en aplicabilidad? ¿Hay partes con efectos globales, behaviors de un solo uso o fragiles, o que opaquen a todos los demas?
9. ¿Estan documentados partes, atributos y behaviors? ¿Hay docs de texto y diagramas enlazados a planillas con los datos parte-atributo? ¿Se pueden leer esas planillas en el juego mientras se desarrolla para acelerar el testeo iterativo?

## 13. Resumen del autor (Summary)

- Se llego al nivel mas detallado y mas "aterrizado" del diseño. Disenar bien las partes arma los sistemas y soporta la experiencia deseada; documentarlas en texto y numericamente en planillas garantiza que sean implementables y que los numeros apoyen los objetivos globales. El cap. 9 muestra como lograr que valores y efectos de las partes den una experiencia balanceada.

---

## 14. Checklists operativos extraidos (para diseñar / analizar / balancear)

**Diseñar una parte nueva**
1. ¿Que tipo es (fisica / no fisica / representacional)? ¿Es atomica o subsistema?
2. Atributos minimos: ¿ya existe uno equivalente en otra parte? ¿el jugador lo ve y decide con el? ¿lo puedo explicar en una frase distinta al otro atributo parecido?
3. Para cada atributo: orden (monto / tasa / tasa-de-la-tasa), rango, tipo (entero, normalizado, etiqueta, string), forma de distribucion (lineal vs campana), escala comunicable al jugador.
4. Si el valor necesita logica -> pasa a ser behavior (y la parte es sistema).
5. Behaviors: ¿que recurso crea/consume/intercambia? ¿es local (mismo nivel y contexto)? ¿solo perturba, no determina? ¿es generico/sin contexto? ¿que feedback produce?
6. ¿Cierra un loop (afecta y es afectada)? Si la conexion es de una sola via, buscar el retorno (reforzador corto, progresion larga, o balanceador).

**Analizar un diseño existente (señales de problema)**
- Atributos de un solo uso, o dos atributos que el jugador no distingue.
- Rangos demasiado grandes (diferencias imperceptibles) o demasiado chicos (sin discriminacion); 0-1.0 sin normalizar; rangos interpretados como lineales cuando la generacion es campana.
- Behaviors que afectan partes de otro nivel o contexto (no locales); partes que "determinan" el estado de otras (rompen encapsulacion).
- Behaviors scriptados, contextuales, de un solo uso (brittle); falta de emergencia.
- Verbos sin feedback; feedback tardio (>250 ms laggy, >1 s desasociado), oscuro, solo textual, inconsistente o decorativo sin estado detras (ruido).
- Partes con cadenas lineales sin retorno; partes con efectos globales que opacan a las demas.
- Sistemas internos que el jugador no ve ni decide pero a los que se les dedica mucho esfuerzo (ej. comercio mercante).
- Granularidad desbalanceada con el interactivity budget (detalle por unidad con cientos de unidades).
- Posible rich-get-richer: perder reduce recursos para recuperarse -> agregar balancing loop.
- Concepto sin cohesion (pila de partes), exceso de variedad de partes irrelevante, "design bible" monolitica, doc desactualizada, decisiones abiertas no marcadas, adjetivos cualitativos sin numero.

**Balancear (ganchos hacia cap. 9)**
- Coeficientes de ponderacion como atributos propios (peso de cañones/crew/capitan en el ataque) para ajustar por iteracion.
- Cada atributo extra = una nueva via de desbalance; por eso minimizar.
- Planilla data-driven con hot reload por timestamp para probar valores sin recompilar; comentar celdas con estado "temporal / testeado".
- Entender la distribucion de probabilidad de cada atributo (percentil vs 2d6) antes de comparar valores.
- Prototipo con core loop completo (aunque feo) antes de afinar numeros.

## 15. Referencias de ejemplos citadas (indice rapido)
- Nautical age-of-sail game (hipotetico): ejemplo guia de partes, atributos, behaviors, loops y rich-get-richer.
- Flocking (boids): emergencia desde 3 reglas locales.
- Conway's Game of Life (Gardner 1970): emergencia desde reglas de vecindad.
- Parable of the Polygons (Nicky Case 2014) / Schelling 1969: emergencia de segregacion desde happiness local.
- Slime Rancher (2016): apilado + busqueda de comida; tabby slimes moviendo comida -> cascadas emergentes.
- Dos d6 (cap. 9, Fig. 9.1): distribucion no uniforme (2 y 12 ~3%, 6 ~17%).
- Idle games / RPG XP: atributos de segundo y tercer orden.
- Armas cuerpo a cuerpo (Fig. 8.3): ejemplo de planilla parte=fila, atributo=columna.
