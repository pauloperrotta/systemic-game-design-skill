# Documento de sistema: loops de tu juego de supervivencia en una isla

Versión 0.1. Pensado para que lo sigas de arriba hacia abajo, solo, en Unity.

## 0. Resumen en 30 segundos

- **Por qué se siente como lista de tareas:** tus cuatro verbos (juntar, craftear, dormir, repetir) forman una **línea**, no un **loop con decisiones**. Cada paso desbloquea el siguiente y nada vuelve hacia atrás ni cambia la situación. La noche es un reloj con bichos que aparecen, no un sistema que responda a lo que hiciste. Dormir es un botón: no hay decisión, porque no hay una opción que cueste algo. Los recursos salen a tasa fija y todos cuestan lo mismo de conseguir, así que no hay nada que "leer".
- **Loop núcleo propuesto:** la **expedición**. Salís de la base con una intención, decidís hasta dónde llegar sabiendo que la mochila, la luz y la energía se acaban, y volvés antes de que te cueste caro. Lo que traés cambia la base. Lo que hacés en la isla cambia a los bichos. Lo que hacen los bichos cambia lo que te espera afuera y adentro.
- **Cómo logra que "pasen cosas que no programaste":** los bichos, los recursos y las estructuras comparten un vocabulario chico de **señales** (luz, ruido, olor) y de **recursos** (comida, madera). Cada uno emite y percibe, y reacciona con reglas locales y genéricas. Las historias salen de ahí (sección 6).

## 1. Supuestos que hice (corregime lo que no cierre)

1. Juego en 3D en primera o tercera persona, **un jugador**, sin multijugador. Tiempo real.
2. La fantasía es "náufrago que convierte una isla hostil en un lugar que conoce y domina". La experiencia buscada es **tensión de salir y alivio de volver**, con la sensación de que la isla es un sitio vivo que no existe solo para vos.
3. Isla chica o mediana, de **3 a 5 zonas** (costa, bosque, pantano, montaña, cueva) a distancias crecientes de la base.
4. Un día completo dura unos **16 minutos reales** (10 de día, 2 de atardecer, 4 de noche). Es un valor de partida; vive en un asset editable.
5. Hay una meta de largo plazo (salir de la isla, o construir algo grande). Si todavía no la tenés, está en la sección 8 como decisión pendiente.
6. Estás solo: todo número de este documento es un **punto de partida para probar**, no un resultado de balance. Los marqué como propios, no son del libro.
7. Fuera del alcance de la v1 (para no inflar): sed, temperatura corporal, clima, estaciones, construcción libre pieza a pieza. Entran después, uno por vez (sección 9).

## 2. Diagnóstico de tu versión actual

| Lo que ves en el playtest | Causa estructural | Qué lo corrige |
|---|---|---|
| "Junto, crafteo, duermo, repito" | **Proceso complicado**, no complejo: pasos en secuencia sin retorno. Lo que pasa en el paso 4 no cambia el paso 1 | Cerrar loops: que lo que hacés vuelva a afectar lo que hay que hacer (ecología, desgaste, agotamiento local) |
| Recolectar no requiere pensar | Recursos con fuente inagotable y tasa fija, sin costo de oportunidad | Stocks locales que se agotan, distancia, mochila y luz como freno |
| Craftear es "completar un checklist" | Conversor sin trade-off: la receta siempre conviene y no hay variantes | Herramientas que se desgastan (sumidero), variantes con trade-off, conocimiento que se descubre |
| La noche no importa | El ciclo es un **reloj**, no un sistema. Los bichos son una amenaza con script, no una parte que responda | Que la noche cambie **qué criaturas actúan y qué se puede hacer**, y que sea una opción además de un castigo |
| Dormir es trámite | Decisión ilusoria: no tiene costo ni riesgo, no abre ni cierra opciones | Que dormir avance el mundo y que la calidad del refugio importe |
| Todos los días iguales | Recompensa a tasa fija: habituación | Variación que sale del estado del mundo (qué agotaste, a quién cazaste), no de tablas de eventos |

Esto no se arregla con más contenido. El contenido nuevo (más recursos, más recetas) en una línea sigue siendo una línea más larga.

## 3. Los loops, uno por uno

Tipos usados: **motor** (mismo recurso), **economía** (se intercambian recursos distintos con ganancia no lineal), **ecología** (balance por intercambio). R es refuerzo, B es balance.

### 3.1 Mapa general (cómo se conectan)

```
                      ┌─────────────────── L6 CONOCIMIENTO (largo plazo) ◀─────────────┐
                      │ desbloquea zonas, recetas, comportamiento de criaturas          │
                      ▼                                                                 │
 [Isla: nodos de recursos]──stock──▶ L2 EXPEDICIÓN (núcleo, 3-8 min) ──trae──▶ L3 BASE Y CRAFTEO
        ▲   regeneran lento                │  ▲                                  │ (economía + motor)
        │                                  │  │ frenos: mochila, luz,            │ produce: herramientas,
        │                                  │  │ energía, hambre                  │ comida, estructuras
        │                                  ▼  │                                  │
        │                       L5 CUERPO (hambre, fatiga, vida)◀──── comida ─────┘
        │                                  ▲
        │                                  │ dormir/descansar (decisión)
        │                                  │
        └──── consumen / compiten ◀── L4 ECOLOGÍA (criaturas: herbívoros, depredadores, carroñeros)
                                           ▲   ▲
                    señales (luz, ruido,   │   │ cazar / cultivar / cocinar / talar
                    olor) que emiten       │   │ alteran quién tiene qué comida
                    las estructuras y tus  │   │
                    acciones ──────────────┘   │
                                               │
                      L1 ACCIÓN (segundos): moverse, golpear, huir  ──────┘
                      L7 TIEMPO (día/noche): cambia qué especies actúan y la luz del mundo
```

Regla del diseño: **cada flecha tiene que existir en el juego como un efecto que el jugador pueda ver**. Si una conexión es solo teórica, sacala.

### 3.2 L1. Acción / feedback (segundos, 3 s)

- Moverse, recolectar un nodo, golpear, esquivar, huir.
- Tipo: loop interactivo rápido. Tiene que ser **limpio y con feedback inmediato (100 a 250 ms)**: golpe al árbol suena y se ve; el nodo muestra cuánto le queda de forma visual, no con un número.
- Lo importante: **no cargarlo de decisiones estratégicas**. Lo rápido expulsa a lo lento. Cuando hay un bicho encima, no tiene que haber que pensar la receta.

### 3.3 L2. Expedición (el loop núcleo, 3 a 8 minutos)

Es el loop que ocupa la atención la mayor parte del tiempo. Es un **braking engine** (los frenos son lo que lo hace un juego) combinado con una **economía de riesgo y recompensa**.

```
(intención: "necesito X")──▶<Decisor: ¿a qué zona voy y cuánto me alejo?>
        ▼
 explorar ──▶ leer el terreno (rastros, nodos, bichos) ──▶ recolectar
        ▼                                    ▲
 [frenos B1]: mochila llena (peso), luz del día baja, energía/hambre,
              herramienta que se rompe, bichos que aparecen
        ▼
 <Decisor: ¿sigo o vuelvo?> ──▶ vuelvo a la base con lo que traje
```

- **Recurso que circula:** materias primas y tiempo de luz.
- **Decisión del jugador:** a qué zona ir, cuánto cargar, cuánto alejarse, cuándo volver. Es la decisión central y tiene incertidumbre real: no sabés qué hay hasta que llegás (pero la lees por rastros, ver 5.4).
- **Gradiente de riesgo y recompensa:** cuanto más lejos de la base, mejores recursos y más peligro. Si esto no está, no hay decisión.
- **Fricción (freno) del loop:**
  - **Peso:** la mochila tiene tope en kg. Madera 2 kg, piedra 3 kg, mineral 5 kg. Capacidad inicial 20 kg.
  - **Luz del día:** si te agarra la noche lejos, la zona cambia (sección 3.7).
  - **Fatiga y hambre:** suben mientras exploras (sección 3.6).
  - **Desgaste de herramientas:** cada uso resta durabilidad (sumidero).
- **Cómo falla y cómo se evita:**
  - *Deadlock:* para hacer el primer hacha hace falta una piedra y un palo. Solución: **recolectar con las manos siempre es posible**, más lento y con menos rendimiento. Nunca hay un recurso que necesites para conseguir el recurso inicial.
  - *Espiral de muerte:* si morís y perdés todo, no podés recuperarte. Solución: al morir dejás la mochila en el lugar (recuperable) y la base siempre guarda un kit mínimo.
  - *Expedición sin riesgo real:* si lo de cerca alcanza para todo, nadie se aleja. Para eso está el sumidero de la sección 3.4 (el bosque cercano se agota).

### 3.4 L3. Base y crafteo (economía y motor, baja tensión)

Es la contracara de baja tensión de la expedición. Acá el jugador **consolida y planifica**. Mezcla economía (conversión con ganancia no lineal) y motor de impulso (¿gasto lo que traje o lo invierto en producir más?).

```
 materias primas ──▶{Conversor: taller, fogata, banco}──▶ herramientas / comida / estructuras
                                    │
          <Decisor: ¿lo gasto ahora o lo invierto en capacidad?>
              ├─▶ uso inmediato (herramienta para la próxima expedición)
              └─▶ inversión (cultivo, trampas, cerca, taller mejor) ──▶ más flujo pasivo (R2)
 [Sumideros]: herramientas que se rompen, comida que se pudre, combustible de la fogata,
              estructuras que se dañan por bichos
```

- **Recursos que circulan:** madera, piedra, fibra, comida cruda y cocida, herramientas, estructuras.
- **No linealidad:** la comida cocida rinde mucho más que la cruda (ejemplo propio: cruda 20 de saciedad y se pudre en medio día; cocida 45 y dura un día y medio). Una herramienta de hueso o piedra afilada cosecha más rápido pero se rompe antes. Hay mejoras que desbloquean zonas más ricas.
- **Decisión del jugador:** gastar vs invertir (un cultivo rinde mañana pero atrae herbívoros hoy), qué herramienta fabricar (variantes con trade-off, ver tabla 5.2), qué defender.
- **Frenos / sumideros (obligatorios):**
  - Todo se gasta o se pudre. Nada es permanente.
  - Combustible: la fogata quema leña. Ejemplo propio: 0,5 leños por hora de juego de noche, o sea unos 5 leños por noche.
  - **Agotamiento local (tragedia de los comunes):** los árboles cercanos tienen stock chico y regeneración lenta. Con 6 árboles de 5 leños y una regeneración de 1 leño por árbol por día, producen 6 por día, y la base solo con la fogata ya consume 5. En pocos días el bosque cercano no alcanza y hay que alejarse. Este desajuste es **deliberado**: empuja el loop núcleo.
- **Cómo falla:** *runaway* si una vez que tenés cultivo y taller todo sobra y ya no salís. Freno: los bichos cambian con el territorio que dominás (3.5), el cultivo se vuelve el blanco de las criaturas, y las mejoras fuertes piden recursos que sólo hay lejos.

### 3.5 L4. Ecología de criaturas (el sistema que hace que pasen cosas)

Es lo que reemplaza "de noche aparecen bichos". Las criaturas **viven en la isla y tienen necesidades**: hambre, territorio y percepción. No aparecen por un timer, **están ahí y actúan según lo que perciben**.

```
 plantas / nodos ──comida──▶ (Herbívoros) ──carne──▶ (Depredadores) ──cadáveres──▶ (Carroñeros)
        ▲   B: herbívoros comen plantas → menos comida → menos herbívoros
        │   B: depredadores comen herbívoros → menos presas → menos depredadores
        └── R: más herbívoros → más reproducción (mientras haya comida)
 JUGADOR perturba esto: caza herbívoros, cultiva, cocina (olor), prende fuego (luz), hace ruido
```

- **Tipo:** ecología, balance por intercambio con loops de refuerzo adentro (la reproducción).
- **Cantidad de especies: tres o más, impar.** Con solo dos (presa/depredador) oscila de forma poco interesante y el jugador es un tercero que la rompe. Con tres (herbívoro, depredador, carroñero/plaga) hay más intersecciones. Propongo arrancar con **3 especies**.
- **Qué hace que sea "ecología" y no "enemigos con script":**
  - Cada criatura tiene **hambre** y busca la **fuente de comida más fuerte según lo que percibe** (olor, ruido, vista).
  - Se reproducen si hay comida abundante y se reducen si no hay.
  - Algunas especies son nocturnas, otras diurnas: eso cambia **quién** está activo según la hora, no cuántos "enemigos" spawnean.
- **El jugador es una parte más:** es comida para el depredador, compite con el herbívoro por las plantas, y es el que más ruido, luz y olor produce. Pero **perturba sin determinar**: cazar un herbívoro quita una presa y reduce la reproducción futura, pero cómo responde el depredador (muere de hambre, migra hacia tu base) lo decide él.
- **Cómo falla y cómo se evita:**
  - *Colapso:* si el jugador caza todo, la ecología se vacía y no hay ni comida ni peligro. Freno: **fuentes de repoblación lentas** (la reproducción de herbívoros vuelve con más tiempo), y que cazar excesivamente tenga consecuencias (depredadores sin presas vienen a tu base).
  - *Estatismo:* si todo está tan balanceado que no pasa nada. Freno: no clavar valores fijos; dejar que las poblaciones oscilen dentro de un rango y que el jugador las empuje.
  - *Estrategia dominante* (por ejemplo una trampa que mata todo sin costo). Cada defensa tiene un costo de mantenimiento y una señal que atrae a otro tipo de criatura.

### 3.6 L5. Cuerpo (supervivencia, balance)

- **Hambre**, **fatiga** y **vida**. Son tres stocks con drenajes (hambre sube con el tiempo y el esfuerzo; fatiga con actividad) y recuperación (comer, descansar).
- **Rol:** son el freno de la expedición (ya descripto) y la razón de que la base sea necesaria. No son un minijuego de mantenimiento: si el jugador se descuida, no muere de un golpe, **pierde capacidad** (se mueve más lento, carga menos), lo que lo empuja a volver.
- **Dormir como decisión real (arregla el "duermo"):**
  - Descansar restaura fatiga, pero **la noche sigue corriendo**: dormir avanza el reloj, así que las criaturas actúan sin vos.
  - La **calidad del refugio** (cerca, fogata, trampas, ruido que hacés) decide si despertás con la base intacta o con daños, comida robada o heridas.
  - Podés **no dormir** y aguantar con fatiga alta, con penalización progresiva. Entonces la noche es un espacio que elegís usar: crafteo en la base, defensa, o salir a por recursos nocturnos.

### 3.7 L7. Tiempo (día y noche) como regulador del ecosistema

El ciclo día/noche **no es un loop de gameplay propio**, es el **ritmo** que cambia los parámetros de todos los demás:

| Fase | Qué cambia en el mundo | Qué hace el jugador típicamente |
|---|---|---|
| Día (10 min) | Especies diurnas activas, luz alta, nodos de superficie disponibles | Expedición (L2) |
| Atardecer (2 min) | La luz baja, algunas criaturas empiezan a moverse | **Decisión de volver**: punto de tensión |
| Noche (4 min) | Especies nocturnas activas, visibilidad baja, aparecen nodos exclusivos (hongos, peces luminosos) | Base (L3: cocinar, craftear, defender) **o** salida arriesgada con alta recompensa |

- **La noche es una opción con precio**, no solo un castigo. Eso la convierte en decisión.
- Pasa lo que ya sabés del patrón de alta tensión (expedición, noche afuera) y baja tensión (base): el cambio entre ambos es el ritmo natural del juego, y evita la fatiga del jugador.

### 3.8 L6. Conocimiento y exploración (largo plazo, meta)

- **El conocimiento es un recurso:** recetas descubiertas, mapa revelado, bestiario (qué come, cuándo sale, qué teme cada especie).
- Se obtiene **haciendo y observando**, no con un árbol de puntos: usar un material nuevo, observar a una criatura sin que te vea, entrar a una zona nueva.
- Desbloquea: nuevas zonas accesibles (necesitás herramienta o conocimiento para entrar), recetas, y la **meta explícita** (salir de la isla, o construir X).
- **Metas implícitas** que el jugador se pone: "domar" una zona, cultivar sin que me roben, sobrevivir una noche entera afuera. No las programes, dales espacio.
- Esto es lo que evita que el juego termine cuando "ya crafteaste todo".

## 4. Resumen de loops y de sus frenos

| Loop | Tipo | Refuerzo (R) | Freno (B) | Decisión central |
|---|---|---|---|---|
| L1 Acción | Interactivo rápido | n/a | Energía, vida | Moverse, esquivar, golpear |
| L2 Expedición | Braking engine + riesgo/recompensa | Mejor equipo y conocimiento permiten ir más lejos | Mochila, luz, fatiga, hambre, desgaste, bichos | ¿Hasta dónde y cuándo vuelvo? |
| L3 Base | Economía + motor | Cultivo, taller, estructuras producen más | Pudrición, combustible, desgaste, daño de bichos | ¿Gasto o invierto? ¿Qué defiendo? |
| L4 Ecología | Ecología | Reproducción | Hambre, depredación, territorio | (indirecta) Qué perturbo y cuánto |
| L5 Cuerpo | Balance | n/a | Comer y descansar | ¿Duermo? ¿Aguanto? |
| L6 Conocimiento | Progresión | Saber más abre zonas y recetas | Hay que hacer y arriesgarse para saber | ¿Qué exploro o qué pruebo? |
| L7 Tiempo | Regulador | n/a | Alterna tensión y alivio | ¿Vuelvo o sigo? |

## 5. Las partes (nivel planilla)

Principio: **pocos atributos, genéricos, con rangos enteros**. Cada atributo nuevo es una nueva forma de desbalancear. Una fila por parte, una columna por atributo, en una hoja por tipo de parte. En Unity: un **ScriptableObject por parte** (o CSV importado) para que puedas tocar números sin recompilar.

### 5.1 Vocabulario compartido (lo que hace posible la emergencia)

Todas las partes hablan con las mismas pocas **señales** y **recursos**. Esto es lo más importante del documento.

| Señal / recurso | Rango | Quién la emite | Quién la percibe |
|---|---|---|---|
| **Luz** | 0 a 10 | Sol/luna (global), fogata, antorcha, hongos | Criaturas (les atrae o repele), el jugador (visión) |
| **Ruido** | 0 a 10 | Talar, picar, correr, trampas, combate | Criaturas (curiosidad o huida) |
| **Olor** | 0 a 10 | Comida cruda/cocinada, cadáveres, cultivo, el jugador herido | Criaturas con olfato |
| **Comida** (recurso) | stock | Plantas, cultivos, cadáveres, carne | Criaturas y jugador |

Decisión de diseño: **no agregues una señal nueva por cada idea**. Si necesitás otra, primero preguntate si no se resuelve con una de estas. Más señales hacen el sistema más caro de entender para el jugador (y de testear para vos).

### 5.2 Hojas de partes

**Hoja A. Jugador (cuerpo)**

| Atributo | Rango / tipo | Notas |
|---|---|---|
| Vida | 0 a 100, entero | Cero = muerte (dejás la mochila) |
| Hambre | 0 a 100 (100 = lleno) | Baja ~1 por minuto de juego; más rápido corriendo |
| Fatiga | 0 a 100 (100 = agotado) | Sube con la actividad. A partir de 70: carga máxima -20% y velocidad -15% (proponer, probar) |
| Capacidad de carga | kg, entero (inicial 20) | Mejorable con equipo |
| Visión | derivado de Luz local | No es atributo propio |

| Comportamiento | Efecto | Feedback |
|---|---|---|
| Recolectar | Resta stock al nodo; suma ítem; emite Ruido; resta durabilidad a la herramienta | Sonido y animación; el nodo se achica |
| Comer / beber | Sube Hambre según Nutrición del ítem | Barra de saciedad, sonido |
| Dormir | Baja Fatiga, **avanza el tiempo del mundo**; el resultado depende del refugio | Pantalla, resumen de lo que pasó |
| Atacar / huir | Daño a una criatura; emite Ruido | Impacto, sacudida |
| Observar | Revela atributos de una criatura/nodo (conocimiento) | Entrada en el bestiario |

**Hoja B. Nodo de recurso** (árbol, roca, arbusto de bayas, veta, charco)

| Atributo | Rango / tipo | Notas |
|---|---|---|
| Tipo | enum | madera, piedra, fibra, baya, mineral, pesca... |
| Stock | 0 a Máx | Cuántas unidades quedan |
| Máx | 1 a 10 | |
| Regeneración | unidades/día (0 a 2) | Solo si Stock >= 1 |
| Herramienta mínima | enum | "manos" siempre es válida (evita deadlock) |
| Zona | ref. | Determina distancia a la base |

| Comportamiento | Efecto |
|---|---|
| Ser recolectado | Resta Stock; si llega a 0 pasa a "agotado" y tarda 3 días en volver a 1 |
| Regenerar | Suma Regeneración/día mientras Stock >= 1 y no agotado |
| Emitir Olor | Las bayas y frutas emiten Olor 2 y atraen herbívoros |

**Hoja C. Ítems** (materiales, herramientas, comida)

| Atributo | Rango / tipo | Notas |
|---|---|---|
| Peso | 0,1 a 20 kg | Fuerza a decidir qué llevar |
| Durabilidad | 0 a 100 usos (herramientas) | Llega a 0 = se rompe y sale del juego |
| Nutrición | 0 a 60 | Solo comida |
| Olor | 0 a 10 | Cocinada emite más |
| Vida útil | horas de juego (comida) | Pasado el tiempo se pudre (sumidero) |

Herramientas de ejemplo (números propios, para arrancar; la lógica es que **ninguna sea mejor en todo**):

| Herramienta | Velocidad de cosecha | Durabilidad | Peso | Costo | Idea |
|---|---|---|---|---|---|
| Palo/manos | 1x | infinita | 0 | gratis | Siempre disponible |
| Hacha de piedra | 2x | 40 | 2 kg | 1 palo, 2 piedras, 1 fibra | Barata, se rompe rápido |
| Hacha de hueso | 2,5x | 25 | 1 kg | Hueso (requiere cazar) | Más rápida y liviana, se gasta antes y depende de la ecología |
| Hacha de metal | 3x | 120 | 4 kg | Mineral (zona lejana) | Cara, pesada, dura. Justifica ir lejos |

**Hoja D. Criatura**

| Atributo | Rango / tipo | Notas |
|---|---|---|
| Especie / Dieta | enum: planta, carne, carroña | Quién come qué |
| Hambre | 0 a 100 | Sube con el tiempo; < 30 puede reproducirse; > 70 busca comida activamente |
| Vida | 1 a 100 | |
| Daño | 0 a 30 | |
| Velocidad | 1 a 10 | |
| Actividad | día / noche / ambas | |
| Percepción | radio 5 a 40 m y sentidos (vista, olfato, oído) | Qué señales detecta y desde dónde |
| Reacción a la Luz | -5 a +5 | + huye, - se siente atraída |
| Reacción al Ruido | -5 a +5 | |
| Territorio | zona | Dónde se queda y a dónde migra si hay hambre |
| Fecundidad | 0 a 10 | Reproducción por día cuando hay comida y poco hambre |

| Comportamiento (genérico, todos los usan) | Efecto |
|---|---|
| Percibir | Lee las señales dentro de su radio, ponderadas por distancia y sentido |
| Elegir objetivo | Va hacia la comida más fuerte (señal / distancia); si el Hambre es baja, ignora |
| Comer | Resta comida al objetivo (planta, cadáver, ítem del jugador) y baja su Hambre |
| Huir / evitar | Se aleja de lo que le dé miedo (Luz, Ruido) según sus reacciones |
| Atacar | Si el objetivo es un ser vivo y el Hambre supera un umbral: perturba Vida del objetivo |
| Reproducirse | Si Hambre < 30 y comida cerca: +Fecundidad cada día |
| Morir | Suelta un cadáver (comida, Olor alto, hueso) |

Tres especies de partida (nombres a tu gusto, los atributos son lo que cuenta):

| | Herbívoro (cabra/jabalí) | Depredador (zorro/lobo) | Carroñero/plaga (cangrejo/rata) |
|---|---|---|---|
| Dieta | planta | carne | carroña, y comida abandonada |
| Actividad | día | noche | noche |
| Reacción a la Luz | +2 (huye) | +1 | -3 (atraído) |
| Percibe | vista, olfato (plantas) | olfato, oído | olfato |
| Daño | 3 (se defiende) | 15 | 2 (pero roba) |
| Efecto en el jugador | Fuente de carne y hueso | Peligro físico | Roba y pudre comida, daña estructuras de madera |

**Hoja E. Estructura de base**

| Atributo | Rango / tipo | Notas |
|---|---|---|
| Función | enum | luz, protección, conversión, almacén, cultivo, refugio |
| Durabilidad | 0 a 100 | Los bichos la dañan |
| Consumo | recurso/hora | Combustible |
| Señal emitida | Luz/Ruido/Olor | Por ejemplo fogata: Luz 6 de noche; cocinando Olor 8 |
| Radio de efecto | m | |

Ejemplos: **fogata** (Luz 6, consume leña, convierte comida cruda en cocida con Olor 8), **cerca** (bloquea movimiento de herbívoros y plagas, no de depredadores grandes; cuesta mantenimiento), **cultivo** (produce comida pasiva, Olor 2, atrae herbívoros), **trampa** (daño a criatura que pasa; hace Ruido al activarse), **refugio** (calidad de descanso, protege al durmiente).

**Hoja F. Zona**

| Atributo | Rango / tipo | Notas |
|---|---|---|
| Distancia a la base | 0 a 4 | Sube riesgo y valor |
| Densidad de nodos | 0 a 10 por tipo | |
| Especies presentes | lista con población | Viva: cambia con la ecología |
| Riesgo base | 0 a 10 | Derivado de especies, no escrito a mano |
| Recursos exclusivos | lista | Obliga a ir |

**Hoja G. Tiempo**

| Atributo | Rango | Notas |
|---|---|---|
| Hora | 0 a 24 | |
| Luz ambiente | 0 a 10 | Entrada para las criaturas y la visión |
| Fase | día / atardecer / noche | |

### 5.3 Revisión de "cada parte afecta y es afectada"

| Parte | Afecta a | Es afectada por |
|---|---|---|
| Jugador | Nodos (los agota), criaturas (caza, Ruido, Luz, Olor), estructuras (las construye y usa) | Hambre y fatiga, criaturas, desgaste de herramientas |
| Nodo | Jugador (materia prima), herbívoros (comida) | Jugador (cosecha), tiempo (regeneración), herbívoros (comen) |
| Criatura | Jugador (daño, robo), nodos (comen), estructuras (dañan), otras criaturas (comen) | Luz, Ruido, Olor, hambre, otras criaturas |
| Estructura | Criaturas (con sus señales), jugador (descanso, conversión) | Criaturas (daño), jugador (combustible, mantenimiento) |
| Zona | Criaturas y nodos (qué hay) | Ecología (poblaciones), jugador (lo que sacó) |
| Tiempo | Todo (Luz, actividad) | Jugador (dormir lo avanza) |

Ninguna parte tiene conexión de una sola vía. Si al implementar descubrís una, buscá el retorno.

## 6. Emergencia esperada (para verificar en playtest)

Si el diseño es sistémico, estas situaciones deberían aparecer **sin que programes ninguna de ellas**. Si no aparecen, algo del diseño está mal.

1. **La carne atrae lo que no querías.** Cazás un herbívoro y cocinás en la fogata de noche: Olor 8 atrae al carroñero (Luz -3 lo atrae también) y a un depredador. Elegís entre apagar el fuego (perdés luz y calor de cocina), defender, o comer crudo.
2. **Migración por sobrecaza.** Cazás mucho herbívoro en la zona cercana: los depredadores se quedan sin presas, su hambre sube y buscan comida más fuerte: tu base. Noches más duras sin un evento programado.
3. **Tragedia del bosque cercano.** Tu consumo de leña supera la regeneración. Nadie "te manda" a explorar más lejos: el stock cercano se agota solo. Cuando salís lejos aparecen riesgos nuevos.
4. **El cultivo es un arma de doble filo.** Un cultivo produce comida estable, pero emite Olor y atrae herbívoros, que a su vez atraen depredadores. Decidís entre vallar (mantenimiento), cazar (ruido) o no cultivar.
5. **Herramienta rota lejos.** Se te rompe el hacha de piedra a mitad de expedición con la mochila a medio llenar. Improvisás con manos (más lento) o volvés. No hay script; es desgaste más distancia.
6. **La noche como oportunidad.** Un jugador con buen refugio y fogata decide salir de noche a buscar hongos y peces luminosos, y se juega la luz de la antorcha contra los carroñeros. Es una historia que el diseño permite, no que cuenta.

## 7. Orden de despliegue (complejidad que se despliega)

No muestres todo de golpe. El modelo mental se arma de a un sistema.

| Etapa | Qué ve y puede hacer el jugador | Sistemas activos |
|---|---|---|
| 1. Primeros 10 min | Recolectar con las manos, hacer un hacha, ir al bosque y volver. La noche trae un bicho | L1, L2 mínimo (un solo tipo de nodo, mochila, luz) |
| 2. Primer día completo | Fogata, comida cocinada, dormir con riesgo | L3 básica, L5, L7 |
| 3. Primeros días | Aparece el segundo bioma, herbívoros y depredador visibles | L4 con 2 especies, gradiente de distancia |
| 4. Semana | Cultivo, cerca, trampas, carroñero | L3 completa, L4 con 3 especies, emergencia (sección 6) |
| 5. Medio y largo plazo | Zonas lejanas, bestiario, meta explícita | L6 |

Regla: **una novedad por vez**. Cada sistema nuevo se introduce cuando el anterior ya se entendió.

## 8. Asuntos abiertos (decisiones tuyas)

1. **Meta de largo plazo.** ¿Salir de la isla (armar una balsa o señal), construir algo, sobrevivir N días? Es lo que da dirección al loop L6.
2. **¿Combate directo con las criaturas o más bien evasivo?** Cuanto más acción, menos presupuesto mental queda para planificar. Mi recomendación: **combate corto y de riesgo**, no el centro del juego.
3. **¿Permadeath, penalización parcial o sin muerte?** Propuesto: perdés la mochila en el lugar (recuperable) y respawneás en la base.
4. **Estética de la información.** Cuánto mostrar del estado de las criaturas (hambre, territorio). Recomiendo mostrarlo con **rastros visibles** (huellas, restos, sonidos) antes que con números.
5. **Escala de la isla y cantidad de criaturas** por zona: afecta el rendimiento en Unity y la legibilidad de la ecología. Empezá con pocas (5 a 15 por zona) y variá.

## 9. Qué construir primero (prototipos de una pregunta)

Rápidos, feos, descartables. **Una pregunta por prototipo**; no migres el código del prototipo al juego.

| # | Pregunta | Qué incluye (y nada más) | Qué observar |
|---|---|---|---|
| P1 | ¿Salir lejos y volver antes del atardecer genera tensión y decisión? | Terreno plano con cubos, base, 2 tipos de nodos (cerca/pobre, lejos/rico), mochila con peso, luz que baja | ¿Vuelven apurados? ¿Hay quien arriesga y quien no? ¿Se aburren cerca? |
| P2 | ¿La ecología mínima genera historias? | 3 especies (cápsulas de colores) con hambre y percepción por señales, una fogata y una fuente de comida | ¿Aparecen los casos 1, 2 y 4 de la sección 6 sin tocar nada? ¿Se entiende por qué pasó? |
| P3 | ¿Dormir y la noche son decisiones o trámites? | Refugio con calidad, dormir avanza el tiempo, criaturas actúan | ¿Hay quien elige no dormir? ¿Quien duerme afuera? |
| P4 | ¿El crafteo con trade-offs y desgaste evita el checklist? | Las 4 herramientas de la tabla 5.2 | ¿Alguien usa siempre la misma? (dominante) ¿Alguien se queda sin herramienta? |

Cómo testear: pocos tests cortos (10 a 20 min), con personas que no conozcan el juego, **sin explicarles nada**, y anotando dónde se confunden y qué historias cuentan al terminar. Preguntá "¿qué intentabas hacer?" y "¿qué esperabas que pasara?". Leé el feedback buscando **problemas**, no las soluciones que propongan. Si cuentan una historia que vos no programaste, es la señal más fuerte de que el sistema funciona.

Medí también por código desde el principio: días de supervivencia, distancia máxima alcanzada por expedición, ratio de expediciones que vuelven antes del atardecer, población de cada especie por día (¿oscila o colapsa?), herramientas rotas por día, y qué receta se usa más (dominancia).

## 10. Riesgos principales y su freno (checklist final)

- **Runaway del jugador con la base** (todo sobra, no sale más): agotamiento del bosque cercano, mejoras que piden recursos lejanos, bichos que atacan lo que construiste.
- **Espiral de muerte**: kit mínimo en la base, mochila recuperable, manos siempre válidas.
- **Ecología que colapsa o se estanca**: repoblación lenta, depredadores que migran, sin valores fijos. Vigilá poblaciones con un gráfico de debug.
- **Estrategia dominante** (una trampa, un arma, una receta): variantes con trade-off, mantenimiento y señal que atrae a otro tipo.
- **Demasiadas reglas o señales**: no sumes señales; si el jugador no entiende por qué pasó algo, bajá el número de reglas en vez de agregar texto.
- **Sobrecarga**: separar en el tiempo lo rápido (acción) de lo lento (planificar en la base).
- **Alcance**: la lista de partes es el alcance. Si un sistema no apoya el loop núcleo, no entra (sed, clima y estaciones esperan a que P1 a P4 funcionen).

## 11. Qué te recomiendo hacer mañana

1. Decidí las 3 preguntas abiertas más baratas: meta, muerte y combate (sección 8).
2. Armá **P1** en un día o dos con cubos. Si la tensión de "salgo y vuelvo antes del atardecer" no aparece ahí, ni el mejor crafteo lo va a arreglar.
3. Recién después **P2**. Es el que justifica todo el enfoque.
