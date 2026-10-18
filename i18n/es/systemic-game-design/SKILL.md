---
name: systemic-game-design
description: Diseño de juegos con enfoque sistémico, basado en "Advanced Game Design. A Systems Approach" de Michael Sellers. Usala para DISEÑAR sistemas de juego (core loop, loops de refuerzo y balance, motores, economías, ecologías, progresión, partes con atributos y comportamientos, emergencia), para ANALIZAR o CRITICAR un diseño (por qué algo aburre, no engancha, se vuelve lista de tareas o grind, tiene una estrategia dominante, inflación, snowball, decisiones que no importan, demasiada carga mental) y para BALANCEAR con números (curvas de XP, poder y costo, valor y precio de armas, ítems o unidades, probabilidad y drops, counters tipo piedra-papel-tijera, fuentes y sumideros de una economía, métricas de retención). Activala siempre que el usuario hable de game design, mecánicas, loops, balance, progresión, economía o dificultad de un juego, o traiga feedback de playtesters sobre la diversión, aunque no diga "sistemas" ni nombre el libro. Sirve para videojuegos y juegos de mesa.
---

# Diseño de juegos sistémico (Sellers)

Esta skill aplica el método de *Advanced Game Design: A Systems Approach* (Michael Sellers, 2018) a juegos concretos. La idea central del libro: un juego es un **sistema**, y la experiencia no la escribe el diseñador sino que **emerge** de partes que interactúan en loops, junto con el jugador. El diseñador controla directamente solo las partes y las reglas. La experiencia la consigue indirectamente, armando el espacio donde ocurre (lo que el libro llama diseño de segundo orden).

Usala para pensar con el usuario sobre **su** juego, no para dar una clase. La teoría sirve si cambia una decisión de diseño.

## La lente: todo, loops, partes

Todo juego se mira en tres niveles. Hay que recorrer los tres y moverse entre ellos:

| Nivel | Qué es | Preguntas |
|---|---|---|
| **Todo** (whole) | La experiencia del sistema juego+jugador: fantasía, tema, qué siente y qué decide el jugador | ¿Qué experiencia buscamos? ¿Qué hace el jugador en cada momento y por qué le importa? |
| **Loops** | Los sistemas: partes conectadas en ciclos de refuerzo o de balance (motores, economías, ecologías) | ¿Qué crece, qué frena, qué se intercambia? ¿Dónde están las decisiones? |
| **Partes** (parts) | Tokens con estado (atributos y valores), límites y comportamientos, especificados "a nivel planilla" | ¿Cuál es el mínimo de atributos y comportamientos que sostiene los loops? ¿Con qué números? |

**Para destrabarse:** si un nivel no avanza, cambiá de nivel. Si no sale la experiencia, mirá qué permiten las partes. Si la experiencia está clara pero no salen los números, mirá qué exigen los loops.

El sistema que importa es **juego + jugador**. El jugador arma un **modelo mental** del modelo interno del juego, y la diversión vive en ese loop: el jugador forma una intención, actúa, el juego cambia y le da feedback, y el jugador actualiza su modelo. Si ese loop no está cerrado, todavía no hay juego.

## Primero: elegí el modo

Fijate qué pide el usuario y seguí el flujo que corresponda. Muchas consultas mezclan modos; en ese caso hacé primero el análisis y después el diseño o el balance.

- **Diseñar:** crear o rediseñar sistemas, loops o partes. Ver "Flujo: diseñar".
- **Analizar o criticar:** algo no funciona, aburre o no engancha, o hay que entender un juego existente. Ver "Flujo: analizar".
- **Balancear:** hay números de por medio: costos, curvas, drops, tasas, precios. Ver "Flujo: balancear".

Las referencias de `references/` tienen el detalle. Leé solo la que necesites:

| Archivo | Cuándo leerlo |
|---|---|
| `references/sistemas-y-loops.md` | Estructura de loops, motores, economías y ecologías, progresión, fallas típicas de loops, documento de sistema |
| `references/interactividad-y-diversion.md` | "No engancha", "aburre", "abruma": modelo mental, seis loops interactivos, flow, presupuesto de interactividad, emociones |
| `references/partes-y-atributos.md` | Bajar a atributos, rangos y comportamientos; feedback; emergencia; planillas data-driven |
| `references/balance.md` | Curvas, costo-beneficio, valor de ítems, probabilidad, economía, métricas |
| `references/vision-y-analisis.md` | Checklist completo de análisis, modelo sistémico (decisiones, oposición, metas), visión y documento de concepto |
| `references/prototipado-y-playtest.md` | Cómo validar: prototipos de una pregunta, playtests, leer feedback |

Las referencias son largas (300 a 700 líneas). No las leas enteras: cada una empieza con un **Índice**. Leé el índice, y después solo las secciones que el caso necesita (con Grep por el título o leyendo ese rango de líneas). Por modo, lo que suele hacer falta:

- **Diseñar:** en `sistemas-y-loops.md`, "Los tres tipos de loops de gameplay", "Combinar loops" y "Catálogo de fallas". En `partes-y-atributos.md`, "Determining Attributes", "Specifying Behaviors" y "Creating Looping Systems".
- **Analizar:** en `vision-y-analisis.md`, "MÉTODO: analizar juegos" y "Decisiones significativas, oposición y metas". En `interactividad-y-diversion.md`, "Checklist de diagnóstico".
- **Balancear:** en `balance.md`, "Tipos de curvas", "Balancear partes (armas)", "Balancear progresión", "Balance de sistemas económicos" y "Fórmulas de un vistazo".

Con la tabla de diagnóstico y los flujos de este archivo alcanza para muchos casos. Abrí una referencia cuando necesites el detalle o un ejemplo.

## Vocabulario mínimo

Usá estos términos (con su nombre en inglés la primera vez) y explicalos en una línea si el usuario no los conoce.

- **Loop de refuerzo** (reinforcing, "feedback positivo"): más genera más. Da progresión y snowball. Sin freno, se desboca (*runaway*): el que va ganando gana cada vez con menos esfuerzo y el que va perdiendo se queda sin opciones.
- **Loop de balance** (balancing, "feedback negativo"): empuja hacia un equilibrio. Da catch-up y estabilidad. En exceso, todo se estanca o nada importa.
- Regla: todo loop de refuerzo necesita un límite en algún lado (un costo, un tope, una fricción, un rubberband o una demora). Buscalo siempre. Si no está diseñado, aparece igual, y peor.
- **Piezas de un loop:** fuente (*source*/faucet) → stock (con o sin tope) → conversor (*converter*: transforma un recurso en otro) → decisor (*decider*: bifurca el flujo) → sumidero (*sink*/drain). Una **moneda** (currency) se intercambia sin consumirse.
- **Tres tipos de loops de gameplay** (cap. 7):
  - **Motor** (engine): mismo recurso. El de impulso (*boosting*) obliga a elegir entre usarlo ahora o invertirlo para tener más flujo después (Monopoly, deckbuilders). El de freno (*braking*) es fricción: stamina, mantenimiento.
  - **Economía**: refuerzo por intercambio o conversión entre recursos distintos, con ganancia de valor no lineal (madera → tablón → pan, cadenas de producción).
  - **Ecología**: balance por intercambio. Cada parte frena a otra y el todo queda en equilibrio dinámico (predador/presa, combate, inventario, tres facciones).
- **Core loop:** lo que ocupa la atención del jugador en ese momento. Suele haber varios anidados en distintas escalas de tiempo ("3 segundos dentro de 30 dentro de 3 minutos", Halo).
- **Seis loops interactivos**, del más rápido al más lento: acción/feedback (menos de 3 s), cognitivo de corto plazo (táctica, puzzle), cognitivo de largo plazo (estrategia), social, emocional, cultural.
- **Presupuesto de interactividad** (interactivity budget): la carga mental total que el jugador está dispuesto a gastar. **Lo rápido expulsa a lo lento**: si hay que esquivar balas, no se puede planificar ni sentir. Las cosas lentas van separadas en el tiempo de las rápidas.
- **Decisión significativa:** hay incertidumbre, el resultado cambia el estado de forma perceptible y abre o cierra opciones futuras. Dos puertas que llevan al mismo lugar no son una decisión.
- **Fuentes de oposición:** las reglas, los oponentes activos, otros jugadores, y el propio jugador (sus trade-offs).
- **Metas:** instantáneas, de corto plazo, de largo plazo, sociales y emocionales. Las explícitas enseñan. Las implícitas, que se pone el propio jugador, son las que dan longevidad.
- **Elegancia:** profundidad (sistemas dentro de sistemas) con pocas excepciones. Fácil de aprender, difícil de dominar (Ley de Bushnell). Cada excepción gasta presupuesto mental.
- **Contenido vs sistemas:** el contenido (niveles, misiones) se consume y obliga a producir más (*content treadmill*). Los sistemas generan situaciones nuevas. Un reskin no enseña nada nuevo.

## Flujo: diseñar

1. **Anclá el todo en dos o tres líneas:** fantasía del jugador, experiencia buscada, qué hace momento a momento, y en qué loops interactivos gasta su presupuesto. Si el usuario no lo dijo, inferilo de lo que contó y declaralo como supuesto. No frenes para preguntar lo que se puede suponer razonablemente.
2. **Definí el core loop y los loops externos.** Para cada loop indicá qué tipo es (motor, economía o ecología; de refuerzo o de balance), qué recurso circula y dónde está la decisión del jugador. Combiná un loop de tensión alta (acción, combate) con uno de tensión baja (construir, gestionar): ese patrón funciona en muchos géneros.
3. **Dibujá los loops** en texto (ver "Formato de diagramas"). Marcá fuentes, stocks, sumideros, decisores y conversores, con + o − en cada flecha, y etiquetá cada ciclo como R (refuerzo) o B (balance).
4. **Revisá cada loop contra sus fallas** (tabla de diagnóstico). Por cada loop de refuerzo, ¿qué lo limita? Por cada recurso, ¿las fuentes superan a los sumideros (inflación) o al revés (estancamiento)? ¿Hay una estrategia dominante?
5. **Bajá a partes:** las partes clave, cada una con sus atributos mínimos (tipo, rango) y sus comportamientos. Los comportamientos tienen que ser **locales** (afectan a partes del mismo nivel y contexto), **genéricos** (no son scripts de un solo uso) y **perturbar sin determinar** (cada parte decide cómo responde). Así sale la emergencia. Cada parte tiene que afectar a otras y ser afectada por otras; si una conexión es de una sola vía, buscá cómo cerrarla.
6. **Señalá la emergencia esperada:** dos o tres situaciones concretas que nadie programó a mano y que deberían surgir de la interacción entre sistemas. Es la prueba de que el diseño es sistémico y no una lista de features.
7. **Desplegá la complejidad de a poco** (unfolding complexity): qué ve el jugador al principio y qué se suma a medida que su modelo mental crece.
8. **Cerrá con la validación:** el prototipo más chico que responde la pregunta de mayor riesgo, y qué observar en el playtest.

Podá sin piedad. Un sistema que no apoya la experiencia sale, aunque guste o haya costado trabajo.

## Flujo: analizar

Un síntoma ("aburre a partir del acto 2", "todos usan lo mismo") casi nunca se arregla tocando un número. Buscá la **estructura** que lo produce.

1. **Reformulá el síntoma como comportamiento observable.** ¿Qué hace o deja de hacer el jugador? ¿En qué momento?
2. **Mapeá los loops implicados**, aunque sea a grandes rasgos: qué se refuerza, qué se balancea, de dónde vienen y adónde van los recursos.
3. **Diagnosticá con la tabla de fallas** y nombrá la causa raíz. Por ejemplo: "economía con fuente que crece y sin sumidero proporcional, o sea inflación", y no "el oro sobra".
4. **Revisá el lado del jugador** (`interactividad-y-diversion.md`): ¿el modelo mental se puede construir? ¿Hay decisiones significativas? ¿Se rompe el presupuesto de interactividad? ¿Habituación (recompensas iguales a la misma tasa)? ¿Está dentro del canal de flow? ¿Hay ciclos de tensión y alivio?
5. **Proponé arreglos sistémicos, priorizados por impacto y costo.** Preferí cambiar la estructura (agregar un sumidero, un costo de oportunidad, un counter cíclico, una demora, un límite) antes que apilar parches. El anti-patrón clásico: frente a una unidad dominante, agregar otra que la contrarreste, que a su vez se vuelve dominante. Corregí el costo en el origen.
6. **Indicá cómo medir si funcionó:** qué métrica, qué observación de playtest o qué simulación.

Si el usuario pide analizar un juego existente (propio o ajeno), usá el checklist de siete pasos de `vision-y-analisis.md`: primer contacto con tu modelo mental, todo, sistemas, loops de progreso, interactividad, partes y síntesis.

## Flujo: balancear

1. **Elegí el recurso central** (*core resource*): lo que el jugador maximiza o no puede perder (vida, XP, oro, territorio). El costo y el beneficio se miden contra él.
2. **Decidí el tipo de balance:**
   - **Cíclico** (counters tipo piedra-papel-tijera): mismo presupuesto de puntos repartido distinto, con un número **impar** de tipos (con un número par se vuelve inestable). Sellers llama "transitivo" a esto, al revés que el resto de la bibliografía; usá "cíclico" y aclaralo si hace falta.
   - **Costo-beneficio** (escalera de poder): más beneficio cuesta proporcionalmente más, sobre una curva.
3. **Valuá las partes** con una suma ponderada de atributos (el "Mod Value" del libro). Ordená los atributos por cadena causal hacia el recurso central, dale peso 1,0 al más directo y escalá los demás según cuánto multiplican oportunidades (por ejemplo, la velocidad o la cadencia "abren la puerta" al daño). Después fijá el **costo en el juego a mano**: un poco por debajo del valor en lo barato (para entrar), un poco por encima en lo top (aspiracional), con el cruce en una pieza de referencia del medio. Ninguna parte puede tener más valor y menos costo que otra: eso es dominancia.
4. **Calculá lo derivado** antes de opinar: DPS sostenido (incluye la recarga), valor por unidad de costo, tiempo para matar, tiempo para subir de nivel. Mostrá las cuentas en una tabla para que el usuario las pueda rehacer.
5. **Elegí la curva** (en `balance.md` están las fórmulas):
   - Exponencial `y = B·A^x` para umbrales de XP y tiers. Niveles para duplicar = ln 2 / ln A.
   - Logística `y = L/(1+e^(−k(x−x0)))` para techos y rendimientos decrecientes.
   - Por tramos o hecha a mano para hitos y sorpresas.
   - La lineal se apaga porque el mismo "+n" pesa cada vez menos (fatiga hedónica).
   - Multiplicar dos lineales da una cuadrática: puede pasar sin querer (enemigos por nivel × oro por enemigo).
6. **Acoplá las curvas:** desafío, poder, recompensa y costo tienen que crecer con bases parecidas. Si el desafío crece ×3 por nivel y el poder ×1,25, el juego se vuelve injugable. Calculá cuántas acciones (enemigos, partidas, minutos) hacen falta por nivel y mirá el **rango**, no solo el promedio.
7. **En una economía**, listá cada fuente y cada sumidero con su tasa. Las recompensas crecientes exigen sumideros crecientes. Evitá el arbitraje: ningún vendedor puede comprar más caro de lo que otro vende. Si hay comercio entre jugadores, considerá un canal con piso y techo de precios (import/export).
8. **Azar:** probabilidad de al menos un éxito en n intentos = 1 − (1 − p)^n. Los jugadores perciben como injustas las rachas que son estadísticamente normales; considerá protección contra la mala suerte (probabilidad que sube tras cada fallo).
9. **Validá:** los números encuentran lo más desbalanceado, no la perfección. Simulá si hay código o planilla, playtesteá y medí (embudos por checkpoint, tasas de victoria por opción, qué mata a los jugadores).

Si el proyecto tiene código, planillas o un simulador, **medí antes de proponer números**. Leer los datos reales evita balancear de memoria.

## Tabla de diagnóstico de fallas

| Síntoma que se ve | Causa estructural | Corrección sistémica |
|---|---|---|
| El que va ganando se despega y la partida se decide temprano | Refuerzo sin balance (runaway, snowball) | Rubberband (blue shell, ladrón de Catan, orden de turno inverso), fricción proporcional al líder, demora en el retorno, tres o más facciones |
| Al perder, el jugador ya no se recupera | Espiral de muerte: perder reduce los recursos para recuperarse | Loop de balance de rescate, piso mínimo de recursos, fuente independiente del rendimiento |
| Todos usan la misma build, arma o unidad | Estrategia dominante: una opción mal costeada o un balance demasiado fino | Recostear en el origen, agregar trade-offs o counters cíclicos; nunca apilar contra-unidades |
| La moneda sobra y no hay en qué gastarla | Inflación: más fuentes que sumideros, recompensas crecientes sin sumideros proporcionales | Limitar fuentes, topes de stock, sumideros que valgan la pena (mejoras, desgaste, consumibles), prestigio |
| Nadie gasta y todos atesoran | Estancamiento: fuentes escasas o mantenimiento caro | Devolver el gradiente: que intercambiar convenga |
| No se puede arrancar el loop | Deadlock: el recurso que da el loop es necesario para empezarlo | Fuente inicial independiente |
| El jugador se queda sin poder actuar | Freno más fuerte que el motor | Bajar la fricción o hacerla proporcional |
| "Se siente como una lista de tareas" o grind | Loops lineales (arcos) sin decisiones ni interacción entre sistemas; recompensas a tasa fija | Conectar sistemas para que se afecten entre sí, poner decisiones con trade-off, que el riesgo y la recompensa dependan del contexto |
| Lo que antes emocionaba ya no | Habituación o fatiga hedónica: misma recompensa a la misma tasa | Novedad, tasa de recompensa creciente (con sumideros), metas aspiracionales, nuevas formas de interactuar |
| Aburre después de X horas | Contenido agotado; profundidad sistémica insuficiente | Sistemas que generen situaciones, metas implícitas, ecologías, complejidad que se despliega |
| Las peleas o niveles se sienten todos iguales | Pocas variables que cambien la decisión; la variedad es solo de números (reskin) | Variar las reglas y el contexto que cambian qué decisión es la mejor, no solo la vida y el daño |
| "No entiendo qué hacer" o abandono temprano | Modelo mental imposible de construir: excepciones, feedback pobre o tardío, demasiadas novedades a la vez | Menos reglas especiales, feedback en 100-250 ms y visual antes que textual, introducir de a una novedad |
| Abruma o estresa | Presupuesto de interactividad excedido: se mezclan reflejos con estrategia o emoción | Separar en el tiempo lo rápido de lo lento |
| Las decisiones no importan | Decisiones ilusorias o un camino óptimo conocido | Incertidumbre real, consecuencias que abren o cierran opciones |
| Un parche arregló algo y después volvió peor | Fixes that fail: un loop lento con demora revierte la solución | Buscar el loop oculto; desconfiar de las soluciones rápidas que se pueden explotar |
| El sistema "se rompe" ante cualquier cambio | Fragilidad: deciders no locales, choke points, balance clavado | Comportamientos locales, equilibrio dinámico en vez de valores fijos |

`sistemas-y-loops.md` tiene la tabla extendida, con ejemplos de juegos.

## Principios transversales

- **Probá operando, no leyendo:** los sistemas se entienden corriéndolos. Toda propuesta termina en un prototipo (una pregunta por prototipo, rápido y feo) o en una medición.
- **Spreadsheet-specific:** "rápido", "mucho" o "más fuerte" no se pueden implementar. Dá números, rangos o fórmulas; lo que no esté decidido, marcalo como asunto abierto.
- **Mínimo de atributos:** cada atributo nuevo es una nueva forma de desbalancear el juego. Si el jugador no distingue dos atributos, fusionalos.
- **Todo verbo tiene feedback** inmediato, comprensible al instante y consistente. Un efecto decorativo sin estado detrás es ruido que el jugador mete en su modelo mental.
- **Los jugadores traen problemas, no soluciones:** leé el feedback buscando la causa, y desconfiá de la minoría ruidosa frente a los datos de la mayoría.
- **Éxito temprano, meta lejana:** un "¡lo lograste!" en el primer minuto y una aspiración que siempre esté un poco más allá.
- **Tema como filtro:** lo que no deriva del tema ni lo apoya se elimina o se altera.

## Formato de la respuesta

Adaptalo al pedido; no hace falta usar todas las secciones. En general:

- **Diseño:** supuestos y experiencia buscada → loops (diagrama, tipo, recurso, decisión) → riesgos de cada loop y cómo se frenan → partes (tabla de atributos y comportamientos) → emergencia esperada → orden de despliegue → qué prototipar primero.
- **Análisis:** diagnóstico en una frase → mapa de loops implicados → causas raíz (nombradas con el vocabulario) → cambios priorizados (impacto/costo, con el porqué de cada uno) → cómo medir que funcionó.
- **Balance:** recurso central y método → tabla de cálculos (valores derivados, valor por costo) → dominantes e inútiles → tabla corregida → curvas propuestas con su fórmula y una tabla de muestra → pasos para repetir el método → qué validar en juego.

Usá tablas para números y partes. Si el usuario pide un documento, armalo como **documento de sistema** (nombre y descripción, metas en términos de experiencia, diagrama, interacciones del jugador, sistemas relacionados, preguntas abiertas), uno corto por sistema y no una "biblia" gigante.

### Formato de diagramas

En texto plano, que se lea en cualquier terminal:

```
[Fuente: enemigos]──oro──▶(Stock: oro)──▶<Decisor: ¿gastar o ahorrar?>
                                  ├─▶{Conversor: herrero}──▶(Arma +1)──+──▶ daño ──+──▶ enemigos muertos ─┐
                                  └─▶[Sumidero: reparaciones]                                              │
  R1: más arma → más muertes → más oro → más arma                                                         │
  B1: más oro gastado en arma → menos oro para reparar → arma se degrada  ◀───────────────────────────────┘
```

`[ ]` fuente o sumidero, `( )` stock, `< >` decisor, `{ }` conversor, `+`/`−` en las flechas, R/B para nombrar los ciclos. Si el usuario usa Mermaid o una pizarra, podés usar ese formato.

## Cuidado con

- **No recitar el libro.** Aplicá un concepto solo si explica algo del juego del usuario.
- **No inventar datos del libro.** Si una cifra o ejemplo no está en las referencias, presentalo como propio.
- **No dar por hecho que hay una sola respuesta.** Cuando haya trade-offs reales, mostrá dos opciones con sus consecuencias y recomendá una.
- **Respetar las reglas de diseño que el usuario ya fijó.** Si el proyecto tiene un documento de diseño o restricciones, trabajá dentro de ellas y avisá si alguna es la causa del problema, sin cambiarla por tu cuenta.
