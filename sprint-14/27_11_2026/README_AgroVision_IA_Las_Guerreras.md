# AgroVision IA · Las Guerreras

> Proyecto de clasificación de enfermedades en hojas de tomate mediante Inteligencia Artificial.

**Brief:** 2 · Cultivos  
**Curso:** IFCD107 · Especialista en IA  
**Defensa:** día 2 del Sprint 17

## 1. El problema en 3 líneas

- **Pregunta de negocio:** ¿Podemos identificar automáticamente si una hoja de tomate está sana o presenta alguna de las enfermedades contempladas en el conjunto de datos?
- **Decisión que apoya y para quién:** Ayudar a agricultores y personal técnico agrícola a identificar posibles enfermedades en las hojas de tomate y orientar una revisión posterior.
- **Métrica de éxito:**
  - **Negocio:** reducir un 30 % el tiempo de detección de enfermedades respecto a la inspección visual manual.
  - **Técnica:** F1-macro, para evaluar el rendimiento en las 10 clases.
  - **Baseline:** F1-macro = 0,0442 y accuracy = 0,2834, obtenidos con un `DummyClassifier` que predice siempre la clase mayoritaria.

**Umbral de éxito acordado:** F1-macro ≥ 0,80 y reducción del tiempo de detección ≥ 30 %.

## 2. Resultados en una tabla

| Modelo | Métrica principal (validación) | Métrica en test | Tiempo | Notas |
|---|---:|---:|---|---|
| Baseline (`DummyClassifier`) | F1-macro: 0,0442 | Pendiente | Pendiente | Accuracy: 0,2834. Predice siempre la clase mayoritaria. |
| Modelo 1 | [Pendiente Sprint 15] | [Pendiente] | [Pendiente] | [Pendiente] |
| Modelo 2 | [Pendiente Sprint 15] | [Pendiente] | [Pendiente] | [Pendiente] |
| **Candidato final** | [Pendiente Sprint 16] | [Pendiente] | [Pendiente] | [Pendiente] |

El baseline se ha evaluado sobre validación. El conjunto de test se ha reservado para la evaluación final.

El detalle de los experimentos se incorporará en `sprint-15/registro.csv` y la memoria técnica en `sprint-16/docs/memoria_tecnica.pdf`.

## 3. Estructura del repositorio

```text
.
├── README.md
├── requirements.txt                 # [Pendiente]
├── sprint-14/
│   ├── ficha_proyecto.md
│   ├── plan_datos_licencias.md
│   ├── 01_eda.ipynb                  # [Confirmar archivo]
│   ├── 02_baseline.ipynb
│   ├── backlog_y_sprints.md
│   ├── riesgos_eticos.md
│   └── descargar_datos.py            # [Pendiente]
├── sprint-15/
│   ├── registro.csv                  # [Pendiente]
│   ├── 03_modelos.ipynb              # [Pendiente]
│   ├── justificacion_candidato.md    # [Pendiente]
│   └── [Archivos del modelo candidato]
├── sprint-16/
│   ├── README.md                     # Versión final
│   ├── notebooks/
│   │   └── 04_evaluacion.ipynb
│   ├── demostrador/
│   │   ├── logica.py
│   │   ├── app.py
│   │   └── tests/
│   └── docs/
│       ├── memoria_tecnica.pdf
│       ├── model_card.md
│       ├── riesgos_eticos.md
│       └── demo.mp4
└── sprint-17/
    └── presentacion_defensa.pdf
```

Cada sprint incluirá también las hojas de autoevaluación individuales. La coevaluación confidencial del anexo B no se subirá al repositorio.

## 4. Cómo reproducirlo (pasos exactos)

**Requisitos:**
- Python: [Confirmar versión con `!python --version` en Colab].
- Sistema operativo: Google Colab, entorno Linux en la nube.
- GPU: no necesaria para ejecutar el baseline; se determinará para los modelos de clasificación de imágenes.
- Google Colab y el archivo CSV de metadatos.

### Preparación y ejecución

1. Abrir el repositorio del equipo: [Añadir URL del repositorio].
2. Abrir `sprint-14/02_baseline.ipynb` en Google Colab.
3. Subir previamente al panel de archivos de Colab el archivo `plantvillage_tomate_metadata_auditado.csv`.
4. Ejecutar las celdas de arriba abajo. La primera parte del cuaderno busca automáticamente el CSV dentro de `/content`.
5. Comprobar que se carga el conjunto de datos.

**Datos de partida:**
- Archivo: `plantvillage_tomate_metadata_auditado.csv`.
- Registros: 18.160.
- Columnas: 11.
- Clases: 10.
- Semilla fija: `SEMILLA = 42`.

**Partición de datos:**

Se ha conservado el conjunto de test original y se ha dividido el conjunto de entrenamiento mediante `GroupShuffleSplit`, agrupando por `leaf_id` para evitar que imágenes de una misma hoja aparezcan simultáneamente en entrenamiento y validación.

| Conjunto | Imágenes |
|---|---:|
| Entrenamiento | 11.513 |
| Validación | 3.013 |
| Test | 3.634 |
| **Total** | **18.160** |

No existen grupos compartidos entre entrenamiento y validación.

6. Ejecutar la evaluación del `DummyClassifier`.
7. Comprobar las métricas obtenidas: F1-macro = 0,0442 y accuracy = 0,2834.
8. Ejecutar la celda de guardado para generar los archivos CSV de cada partición, los resultados JSON y el archivo comprimido `AgroVision_IA_datos_baseline.zip`.

**Importante:** en una sesión nueva de Colab será necesario volver a subir el CSV si no está guardado en una ubicación persistente.

**Tiempo total aproximado:** [Pendiente de medir].

## 5. Cómo lanzar el demostrador

[Pendiente de desarrollar en el Sprint 16.]

- **Comando de ejecución:** [Pendiente].
- **Dirección de acceso:** [Pendiente].
- **Qué probar:** [Tres imágenes de ejemplo y resultado esperado].
- **Entradas no admitidas y mensaje mostrado:** [Pendiente].
- **Plan B:** [Vídeo demostrativo en `sprint-16/docs/demo.mp4` o enlace].

## 6. Datos y licencias

El proyecto utiliza el conjunto de datos PlantVillage, con imágenes de hojas de tomate, obtenido a través de Hugging Face.

| Conjunto | Fuente | Licencia | ¿Incluido en el repositorio? |
|---|---|---|---|
| PlantVillage (imágenes de hojas de tomate) | [mohanty/PlantVillage en Hugging Face](https://huggingface.co/datasets/mohanty/PlantVillage) | `cc-by-sa-3.0`es una licencia libre, reconocida para contenidos y bases de datos, aunque no es una licencia de software.Entrenar modelos de Machine Learning. Utilizarlas con fines comerciales.| No; se conserva fuera del repositorio. |
| Metadatos auditados | `plantvillage_tomate_metadata_auditado.csv` | creado por el equipo | si |

**Preparación de los datos:**

- El conjunto de datos contiene 18.160 registros en el CSV auditado.
- Se han identificado 10 clases de hojas de tomate.
- Se han detectado 14 duplicados exactos mediante MD5 en la revisión previa de los datos.
- Se han identificado 10 registros marcados como `posible_fuga`, correspondientes a cinco parejas de imágenes con identificadores fallback.
- La partición se ha realizado agrupando por `leaf_id` para mantener juntas las imágenes del mismo grupo.
- 6.749 registros (37,16 %) no tienen correspondencia en `leaf-map`, por lo que existe una limitación para garantizar la separación de todas las hojas físicas.

**Datos personales:** el proyecto trabaja con imágenes de hojas de tomate y no necesita datos personales para su funcionamiento.

## 7. IA responsable (resumen)

- **Clasificación de riesgo (AI Act):**  Datos personales: no se necesitan para el funcionamiento del proyecto.
- **Principales riesgos y medidas:**
  1. **Errores de clasificación:** contrastar las predicciones con la evaluación de especialistas y comunicar las limitaciones.
  2. **Desequilibrio entre clases:** utilizar F1-macro y revisar los resultados de cada clase.
  3. **Calidad de las imágenes:** comprobar que las imágenes sean legibles y adecuadas para el modelo.
  4. **Fuga de datos:** separar los conjuntos agrupando por `leaf_id` y revisar los identificadores problemáticos.
  5. **Limitación de representatividad:** tener en cuenta que parte de las imágenes no dispone de correspondencia en `leaf-map`.
  6. **Uso inadecuado de las predicciones:** no considerar el resultado del modelo como diagnóstico definitivo ni como sustituto del asesoramiento técnico agrícola.
- **Limitaciones y usos no permitidos:** el modelo se desarrolla con imágenes de hojas de tomate del conjunto PlantVillage. No debe extrapolarse a otros cultivos ni utilizarse como diagnóstico definitivo sin validación. Su rendimiento en condiciones reales de campo deberá comprobarse.
- **Uso de IA:** Se ha utilizado ChatGPT como herramienta de apoyo durante el desarrollo de AgroVision IA. Se ha empleado para:
Ayudar a definir el problema de negocio, los objetivos y las métricas de éxito.
Apoyar la preparación y documentación del conjunto de datos PlantVillage.
Elaborar y revisar código Python para la carga, auditoría, partición y análisis de los datos.
Implementar y comprobar el baseline con DummyClassifier.
Documentar la estrategia de separación de entrenamiento, validación y test, evitando que imágenes del mismo grupo leaf_id aparezcan en entrenamiento y validación.
Redactar y revisar la documentación técnica y los riesgos éticos.
Fuentes y verificaciones manuales: El equipo ha trabajado con el conjunto PlantVillage, obtenido a través de Hugging Face. La procedencia y las condiciones de licencia deben quedar documentadas y verificadas antes de redistribuir los datos.
Revisión humana: Las integrantes del equipo han revisado los resultados obtenidos en Colab, comprobado las particiones y las métricas, y supervisado los cambios realizados en el código y la documentación. ChatGPT se ha utilizado como apoyo, no como sustituto de las decisiones técnicas del equipo.
El detalle se ampliará en `sprint-16/docs/riesgos_eticos.md` y `sprint-16/docs/model_card.md`.

## 8. Equipo y contribuciones

| Persona | Roles (S14 / S15 / S16) | Contribución principal (enlaces a commits / PR) |
|---|---|---|
| Montse | Scrum Master / Técnica / Datos
Coordinación del equipo en S14; responsabilidad técnica en S15; gestión y preparación de datos en S16. https://github.com/maryelenallanosramirez00/IFCD107-LAS-GUERRERAS/commits/main/sprint-14
| Cande | Técnica / Datos / IA responsable
Responsabilidad técnica en S14; preparación de datos en S15; revisión de aspectos de IA responsable en S16| https://github.com/maryelenallanosramirez00/IFCD107-LAS-GUERRERAS/commits/main/sprint-14
| Marisol | Datos / IA responsable / Scrum Master
Preparación y revisión de datos en S14; responsabilidad de IA responsable en S15; coordinación del equipo en S16. |https://github.com/maryelenallanosramirez00/IFCD107-LAS-GUERRERAS/commits/main/sprint-14
| Elena | A responsable / Scrum Master / Técnica
Revisión de riesgos y aspectos éticos en S14; coordinación del equipo en S15; responsabilidad técnica en S16. Trabajo documentado en métricas, partición de datos y baseline https://github.com/maryelenallanosramirez00/IFCD107-LAS-GUERRERAS/commits/main/sprint-14

**Convención de commits:** `tipo: descripción` (`feat:`, `fix:`, `docs:`, `data:`, `exp:`).

Todas las personas deben tener commits propios que permitan identificar sus contribuciones.

## 9. Evidencias de metodología

- **Tablero:** https://github.com/maryelenallanosramirez00/IFCD107-LAS-GUERRERAS
- **Backlog:** `sprint-14/backlog_y_sprints.md`.
- **Planning, review y retrospectiva:** [Añadir evidencias de cada sprint].
- **Documentación del Sprint 14:** ficha del proyecto, plan de datos y licencias, EDA, baseline y riesgos éticos.
- **Evidencias de trabajo:** notebook `02_baseline.ipynb`, particiones CSV y resultados JSON.

## 10. Créditos y licencia del código

- **Datos:** PlantVillage, atribución a sus autores originales y a la fuente de descarga. [Completar atribución y licencia exactas].
- **Librerías principales:** Python, Pandas, NumPy y Scikit-learn. [Añadir versiones definitivas].
- **Licencia del código:** [MIT / propia / pendiente de decisión].
- **Fuente de datos:** [mohanty/PlantVillage en Hugging Face](https://huggingface.co/datasets/mohanty/PlantVillage).

---

## Revisión con la rúbrica

**Revisado por:** [Persona de otro equipo]  
**Fecha:** [dd/mm/aaaa]

| Criterio | Nivel (1–4) | Prueba: una frase de lo que has comprobado |
|---|---:|---|
| Corrección técnica | [1–4] | [Comprobar ejecución de los cuadernos, partición y métricas]. |
| Reproducibilidad | [1–4] | [Reproducir el baseline siguiendo únicamente este README]. |
| Análisis y comunicación al cliente | [1–4] | [Comprobar que se entienden el problema, la decisión y las métricas]. |
| IA responsable | [1–4] | [Comprobar riesgos, medidas, limitaciones y uso de IA]. |

**Lo primero que mejoraríamos:**

[Completar después de la revisión por otro equipo.]
