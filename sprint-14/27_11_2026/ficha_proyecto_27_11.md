# Ficha de proyecto (1 página) · Anexo A

**Equipo (nombre de la consultora):** Las Guerreras · **Fecha:** 27/11/2026 · **Versión:** 1

## 1. Equipo y roles iniciales

| Persona | Rol en el Sprint 14 | Rotación prevista (S15 / S16) |
|---|---|---|
| Montse | Scrum Master | Técnica / Datos |
| Cande | Responsable técnico | Datos / IA responsable |
| Marisol | Responsable de datos | IA responsable / Scrum Master |
| Elena | Responsable de IA responsable | Scrum Master / Técnica |

## 2. Brief elegido y pregunta de negocio

- **Brief:** 2 Cultivos.
- **Pregunta de negocio en una frase:** «¿Podemos clasificar fotografías de hojas de tomate para que agricultores y técnicos agrícolas puedan identificar posibles enfermedades y priorizar las plantas que necesitan una inspección profesional?»

## 3. Cliente y decisión que se apoyará

- **Quién usará el resultado:** Agricultores y técnicos agrícolas.
- **Decisión concreta que mejorará** (y qué pasa hoy sin el modelo): Ayudar a identificar de forma preliminar posibles enfermedades en las hojas y priorizar qué plantas revisar primero. Actualmente, la identificación inicial depende de la inspección visual y de la experiencia de la persona. La herramienta será un apoyo orientativo y no sustituirá el diagnóstico de un profesional.

## 4. Datos

| Fuente (enlace) | Licencia | Tamaño | Variables clave | Limitaciones previstas |
|---|---|---|---|---|
| [Hugging Face – mohanty/PlantVillage](https://huggingface.co/datasets/mohanty/PlantVillage). Fuente original: Hughes, D. P. y Salathé, M. (2015), *An open access repository of images on plant health to enable the development of mobile disease diagnostics*. | CC BY-SA 3.0, según la ficha de Hugging Face;  es una licencia libre, reconocida para contenidos y bases de datos, aunque no es una licencia de software.Entrenar modelos de Machine Learning. Utilizarlas con fines comerciales. | PlantVillage: 54.305 imágenes. Subconjunto de tomate: 18.160 imágenes en 10 clases (1 sana y 9 enfermedades): 14.521 para train y 3.639 para test. | `image`, `image_path`, `label` y `leaf_id`. | Imágenes tomadas en condiciones controladas, por lo que pueden diferir de fotografías reales de campo. Posible desbalance entre clases. Hay que comprobar nulos y duplicados tras la descarga y revisar `leaf_id` para evitar fugas de información entre train y test; si corresponde, separar por grupos. |

## 5. Métrica de éxito y baseline

- **Métrica de negocio:**Reducir el tiempo de detección de enfermedades en hojas de tomate en un 30 %, respecto a la inspección visual manual.
- **Métrica técnica:**  F1-macro, para evaluar el rendimiento del modelo en las 10 clases (1 clase sana y 9 enfermedades).
- **Umbral de éxito acordado:**F1-macro ≥ 0,80 y reducción del tiempo de detección ≥ 30 %.
- **Baseline previsto:** DummyClassifier(strategy="most_frequent"), que predice siempre la clase mayoritaria. Resultado obtenido en validación: F1-macro = 0,0442 y accuracy = 0,2834.
- **Partición de los datos:** División por grupos leaf_id, para evitar que imágenes de una misma hoja aparezcan en entrenamiento y validación:
Entrenamiento: 11.513 imágenes (63,4 %)
Validación: 3.013 imágenes (16,6 %)
Test: 3.634 imágenes (20 %)

## 6. Modelos previstos (≥ 3, incluyendo redes neuronales / LLM según el brief)

- **Enfoque elegido y por qué:** Clasificación supervisada de imágenes. Se dispone de 18.160 fotografías de hojas de tomate etiquetadas en 10 clases. Se compararán modelos clásicos y redes neuronales para evaluar su capacidad de distinguir las clases y detectar los errores por enfermedad.
1. **Baseline:** predicción de la clase mayoritaria.
2. **HOG + SVM:** extracción de características visuales HOG y clasificación mediante Support Vector Machine.
3. **CNN sencilla:** red neuronal convolucional entrenada con las imágenes del conjunto de datos.
4. **MobileNetV2:** red neuronal convolucional con transferencia de aprendizaje.

## 7. Demostrador previsto

- **Tecnología:** Streamlit · Gradio · notebook con widgets · API. **Qué hará:** ______
- **Plan B si falla la demo:** vídeo de 90 s.

## 8. Riesgos y mitigación

| Riesgo | Tipo (datos / cómputo / ética / equipo) | Mitigación |
|---|---|---|
| | | |
| | | |
| | | |

*Clasificación preliminar AI Act: ______ · ¿Datos personales? sí / no*

## 9. Backlog inicial (10-15 historias) y objetivo de cada sprint

- **Historias principales:** *(lista corta; el backlog completo está en el tablero)* ______
- **Objetivo S14:** ______ · **Objetivo S15:** ______ · **Objetivo S16:** ______ · **Objetivo S17:** ______

---

**Firmas del equipo (nombres):** ______ · **Respuesta del docente:** ☐ GO ☐ GO con cambios ☐ NO-GO — Comentarios: ______
