# Plan de datos y licencias

**Proyecto:** AgroVision IA – clasificación orientativa de enfermedades en hojas de tomate · **Responsable de datos:** Montse · **Última actualización:** 27/11/2026

> Sin licencia clara no hay proyecto (R2). Si un dato no tiene licencia, no lo uséis: preguntad al docente.

## 1. Inventario de fuentes
| ID | Nombre del conjunto | Fuente / enlace | Fecha de descarga | Licencia | ¿Permite uso académico / redistribución? | Formato y tamaño | ¿Datos personales? |
|---|---|---|---|---|---|---|---|
| D1 | PlantVillage Dataset (subconjunto de hojas de tomate) | [Hugging Face – mohanty/PlantVillage](https://huggingface.co/datasets/mohanty/PlantVillage) | 27/11/2026 | La ficha de Hugging Face declara `cc-by-sa-3.0` (CC BY-SA 3.0);  es una licencia libre, reconocida para contenidos y bases de datos, aunque no es una licencia de software.Entrenar modelos de Machine Learning. Utilizarlas con fines comerciales. | `data.zip`, 2,18 GB; 18.160 imágenes seleccionadas, JPEG, 256 × 256, RGB | No se han identificado datos personales en las imágenes de hojas ni en las columnas revisadas |

**Licencias frecuentes (orientativo, léelas siempre en la fuente):**
- **CC BY 4.0:** libre uso con atribución. **CC BY-SA:** además, misma licencia al redistribuir. **CC BY-NC:** solo uso no comercial. **CC0:** dominio público.
- **Licencias de datos abiertos de administraciones:** normalmente exigen citar la fuente y la fecha.
- **Kaggle / Hugging Face:** cada conjunto tiene su propia licencia; **no asumas** que es libre.

## 2. Descripción de las variables (diccionario de datos)
| Variable | Tipo | Unidad | Significado | Valores válidos | % nulos |
|---|---|---|---|---|---|
| `image_path` | Texto | Ruta | Ruta del archivo de imagen | Rutas existentes bajo `/content` | 0 % |
| `tipo_imagen` | Categórica | No aplica | Tipo de imagen del subconjunto auditado | Un único valor | 0 % |
| `clase` | Categórica | No aplica | Clase objetivo de la imagen | 10 clases de tomate: 1 sana y 9 enfermedades | 0 % |
| `crop` | Categórica | No aplica | Cultivo | `Tomato` | 0 % |
| `disease` | Categórica | No aplica | Enfermedad o condición asociada a la hoja | 10 categorías, incluida la clase sana | 0 % |
| `particion` | Categórica | No aplica | Partición de origen | `train`, `test` | 0 % |
| `image_identifier` | Texto / identificador | No aplica | Identificador asociado a la imagen | Se detectaron 14 identificadores repetidos | 0 % |
| `existe_en_leaf_map` | Booleano | No aplica | Indica si el identificador aparece en el mapa oficial de hojas | `True`, `False` | 0 % |
| `leaf_id` | Texto / identificador | No aplica | Identificador de hoja física, cuando está disponible | Identificadores presentes; puede faltar correspondencia en leaf-map | 0 % |
| `posible_fuga` | Booleano | No aplica | Marca registros señalados para revisión | `True`, `False` | 0 % |
| `particion_auditada` | Categórica | No aplica | Partición tras la auditoría | `train`, `test` | 0 % |

## 3. Informe de calidad del dato (resumen del EDA)
| Aspecto | Hallazgo | Acción tomada y justificación |
|---|---|---|
| Nulos | 0 valores nulos en las 11 columnas del CSV (18.160 registros). | No se imputan valores; se conserva el conjunto porque no se detectaron nulos. |
| Duplicados | 14 copias exactas adicionales detectadas mediante hash MD5. No quedan duplicados exactos tras la limpieza. | Se eliminaron las 14 copias adicionales del dataframe de trabajo con `drop_duplicates(subset="hash_md5", keep="first")`. Se conservan los archivos originales. Conjunto limpio: 18.146 imágenes. |
| Valores imposibles / outliers | No hay columnas numéricas continuas (`select_dtypes(include="number")` devuelve `[]`), por lo que no procede aplicar IQR. Las 18.160 imágenes originales son legibles, JPEG, RGB y de 256 × 256 píxeles, sin errores de lectura. | No se eliminan registros por IQR. Se aplican comprobaciones de integridad adecuadas a imágenes. La limpieza elimina solo las 14 copias exactas. |
| Formatos y tipos | Las 18.160 imágenes originales existen y se leen correctamente; todas son JPEG, RGB y de 256 × 256 píxeles. El CSV tiene 9 columnas de texto y 2 booleanas; no hay nulos. | Se conservan las imágenes que superan las comprobaciones. Se añade `hash_md5` al dataframe de trabajo para identificar copias exactas. |
| **Sesgo de muestreo** (¿quién o qué falta en los datos?) | PlantVillage contiene imágenes de hojas tomadas en condiciones controladas. No representa necesariamente condiciones reales de campo: iluminación variable, fondos naturales, hojas parcialmente ocultas y distintas calidades de fotografía. | Se documenta como limitación de representatividad. Se recomienda evaluar también con al menos 20 fotografías reales de hojas de tomate, separadas del entrenamiento, según la recomendación docente. |
| Desequilibrio de clases / periodos | Hay 10 clases y una distribución desigual. La mayoritaria es Tomato Yellow Leaf Curl Virus (5.357; 29,50 %) y la minoritaria Tomato mosaic virus (373; 2,06 %); relación aproximada 14,4:1. | Se conserva la distribución y se documenta el desequilibrio. La evaluación debe informar por clase y utilizar una métrica que no oculte el rendimiento de las clases minoritarias. |
| **Fuga de datos potencial** (variables que no se conocen al decidir) | Hay 5 registros marcados `posible_fuga=True`, todos en train. Además, 6.735 imágenes (37,16 %) no tienen correspondencia en `leaf-map`; no se puede garantizar la separación por hoja física en todos los casos. | `clase` y `disease` son etiquetas objetivo y no se usarán como entradas. `image_identifier`, `leaf_id`, `particion`, `particion_auditada`, `existe_en_leaf_map` y `posible_fuga` se reservan para auditoría/organización, no como características predictoras. La limitación se revisará antes del entrenamiento final. |

## 4. Linaje del dato (de dónde viene y qué le hemos hecho)
```text
Hugging Face: mohanty/PlantVillage (ficha consultada 27/11/2026; licencia declarada cc-by-sa-3.0)
→ descarga de data.zip mediante hf_hub_download (27/11/2026; archivo de 2,18 GB)
→ extracción en /content/raw y selección del subconjunto de tomate (18.160 imágenes)
→ auditoría de metadatos e integridad en 01_eda.ipynb; comprobación de existencia, lectura, JPEG, RGB y 256 × 256
→ cálculo de hash_md5 y eliminación de 14 copias exactas adicionales (18.146 imágenes)
→ partición auditada existente: train 14.512 / test 3.634; validación y estrategia final por grupos/hoja pendientes de cerrar
→ modelo: todavía no entrenado; baseline pendiente en 02_baseline.ipynb
```
- Script de descarga / preparación: descarga realizada en Colab mediante `hf_hub_download(repo_id="mohanty/PlantVillage", filename="data.zip", repo_type="dataset")`; extracción y auditoría documentadas en `01_eda.ipynb`. El script reproducible `src/datos/preparar.py` / `descargar_datos.py` todavía está pendiente de crear y validar.
- **Huella (hash) del conjunto final:** pendiente. Se calculará SHA-256 del artefacto final cuando se cierre la preparación y la partición.
- ¿Se puede recrear todo desde el README? **Todavía no**; falta documentar y validar el procedimiento reproducible de descarga/preparación en el README.

**Hallazgo para la review:** PlantVillage contiene imágenes en condiciones controladas y no representa necesariamente las condiciones reales del campo. Esto cambia el enfoque de evaluación: además del test del conjunto, se recomienda probar el sistema con al menos 20 fotografías reales de hojas de tomate, no utilizadas para entrenar.

##5. Partición de datos
Estrategia: se conserva la partición original de PlantVillage para separar el conjunto de test y se divide el conjunto de entrenamiento en entrenamiento y validación mediante GroupShuffleSplit, utilizando leaf_id como identificador de grupo y random_state=42.
Tamaños definitivos:
Conjunto
Imágenes
Porcentaje aproximado
Entrenamiento
11.513
63,4 %
Validación
3.013
16,6 %
Test
3.634
20,0 %
Total
18.160
100 %
Justificación para evitar fugas: la separación por grupos mantiene las imágenes con el mismo identificador leaf_id dentro de un único conjunto. Se comprobaron los grupos de entrenamiento y validación y no se encontraron identificadores compartidos. Las cinco parejas marcadas inicialmente como posible fuga quedaron agrupadas correctamente: seis registros marcados permanecen en entrenamiento y cuatro en validación. No hay registros marcados como posible fuga en test.
Limitación: 6.749 imágenes (37,16 %) no tienen correspondencia en leaf-map. Para ellas no se puede garantizar que no existan fotografías de una misma hoja física en diferentes conjuntos. Los identificadores fallback permiten agrupar las cinco parejas detectadas, pero no sustituyen a un identificador oficial para todas las imágenes.
Protección del test: el conjunto de test permanece reservado y no se utiliza para entrenar ni ajustar los modelos. La evaluación inicial del baseline se realiza exclusivamente sobre validación.
Semilla: SEMILLA = 42.
Baseline inicial: DummyClassifier(strategy="most_frequent"). En validación obtiene F1-macro = 0,0442 y accuracy = 0,2834. Predice siempre la clase mayoritaria Tomato___Tomato_Yellow_Leaf_Curl_Virus. Este resultado sirve como referencia para comparar los siguientes modelos; no representa el rendimiento de un clasificador de imágenes.

## 6. Privacidad y RGPD
- ¿Hay datos personales? **No se han identificado en las imágenes de hojas ni en las columnas del CSV revisadas**. 
- ¿Hay datos de menores, salud, biometría u otras categorías especiales? **No se han identificado**; el contenido son fotografías de hojas de tomate.
- Datos que **no** subiremos al repositorio: dataset completo, imágenes originales (`.jpg`, `.jpeg`, `.png`), ZIP descargado, cachés, archivos temporales, credenciales/tokens (`.env`) y cualquier metadato que pudiera identificar a una persona (ponerlos en `.gitignore`).

## 7. Atribución y cita (pegar tal cual en la memoria)
> Mohanty, S. P., Hughes, D. P. y Salathé, M. (2016). *Using Deep Learning for Image-Based Plant Disease Detection*. Frontiers in Plant Science, 7, artículo 1419. https://doi.org/10.3389/fpls.2016.01419. Conjunto: *PlantVillage Dataset*, mantenido en Hugging Face por `mohanty`: https://huggingface.co/datasets/mohanty/PlantVillage. Versión/commit descargado: `9e97599868962bd0079b8db4b7f1efa9185fa1e7`. Fecha de descarga: 27/11/2026. La ficha de Hugging Face declara licencia `cc-by-sa-3.0` (CC BY-SA 3.0); se debe contrastar con las condiciones de la fuente original antes de redistribuir.
