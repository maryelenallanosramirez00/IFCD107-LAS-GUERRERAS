# Dictamen · ¿Nos fiamos de este informe?

**Equipo:** …… · **Fecha:** …… · **Personas:** ……

> Copia este archivo a `sprint-02/dictamen.md` del repositorio del equipo y sustituye los `……` (cómo hacerlo: [subir a GitHub sin instalar nada](../../../material/5.%20Como_entregar_en_GitHub.md)). Las cartas de error están en la [ficha del reto](Reto_Sprint_02.md) (paso 2).
> Cómo se evalúa: [rúbrica del dictamen](rubrica_dictamen.md).
> **Veredictos:** fiable · parcialmente fiable · no fiable · no se puede saber. «No se puede saber» es válido: no inventes números.

---

## Afirmación 1 · «La tasa de cancelación global es del 21 %, así que estamos en la media del sector»

- **Carta:** 1 · Comparación sin fuente
- **Veredicto:** parcialmente fiable
- **Por qué:** la cuenta sale, pero «la media del sector» no aparece en ningún dato.
- **Cálculo:** cancelaciones 300 + 70 + 20 + 120 = 510; reservas 2.400; 510 ÷ 2.400 × 100 = **21,25 %**.
- **Cómo debería decirse:** «Nuestra tasa global es del 21,25 % (510 de 2.400 reservas). No tenemos datos del sector para compararla».
- **Qué datos faltan:** la tasa media del sector, con su fuente y su periodo.

*(Este bloque ya está resuelto: es el modelo para los demás.)*

---

## Afirmación 2 · «Las reservas de la web intermediaria se cancelan menos (15,8 %) que las directas (26,7 %)… y por tanto deberíamos priorizar ese canal»

- **Carta:** 2
- **Veredicto:** No fiable

**Tabla de cálculo** (tasa = cancelaciones ÷ reservas × 100):

| Tarifa 		| Canal 	| Reservas 	| Cancelaciones | Tasa (%) |
|---|---|---|---|---|
| flexible 		| directo 	| 1000 		| 300 		| 30% |
| flexible 		| intermediaria | 200 		| 70 		| 35% |
| no reembolsable 	| directo 	| 200		| 20 		| 10% |
| no reembolsable 	| intermediaria | 1000 		| 120 		| 12% |

- **Por qué:** Dentro de cada tarifa, la intermediaria cancela más que el directo. En el total parece menos porque vende sobre todo tarifa no reembolsable, que se cancela menos.
- **Cómo debería decirse:** La intermediaria presenta una tasa de cancelación más alta que el canal directo dentro de cada tipo de tarifa, aunque en el total pueda parecer que cancela menos.
- **Qué datos faltan:** Porcentajes de comisiones y beneficios de cada canal

### Recomendación sobre el canal (tres líneas)
*Recomendamos seguir mirando, porque aunque la intermediaria tiene una tasa global de cancelación menor, dentro de cada tarifa presenta más cancelaciones que el canal directo.
Antes de decidir habría que comparar los ingresos, las comisiones y los beneficios de cada canal.
También conviene analizar los resultados durante varios meses para tomar una decisión más segura.*

---

## Afirmación 3 · «Las reservas con depósito se cancelan menos, por lo que el depósito reduce las cancelaciones».»  *(repite este bloque para cada afirmación que elijas de la 3 a la 6)*

- **Carta:** Muestra pequeña 
- **Veredicto:** No fiable
- **Cálculo** *(si lo hay; la afirmación 6 sí)*: No se puede comprobar con la información disponible, ya que no conocemos el número exacto de reservas con depósito y sin depósito ni sus respectivas cancelaciones.
- **Cómo debería decirse:** En una muestra de 40 reservas de un fin de semana de agosto se observó una posible relación entre el depósito y una menor cancelación, pero no está demostrado que el depósito sea la causa.
- **Qué datos faltan:** El número de reservas con y sin depósito, las cancelaciones de cada grupo, más fines de semana y temporadas, y datos que permitan comparar reservas similares.

## Afirmación 4 · «El 90 % de nuestros clientes está satisfecho»: encuesta enviada solo a clientes que dejaron su correo en la web.»

- **Carta:**  Muestra sesgada 
- **Veredicto:** parcialmente fiable
- **Cálculo:** No hay datos
- **Cómo debería decirse:** El 90 % de los clientes que respondieron a nuestra encuesta está satisfecho. La encuesta se envió únicamente a clientes que dejaron su correo en la web, por lo que los resultados podrían no representar a todos nuestros clientes
- **Qué datos faltan:** no se indica el número total de clientes, cuántos recibieron la encuesta, cuántos respondieron, cuántos estaban satisfechos y si la muestra representa adecuadamente al conjunto de clientes.

## Afirmación 5 · ««Cada vez que sube la temperatura suben las cancelaciones, así que el calor provoca cancelaciones».»

- **Carta:** Correlación no es causa
- **Veredicto:**  Parcialmente fiable
- **Cálculo:** La correlación es de 0,7, lo que indica una relación positiva relativamente fuerte: cuando sube la temperatura, las cancelaciones tienden también a subir. Sin embargo, esto no demuestra que una cosa provoque la otra.
- **Cómo debería decirse:** Los datos muestran una relación positiva entre la temperatura y las cancelaciones, pero no podemos asegurar que el calor sea la causa
- **Qué datos faltan:** Saber si existen otros factores que influyen en las cancelaciones, como la época del año, el tipo de cliente, los precios o los motivos del viaje. También necesitaríamos más datos para comprobar si esta relación se mantiene.

## Afirmación 6 · «Las cancelaciones de este mes (30) han bajado un 25 % respecto al mes pasado (40)»

- **Carta:** Base de comparación distinta
- **Veredicto:** parcialmente fiable
- **Cálculo:** Primero calculamos la diferencia: 40-30=10 cancelaciones menos.
		Después calculamos el porcentaje de reducción respecto al mes pasado: (40-30)/40 *100=25%
		Por tanto, las cancelaciones totales han bajado un 25 %.
- **Cómo debería decirse:** Este mes se han registrado 30 cancelaciones, frente a las 40 del mes pasado: un 25 % menos en total. Sin embargo, como el mes pasado tuvo 31 días de alta ocupación y este mes 28 días de baja ocupación, no podemos afirmar que haya mejorado la situación sin comparar los datos teniendo en cuenta la ocupación
- **Qué datos faltan:** El número total de reservas de cada mes, los días de ocupación y el porcentaje de cancelaciones sobre el total de reservas. Así podremos comparar ambos meses de forma más justa.


---

## IA responsable (una frase)

*Si entrenáramos un modelo con datos incompletos o sesgados, aprendería conclusiones equivocadas, porque los datos no representarían correctamente la realidad.*

## Uso de IA

- ¿Hemos usado IA? Sí. Si sí: **para qué** Para ayudarnos a analizar las afirmaciones del informe, realizar los cálculos y detectar posibles errores en las conclusiones y **qué hemos comprobado a mano** Hemos revisado los porcentajes, las operaciones matemáticas y si las conclusiones están justificadas por los datos disponibles.
