# Balance de armas y curva de XP/monedas

**Diagnóstico en una frase:** no está balanceado. Con tus números hay un arma mal costeada (Escopeta, dominada), otra casi inútil en un solo objetivo (Lanzacohetes), y la economía no tiene sumideros ni curva: es lineal en recompensas, con precios fijos. Todas las monedas se gastan antes del nivel 14 y después la moneda no sirve para nada.

## Supuestos (los declaro porque no me los diste)

- Todas las balas impactan (precisión 100%). Es el techo teórico de cada arma.
- No hay HP de enemigos ni dato de armadura. Comparo armas entre sí, no contra enemigos.
- Escopeta: 8 de daño x 6 perdigones = 48 por disparo si todos pegan.
- Lanzacohetes: promedio de 2,5 enemigos dentro del área.
- Recurso central = daño por segundo al enemigo (es lo que el jugador maximiza para sobrevivir). Todo se mide contra eso.
- Los niveles llegan hasta ~20.

## 1. Cuentas de las armas

Fórmulas:
- DPS ráfaga = daño por disparo x balas por segundo.
- Ciclo = cargador / cadencia + recarga.
- DPS sostenido = daño x cargador / ciclo. **Este es el que importa**, porque la recarga cuenta.

| Arma | DPS ráfaga | Tiempo disparando | Ciclo | DPS sostenido | Daño por cargador | Precio | Precio / DPS sost. |
|---|---|---|---|---|---|---|---|
| Pistola | 40 | 3,0 s | 4,0 s | **30,0** | 120 | 0 | 0 |
| Subfusil | 72 | 2,5 s | 4,3 s | **41,9** | 180 | 300 | 7,2 |
| Escopeta | 57,6 | 5,0 s | 7,5 s | **38,4** | 288 | 450 | 11,7 |
| Rifle | 70 | 5,0 s | 7,0 s | **50,0** | 350 | 600 | 12,0 |
| Minigun | 100 | 10,0 s | 15,0 s | **66,7** | 1000 | 1200 | 18,0 |
| Lanzacohetes | 60 | 2,0 s | 5,0 s | **24,0** (x2,5 en área = 60) | 120 | 1500 | 62,5 |

### Dominantes e inútiles

1. **Escopeta: dominada.** Cuesta 450 y rinde 38,4 contra 41,9 del Subfusil, que cuesta 300. Es peor en ráfaga (57,6 vs 72) y en sostenido, y más cara. Solo la salvaría la mecánica de cercanía (perdigones que pegan más cerca), y no la declaraste. Con tus números nadie debería comprarla.
2. **Subfusil: dominante en valor.** Por 300 monedas pasa de 30 a 41,9 DPS (+40%). Es la mejor relación precio/DPS de las armas de pago, por lejos (7,2 vs 12 o más del resto). Es la compra obligada y casi nadie pasará de ahí por eficiencia.
3. **Rifle: caro para lo que da.** Sube 19% de DPS sobre el Subfusil por el doble de precio. Solo se justifica por el daño por impacto (35), que importa contra enemigos con armadura. Si no hay armadura en el juego, el Rifle es una mala compra.
4. **Minigun: coherente pero con un costo oculto.** Tiene el DPS más alto (66,7), pero 5 s de recarga y un cargador de 10 s de fuego sin recargar. Su precio 1200 es consistente con una curva cúbica del DPS (ver abajo), así que lo dejo casi igual.
5. **Lanzacohetes: inútil contra un solo enemigo.** 24 DPS sostenido: peor que la Pistola gratis (30), por 1500. Solo vale con grupos. Si tus oleadas tienen 1 o 2 enemigos a la vez, es una trampa de precio.
6. **Pistola:** es gratis y rinde 30 DPS, 72% del Subfusil. Está bien como base, pero el salto a la primera compra (+40%) es chico.

**Causa raíz, en vocabulario de sistemas:** los precios no siguen una curva de costo-beneficio. La ley es: más beneficio tiene que costar proporcionalmente más, y ninguna parte puede tener más valor y menos costo que otra. Aquí el orden de precio (SMG < Escopeta < Rifle < Minigun < Cohete) no coincide con el orden de valor (Escopeta < SMG < Rifle < Minigun, y el Cohete depende del contexto). Eso es dominancia, y se corrige en el origen: moviendo costos, no agregando armas que la compensen.

## 2. Método para valuar y costear (repetible)

Esto es el método de "Mod Value" y costo manual (Sellers, cap. 10), aplicado a tu caso.

**Paso 1: elegí el recurso central.** Daño por segundo al enemigo.

**Paso 2: ordená los atributos por cadena causal hacia ese recurso.** Para llegar al daño hace falta, en orden: poder disparar (cargador y recarga), la cadencia, y el daño por bala. El DPS sostenido ya combina los tres. Le sumo dos cosas que el DPS solo no ve: la ráfaga (quien mata rápido recibe menos daño) y el daño por impacto (vale contra armadura).

**Paso 3: Mod Value (valor calculado).** Fórmula que propongo:

`MV = 0,6 x DPS sostenido + 0,4 x DPS ráfaga + 0,15 x daño por impacto + bono de área`

Bono de área = DPS sostenido x (objetivos - 1) x 0,5. El Cohete usa 2,5 objetivos. Los pesos son una primera hipótesis: el 0,6 pone el peso mayor en el sostenido, que es el más ligado al recurso central. Los otros se ajustan jugando.

| Arma | MV |
|---|---|
| Pistola | 35,5 |
| Escopeta | 47,3 |
| Subfusil | 54,8 |
| Rifle | 63,2 |
| Lanzacohetes | 74,4 |
| Minigun | 80,8 |

**Paso 4: elegí una pieza ancla y una curva.** Uso el Rifle como ancla (queda en 600, su precio actual). La relación MV a precio la tomo cúbica:

`precio = 600 x (MV / MV_rifle)^3`

Con exponente 3, un arma con 30% más de valor cuesta ~2,2 veces más. El exponente lo elegí mirando que el Minigun cae casi en su precio actual (1249 vs 1200); si querés una escalera más suave, bajalo a 2,5.

**Paso 5: el precio final se fija a mano, no es el calculado.** Armas flojas un poco por debajo del valor (para entrar) y las de punta un poco por encima (aspiracional). Después verificás la regla de oro: el orden por MV coincide con el orden por precio.

### Tabla corregida de precios

| Arma | MV | Precio calculado | **Precio propuesto** | Cambio |
|---|---|---|---|---|
| Pistola | 35,5 | 106 | **0** | igual |
| Escopeta | 47,3 | 251 | **250** | 450 a 250 |
| Subfusil | 54,8 | 391 | **400** | 300 a 400 |
| Rifle | 63,2 | 600 | **600** | igual (ancla) |
| Lanzacohetes | 74,4 | 977 | **1000** | 1500 a 1000 |
| Minigun | 80,8 | 1249 | **1250** | 1200 a 1250 |

Total para tener todo: 3500 monedas (antes 4050).

**Dos cambios que son de stats, no de precio** (porque el precio solo no arregla un arma sin nicho):

- **Escopeta:** a 250 deja de ser dominada en precio, pero sigue sin un lugar propio. Dale uno: los perdigones hacen +50% de daño a menos de 3 m, o 7 perdigones. Si pasa a 8x7 rinde 44,8 DPS sostenido, y entonces subí su precio a ~350. Es una decisión de diseño: o es barata y flaca, o es cara y con rol de corto alcance.
- **Lanzacohetes:** su valor es el área. Asegurate de que existan oleadas de 3 o más enemigos agrupados; si no, el arma no tiene sentido a ningún precio. Alternativa: bajá la recarga a 2,0 s (DPS sostenido 28,6).

Asunto abierto: si agregás armadura o precisión a los enemigos, hay que recalcular los pesos (el 0,15 del daño por impacto subiría).

## 3. Economía y curva de XP

### Qué está pasando con tus números

- Enemigos necesarios por nivel = 100n / 10n = **10 en todos los niveles**. Siempre 10 kills por nivel. Subir de nivel nunca se siente más lejano ni más cerca: una curva plana de esfuerzo que se vuelve rutinaria (fatiga hedónica).
- Monedas por nivel = 10 kills x 5n = **50n**, lineal. Monedas acumuladas hasta el nivel n = 25n(n+1): nivel 3 = 300, nivel 7 = 1400, nivel 10 = 2750, nivel 13 = 4550.
- Con precios fijos y sin otros gastos, **tenés todas las armas (4050) antes del nivel 13** y desde ahí las monedas no sirven. Es inflación: fuentes crecientes (5n por kill), sumideros que son una lista finita y de un solo uso. Y los primeros niveles son lentos: el Subfusil recién llega al nivel 3.
- Ojo: ¿el desafío crece con n? Si los enemigos del nivel n tienen HP proporcional a n pero tus armas no mejoran, hay un desajuste (los desafíos suben y el poder no). No me diste el HP, así que lo dejo como pendiente: la regla es que la base de la curva de desafío y la de poder sean parecidas.

### Curva propuesta

La regla: el umbral crece más rápido que lo que da cada kill, así los kills por nivel suben suave y el jugador siente que cada nivel pide algo más. Exponenciales con bases cercanas:

- XP para pasar de n a n+1: `req(n) = 100 x 1,25^(n-1)`
- XP por enemigo del nivel n: `xp(n) = 10 x 1,15^(n-1)`
- Monedas por enemigo: `oro(n) = 5 x 1,15^(n-1)` (misma base que el XP, así las recompensas suben a la par)
- Kills por nivel: req / xp = 10 x (1,25/1,15)^(n-1) = 10 x 1,087^(n-1). Va de 10 a ~49 en el nivel 20.

Por qué estas bases: 1,25 duplica el umbral cada ~3,1 niveles (ln 2 / ln 1,25). La base de 1,15 en la recompensa mantiene el crecimiento del esfuerzo moderado. Si las subís juntas, el ritmo no cambia; si abrís la brecha entre ambas, el juego se hace más lento o más rápido.

| Nivel n | XP para subir | XP por kill | Kills por nivel | Monedas por kill | Monedas por nivel | Monedas acumuladas |
|---|---|---|---|---|---|---|
| 1 | 100 | 10,0 | 10 | 5,0 | 50 | 50 |
| 3 | 156 | 13,2 | 12 | 6,6 | 79 | 193 |
| 5 | 244 | 17,5 | 14 | 8,7 | 122 | 414 |
| 7 | 381 | 23,1 | 17 | 11,6 | 197 | 771 |
| 10 | 745 | 35,2 | 22 | 17,6 | 387 | 1704 |
| 13 | 1455 | 53,5 | 28 | 26,8 | 749 | 3543 |
| 15 | 2274 | 70,8 | 33 | 35,4 | 1167 | 5633 |
| 20 | 6939 | 142,3 | 49 | 71,2 | 3487 | 17366 |

Comparación con tu curva: hasta el nivel 10 se acumulan 1704 monedas (antes 2750). Esto es a propósito: las monedas iniciales cuestan más trabajo y las armas se sienten ganadas. Con la tabla de precios nueva, el Subfusil (400) llega cerca del nivel 5 y el Rifle (600) cerca del nivel 7.

### Sumideros: sin esto, la curva sola no alcanza

Aun con la curva nueva, el total de armas (3500) se cubre al nivel 13 de 20, y del 14 al 20 el jugador junta ~13.800 monedas sin nada que comprar. Las recompensas crecientes exigen sumideros crecientes. Propuesta:

1. **Mejoras por arma, con costo creciente.** Cada mejora +20% de daño (o -15% de recarga). Costo de la mejora k de un arma: `0,5 x precio_del_arma x 1,8^(k-1)`, con 4 mejoras por arma. Un arma completa cuesta 0,5 x p x (1+1,8+3,24+5,83) = ~5,9 x p. Sumando todas las armas: ~20.700 monedas, muy parecido a los 17.366 que se generan hasta el nivel 20. El jugador no puede mejorarlo todo y tiene que elegir qué arma potenciar: esa es la decisión significativa.
2. **Munición o reparación como sumidero chico y continuo** (opcional): por ejemplo 10% del oro ganado. Evita el atesoramiento.
3. **Consistencia de precios:** si hay venta de armas usadas, el precio de recompra nunca puede superar el de compra (si no, hay arbitraje y se infla la moneda).

## 4. Cómo repetirlo vos (pasos)

1. Hoja de cálculo: una fila por arma; columnas daño, cadencia, cargador, recarga, precio.
2. Calculá DPS ráfaga, ciclo y DPS sostenido (fórmulas arriba). Calculá precio / DPS.
3. Armá el MV con pesos (empezá con los míos) y ordená por MV. Chequeá que el orden por precio sea el mismo. Todo arma con más valor y menos precio que otra es dominante: arreglala bajando su valor o subiendo su precio.
4. Elegí un ancla y una curva `precio = P_ancla x (MV/MV_ancla)^k`, con k entre 2 y 3.
5. Fijá el precio a mano alrededor del calculado (un poco abajo en lo barato, un poco arriba en lo caro).
6. Para la progresión: elegí una base para el umbral (`req = B x A^(n-1)`) y otra más chica para la recompensa por kill. Kills por nivel = req / xp. Mirá que la curva de kills suba suave (idealmente 10 a 50, no 10 a 500).
7. Listá fuentes (oro por kill) y sumideros (armas, mejoras, munición) y compará los totales por nivel. Si las fuentes acumuladas superan por mucho los sumideros, agregá sumideros.
8. Cambiá una variable a la vez y recalculá.

## 5. Qué validar jugando

- ¿Qué arma elige cada jugador en la primera compra? Si más del ~70% elige la misma, hay una dominante.
- ¿Cuánto tarda cada nivel en minutos reales? Medí el rango (mínimo y máximo), no solo el promedio. Una curva con niveles de 2 min y otros de 20 min se siente injusta.
- ¿Cuántas monedas tiene sin gastar el jugador promedio en el nivel 10 y en el 15? Más de 2 compras grandes acumuladas = faltan sumideros.
- ¿Dónde abandonan? Si cae más de ~50% entre checkpoints consecutivos, es una alarma de dificultad.
- Los números encuentran lo más desbalanceado, no la perfección: usá esta tabla como punto de partida e iterá con playtest.
