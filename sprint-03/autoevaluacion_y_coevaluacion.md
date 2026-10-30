# Autoevaluación y coevaluación · «Primer modelo en producción»

**Para qué sirve:** antes de entregar, cada persona se puntúa a sí misma (**autoevaluación**) y valora el trabajo de otra persona o equipo (**coevaluación**, durante la *review*). Se puntúa con la rúbrica del reto (criterios de evaluación de la [ficha del reto](Reto_Sprint_03.md)), de 1 a 4.

**Cómo se rellena y se sube (sin instalar nada):** cada persona entrega **su propio archivo**, con su cuenta de GitHub. Es el mismo procedimiento que el del entregable ([guía completa: cómo subir a GitHub](../../../material/5.%20Como_entregar_en_GitHub.md)).

1. **Consigue el texto de este archivo.** Elige una de las dos formas:
   - **Copiar:** en la página del archivo pulsa el botón **Raw** (arriba a la derecha, junto a los iconos del archivo). Se abre el texto sin formato: pulsa `Ctrl + A` (seleccionar todo) y `Ctrl + C` (copiar).
   - **Descargar:** pulsa los **tres puntos ⋯** (arriba a la derecha) → **Download**. Cambia el nombre del archivo descargado a `autoevaluacion_nombre.md` (ver el paso 3) y salta al paso 2b.
2. Entra en el repositorio de tu equipo → carpeta `sprint-03/` y, según lo que hayas hecho en el paso 1:
   - **2a (copiado):** **Add file → Create new file**, escribe el nombre (paso 3) y pega el texto con `Ctrl + V`.
   - **2b (descargado):** **Add file → Upload files**, arrastra tu archivo ya renombrado y pulsa **Commit changes**. Después ábrelo y pulsa el lápiz ✏️ para rellenarlo.
3. **Nombre del archivo:** `autoevaluacion_nombre.md`, con tu nombre, en minúsculas, sin espacios ni tildes (por ejemplo `autoevaluacion_marta.md`). Si dos personas usan el mismo nombre, la segunda borra lo de la primera.
4. Sustituye los `……` por tus respuestas **sin borrar las barras `|` de las tablas**. Para ver cómo queda, pulsa **Preview**.
5. Pulsa **Commit changes**, escribe un mensaje corto («Subo mi autoevaluación») y confirma. **Sin ese botón no se guarda nada.**
6. Para completarlo en otro momento: abre tu archivo → lápiz ✏️ → cambia → **Commit changes**.

**Quién rellena qué:**
- **Parte 1 (autoevaluación):** la rellenas tú sobre **tu** trabajo y el de tu equipo.
- **Parte 2 (coevaluación):** la rellenas tú, en **tu mismo archivo**, sobre el trabajo de **la persona o el equipo que te toca revisar** (el docente te lo indica en la *review*). No escribas en el archivo de otra persona: cada cual sube lo suyo, y vuestra revisión se la comentáis también de palabra.

Volver a la [ficha del reto](Reto_Sprint_03.md).

---

## 1. Autoevaluación (cada persona, unos 5 minutos)

**Nombre:** Marisol

**Repaso rápido** (las mismas preguntas del final de la ficha del reto; contesta Sí / No / A medias):

| Pregunta | Mi respuesta |
|---|---|
| ¿El informe tiene las tres partes y cabe en 4 páginas? 				|SI|
| ¿La métrica y el umbral están explicados en lenguaje de negocio? 			|SI|
| ¿Hay evidencia de una llamada a la API (petición y respuesta), sin credenciales? 	|SI|
| ¿Explicamos qué variables hemos excluido y por qué?					|SI|
| ¿Hemos cerrado y eliminado todos los recursos y lo demostramos? 			|SI|
| ¿Hay al menos dos riesgos de IA responsable y una medida? 				|SI|
| ¿Otra persona ha revisado el informe con la rúbrica? 					|SI|

**Nombre:** Cande

**Repaso rápido** (las mismas preguntas del final de la ficha del reto; contesta Sí / No / A medias):

| Pregunta | Mi respuesta |
|---|---|
| ¿El informe tiene las tres partes y cabe en 4 páginas? 				|SI|
| ¿La métrica y el umbral están explicados en lenguaje de negocio? 			|SI|
| ¿Hay evidencia de una llamada a la API (petición y respuesta), sin credenciales? 	|SI|
| ¿Explicamos qué variables hemos excluido y por qué?					|SI|
| ¿Hemos cerrado y eliminado todos los recursos y lo demostramos? 			|SI|
| ¿Hay al menos dos riesgos de IA responsable y una medida? 				|SI|
| ¿Otra persona ha revisado el informe con la rúbrica? 					|SI|

**Nombre:** Elena

**Repaso rápido** (las mismas preguntas del final de la ficha del reto; contesta Sí / No / A medias):

| Pregunta | Mi respuesta |
|---|---|
| ¿El informe tiene las tres partes y cabe en 4 páginas? 				|SI|
| ¿La métrica y el umbral están explicados en lenguaje de negocio? 			|SI|
| ¿Hay evidencia de una llamada a la API (petición y respuesta), sin credenciales? 	|SI|
| ¿Explicamos qué variables hemos excluido y por qué?					|SI|
| ¿Hemos cerrado y eliminado todos los recursos y lo demostramos? 			|SI|
| ¿Hay al menos dos riesgos de IA responsable y una medida? 				|SI|
| ¿Otra persona ha revisado el informe con la rúbrica? 					|SI|

**Nombre:** Montse

**Repaso rápido** (las mismas preguntas del final de la ficha del reto; contesta Sí / No / A medias):

| Pregunta | Mi respuesta |
|---|---|
| ¿El informe tiene las tres partes y cabe en 4 páginas? 				|SI|
| ¿La métrica y el umbral están explicados en lenguaje de negocio? 			|SI|
| ¿Hay evidencia de una llamada a la API (petición y respuesta), sin credenciales? 	|SI|
| ¿Explicamos qué variables hemos excluido y por qué?					|SI|
| ¿Hemos cerrado y eliminado todos los recursos y lo demostramos? 			|SI|
| ¿Hay al menos dos riesgos de IA responsable y una medida? 				|SI|
| ¿Otra persona ha revisado el informe con la rúbrica? 					|SI|





**Puntúate de 1 a 4** en cada criterio de la rúbrica:

| Criterio 				| Mi puntuación (1–4) | Por qué (una frase) | Qué haría para subir un punto |
|---|---|---|---|
| Corrección técnica 			| 3 | Hemos seleccionado LightGBM como modelo y trabajado en la interpretación de sus métricas y resultados. | Profundizar en la validación del modelo con datos reales posteriores y comprobar su rendimiento en producción. |
| Reproducibilidad 			| 3 | Hemos documentado el proceso y aportado evidencias de la llamada a la API y del funcionamiento del modelo. | Mejorar la documentación técnica para que cualquier persona pueda repetir el proceso sin dificultades. |
| Análisis y comunicación al cliente 	| 3 | Hemos explicado los resultados del modelo y relacionado las métricas con las necesidades del negocio. | Profundizar en el análisis de costes reales, umbrales y diferencias de rendimiento por país y canal. |
| IA responsable			| 3 | Hemos identificado riesgos relacionados con el uso de IA y planteado medidas para reducirlos. | Concretar más las medidas de control, seguimiento y detección de posibles sesgos. |

- **Lo que más me costó fue comprender e interpretar las métricas técnicas y relacionarlas con las decisiones de negocio, porque necesitaba entender cómo afectan los resultados del modelo a la empresa.**
- **He usado IA para ayudarme a comprender conceptos técnicos, organizar información y redactar partes del informe, y lo que he comprobado a mano es la coherencia de los resultados, las métricas y las decisiones tomadas en el proyecto.**

---

## 2. Coevaluación (durante la review, unos 10 minutos)

**Trabajo revisado de (persona o equipo):** ……  **Revisado por (yo):** ……

**¿Está lo que pide el reto?** Marca ✔ (sí), ✘ (no) o — (no procede).

| Entregable (nómbralo) | ¿Está y se entiende? | Comentario breve |
|---|---|---|
| Informe del modelo predictivo | ✔ | Presenta las partes solicitadas y explica la elección del modelo y sus resultados. |
| Evidencia de funcionamiento de la API | ✔ | Se muestra una petición y su respuesta, permitiendo comprobar el funcionamiento del servicio. |
| Documentación de IA responsable y cierre de recursos | ✔ | Se identifican riesgos y medidas de prevención, además de documentar el cierre de los recursos. |

**Puntuación (1–4) de quien revisa:**

| Criterio 				| Puntuación | Comentario breve |
|---|---|---|
| Corrección técnica 			| 3 | El modelo está bien seleccionado y los resultados se explican correctamente. |
| Reproducibilidad 			| 3 | La documentación y las evidencias permiten comprender los pasos realizados. |
| Análisis y comunicación al cliente 	| 3 | Los resultados se presentan de forma comprensible y relacionados con el objetivo del negocio. |
| IA responsable 			| 3 | Se contemplan riesgos y medidas para conseguir un uso responsable del modelo. |

- **Lo que está muy bien:** Me ha gustado que el equipo haya sabido aplicar los conocimientos adquiridos durante el reto y que haya utilizado un modelo predictivo para dar respuesta a una necesidad real del negocio. Además, la presentación de los resultados facilita entender el trabajo realizado.
- **Lo que yo cambiaría, y por qué:** Añadiría más ejemplos prácticos sobre cómo se utilizarían las predicciones para tomar decisiones en la empresa, porque así sería más fácil comprender el valor real del modelo y cómo puede ayudar a mejorar los resultados.

> Se valora el **trabajo**, no a la persona. Frases que ayudan: «Me ha ayudado que …», «Yo cambiaría … porque …».
