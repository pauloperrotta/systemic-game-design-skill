# Balance: métodos y práctica (caps. 9 y 10)

Leer para BALANCEAR con números: los cuatro métodos (diseñador, jugadores, analítica, matemática), probabilidad (1-(1-p)^n, distribuciones, justicia percibida), relaciones cíclicas tipo piedra-papel-tijera vs costo-beneficio, curvas (lineal, polinómica, exponencial, logística, por tramos, NAP), procedimiento para valuar y costear ítems (Mod Value), ritmo y tiempo por nivel, economía (inflación, estancamiento, arbitraje, canal import/export) y métricas (embudos, cohortes, retención).

Resumen parafraseado de Sellers, *Advanced Game Design: A Systems Approach* (2018). Entre corchetes va la sección del libro de donde sale cada bloque.

## Índice
- PARTE A — CAP. 9: MÉTODOS DE BALANCE
- A1. Qué es "balance" [sec: Finding Balance in Your Game]
- A2. Las cuatro familias de métodos [sec: Overview of Methods and Tools]
- A3. Probabilidad en el balance [sec: Using Probability in Game Balancing]
- A4. Sistemas transitivos e intransitivos [sec: Transitive and Intransitive Systems]
- PARTE B — CAP. 10: PRÁCTICA DE BALANCE
- B1. Curvas de progresión y poder: fundamentos [sec: Creating Progression and Power Curves]
- B2. Tipos de curvas costo-beneficio [sec: Defining Cost-Benefit Curves]
- B3. Balancear partes (armas) [sec: Balancing Parts, Progression, and Systems → Balancing Parts]
- B4. Balancear progresión [sec: Balancing for Progression]
- B5. Balance de sistemas económicos [sec: Economic System Balance]
- B6. Balance analítico y métricas [sec: Analytical Balance]
- B7. Resumen del capítulo y mensajes finales [sec: Summary]
- PARTE C — SÍNTESIS PARA USAR (derivada de lo anterior)
- C1. Flujo recomendado de balance (compuesto de los dos capítulos)
- C2. Errores comunes y cómo detectarlos
- C3. Fórmulas de un vistazo
- C4. Ejemplos de juegos citados (una línea cada uno)

---

---------------------------------------------------------------------
# PARTE A — CAP. 9: MÉTODOS DE BALANCE
---------------------------------------------------------------------

## A1. Qué es "balance" [sec: Finding Balance in Your Game]

- **Game balance**: qué tan bien juega el juego; es resultado de las relaciones entre partes (atributos, valores, comportamientos que se afectan entre sí). En el fondo son números (valores de atributos), pero es una propiedad del sistema jugador+juego (incluye el modelo mental del jugador, psicología, sistemas y matemática).
- Incluye: ritmo de progresión individual y global (¿avanza demasiado fácil/rápido o con demasiados impedimentos?, ¿todos los jugadores avanzan a ritmo parecido sin sentirse "en riel"?).
- **Juego balanceado** =
  - No hay un único camino/estrategia dominante ni jugador con ventaja insuperable inherente.
  - Hay un **espacio de posibilidades explorable** con decisiones significativas y varias direcciones viables.
  - No se estrecha el espacio hasta que cómo ganar sea obvio; retrospectivamente no hay "la forma más fácil de ganar".
- Un juego no balanceado (estrategia dominante) **reduce engagement y rejugabilidad**: sabido el truco, para qué seguir. Si todos tienen oportunidades similares, se siente justo; el que pierde siente que pudo ganar y reintenta (sobre todo si no vio que otro explotó un defecto).
- Desde el jugador: puede asumir riesgos y recuperarse; no siente que el final está decidido mucho antes. Se queda en el **flow channel** (habilidad vs. desafío que se igualan dinámicamente, ni aburrido ni frustrante).
- **Metáfora de la bicicleta**: el balance es dinámico, no estático. Si el jugador cae en un estado de fallo irrecuperable, o el juego está balanceado al inicio pero no más adelante, "se cae la bici".
- Casi ningún juego nace balanceado: se logra en el **designer's loop** (iterar + testear). Armar el juego con **sistemas jerárquicos que encastran** permite balancear cada sistema solo y después como parte del superior, en vez de todo el juego de una.
- Enfoque: pensar el balance como manipular **partes y loops** del sistema.

## A2. Las cuatro familias de métodos [sec: Overview of Methods and Tools]

Dos grandes categorías: cualitativos/heurísticos (intuición) y cuantitativos (matemática). Son **complementarios**, no excluyentes.

### 1) Designer-Based Balancing (basado en el diseñador)
- Usar la intuición ("¿se siente bien?"). Necesitás un set de heurísticas de diseño. Imprescindible al principio.
- Ojo: lo difícil no implica desbalanceado (Dark Souls, Super Meat Boy: duros, no para todos, pero no mal hechos).
- **Cautelas**: la intuición también te lleva mal; ningún diseñador acierta un sistema mayor a la primera. No te desanimes si un juego "hermoso" resulta injugable. Peor: **discusiones de horas/días por intuición** sobre algo que se resuelve con un prototipo rápido. Regla: cortar esas discusiones con otras herramientas (prototipar y medir). Las heurísticas sirven para ver qué relación entre atributos produce la experiencia buscada y para decidir cuándo seguir o cortar pérdidas, pero ningún diseñador sabio confía del todo en ellas.

### 2) Player-Based Balancing (basado en jugadores)
- Playtesting: los jugadores juegan y reportan; es el designer's loop en acción. Usarlo liberalmente.
- **Cautela**: los jugadores dan *feedback*, no soluciones. Te dicen qué no les gusta, rara vez cómo arreglarlo; encontrar la solución es trabajo del diseñador (no son diseñadores, así como el que ve películas no es director).

### 3) Analytical Methods (analíticos, hacia atrás)
- Analizan datos reales de cómo se juega. Necesitan suficientes jugadores (cientos/miles) y que el juego esté jugable.
- Mirar comportamiento, no solo cantidad de usuarios: qué caminos siguen, qué misiones repiten o evitan, **cada punto de decisión importante** (registrar la elección y cuánto tardan en decidir).
- Ejemplos de qué medir: en estrategia, qué facción gana cuántas batallas (si una gana mucho más → problema); en RPG, qué personajes eligen al entrar, si leen descripciones, si terminan el tutorial; tiempo para que cada clase llegue a cierto nivel.
- **Ojo con correlaciones**: si los ladrones suben más rápido, puede ser ventaja inherente de la clase O que los juegan veteranos. Cruzar con otros factores (antigüedad del jugador, duración de sesión, cantidad de personajes jugados) antes de concluir.
- Requiere instrumentar el juego: loguear y enviar datos (con permiso en offline). En analógicos: medir duración de partida, de turnos, piezas/estrategias usadas en playtests.

### 4) Mathematical Methods (matemáticos, hacia adelante)
- Modelos de cómo va a funcionar el juego; más útiles al crear un juego nuevo y en juegos competitivos con mucha progresión. Requieren algo de probabilidad/estadística.
- Se apoyan en **hojas de cálculo** (filas = objetos, columnas = atributos compartidos, celdas = valores; formato por color y comentarios para mantener orden). Sirven para visualizar relaciones y armar fórmulas que calculan valores.
- Aseguran: (a) costos y beneficios de los objetos en balance; (b) ningún objeto es "el que vence a todos" ni "al que todos vencen"; (c) objetos, costos y recompensas progresan a un ritmo aproximadamente igual y acorde con la sensación de justicia/engagement y con la velocidad deseada.

### Cautelas de los métodos analíticos [sec: Cautions About Analytical Methods]
- **Analytics-driven vs analytics-informed**: no dejes que los datos (ni los testers ni tu gusto) pasen por encima de todo; interpretalos en contexto. Intentar construir un juego "garantizado" a partir de datos de preferencias (género, mecánicas, arte) falla porque ignora efectos sistémicos/emergentes y lo que los jugadores no pueden pedir porque no lo conciben (cita atribuida a Ford: "caballos más rápidos").
- **Tamaño de muestra y distorsión**: si un % grande de TODOS los jugadores nunca construye X o nunca juega Y, es dato fuerte. Basarse en amigos/focus group chico/comunidad chica es riesgoso (peor caso: cambios porque "al sobrino del jefe no le gusta").
- **Minoría vocal**: los fans más comprometidos son los más ruidosos y los más resistentes al cambio. Caso del autor: juego con ~100.000 jugadores/día, cambios grandes, foros explotaron; el análisis mostró que las métricas clave subían y que los quejosos eran unas pocas docenas (<0,05%). Se mantuvo el cambio; se acostumbraron. Salvedad: a veces los vocales son "líderes de opinión" que anticipan al resto; distinguirlo mirando datos.
- Nota al pie: "learn to play" no es respuesta válida del diseñador a la percepción de dificultad.

### Caso Tumbleseed (análisis de progresión) [sec: An Example: Tumbleseed]
- Postmortem con datos de embudo de progresión: 41% llegó a la Jungla; 8,3% al Desierto; 1,8% a la Nieve; 0,8% a la Cumbre; 0,2% terminó el juego. El 59% no pasó el primer checkpoint y cada uno de los dos siguientes perdía ~80% de los restantes. Debió haber disparado alarmas de rampa de dificultad.
- Causa: el jugador debía dominar a la vez: control nuevo, reglas nuevas, terreno nuevo (aleatorio cada vez), enemigos nuevos (a veces varios), poderes nuevos (algunos peligrosos) → superó el **interactivity budget** (acción/feedback + cognitivo corto + cognitivo largo al mismo tiempo). Además desajuste entre gráficos casuales/coloridos y dificultad dura (afectó ventas).
- Lección: no se arregla "tocando una clase o un nivel"; es un problema que se detecta temprano con playtesting. Lo bueno: instrumentaron progresión y pudieron saber por qué se percibía tan difícil.
- **Heurística de uso**: medir el embudo por checkpoints; caídas de ~80% en pasos consecutivos = alarma. Ritmo de introducción de novedades (no apilar varias a la vez).

### Cautelas de los modelos matemáticos [sec: Cautions About Mathematical Modeling]
- Son un medio, no un fin; la ilusión de "dejar el balance perfecto" es una trampa que consume tiempo. Los modelos encuentran **las partes más desbalanceadas**, no llegan a precisión arbitraria.
- No toman decisiones estéticas: si querés un vehículo más rápido/vistoso sin que cueste más, tenés que compensar con otros costos (mantenimiento alto, mal manejo) usando atributos o sistemas existentes o nuevos.
- Ningún método reemplaza el juicio del diseñador.

---------------------------------------------------------------------
## A3. Probabilidad en el balance [sec: Using Probability in Game Balancing]
---------------------------------------------------------------------

### Primer básico [sec: A Quick Primer on Probability in Games]
- Probabilidad como número entre 0 y 1 (100% = 1,0; 50% = 0,5): permite manipularlas matemáticamente.
- Se usa para **simular sistemas que no implementás**: el punto donde la jerarquía de sistemas "se corta" y asignás una probabilidad (espada que golpea, seducir con ingenio) en vez de modelar física/psicología. Se fija una prob. de éxito, se genera un valor aleatorio y se ve qué pasa.
- **Aleatoriedad**: dados, cartas, contadores, RNG. Alcanza con **aleatoriedad aparente/funcional** (que el mazo no esté trucado, que el período del RNG sea indetectable).

### Eventos separados vs. enlazados [sec: Separate and Linked Events]
- Las probabilidades de todos los resultados posibles suman exactamente 1,0.
- **Eventos separados (independientes)**: la moneda no tiene memoria; tras 100 caras, la siguiente sigue siendo 0,5.
- **Eventos enlazados**: si exigís que se cumplan varios (3 caras seguidas, o 3 monedas a la vez), **multiplicás** probabilidades: 0,5×0,5×0,5 = 1/8 = 12,5% (cada moneda adicional divide por 2).
- Dado: sacar 6 = 1/6 ≈ 0,167; dos 6 a la vez = 1/36 ≈ 2,8%.
- Fórmula práctica: P(A y B independientes) = P(A)×P(B).

### Distribuciones de probabilidad [sec: Probability Distributions]
- Con varios dados sumados NO todos los totales son equiprobables. Prob. de un total = (combinaciones que lo dan) / 6^n (con n dados; 2d6 → 36).
- 2d6: total 5 → 1+4, 2+3, 3+2, 4+1 = 4/36 ≈ 11,1%. Distribución completa 2d6 (2..12): 2,7%; 5,6%; 8,3%; 11,1%; 13,9%; 16,7%; 13,9%; 11,1%; 8,3%; 5,6%; 2,7% → "campana" (distribución normal/gaussiana). Aparece al combinar varios eventos independientes.
- Definiciones:
  - **Mean (media)**: sumar y dividir por la cantidad.
  - **Mode (moda)**: el valor más probable (el pico).
  - **Median (mediana)**: el del medio (tantos arriba como abajo).
  - **Range (rango)**: diferencia entre extremos (2d6: 2-12).
- En distribuciones simétricas coinciden media, moda y mediana; en las asimétricas difieren (si moda y mediana están arriba de la media, la "joroba" se corre a la derecha). Ejemplo: la fuerza de los personajes de un RPG (escala 1-100) tiende a tener media >50 porque a los jugadores les gustan personajes más fuertes que el promedio poblacional.
- **Uso en diseño**: sumar más dados = resultados más concentrados al centro y menos volatilidad; un solo dado = todo igual de probable (más "swingy"). Para elegir cuánta varianza querés en un resultado.

### Probabilidades cambiantes [sec: Changing Probabilities]
- Sacar cartas sin reposición: la probabilidad de la carta buscada sube con cada fallo (1/52 → tras 32 cartas sin verla, 1/20 → 1/1 al final).
- Se usa para dar sensación de "me acerco" (pity timers / probabilidades que crecen). Ej: cajas ciegas con prob. de premio raro 1% independiente vs. enlazadas (sube un poco tras cada fallo). Como esos juegos tienen miles de ítems posibles, igual la prob. de conseguir uno específico es pequeña y requiere muchísimos intentos/compras.

### Sesgos cognitivos y el problema de las tres puertas [sec: Cognitive Biases and the Three-Door Problem]
- Las personas estiman mal las probabilidades (ej.: se compran más billetes de lotería cuanto mayor el premio aunque la chance sea ínfima).
- **Monty Hall**: 3 puertas, el anfitrión (que SABE dónde está el premio) abre una puerta con la cabra tras tu elección. Quedarte = 1/3; cambiar = 2/3. Clave: la apertura no fue al azar, así que no cambia el 1/3 de tu elección original; todo el 2/3 restante se concentra en la otra puerta. Versión de 100 puertas: abre 98, cambiar = 99%.
- Relevancia: el modelo mental del jugador sobre probabilidades suele ser incorrecto y eso es parte del diseño.

### Justicia percibida (Fairness) y fórmula de Bernoulli [sec: Fairness]
- Los jugadores perciben probabilidades puras como "injustas" si el resultado tarda (sobre todo en digital). 
- **Probabilidad de al menos 1 éxito en n intentos** (proceso de Bernoulli):
  - P(≥1 éxito en n) = 1 − (1 − p)^n
  - Ejemplo p=0,33: n=3 → 1−0,67³ = 1−0,30 = 0,70 (70%). Tras 5 intentos fallidos la chance de eso era ≈13,5% (la gente ya sospecha trampa). Tras 10 intentos aún ~2% de no haber ganado.
- Ejemplo de rareza: p=1/100.000 (0,00001): 100 intentos → ~1%; para 50% hacen falta casi 70.000 intentos (≈69.300; n = ln0,5/ln(1−p)).
- **Regla de diseño**: se diseña para engagement/disfrute, no rigor estadístico. Se puede inclinar las probabilidades a favor (o en contra) del jugador de forma creativa sin arruinar la experiencia.
- Ítem superraro con valor social (MMO): se puede hacer imposible las primeras horas/días para construir tensión, o subir las chances fuertemente **una sola vez** para disparar el incentivo (otros lo ven y quieren uno) y reajustar de inmediato para no inundar el juego (pierde valor social).

### Eventos improbables con población grande [sec: The Likely Occurrence of Unlikely Events]
- Con mucha gente, lo raro pasa solo. 1M jugadores/día, 100.000 intentos al día con p=0,00001 → 1−(1−0,00001)^100.000 ≈ 63% de que aparezca el ítem en un día. "Lógica de lotería": alguien gana aunque cada uno tenga chance mínima.
- Decisión: o inclinás las probabilidades para alentar, o dejás que la escala de jugadores haga el trabajo.
- **Juegos de casino social** (sin dinero real de salida, no sujetos a regulación de azar): permiten trucos como el **near miss** (el juego ya decidió que perdés y anima "casi" ganar: 3 de 4 barcos alineados, el cuarto se pasa/se queda corto). Falacia: creer que "casi ganar" o fallar varias veces hace más probable la próxima ("me toca una"). Dos eventos secuenciales son independientes, pero la mente no lo ve así.
- **Uso ético**: (a) *ayuda silenciosa*: subir discretamente la prob. de éxito tras fallos (basketball virtual, golpear monstruos) para evitar frustración; (b) usos manipuladores (empujar gasto). Si se exagera el jugador lo descubre y abandona sintiendo que "nunca tuvo chance". Decisión ética del diseñador.

### Lista de procedimientos de probabilidad (para aplicar)
1. Definir si los eventos son independientes o enlazados; multiplicar para enlazados.
2. Chance de lograr algo en n intentos: 1−(1−p)^n; intentos para llegar a una chance objetivo q: n = ln(1−q)/ln(1−p).
3. Para ver si el ritmo de recompensa se percibe justo, calcular a qué n el jugador "ya debería haber ganado" (p. ej. ≥90%) y ver cuántos jugadores superan eso sin premio.
4. Decidir si hace falta mecanismo de "mala suerte protegida" (prob. creciente) según tolerancia de percepción de injusticia.
5. Elegir cantidad de dados/eventos para controlar varianza (más sumandos = más campana).

---------------------------------------------------------------------
## A4. Sistemas transitivos e intransitivos [sec: Transitive and Intransitive Systems]
---------------------------------------------------------------------
> **Atención con la terminología.** Sellers llama "transitivo" al ciclo tipo piedra-papel-tijera e "intransitivo" a la escalera costo-beneficio. La mayoría de la bibliografía (Schreiber, Adams, Ernest) usa los términos **al revés**: ahí "intransitivo" = piedra-papel-tijera y "transitivo" = A mejor que B mejor que C, compensado por costo. Esta referencia conserva los términos del libro dentro de esta sección, pero al hablar con el usuario conviene usar nombres sin ambigüedad: **balance cíclico** (counters tipo piedra-papel-tijera) y **balance por costo-beneficio** (escalera de poder pagada con costo), y aclarar la inversión si el usuario usa uno de los dos términos.

### Balance cíclico ("transitivo" según Sellers; piedra-papel-tijera, RPS) [sec: Transitive Balance]
- **Definición del autor**: cada parte es mejor que una e inferior a otra; ninguna domina a todas. RPS es el ejemplo; hay variantes de más partes (hasta 101; Rock-Paper-Scissors-Lizard-Spock: cada una vence a dos y pierde con dos).
- Ejemplos: Wu Xing (5 fases: madera, fuego, tierra, metal, agua; ciclo generador y ciclo de superación); lagartos con tres colores de machos (naranja>azul>amarillo>naranja; cada color "invade" a otro cuando es raro y es invadible cuando es común → balance dinámico); **Dark Age of Camelot** (RvR con tres reinos, cada uno domina a otro; si uno crece demasiado, los otros dos se alían: autoequilibrio); doctrina militar de EE.UU. 1975 (unidades como RPS). Muchos wargames lo usan por ser fácil de entender y de balancear a nivel sistémico; tiende a un balance dinámico y evita el "rich-get-richer".

### Requisitos para balance transitivo [sec: Requirements for Transitive Balance]
- **Número impar de partes** al mismo nivel de organización: cada una debe dominar exactamente la mitad de las demás y ser dominada por la otra mitad. Con 5 partes: vence a 2, pierde con 2.
- El dominio puede ser **probabilístico** (ventaja significativa, no victoria asegurada), pero debe ser claro.
- **Número par → no hay balance transitivo estable**: siempre puede surgir una ventaja/desventaja desigual. Caso: Horde vs Alliance en WoW (solo 2 facciones) → colapso ecológico continuo que los diseñadores tuvieron que corregir.
- Cada tipo puede tener **varias instancias/subtipos** si agregan en un grupo con las mismas características transitivas (varias infanterías, caballerías, arqueros, mientras que las infanterías como grupo venzan a caballería, etc.).
- Más de 3 tipos principales es posible pero **difícil de definir con valores de atributos**; incluso con 3 es complicado. Por eso casi todos los juegos se quedan en 3 tipos principales + muchos subtipos.

### Cómo lograr el balance transitivo (procedimiento) [sec: Achieving Transitive Balance]
1. Elegir atributos compartidos por todas las partes (ej.: Attack, Defense, Range, Speed).
2. Darle a cada parte el **mismo total de puntos** ("+") para igualar capacidad global (primer nivel de balance).
3. **Distribuir esos puntos distinto** para que cada una destaque en un atributo.
4. Verificar que cada par ganador cumpla la regla.

Tabla 9.1 (reconstruida): 
| Unidad | Attack | Defense | Range | Speed |
|---|---|---|---|---|
| Infantry | +++ | ++ | + | + |
| Cavalry | ++ | + | + | +++ |
| Archers | + | + | +++ | ++ |
(cada fila suma 7 "+"; la distribución exacta se infiere del texto.)
- Infantería vence a caballería (Attack +++ vs Defense +; la caballería corre pero si la infantería cierra distancia, pierde).
- Caballería vence a arqueros (Attack ++ vs Defense +; Speed +++ vs ++ impide huir).
- Arqueros vencen a infantería (Range +++ vs Defense +; la infantería tiene más ataque pero los arqueros mantienen distancia).
- **Cautela**: el sistema transitivo existe dentro de uno mayor (terreno, clima, estilos). Si es demasiado rígido e insensible a influencias externas, nadie logra ventaja y el juego se estanca. Si los jugadores descubren que "terreno rocoso hace invencibles a los arqueros", el espacio de decisiones colapsa a una sola estrategia. **Playtestear bajo distintas condiciones** para que sea resiliente pero no estático ni reducible a una estrategia, y siga perturbable por el jugador.

### Balance por costo-beneficio ("intransitivo" según Sellers) [sec: Intransitive Balance]
- Definición del autor: en un par dado, una parte es simplemente mejor que la otra (siempre o probabilísticamente). Tomado solo, cada par transitivo es intransitivo.
- Otro modo de balancear: no iguala todas las partes a nivel sistema, sino que las **balancea por costo-beneficio**: más beneficio ↔ proporcionalmente más costo. Aparece en cualquier juego con **progresión** (personaje, objetos, ejércitos, cultivos que crecen en poder).
- Intuitivo: una daga oxidada cuesta menos que una gran espada de adamantium; la pregunta difícil es **cuánto más**. Requiere definir la relación matemática entre tipos de partes + mucha iteración.
- Para balancear sistemas intransitivos hay que definir la **curva de progresión/poder**, lo que implica definir costos y beneficios (Cap. 10).

### Resumen de la regla de oro
- Transitivo: mismo "presupuesto" de puntos, distinta distribución, ciclo de dominancias (impar). Intransitivo: costo proporcional al beneficio, curva de poder.

---------------------------------------------------------------------
# PARTE B — CAP. 10: PRÁCTICA DE BALANCE
---------------------------------------------------------------------

## B1. Curvas de progresión y poder: fundamentos [sec: Creating Progression and Power Curves]

Dos ideas base:
1. **Todo beneficio tiene un costo**; al subir el costo sube el beneficio y viceversa, atados. La demora en poder pagar costos más altos es lo que regula el ritmo del juego mientras el jugador sigue sintiendo mejora.
2. Tanto el representante del jugador como los objetos que usa (o que lo enfrentan) avanzan mejorando valores de atributos. Las curvas regulan que **jugador y desafío** crezcan al ritmo que querés.

### Definir costos y beneficios [sec: Defining Costs and Benefits]
- La relación costo/beneficio es **económica** (el jugador intercambia costos por beneficios). Si el jugador siente que quedó peor tras avanzar (subir de nivel, sumar unidades), los recursos pierden valor y cae el engagement.
- Costos y beneficios se expresan en atributos relevantes = recursos. Costos: XP, moneda, commodities, batallas ganadas, animales criados. Beneficios: más salud, poder mágico, cartas, provincias, puntos de acción.

### Recursos centrales / core resources [sec: Core Resources]
- Uno o pocos recursos que el jugador maximiza y/o no puede perder para seguir jugando (puntaje y vidas en un arcade). Se ligan a los core loops. Ej.: salud y XP en RPG; dinero en tycoon; área controlada en estrategia.
- **Procedimiento para encontrarlos**: revisar la hoja de partes (Cap. 8: atributos en columnas, partes en filas); buscar los atributos de los que el jugador depende más y sin los cuales no puede seguir. Puede haber varios si hay varios loops (se enfoca uno por vez).
- Si hay varios candidatos: ver si uno **abarca** a los demás (puede ser el emergente de la sinergia de otros), o si son **secuenciales** (salud → riqueza → estatus social por fases).
- **Shadow resource (recurso sombra)**: recurso no visible en el juego que englobe varios recursos para basar costos/curvas de poder.
- Si de verdad son inconmensurables → una curva de progresión por recurso, cuidando el **traspaso** de uno a otro sin perder impulso.
- Objetivo: tener UN recurso central como pilar del costo o beneficio de la curva primaria de progresión/poder (puede requerir reorganizar atributos; vale la pena).

### Recursos subsidiarios [sec: Subsidiary Resources]
- Los que sostienen/mejoran/reparan a los centrales; sus beneficios son indirectos al central. Ej.: en estrategia con "área controlada" central, ejércitos/fortificaciones/tecnología son subsidiarios; en romance, la relación con una persona es central y amigos/dinero/información son subsidiarios.
- Primero curvas del recurso central, después las secundarias derivadas.

### Casos especiales [sec: Special Cases]
- Recursos que afectan a otros y tienen efectos limitados o periódicos. Ejemplo nave espacial: mineral = central; velocidad y blindaje = subsidiarios; un **turbo** ocasional que daña un poco la nave es un caso especial (no importa hasta que importa mucho). Más complicado: gastar mineral para aumentar duración del turbo o reducir su recarga.
- Reducir todo a una sola ecuación (shadow resource) puede ser una meta que se aleja, o aplastar la **dimensionalidad** del juego haciendo los trade-offs demasiado obvios.
- Parte de la correlación costo-beneficio se tendrá que hacer **heurísticamente** + playtesting iterativo; los costos/beneficios terminan cerca de una curva que quizá no pudiste predecir.

---------------------------------------------------------------------
## B2. Tipos de curvas costo-beneficio [sec: Defining Cost-Benefit Curves]
---------------------------------------------------------------------

### Resumen comparativo

| Curva | Fórmula | Tasa de cambio | Característica clave | Uso / riesgo |
|---|---|---|---|---|
| Lineal | y = A·x + B | constante | pendiente fija | simple; el cambio relativo se achica (fatiga hedónica) |
| Polinómica | y = x^n (con multiplicadores) | crece, pero la proporción respecto de y tiende a lineal | se "aplana" relativamente | poder que sube con cuadrática; igual problema que lineal arriba |
| Exponencial | y = A^x ó y = B·A^x | crece SIEMPRE | proporción constante entre pasos | la más usada en progresión; números gigantes arriba |
| Logística/sigmoide | y = L / (1 + e^(−k(x−x0))) | lenta-rápida-lenta | tope L | poder con rendimientos decrecientes; economía de recursos apilados |
| Lineal por tramos | segmentos lineales | constante por tramo | hecha a mano | hitos, objetivos intermedios |
| NAP | sin ecuación | irregular | números redondos/a mano | "sorpresa y deleite", dar variedad |

### Curvas lineales [sec: Linear Curves]
- y = A·x + B. A = pendiente (cuánto cambia y por unidad de x); B = desfase (a menudo 0).
- En progresión A>0 (más poder a medida que avanzás). Ejemplo: A=2, B=0 → x=1→y=2; x=3→y=6.
- **Problema**: el mismo cambio absoluto es cada vez menor en proporción. y=2x: de x=8→10 (y 16→20) es +25%; de x=98→100 (y 196→200) es +2%, misma suma absoluta pero "¿y qué?". Esto alimenta la **hedonic fatigue**. Por eso la lineal casi no se usa sola en poder/progresión.

### Curvas polinómicas [sec: Polynomial Curves]
- y = x^n (con multiplicadores: p. ej. 5x²). x=1..5 con x²: y = 1, 4, 9, 16, 25; diferencias 3, 5, 7, 9 (la **segunda diferencia** es lineal → propiedad de los polinomios).
- **Basic progression ratio** (Bateman 2006): diferencia de y entre pasos consecutivos. En lineal es constante; en polinómica crece. **Total progression ratio**: esa diferencia como proporción del valor total de y; en polinómicas tiende a 1,0 al crecer x (la curva "se aplana", se parece a lineal). Consecuencia: en juego, el arriba de la curva se siente de cambio similar (pierde impacto), pero tampoco hay saltos astronómicos como en exponenciales.
- **Propiedad útil**: un polinomio cuadrático es el **producto de dos progresiones lineales** (Achterman 2011). Ejemplo: monstruos por nivel 1,2,3,4,5 (lineal) × oro por monstruo 10,20,30,40,50 (lineal) = oro por nivel 10, 40, 90, 160, 250 (cuadrático). Dos sistemas simples que interactúan dan crecimiento más rápido que la suma de las partes. Cuidado: multiplicar dos lineales sin querer produce una curva que acelera.

### Curvas exponenciales [sec: Exponential Curves]
- y = A^x (o y = B·A^x). La tasa de cambio sigue creciendo sin aplanarse. Si la **base A es chica**, no sube demasiado rápido. 
- RuneScape: ecuación de XP compleja con componente exponencial de base 1,1^x → pasos que al principio crecen lento: niveles tempranos alcanzables y rápidos (sensación de logro), niveles tardíos parecen sobrehumanos, pero cuando llegás ya ganás muchísimo XP.
- **Propiedad perceptual**: el *total progression ratio* queda bajo respecto del valor actual: lo lejano parece una montaña imposible, pero lo próximo se ve alcanzable comparado con lo ya recorrido → ayuda a seguir y evita fatiga hedónica.
- Es probablemente la curva **más usada** en progresión/poder: fácil de ajustar y de ajustar a los objetos. Riesgo: números absurdos (miles de millones, trillones...; Adventure Capitalist llega a 10^300 = "1 novemnonagintillion"): al no poder imaginarlos pierden significado (hedonic fatigue otra vez). El placer de "números que suben" (A Dark Room: "gente a la que le gusta que suban los números" + "explorar lo desconocido") existe pero se agota si se exagera.

#### Uso para niveles/umbrales (procedimiento)
1. Cada nivel/hito = valor x; los puntos que requiere = y de la función exponencial.
2. Si el jugador gana más puntos por desafíos cada vez más difíciles, los umbrales deben separarse más o los alcanzará cada vez más rápido.
3. **La base es la heurística de cuánto crece cada paso**: y = 1,4^x → cada nivel pide 1,4× el anterior; tras 4 niveles se duplicó (1,4⁴ ≈ 3,84 ≈ casi 4×; "más del doble" según el texto es una sub-afirmación: en 2 niveles ya 1,96 ≈ 2). Mover la base (1,2; 1,3; 1,5...) para ajustar subida y **tiempo de duplicación**.
   - Atajo (derivado, no está en el libro): niveles para duplicar = ln2 / ln(base): base 1,1 → 7,3; 1,2 → 3,8; 1,4 → 2,06; 1,5 → 1,71.
4. Decidir según tiempo/batallas por hito, dureza de desafíos y tamaño de recompensas, y luego **balancear desafíos, poder y recompensas entre sí**.

**Tabla 10.1: XP = 1.000 × 1,4^nivel** (redondeado a centenas; nivel 1 puesto a 0 arbitrariamente): 
| Nivel | XP | Nivel | XP |
|---|---|---|---|
| 1 | 0 | 10 | 28.900 |
| 2 | 2.000 | 15 | 155.600 |
| 3 | 2.700 | 20 | 836.700 |
| 4 | 3.800 | 25 | 4.499.900 |
| 5 | 5.400 | 30 | 24.201.400 |
- Ratio entre niveles consecutivos ≈ 1,4: aceptable; pero los absolutos se vuelven enormes.

#### Error clave: curvas de desafío y de recompensa mal acopladas
- Ejemplo del libro: si los desafíos suben ×3 por nivel y la recompensa del recurso central (salud, ataque) sube solo ×1,25, el juego se vuelve injugable rápido (los desafíos crecen mucho más rápido que la capacidad de enfrentarlos). Regla: **las bases de las curvas de desafío y de poder deben ser similares** (o la de poder algo mayor si querés fantasía de poder; algo menor si querés tensión creciente).
- Cuántas misiones/monstruos por nivel sigue siendo decisión del diseñador y de playtests; la matemática solo avisa si los jugadores "queman" el juego muy rápido o se frustran.

### Curvas logísticas / sigmoides [sec: Logistic Curves]
- Menos usadas para balance, útiles. Modelan procesos reales (aprendizaje, ecología: crecimiento inicial lento → expansión rápida → desaceleración al consumirse recursos). Muy usadas en simulación e IA.
- **Fórmula**: y = L / (1 + e^(−k(x − x0)))
  - L = valor máximo (el techo)
  - e ≈ 2,718
  - k = pendiente/empinado (cuán rápido sube en el medio)
  - x0 = x del punto medio (abajo de x0 lo bajo, arriba lo alto; en x0, y = L/2)
- Forma: lento – rápido – lento – tiende a no cambiar. En juego: poder que al principio exige inversión larga, en el tramo medio rinde mucho, y arriba tiene **rendimientos decrecientes** (diminishing returns). Figura 10.1: L=6, k=1,0.
- Ventaja sobre la exponencial: no tiene el cambio disparado en y.
- **Logísticas apiladas (stacked)**: una por recurso; el jugador debe decidir cuándo cambiar de recurso al llegar el primero a rendimientos decrecientes (Fig. 10.2: 4 recursos con curvas distintas). Amplía el rango de valores de una economía sin desbalancearla y reparte el "efecto de subida rápida" de una exponencial entre varias logísticas. Balancear cada objeto sobre su curva es más simple que cubrir todo el rango con una sola curva.

### Curvas lineales por tramos (piecewise linear) [sec: Piecewise Linear Curves]
- Motivación: la suavidad de una ecuación se vuelve aburrida; el jugador conoce la tasa (siempre +n espada = cierta mejora sobre n−1) y no decide nada. Se hace a mano, aproximando una exponencial con segmentos lineales (por suma o por interpolación lineal).
- **Método por suma (tasas conocidas)**: HP de RPG: base nivel 1 = 12 (≠0 para que el gráfico sea claro); +2/nivel en niveles 1-10 (→30 en nivel 10); +5/nivel en 11-20 (→80 en 20); +10/nivel en 21-30 (→180 en 30).
- **Método por interpolación (extremos conocidos)**: querés 2 HP en nivel 1, 20 en nivel 10, 100 en nivel 20. 
  - Pendiente del tramo = (y1 − y0) / (x1 − x0).
  - Tramo 1: (20−2)/(10−1) = 18/9 = 2 HP/nivel. Tramo 2: (100−20)/(20−10) = 80/10 = 8 HP/nivel.
  - En una hoja de cálculo se juega cambiando los y de los extremos hasta lograr los números y pendientes deseados.
- Cada segmento es lineal pero el conjunto parece curvo/exponencial. Es más simple que mapear a una exponencial si tus matemáticas están oxidadas y además **da hitos**: saber que en el nivel 11 el HP por nivel salta de 2 a 8 es un objetivo intermedio para el jugador.

### Near-Arithmetic Progression, NAP [sec: Near-Arithmetic Progression Curves]
- Término de Bateman (2006): curvas hechas a mano, parecidas a las aritméticas (lineales) pero sin ecuación; típicas de RPG, hechas "a ojo" o para conservar números redondos.
- Ejemplo WoW niveles iniciales: 1→2 pide 400 XP; luego +500 para 2→3 y 3→4; +700 para 4→5 y 5→6; etc. (el patrón no se sostiene en todos los niveles).
- Beneficio: curvas "irregulares" con zonas de aceleración rápida o lenta para **sorprender y deleitar** (Pecorella 2015), evitar aburrimiento por predictibilidad, y coordinar curvas de poder tal que **un tipo de objeto/recurso rinda más por su costo que otro en ciertos tramos**, de modo que el jugador explore el espacio de curvas decidiendo cómo gastar.

### Principio general: "que funcione para el juego, no para la matemática" [sec: Making It Work for Gameplay, Not Math]
- La matemática nunca es perfecta pero cuanto mejor balanceada la curva, menos tiempo de iteración. Después se vuelve a playtesting e intuición para encontrar los puntos de balance. Puede empezar exponencial y terminar a mano, y está bien.

### Cuándo usar cada curva (guía derivada)
- **Lineal**: pocas veces sola; sirve para tramos cortos o como componente de un producto (cantidad × valor).
- **Polinómica / cuadrática**: cuando querés crecimiento acelerado moderado y sin explosión; ojo que sale solo al multiplicar dos lineales.
- **Exponencial**: curva madre para XP por nivel, tiers de ítems, rareza; ajustar con la base.
- **Logística**: para recursos/ítems con techo y rendimientos decrecientes; para forzar decisiones de cambio de recurso; como guía de comparación costo-beneficio (el libro la usa así en Fig. 10.7 con k=0,95 y x0=3,5).
- **Por tramos / NAP**: arrancar con una de las anteriores y mecanizar a mano hitos, picos de recompensa y tramos de comienzo atractivos.

---------------------------------------------------------------------
## B3. Balancear partes (armas) [sec: Balancing Parts, Progression, and Systems → Balancing Parts]
---------------------------------------------------------------------

### Contexto
- Tarea frecuente: que las partes de un sistema estén balanceadas entre sí. Son objetos **intransitivos**: unos mejores que otros pero proporcionales al costo. Ejemplo: armas de un RPG (atributos Attack, Damage, Speed; las escalas no coinciden entre sí, lo cual es normal).
- Criterio de balanceado (no es "iguales"): cada parte tiene **un lugar válido** (una situación donde elegirla), son lo bastante **diferentes**, y al jugador le parece que **beneficios y costos se compensan**. Si los costos fueran iguales, nadie usaría otra cosa que la más poderosa.

### Procedimiento paso a paso (el ejemplo del libro)
0. **Tabla inicial** (hoja de cálculo; reconstrucción de Fig. 10.5: columnas Attack/Damage/Speed; en resumen: la daga con el menor Attack y Damage, la espada grande con 8/8 pero velocidad 0-2 "por lejos la más lenta"; dagas/espada corta/estoque comparten la velocidad más alta). Gráfico de líneas (Fig. 10.6) para ver el agrupamiento: la mayoría de valores en un rango medio estrecho, solo daga y espadón se separan → hace falta más variedad.
   - Nota: línea no es técnicamente correcta para datos categóricos (barras lo sería), pero sirve para ver cómo se relacionan; explorar visualizaciones.
1. **Elegir el recurso central** para balancear: en RPG, la salud (HP). Un enemigo a 0 = victoria y botín; el jugador a 0 = muerte/retroceso.
2. **Ordenar atributos por su cadena causal hacia el recurso central**: el daño reduce la salud, pero primero hay que golpear (Attack) y antes poder atacar (Speed): Speed es la primera "compuerta", luego Attack, luego Damage.
3. **Hipótesis de costo inicial**: sumar Attack+Damage+Speed da costos poco convincentes (corta y cutlass ambas 10; daga 7; broad 11).
4. **Pesos/coeficientes por atributo**: Damage = 1,0 (el más ligado al recurso central); Speed = 2 (más velocidad = más oportunidades de pegar); Attack = 1,5 (importante, pero difícil saber cuánto). Probar en la hoja. Resultado: rango de ~10 (daga) a ~20 (espadón) → algo angosto (el más caro solo 2× el más barato) pero bien; problema: el cutlass queda más barato que la espada corta (pierde valor por Speed baja).
5. **Mover los valores de atributos**, no solo los pesos (si se puede; si no, queda manipular multiplicadores o **factores situacionales** como dificultad de conseguirlo; ojo: pueden bloquear al jugador, p. ej. no puede pagar otra arma y no encuentra dónde está la que quiere o ir allí es morir).
   - Elegir un **objeto base/línea media**: la espada ancha con todo en 5. Subir un poco la daga en Attack (0→1). Subir espadón de 8/8 a 10/10. Esto "destapa" el medio.
   - Vigilar el gráfico de atributos para evitar aglomeración y absurdos (cutlass más rápido que estoque).
   - Iterar pesos y valores juntos (se afectan mutuamente).
6. **Desacoplar costo de valor** (decoupling): llamar **Mod Value** a la suma ponderada y fijar el **Cost** en juego a mano, independiente. Graficar Mod Value vs. Cost junto con una **curva logística guía** (k=0,95, x0=3,5 en Fig. 10.7) como confirmación de que sigue el tipo de relación deseada.
7. **Resultado final** (Fig. 10.8; Mod Value = 1,3·Attack + 1,0·Damage + 1,75·Speed). Tabla reconstruida y verificada con la fórmula:

| Arma | Attack | Damage | Speed | Mod Value | Costo |
|---|---|---|---|---|---|
| Dagger | 1 | 1 | 6 | 13 | 10 |
| Short sword | 2 | 1 | 6 | 14 | 12 |
| Cutlass | 4 | 7 | 3 | 17 | 15 |
| Broad sword | 5 | 5 | 5 | 20 | 20 |
| Rapier | 5 | 3 | 8 | 24 | 25 |
| Long sword | 7 | 6 | 6 | 26 | 28 |
| Great sword | 10 | 10 | 3 | 28 | 30 |
(Verificación: daga 1,3+1+10,5 = 12,8≈13; espada ancha 6,5+5+8,75 = 20,25≈20; espadón 13+10+5,25 = 28,25≈28.)

8. **Costo a mano con intención** (lectura de Fig. 10.7):
   - Armas flojas cuestan **un poco menos** que su Mod Value (ventaja a jugadores nuevos/pobres).
   - Armas de punta cuestan **un poco más** (prima aspiracional: ver un espadón = personaje pagó mucho).
   - Las líneas costo/beneficio **se cruzan en la espada ancha** (punto fijo del modelo mental, en el medio).
9. **Verificar**: los atributos tienen cada arma con fortalezas y debilidades distintas; rangos amplios; seguir la curva costo-beneficio ascendente implica que la relación es proporcional y el jugador la capta intuitivamente.
10. **Playtestear**: ¿los jugadores construyen rápido y con gusto un modelo mental de efectividad/costo relativos? Más iteración seguro.

### Reglas prácticas de este procedimiento
- Asignar el peso 1,0 al atributo más directamente ligado al recurso central; escalar los otros según su posición en la cadena causal (compuertas de frecuencia).
- Probar pesos con hoja de cálculo y mirar rangos relativos (relación máx/mín de costos).
- Evitar el "centro congestionado": ensanchar el rango de atributos; elegir una pieza ancla en el medio.
- Costo en juego ≠ valor calculado; usar la diferencia como palanca de diseño (accesible/aspiracional).
- Señal de balance: orden del Mod Value coincide con el del costo; ningún arma con mejor Mod Value Y menor costo que otra (dominada/dominante).
- Una vez establecidos los pesos, **se puede valorar cualquier variante**: p. ej. cuánto más beneficio da una daga con +2 Speed vs. una espada ancha con +1 Damage (comparación de delta × peso).

---------------------------------------------------------------------
## B4. Balancear progresión [sec: Balancing for Progression]
---------------------------------------------------------------------

- Tipos de progresión: (1) la del representante del jugador (personaje, ejército, granja) en atributos; (2) progresión económica: monedas, disponibilidad y mejora de objetos.
- Pasos para diseñar progresión del jugador:
  1. Elegir los **atributos portadores** de la mejora (los core attributes).
  2. Esos atributos conducen a los **recursos que son el costo** de avanzar.
- Ejemplo estándar: subir de nivel = acumular XP y "gastarlos" automáticamente al cruzar el umbral (más salud, poderes, acceso a contenido). El umbral siguiente es mayor que el total actual (no se reinicia el XP a cero): permite curvas exponenciales de puntos por nivel y la sensación de números que siempre suben. "Acceso a contenido" es un atributo especial difícil de cuantificar.
- **Más de un recurso de progresión**: más trabajo (hay que evaluar dificultad y tiempo para cada uno) pero si distintos recursos rinden distinto según la etapa, el jugador elige su camino estratégicamente → más decisiones significativas. Ejemplo: progresar por combate/salud al principio, luego por riqueza, luego por amigos, a medida que salud y riqueza dan menos retorno (el paso al siguiente nivel crece exponencial mientras los puntos ganados no). Cuidado: no todos quieren un sistema multifacético; quien empieza por un recurso debe poder **continuar** con él. Los optimizadores querrán la ruta óptima, así que ofrecer cambio de foco puede subir engagement.
- **Regla sagrada**: el jugador siempre debe sentir que avanza. Si el progreso se detiene o el próximo avance está "infinitamente lejos" dada la recompensa de su nivel de desafío, el engagement se evapora. (Idle games: el loop externo de *prestige* da otra vía cuando la primaria se vuelve lenta.) Aunque tenga varias dimensiones, siempre debe ver formas significativas de progresar en al menos una.

### Ritmo (Pacing) [sec: Pacing]
- La progresión suele ser **puntuada (discreta)**, no continua: mejoras en hitos, más gratificante (algo que esperar) y más fácil de balancear (elegís dónde caen los level-ups). Una curva continua es posible pero difícil de balancear.
- Decidir el **ritmo** en unidades del juego (monstruos, provincias, flores).
- La **forma de la curva** costo-beneficio define el ritmo: si querés que den cada vez más puntos pero tarden más en avanzar, exponencial. También híbridos: tramo inicial a mano (piecewise) para enganchar, luego logísticas apiladas con distinto recurso de costo que aproximan en conjunto una exponencial. No hay fórmula única.

### Tiempo y atención [sec: Time and Attention]
- Los recursos últimos son **atención y tiempo** (parecidos pero no idénticos: atención = jugando activamente; tiempo = puede ser pasivo).
- **Procedimiento de estimación del tiempo para avanzar** (cálculo de actividades):
  - Puntos por actividad × veces necesarias × tiempo por actividad. Ej. zoo: 10 puntos por animal alimentado, 100 para subir → 10 animales; 2 min cada uno → 20 min de atención plena.
  - Con aleatoriedad y fallos: ejemplo gemas: 1.000 puntos para subir; 50-200 puntos por gema cortada con éxito → 5 a 20 gemas; con éxito 80% → ~7 a 25 gemas incluyendo fallos (en realidad 5/0,8 = 6,25 y 20/0,8 = 25); 1-3 min por gema → mínimo ~7 a 75 min (valores del libro); rango muy ancho → reconsiderar el sistema para que no se sienta desparejo.
  - Remedios de ejemplo: a más tiempo cortando (hasta un máximo), menor chance de fallo; bonus por cortar muy bien.
  - Fórmula resumen: tiempo_mín ≈ (puntos_nivel / puntos_máx_por_acción) / p_éxito × t_mín; tiempo_máx análogamente con los máximos. Importa el **rango**, no solo el promedio.
- **Tiempo de reloj (timers)**: si parte de la progresión se regula por tiempo de reloj (cultivos, ejércitos), controlás con certeza cuán rápido avanzan, pero baja el engagement: el jugador inicia el proceso y se va (poco que hacer, menos probabilidad de volver). Hay que respetar el tiempo del jugador.

### Progresión secundaria [sec: Secondary Progression]
- En juegos complejos, caminos secundarios de corto plazo mantienen el engagement cuando los hitos primarios están lejos.
- Ejemplo WoW: **inventario** limitado al principio (decisiones difíciles sobre qué guardar); con nivel y riqueza se compran bolsas más grandes; con oficios se craftean. No está atado rígidamente (ej. "2 slots más en nivel 10"), sino a nivel, riqueza y habilidades secundarias → **casi auto-balanceado** porque el jugador atiende la necesidad cuando se vuelve un problema. Mantener estas progresiones desacopladas pero que no desborden la progresión global.

---------------------------------------------------------------------
## B5. Balance de sistemas económicos [sec: Economic System Balance]
---------------------------------------------------------------------

- Economía = recursos que entran por **sources** (fuentes), se intercambian y salen por **sinks** (sumideros), en loops de refuerzo. Los recursos y objetos son una progresión secundaria (riqueza y posesión como marcadores de logro y estatus). Balancear economías sigue siendo "arte inexacto".

### Inflación, estancamiento, arbitraje [sec: Inflation, Stagnation, and Arbitrage]
- **Inflación**: demasiadas fuentes y pocos sumideros → el recurso se acumula y vale cada vez menos. Le pasa a casi todo juego con economía (no se conocen todavía todos los principios para prevenirla).
- **Estancamiento**: pocas fuentes → poca **velocidad económica** (rapidez con la que fluyen los recursos, como un río). Si baja, la economía muere. Suele pasar por sobrecorregir contra la inflación (recursos demasiado preciosos → frustración).
- **Arbitraje**: comprar barato en un lugar y vender caro en otro; si no se maneja, produce inflación masiva.

### Caso Habitat: muñecas y bolas de cristal [sec: The Lesson Learned from Dolls and Crystal Balls]
- Habitat (1987): jugadores empiezan con 2.000 tokens (fuente). Vendroids = sumideros (venden ítems), Pawn Machines = compran de vuelta (fuentes de tokens). Dos Vendroids lejanos entre sí tenían precios bajos en ciertos ítems: muñecas a 75 tokens que una Pawn Machine recompraba a 100 (+25 por muñeca); bolas de cristal a 18.000 que otra Pawn Machine recompraba a 30.000 (+12.000 cada una). Se acumuló tanto dinero que la oferta se quintuplicó en una noche, sin bug ni reportes.
- Causa: cada recompra creaba tokens de la nada; precios inconsistentes entre máquinas = bucle de arbitraje. Por suerte los jugadores gastaron el dinero en cazas del tesoro en vez de inundar el mercado; se corrigieron los precios.
- **Lecciones**: (1) consistencia: el precio de venta del NPC nunca debe ser menor al precio de compra de otro NPC para el mismo ítem; (2) **monitorear** la masa monetaria total y los saldos por jugador diariamente (los admins de Habitat lo tenían y lo detectaron); (3) toda recompra es una fuente: cuenta como tal.

### Fuentes que deben crecer, sumideros que acompañan
- Las recompensas demasiado tacañas → estancamiento y abandono; si son iguales a la anterior → fatiga hedónica. Por eso la mayoría de los juegos con economía inyecta cada vez más moneda a medida que el jugador progresa y luego **lucha por encontrar sumideros**. WoW: el valor monetario por monstruo sube más de 750× del nivel 1 al 60. Si no se acompaña con sumideros enormes, la moneda pierde sentido como recompensa.

### Construcción de economía con tiers y rareza (Albion Online) [sec: Constructing a Game Economy]
- Objetos agrupados en **tiers** (rareza + poder/utilidad). Tiers 1-3 = entrenamiento (poco efecto económico); tiers 4-8 = núcleo de la economía. Zonas del mundo con distintos tiers; el valor/poder escala con peligro/dificultad de obtención.
- **Poder del ítem**: exponencial **1,2^tier** → cada tier es 20% más avanzado; tier 8 ≈ 1,2⁴ ≈ 2,07× la utilidad del tier 4 (sensación de progreso sin que la distancia entre arriba y abajo sea imposible). Se obtuvo **empíricamente** con muchísimo playtest; una vez hallada, ahorra tiempo al agregar contenido (no se vuelve a derivar). Para más diferencia: más tiers y/o base mayor.
- **Rareza** (probabilidad de encontrar el ítem): exponencial **3^tier** → cada tier es 3× más raro; tier 8 es 3⁴ = 81× más raro que tier 4. Los dos tiers más altos, extremadamente raros y valiosos.
- **Desacople de las dos curvas** (poder vs. rareza): mantiene a raya el "creep" de poder, porque la rareza (y por ende el costo) por unidad de poder es alta y crece de forma no lineal (diferentes bases). Permite una economía dirigida por jugadores.
- Crafteo en Albion: transmutar hacia tiers superiores y desarmar (salvage) tiers altos hacia bajos + dinero (fuente de moneda).

### Límites de precio / market channel [sec: Price Boundaries / Creating the Market Channel]
- **Price boundaries**: dan espacio para que los jugadores formen precios fluctuantes (interactividad estratégica y social) sin excluir a otros ni permitir precios inflacionarios.
- **Mecanismo**: mercado virtual de **import/export** (fuentes y sumideros independientes del jugador). Si no encontrás comprador, vendés al **export** (paga poco pero siempre compra). Si no encontrás vendedor, comprás del **import** (casi cualquier cosa, a precio alto). Excepciones: ítems únicos reservados por el diseñador.
- Efecto: todo ítem es comprable y vendible; nadie queda fuera (si tiene plata); el diseñador fija **piso y techo** de precios. Mientras haya distancia entre piso y techo, el mercado de jugadores se autobalancea y es inmune a largo plazo a inyecciones excesivas de moneda (poca inflación). Fluctuaciones temporales no cambian la estructura.
- Un jugador vendiendo un caballo: lo pone a precio > export y < import. Si vende bajo el export, el comprador revende al export con ganancia instantánea (poco probable); si > import, nadie compra.
- **Procedimiento para armar el canal**:
  1. Definir una curva de rareza (o de poder) por tier, p. ej. rareza = 1,5^tier.
  2. **Export (piso)** = fracción de ese valor (ej. 50%) — o fracción del valor tiempo promedio (en moneda) de obtener un ítem de esa rareza; no debe ser 0.
  3. **Import (techo)** = múltiplo de ese valor (ej. 200%).
  4. Los multiplicadores (50%, 200%) se afinan en playtest.
  5. Ítems nuevos que respetan el mismo esquema de rareza entran automáticamente al canal.
  6. El canal se **ensancha con el tier** (por ser exponencial): estable y casi fijo en bajos tiers, abierto y volátil en altos. Subir la base aunque sea poco ensancha el canal y la volatilidad potencial.
  - Ejemplo Fig. 10.10: tiers 1-10, rareza 1,5^tier; export = 50%, import = 200% → tier 1: 0,75 / 3; tier 10: 1,5¹⁰ ≈ 57,7 → export ≈ 29 / import ≈ 115 (cálculo derivado).
- Si hay crafteo: costos y rarezas de los ingredientes algo por debajo y proporcionales al costo del producto; derivarlos de los precios mínimo/máximo de los productos.

### Todo junto [sec: Putting It All Together]
1. Armas base (tabla 10.8) con costos del recurso central = tier más bajo/menos raro = cotas inferiores de precio.
2. Calcular costo/beneficio de cada ítem sucesivo con los mismos pesos (p. ej. comparar +2 Speed en daga vs +1 Damage en espada ancha).
3. Asignar cada ítem a un tier según ritmo y agrupamiento costo-beneficio (idealmente sobre una curva exponencial de beneficio total).
4. Armar el market channel si querés comercio entre jugadores.
- Es mucho más trabajo con decenas/centenas de ítems; partir de diseño de partes/atributos → recursos centrales → objetos intransitivos diversos y balanceados → curva económica de progresión que se aplique a cada objeto.
- Balancear una economía es de las tareas más difíciles; mezcla matemática, analítica y heurística; no hay sustituto de construir, playtestear y encontrar tus propios puntos de balance.

---------------------------------------------------------------------
## B6. Balance analítico y métricas [sec: Analytical Balance]
---------------------------------------------------------------------

- La analítica es la pareja del modelado matemático. Se centra en la **experiencia global**: ¿es atractivo, se siente balanceado, y por cuánto tiempo?
- **Tres tipos de métricas/datos**:
  1. **Datos del proceso de desarrollo** (¿vamos bien?; Cap. 12).
  2. **Datos de rendimiento** (fps, memoria; profiling).
  3. **Datos de comportamiento del usuario** (qué hacen los jugadores en conjunto → salud y éxito del juego). Este es el relevante para balance; no arma estructura, **registra lo que hacen**. Sirve solo con muchos jugadores (casi lanzamiento comercial) y datos regulares, ideal casi en tiempo real.

### Cómo recolectar [sec: Collecting Player Information]
- Útil sobre todo en juegos con componente online; F2P requiere mucha más información. Offline y analógico: difícil/poco útil.
- Llamadas en el software que registran: ID del jugador, dónde está en el juego, información adicional (tiempo en la sesión). Se envían como strings cortos a un servidor.
- **No instrumentar todo**: recolectar solo **KPIs** (key performance indicators); si no es un KPI, no lo recolectes (es dato que hay que analizar sin beneficio).
- **Frescura**: >1 hora de atraso suele ser viejo; >1 día puede llevar a malas decisiones (salvo uso retrospectivo o comparación con el mismo día de la semana anterior). Ideal: continuo/tiempo casi real; en la práctica, cada pocos minutos alcanza.

### Cohortes [sec: Grouping Players Together]
- Los datos individuales casi nunca sirven (hasta pueden engañar); se agregan en **cohorts** (grupos). El método típico: por día o semana en que empezaron a jugar. Se sigue a la cohorte en el tiempo y se **comparan cohortes** (ej. empezados semana del 9/7 vs 16/7) en tiempo de avance, duración de sesión, comportamiento de compra → ver si el juego mejora o empeora.

### Categorías de comportamiento [sec: Analyzing Player Behavior]
Lista completa: (1) Acquisition y primera experiencia, (2) Retention, (3) Conversion, (4) Usage, (5) Community.

**1. Adquisición / FTUE [sec: Acquisition]**
- **FTUE** (first-time user experience): primera impresión; si es confusa/frustrante el jugador se va.
- Medir: cuántos inician el juego, cuánto llegan en la primera sesión; retroceder a descargas/instalaciones/clics en la web.
- **Heurística**: perdés ~**50% de jugadores por cada clic/tap** desde que arrancan hasta que juegan. 3 clics (elegir nación, personaje, género) → 50%×50%×50% = 12,5% quedan (≈87% perdido). Moraleja: meter al jugador al juego lo más rápido posible.
- **Acquisition funnel**: caída de ~**10×** por etapa: para 1 jugador regular hacen falta 10 que inicien el juego, 100 que lo instalen, 1.000 que lo busquen, 10.000 que sepan de él (no contar con mejor).
- Ya dentro: registrar qué hacen; Tumbleseed como ejemplo (la mayoría no llegó al primer checkpoint y ~80% de los que llegaron no pasaron al siguiente).
- Tutorial: medir respuesta del jugador en los primeros minutos; los tutoriales frustran o su ausencia confunde → balancear esa parte con datos.

**2. Retención [sec: Retention]**
- Medida en días: D0 (primer día), D1, D7, D30; cohortes por inicio → % que vuelve en D1, D7, D30. Mejorar con la FTUE e incentivos de regreso (bonus por volver al día siguiente, celebrar el regreso). Un juego que no hace volver al jugador al otro día lo tiene muy difícil.
- **DAU** (daily active users): "latido"; mirar variaciones por día de semana (el martes suele ser el más flojo: una caída ahí no es relevante; una caída del 50% sábado vs. sábado anterior sí es alarma).
- **MAU** (monthly active users): jugadores en los últimos 30 días (retrospectivo).
- **Stickiness = DAU / MAU**: si sube con el tiempo el juego está sano; si baja, mala señal, actuar rápido.
- **Lifetime del jugador**: la mayoría juega <1 día. Mejorar FTUE y balance temprano; a la inversa, medir cuánto juegan los habituales (semanas/meses) y **por qué paran** (ej. se les acaba el contenido, más común en juegos de contenido que en sistémicos).

**3. Conversión (F2P) [sec: Conversion]**
- 98-99% de los jugadores F2P nunca compran (jugadores ≠ clientes). **Conversion** = pasar de jugador a cliente.
- Medir por cohorte: cuándo hacen la primera compra, gasto diario medio, probabilidad de segunda compra. Mejor FTUE ⇒ compra más pronto y más; quien compra una vez compra otra con mucha más probabilidad.
- **ARPU** (average revenue per user) = ingresos / todos los usuarios. **ARPDAU** (por usuario activo diario). **LTV** (lifetime value) = ingreso medio por jugador durante toda su vida; "la métrica más importante" de balance de experiencia y éxito comercial.
- **Ecuación de hierro de F2P**: LTV > eCPU + Ops (eCPU = costo efectivo de adquirir un usuario; Ops = costo operativo por jugador durante su vida). Ejemplo: jugador dura 1 año, operar cuesta $1/mes, adquirir cuesta $3 → hace falta LTV > 3 + 1×12 = $15; si cada jugador paga $10 de media en su vida, vas a la quiebra.
- Monetización es parte del diseño: construir la experiencia para que el jugador no sienta que *debe* comprar pero elija hacerlo lo suficiente.

**4. Uso [sec: Usage]**
- Misiones: ¿todas se completan parecido? La que se repite mucho puede estar desbalanceada a favor del jugador; la que casi nadie completa puede ser muy difícil o tediosa.
- **Cómo mueren / pierden**: ver qué causa la derrota revela partes desbalanceadas.
- Medidas económicas (Habitat): variación de la masa de dinero total y saldo diario por jugador. Cualquier cosa que afecte uso, fuentes/sumideros y acumulación de recursos centrales merece ser medida.
- Tip de dónde empezar: instrumentar **todo evento que dispare un sonido/feedback auditivo**; si genera demasiado dato inútil, filtrar.

**5. Comunidad [sec: Community]**
- Tiempo de chat general y con personas concretas, cantidad de grupos persistentes (gremios) y su actividad → modelo aproximado del contacto social (quién conecta con quién), detectar **influyentes y early adopters**. Si un grupo de influyentes baja su tiempo de juego, puede ser señal temprana (se quedaron sin contenido).
- Cantidad y tipo de **quejas** por parte del juego: revelan bugs y zonas percibidas como desbalanceadas, difíciles, tediosas o poco enganchantes.

---------------------------------------------------------------------
## B7. Resumen del capítulo y mensajes finales [sec: Summary]
---------------------------------------------------------------------
- Balancear es un ejercicio **continuo**; nunca es perfecto ni está terminado. Si el juego parece básicamente justo para vos y los jugadores, vas bien. Cada jugador puede desbalancear el juego de maneras nuevas → construir sistemas **resilientes** reduce la probabilidad de ruptura y de pérdida de engagement.

---------------------------------------------------------------------
# PARTE C — SÍNTESIS PARA USAR (derivada de lo anterior)
---------------------------------------------------------------------

## C1. Flujo recomendado de balance (compuesto de los dos capítulos)
1. Definir el tipo de relación entre partes: cíclica ("transitiva" en Sellers: ciclo de counters, nº impar de tipos, mismo presupuesto de puntos) o por costo-beneficio ("intransitiva" en Sellers: costo proporcional al beneficio).
2. Identificar el recurso central (y subsidiarios, y casos especiales). Buscar shadow resource si hay varios.
3. Tabular partes × atributos en hoja de cálculo; ordenar atributos por cadena causal hacia el recurso central; asignar pesos (1,0 al más directo).
4. Calcular Mod Value (suma ponderada) → fijar costo en juego a mano (barato abajo, prima arriba, cruce en la pieza central).
5. Elegir curva madre (exponencial para umbrales/tiers; logística para techos/rendimientos decrecientes; por tramos/NAP para hitos y variedad); ajustar la base y chequear tiempo de duplicación.
6. Acoplar curvas de desafío ↔ poder ↔ recompensa ↔ costo (misma base aproximada).
7. Estimar tiempo/atención por hito (actividades × éxito × duración) y vigilar el **rango**, no solo el promedio.
8. Economía: balancear fuentes y sumideros, evitar arbitraje (precios consistentes), poner piso/techo (import/export) atado a la curva de rareza.
9. Playtest para validar el modelo mental del jugador; instrumentar KPIs y mirar cohortes; comparar con intuición.
10. Iterar; aceptar que no se llega a perfección.

## C2. Errores comunes y cómo detectarlos
- **Estrategia dominante / espacio colapsado**: un objeto/arma/clase con mejor Mod Value y menor costo que otros; una facción que gana mucho más (analítica de win rates por facción/clase); un terreno o condición que hace invencible a un tipo (playtest en condiciones distintas).
- **Partes agrupadas en el medio** (poca variedad): graficar los atributos y ver aglomeraciones.
- **Curvas desacopladas**: desafíos ×3 vs. poder ×1,25 → injustificable; revisar bases de cada curva.
- **Curva lineal/polinómica a escala alta**: el "+n" ya no se siente; fatiga hedónica.
- **Exponencial con números inimaginables**: pierde sentido; limitar niveles/tiers o pasar a logísticas apiladas/prestige.
- **Multiplicar dos progresiones lineales sin darte cuenta**: crecimiento cuadrático inesperado.
- **Inflación**: fuentes > sumideros; **estancamiento**: sobrecorrección; **arbitraje**: precios inconsistentes (Habitat). Detección: monitorear masa monetaria y saldos diarios.
- **Rango de tiempo de avance demasiado ancho** (ej. 7 a 75 min por nivel): jugadores desparejos.
- **Progreso que se siente detenido** o próximo hito infinitamente lejano: engagement se evapora.
- **Sistema transitivo con nº par de tipos**: ecología inestable (WoW Horda/Alianza).
- **Apilar demasiadas novedades a la vez** (Tumbleseed): romper el presupuesto de interactividad; detectar con embudo de progresión.
- **Confiar solo en intuición o solo en jugadores vocales**: usar datos de la mayoría, no de la minoría ruidosa; muestras no representativas.
- **Datos viejos o sobre-instrumentación**: sin KPIs claros se pierde tiempo.
- **Percepción de injusticia con azar puro**: mal cálculo de la gente sobre rachas; usar 1−(1−p)^n y considerar protección contra mala suerte.

## C3. Fórmulas de un vistazo
- Lineal: y = A·x + B
- Polinómica: y = x^n (o a·x^n); cuadrática = producto de dos lineales
- Exponencial: y = A^x ó y = B·A^x; niveles para duplicar ≈ ln2 / ln A
- Logística: y = L / (1 + e^(−k(x − x0))); en x0, y = L/2
- Pendiente de tramo: (y1 − y0) / (x1 − x0)
- Probabilidad enlazada: P = p1 × p2 × ...
- Éxito en n intentos: P = 1 − (1 − p)^n
- Combinaciones en nd6: n°combos / 6^n
- Mod Value (ejemplo armas): 1,3·Attack + 1,0·Damage + 1,75·Speed (pesos iniciales probados 1,5 / 1 / 2)
- XP por nivel (ejemplo): 1.000 × 1,4^nivel
- Poder por tier (Albion): 1,2^tier; rareza: 3^tier; canal de mercado: rareza×0,5 (export) a rareza×2 (import)
- Embudo: ~50% de pérdida por clic; ~10× por etapa de adquisición
- Stickiness = DAU / MAU
- Iron equation F2P: LTV > eCPU + Ops

## C4. Ejemplos de juegos citados (una línea cada uno)
- Dark Souls / Super Meat Boy: difíciles sin estar desbalanceados (gusto vs. balance).
- Tumbleseed: embudo de progresión muy empinado; sobrecarga de novedades; desajuste estética casual/dificultad.
- Rock-Paper-Scissors / RPSLS: balance transitivo básico (cada una vence a la mitad).
- Wu Xing, lagartos de tres colores: ejemplos naturales/culturales de ciclos transitivos.
- Dark Age of Camelot (RvR): tres reinos con dominio cíclico y alianza contra el más fuerte.
- Horde vs Alliance (WoW): dos facciones (par) → inestable.
- RuneScape: exponencial con base 1,1 para XP.
- Adventure Capitalist: exponencial que llega a ~10^300 (números sin sentido).
- A Dark Room: placer de que "suban los números" + explorar lo desconocido.
- WoW niveles iniciales: curva NAP con números redondos (400, 500, 500, 700, 700...).
- WoW inventario/bolsas: progresión secundaria auto-balanceada.
- WoW dinero por monstruo: ×750 de nivel 1 a 60; ejemplo de inyección masiva de moneda.
- Habitat: arbitraje muñecas/bolas de cristal; monitoreo de masa monetaria.
- Albion Online: poder 1,2^tier vs rareza 3^tier; mercado con import/export.
- Juegos de cajas ciegas / casino social: probabilidades enlazadas y near-miss.
- Let's Make a Deal (Monty Hall): sesgos cognitivos de probabilidad.
