# Diagnóstico y cambios para tu roguelite de cartas (acto 2 aburre)

## Diagnóstico en una frase

Tu juego tiene un motor de refuerzo (poder del mazo) sin freno, una moneda sin sumideros que valgan la pena, y un loop de combate donde la única variable que cambia entre peleas son los números. El resultado: a partir del acto 2 hay una estrategia dominante, el oro no sirve y no hay decisiones que importen.

**Supuestos que hago** (no me dijiste): el mazo inicial es parecido al de Slay the Spire (ataques, defensas y alguna carta especial); las cartas de recompensa te las ofrecen de a 3 y podés saltearlas; hay una sola clase o clases con poca diferencia entre sí; las peleas de elite solo tienen más vida, más daño y mejor recompensa. Si alguno es falso, la prioridad de los cambios puede moverse.

## Mapa de loops (lo que está pasando)

```
R1 (motor de impulso, mazo):
  (poder del mazo)──+──▶ peleas ganadas rápido ──+──▶ (cartas/oro/reliquias) ──+──▶ (poder del mazo)
  Límite diseñado: casi ninguno. La dificultad crece, pero el mazo "ataque puro" crece más rápido.

R2 (economía, oro):
  [Fuente: peleas, elites, eventos]──oro──▶(Stock: oro, sin tope)──▶<¿tienda?>──▶[Sumidero: tienda]
  La tienda no ofrece nada que cambie el R1 ⇒ el sumidero está tapado ⇒ el stock solo crece.

B1 (freno esperado, enemigos): la vida/daño de los enemigos debería frenar R1.
  Si un solo arquetipo de mazo lo supera siempre, B1 no está frenando: está calibrado
  contra "daño", no contra "mazo".
```

## Causas raíz (con nombre)

1. **Estrategia dominante (ataque puro).** Si casi todos ganan con la misma build, no es que "los jugadores sean listos": hay una opción mal costeada o un entorno donde matar rápido resuelve todo. En Slay the Spire, el ataque puro no gana porque matar rápido no alcanza: hay enemigos con escalado, mecánicas que castigan el daño bruto y bloqueo que vale. Si en tu juego las peleas se resuelven por tiempo-para-matar, defender y escalar no valen su costo de oportunidad. **Esto es un problema de costo en el origen, no de falta de contra-cartas.**
2. **Inflación de oro (más fuentes que sumideros).** El oro es una moneda: se intercambia por valor. Si el jugador percibe que no vale nada, para él la moneda no existe y la economía muere. Es la falla exacta de Diablo II descripta en el libro: faucets abundantes + nada en qué gastar. Además, un stock de oro que crece sin uso rompe el ritmo de decisión del mapa: los nodos de tienda dejan de ser una decisión.
3. **Decisiones ilusorias en el mapa y en la construcción del mazo.** Si todos los caminos llevan a "más ataque" (elegir entre tienda, descanso o pelea da lo mismo cuando el mazo ya ganó), las decisiones no abren ni cierran opciones. Dos puertas que llevan al mismo lugar no son una decisión.
4. **Variedad solo de números (reskin sistémico).** Elite = normal con más vida. Si el jugador no tiene que cambiar su plan frente a un elite, el elite no es otro encuentro: es el mismo con otra barra. Esto es lo que el libro llama contenido que no cambia tokens ni reglas: se nota enseguida que no hay nada nuevo que aprender.
5. **Habituación en el acto 2.** Recompensas a tasa fija y plan óptimo conocido: la novedad se acaba justo cuando el jugador ya tiene el modelo mental completo. Del acto 2 en adelante, el jugador ya sabe qué hacer; si el juego no le plantea preguntas nuevas, está en la zona de aburrimiento del canal de flow (habilidad mayor que el desafío).

## Cambios propuestos, ordenados por prioridad (impacto/costo)

### Prioridad 1: romper la estrategia dominante (es lo que más pesa y lo que primero hay que medir)

**Antes de tocar nada, medilo:** tasa de victoria por arquetipo de mazo, turnos promedio por pelea, y cuánto daño recibe el jugador en el acto 2 en las partidas ganadoras. Si el "ataque puro" gana con casi nada de daño recibido, el freno B1 no existe.

Cambios concretos (elegí 2 o 3, no todos):

- **Dar al ataque puro un costo estructural**, no una contra-carta. Ejemplos:
  - Enemigos del acto 2 con una **fase de escalado** (cada turno ganan fuerza o armadura): el que mata lento pierde, el que mata muy rápido gasta el mazo y llega vacío al elite. Pero hacelo con una regla clara, no con otra excepción más.
  - **Daño que no alcanza**: enemigos con "umbral" (reciben un máximo por turno, o ignoran el primer golpe). Obliga a repartir recursos entre daño, bloqueo y setup.
  - **Presión de mazo**: añadí cartas basura o de estado que entran al mazo cuando recibís daño (la forma más barata de que defender valga). Así el ataque puro que ignora la defensa ensucia su ciclo.
- **Recostear en el origen:** si las cartas de ataque comunes rinden más por energía que las de defensa o utilidad, subir el costo/nerf del ataque es mejor que agregar otra carta que lo contrarreste (el anti-patrón clásico: la contra-unidad que se vuelve la nueva dominante).
- **Recompensas de carta con trade-off real.** Que las mejores cartas de ataque del acto 2 cuesten algo (vida máxima, una carta de estado, una maldición leve). El jugador decide si vale la pena.

**Cómo saber si funcionó:** ningún arquetipo supera, por ejemplo, 35-40% de victorias sobre el total de partidas ganadoras (número mío, ajustalo), y los playtesters ya no describen su estrategia con la misma frase.

### Prioridad 2: arreglar el oro (sumideros que valgan, sin tocar la fuente al principio)

Primero identificá cuánto oro llega por acto y cuánto se puede gastar hoy. Si al llegar al acto 2 ya hay más oro que catálogo de tienda, falta sumidero, no sobra fuente.

- **Tienda con productos que cambian la estructura del mazo**, no solo cartas sueltas:
  - **Quitar carta** (con precio creciente: 75, 100, 125...). Es el sumidero clásico y de los más valiosos, porque adelgazar el mazo es una decisión real.
  - **Mejorar carta** (en la tienda, no solo en descansos).
  - **Reliquias** de gama media y alta con precios altos (150-300), siempre al menos una que invite a cambiar de estrategia.
  - **Consumibles** potentes que valen para un elite o jefe concreto.
  - **Servicios**: curación a precio fijo, rerollear la tienda, comprar información (ver el próximo elite o el jefe).
- **Que lo caro sea aspiracional:** al menos un artículo por tienda que cueste más de lo que el jugador tiene en ese momento, para que ahorrar sea una decisión (gastar ahora vs. juntar para la tienda siguiente).
- **Precio creciente por acto** (las recompensas crecen, los precios también): evitás que el oro del acto 3 sea el del acto 1 con otro nombre.
- **Si aún sobra:** tope de oro por acto o un impuesto por nodo de descanso, solo como última opción. Es un parche; el problema real es la falta de cosas que comprar.

**Cómo saber si funcionó:** oro sin gastar al terminar el acto 2 menor al precio de un artículo medio, y algún playtester diciendo "no me alcanza para todo lo que quiero".

### Prioridad 3: elites que sean otro tipo de pelea (no solo más vida)

El elite tiene que cambiar la **decisión**, no solo los números. Cada elite debería obligar a un plan distinto. Ejemplos de reglas, no de números:

| Elite | Regla que cambia la decisión |
|---|---|
| Escalador | Gana fuerza cada turno: premia matar rápido o controlar |
| Blindado | Inmune al daño hasta que se le rompe un escudo con cartas específicas: premia mazos con utilidad |
| Invocador | Genera adds que hay que priorizar: castiga el daño de un solo objetivo |
| Castigador | Reacciona a lo que más usás (ej.: contraataca cada ataque barato): castiga el spam |
| Reloj | Cuenta atrás: si no matás en N turnos pasa algo grave |

- Cada elite debería tener un **counter por estructura** (cartas o reliquias que el jugador puede haber elegido antes), no una solución universal. Así lo que elegiste en la tienda te prepara (o no) para el elite.
- **Hacelos legibles:** mostrar su regla antes de la pelea (intención clara, nombre del elite en el mapa). Un elite del que se puede prepararse da decisión; uno que sorprende da frustración.
- **Recompensa distinta y con riesgo:** que el elite dé algo que no encontrás en otro lado (reliquia de elite), de modo que la decisión de ir o no al elite sea significativa en el mapa.

**Cómo saber si funcionó:** los playtesters cambian de plan antes o durante un elite, y las tasas de victoria varían por tipo de elite (si todos los elites ganan igual, siguen siendo el mismo).

### Prioridad 4: que el mapa y los eventos sean decisiones de verdad

- Nodos con **riesgo/recompensa variable** (evento con maldición a cambio de reliquia, tienda con descuento pero lejos, descanso vs. mejora).
- **Caminos con identidad:** un camino con más elites y mejores recompensas, otro seguro y pobre. Hoy, si el mapa no deja ver diferencias, el jugador no decide, deriva.
- **Eventos que dependan del mazo o las reliquias** (el jugador con mazo de ataque ve otras opciones que el de defensa). Esto conecta sistemas entre sí: es lo que produce situaciones que nadie escribió a mano.

### Prioridad 5: novedad al abrir el acto 2 (para la habituación)

- Introducí **una regla nueva por acto** (un tipo de enemigo con mecánica nueva, un recurso nuevo, un tipo de nodo nuevo), de a una, para que el modelo mental crezca sin sobrecargarse.
- **Metas implícitas:** reliquias o logros que invitan a jugar distinto (ganar sin quitar cartas, ganar sin atacar un turno), para que el jugador se ponga metas propias.
- **Ritmo:** acto 2 con picos de tensión (elite, evento de riesgo) seguidos de alivio (descanso, tienda), no una línea plana.

## Orden de trabajo recomendado

1. **Medir** (1 sesión): tasa de victoria por arquetipo, daño recibido, oro acumulado por acto, uso de la tienda. Sin esto, cualquier número es una apuesta.
2. **Prioridad 2 (tienda)** es la más barata y la más segura: agregar sumideros casi no puede empeorar el juego. Hacela primero o en paralelo a la medición.
3. **Prioridad 1 (dominante)** es la que cambia el juego; probala con un prototipo de una pregunta: "si el acto 2 tiene enemigos con escalado, ¿el ataque puro sigue ganando?".
4. **Prioridad 3 (elites)** una vez que el balance base ya no está roto; si no, estás diseñando elites sobre una dominante.
5. **Prioridades 4 y 5** después, con playtests.

**Un solo cambio por tanda de playtest**, así sabés qué lo movió. Ojo con los "fixes that fail": una reducción al ataque puro puede mandar a todos hacia el segundo mazo más fuerte, que pasa a ser el nuevo dominante. Si pasa, la causa no es la carta, es el entorno que la premia.

## Qué prototipar primero

Un solo experimento: **un acto 2 con 3 elites nuevos con reglas distintas y una tienda con "quitar carta" + 2 reliquias caras**, y comparar contra el actual con la misma cantidad de playtesters. Observá: (a) si cambian de mazo entre peleas, (b) cuánto oro les queda, (c) qué dicen del elite antes de pelearlo.

## Qué me quedó abierto

- Cuánto oro entra por acto y qué precios tiene hoy la tienda (necesito los números para proponer cifras concretas).
- Si hay más de una clase o personaje, y cómo se reparten las cartas.
- Si el ataque puro gana por velocidad o por falta de presión de los enemigos (cambia si el arreglo es escalado o daño).
