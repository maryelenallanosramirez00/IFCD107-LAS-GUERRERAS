# Autoevaluación y coevaluación · «Herramientas internas»

**Para qué sirve:** antes de entregar, cada persona se puntúa a sí misma (**autoevaluación**) y valora el trabajo de otra persona o equipo (**coevaluación**, durante la *review*). Se puntúa con la rúbrica del reto (en [Entrega y rúbrica](entrega_y_rubrica.md)), de 1 a 4.

**Cómo se rellena y se sube (sin instalar nada):** cada persona entrega **su propio archivo**, con su cuenta de GitHub. Es el mismo procedimiento que el del entregable ([guía completa: cómo subir a GitHub](../../../../material/5.%20Como_entregar_en_GitHub.md)).

1. **Consigue el texto de este archivo.** Elige una de las dos formas:
   - **Copiar:** en la página del archivo pulsa el botón **Raw** (arriba a la derecha, junto a los iconos del archivo). Se abre el texto sin formato: pulsa `Ctrl + A` (seleccionar todo) y `Ctrl + C` (copiar).
   - **Descargar:** pulsa los **tres puntos ⋯** (arriba a la derecha) → **Download**. Cambia el nombre del archivo descargado a `autoevaluacion_nombre.md` (ver el paso 3) y salta al paso 2b.
2. Entra en el repositorio de tu equipo → carpeta `sprint-04/` y, según lo que hayas hecho en el paso 1:
   - **2a (copiado):** **Add file → Create new file**, escribe el nombre (paso 3) y pega el texto con `Ctrl + V`.
   - **2b (descargado):** **Add file → Upload files**, arrastra tu archivo ya renombrado y pulsa **Commit changes**. Después ábrelo y pulsa el lápiz ✏️ para rellenarlo.
3. **Nombre del archivo:** `autoevaluacion_nombre.md`, con tu nombre, en minúsculas, sin espacios ni tildes (por ejemplo `autoevaluacion_marta.md`). Si dos personas usan el mismo nombre, la segunda borra lo de la primera.
4. Sustituye los `……` por tus respuestas **sin borrar las barras `|` de las tablas**. Para ver cómo queda, pulsa **Preview**.
5. Pulsa **Commit changes**, escribe un mensaje corto («Subo mi autoevaluación») y confirma. **Sin ese botón no se guarda nada.**
6. Para completarlo en otro momento: abre tu archivo → lápiz ✏️ → cambia → **Commit changes**.

**Quién rellena qué:**
- **Parte 1 (autoevaluación):** la rellenas tú sobre **tu** trabajo y el de tu equipo.
- **Parte 2 (coevaluación):** la rellenas tú, en **tu mismo archivo**, sobre el trabajo de **la persona o el equipo que te toca revisar** (el docente te lo indica en la *review*). No escribas en el archivo de otra persona: cada cual sube lo suyo, y vuestra revisión se la comentáis también de palabra.

Volver a [Entrega y rúbrica](entrega_y_rubrica.md).

---

## 1. Autoevaluación (cada persona, unos 5 minutos)

**Nombre:** Cande

**Repaso rápido** (son las comprobaciones de «Antes de cerrar el sprint» del [README del sprint](../../README.md); contesta Sí / No / A medias):

| Pregunta 													| Mi respuesta |
|---|---|
| ¿`python test_kpis.py` termina con todas las pruebas superadas?						| SI |
| ¿`python kpis.py reservas_turisdata.csv salida.json` genera el JSON con los tres KPIs y la sección `calidad`? | SI |
| ¿El programa informa con claridad si falta el fichero o una columna? 						| SI |
| ¿Todas las funciones tienen docstring y siguen PEP 8? 							| SI |
| ¿El README explica cómo ejecutar, cómo probar y qué significa cada KPI? 					| SI |
| ¿Hay al menos 3 commits con mensajes claros y sin claves ni datos personales? 				| SI |
| ¿Otra persona ha revisado el código con la rúbrica? 								| NO |

**Puntúate de 1 a 4** en cada criterio de la rúbrica:

| Criterio 				| Mi puntuación (1–4) | Por qué (una frase) | Qué haría para subir un punto |
|---|---|---|---|
| Corrección técnica 			| 3 | Las funciones devuelven los resultados esperados y el programa devuelve exit code 0 o 1 según el caso. | Revisar el estilo PEP 8 (espacios sobrantes) y quitar el código repetido. |
| Reproducibilidad 			| 3 | Cualquiera puede ejecutar el comando del README con el CSV en la misma carpeta. | Pegar en el README la salida real del script para poder compararla. |
| Análisis y comunicación al cliente 	| 3 | Los KPIs están definidos, pero faltan conclusiones sobre lo que significan los números. | Escribir una frase por KPI interpretando el resultado para el cliente. |
| IA responsable 			| 3 | No hemos usado la IA | Utilizar la IA para mejorar |

- **Lo que más me costó fue gestionar los errores en leer_reservas con try/except, porque no entendía cómo se pasa un error de una función a otra.**
- **He usado IA para ……, y lo que he comprobado a mano es ……**

*Nombre:** Elena

**Repaso rápido** (son las comprobaciones de «Antes de cerrar el sprint» del [README del sprint](../../README.md); contesta Sí / No / A medias):

| Pregunta 													| Mi respuesta |
|---|---|
| ¿`python test_kpis.py` termina con todas las pruebas superadas?						| SI |
| ¿`python kpis.py reservas_turisdata.csv salida.json` genera el JSON con los tres KPIs y la sección `calidad`? | SI |
| ¿El programa informa con claridad si falta el fichero o una columna? 						| SI |
| ¿Todas las funciones tienen docstring y siguen PEP 8? 							| SI |
| ¿El README explica cómo ejecutar, cómo probar y qué significa cada KPI? 					| SI |
| ¿Hay al menos 3 commits con mensajes claros y sin claves ni datos personales? 				| SI |
| ¿Otra persona ha revisado el código con la rúbrica? 								| NO |

**Puntúate de 1 a 4** en cada criterio de la rúbrica:

| Criterio 				| Mi puntuación (1–4) | Por qué (una frase) | Qué haría para subir un punto |
|---|---|---|---|
| Corrección técnica 			| 3 | Las funciones devuelven los resultados esperados y el programa devuelve exit code 0 o 1 según el caso. | Revisar el estilo PEP 8 (espacios sobrantes) y quitar el código repetido. |
| Reproducibilidad 			| 3 | Cualquiera puede ejecutar el comando del README con el CSV en la misma carpeta. | Pegar en el README la salida real del script para poder compararla. |
| Análisis y comunicación al cliente 	| 3 | Los KPIs están definidos, pero faltan conclusiones sobre lo que significan los números. | Escribir una frase por KPI interpretando el resultado para el cliente. |
| IA responsable 			| 3 | No hemos usado la IA | Utilizar la IA para mejorar |

- **Lo que más me costó fue gestionar los errores en leer_reservas con try/except, porque no entendía cómo se pasa un error de una función a otra.**
- **He usado IA para ……, y lo que he comprobado a mano es ……**

*Nombre:** Marisol

**Repaso rápido** (son las comprobaciones de «Antes de cerrar el sprint» del [README del sprint](../../README.md); contesta Sí / No / A medias):

| Pregunta 													| Mi respuesta |
|---|---|
| ¿`python test_kpis.py` termina con todas las pruebas superadas?						| SI |
| ¿`python kpis.py reservas_turisdata.csv salida.json` genera el JSON con los tres KPIs y la sección `calidad`? | SI |
| ¿El programa informa con claridad si falta el fichero o una columna? 						| SI |
| ¿Todas las funciones tienen docstring y siguen PEP 8? 							| SI |
| ¿El README explica cómo ejecutar, cómo probar y qué significa cada KPI? 					| SI |
| ¿Hay al menos 3 commits con mensajes claros y sin claves ni datos personales? 				| SI |
| ¿Otra persona ha revisado el código con la rúbrica? 								| NO |

**Puntúate de 1 a 4** en cada criterio de la rúbrica:

| Criterio 				| Mi puntuación (1–4) | Por qué (una frase) | Qué haría para subir un punto |
|---|---|---|---|
| Corrección técnica 			| 3 | Las funciones devuelven los resultados esperados y el programa devuelve exit code 0 o 1 según el caso. | Revisar el estilo PEP 8 (espacios sobrantes) y quitar el código repetido. |
| Reproducibilidad 			| 3 | Cualquiera puede ejecutar el comando del README con el CSV en la misma carpeta. | Pegar en el README la salida real del script para poder compararla. |
| Análisis y comunicación al cliente 	| 3 | Los KPIs están definidos, pero faltan conclusiones sobre lo que significan los números. | Escribir una frase por KPI interpretando el resultado para el cliente. |
| IA responsable 			| 3 | No hemos usado la IA | Utilizar la IA para mejorar |

- **Lo que más me costó fue gestionar los errores en leer_reservas con try/except, porque no entendía cómo se pasa un error de una función a otra.**
- **He usado IA para ……, y lo que he comprobado a mano es ……**

*Nombre:** Montse

**Repaso rápido** (son las comprobaciones de «Antes de cerrar el sprint» del [README del sprint](../../README.md); contesta Sí / No / A medias):

| Pregunta 													| Mi respuesta |
|---|---|
| ¿`python test_kpis.py` termina con todas las pruebas superadas?						| SI |
| ¿`python kpis.py reservas_turisdata.csv salida.json` genera el JSON con los tres KPIs y la sección `calidad`? | SI |
| ¿El programa informa con claridad si falta el fichero o una columna? 						| SI |
| ¿Todas las funciones tienen docstring y siguen PEP 8? 							| SI |
| ¿El README explica cómo ejecutar, cómo probar y qué significa cada KPI? 					| SI |
| ¿Hay al menos 3 commits con mensajes claros y sin claves ni datos personales? 				| SI |
| ¿Otra persona ha revisado el código con la rúbrica? 								| NO |

**Puntúate de 1 a 4** en cada criterio de la rúbrica:

| Criterio 				| Mi puntuación (1–4) | Por qué (una frase) | Qué haría para subir un punto |
|---|---|---|---|
| Corrección técnica 			| 3 | Las funciones devuelven los resultados esperados y el programa devuelve exit code 0 o 1 según el caso. | Revisar el estilo PEP 8 (espacios sobrantes) y quitar el código repetido. |
| Reproducibilidad 			| 3 | Cualquiera puede ejecutar el comando del README con el CSV en la misma carpeta. | Pegar en el README la salida real del script para poder compararla. |
| Análisis y comunicación al cliente 	| 3 | Los KPIs están definidos, pero faltan conclusiones sobre lo que significan los números. | Escribir una frase por KPI interpretando el resultado para el cliente. |
| IA responsable 			| 3 | No hemos usado la IA | Utilizar la IA para mejorar |

- **Lo que más me costó fue gestionar los errores en leer_reservas con try/except, porque no entendía cómo se pasa un error de una función a otra.**
- **He usado IA para ……, y lo que he comprobado a mano es ……**


---

## 2. Coevaluación (durante la review, unos 10 minutos)

**Trabajo revisado de (persona o equipo):** todas **Revisado por (yo):** todas

**¿Está lo que pide el reto?** Marca ✔ (sí), ✘ (no) o — (no procede).

| Entregable (nómbralo) 	| ¿Está y se entiende? 	| Comentario breve |
|---|---|---|
| kpis				| ✔ 			| 	Todas las funciones tienen docstring y el código se entiende. |
| readme.md		   	| ✔ 			| Explica cómo ejecutar, cómo probar y qué significa cada KPI. |
| salida.json y test_kpis.py  	| ✔ 			| 	El JSON incluye los tres KPIs y la sección calidad, y las pruebas se ejecutan. |

**Puntuación (1–4) de quien revisa:**

| Criterio 				| Puntuación 	| Comentario breve |
|---|---|---|
| Corrección técnica 			| 3 		| He ejecutado las pruebas y pasan; hay algún detalle de estilo PEP 8 por mejorar. |
| Reproducibilidad 			| 3 		| Con el comando del README he obtenido el mismo JSON. |
| Análisis y comunicación al cliente 	| 3 		| Se entienden los KPIs y sus límites, pero faltan conclusiones con los resultados reales. |
| IA responsable 			| 1 		| No hemos utilizado la IA |

- **Lo que está muy bien:** Me ha ayudado que el README explique cada KPI con su fórmula y sus limitaciones, y que los mensajes de error sean claros.
- **Lo que yo cambiaría, y por qué:** Yo añadiría una conclusión con los resultados reales, porque así el cliente entendería mejor qué canal cancela más.

> Se valora el **trabajo**, no a la persona. Frases que ayudan: «Me ha ayudado que …», «Yo cambiaría … porque …».
