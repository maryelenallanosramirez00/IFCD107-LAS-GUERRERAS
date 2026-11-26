# Ficha de proyecto (1 página) · Anexo A
>Equipo (nombre de la consultora): **Las Guerreras** · Fecha:**26/11/2026** · Versión: **1**
## 1. Equipo y roles iniciales
  Persona   Rol en el Sprint 14             Rotación prevista (S15 / S16)
  --------- ------------------------------- -------------------------------
  Montse    Scrum Master                    Técnica / Datos
  Cande     Responsable técnico             Datos / IA responsable
  Marisol   Responsable de datos            IA responsable / Scrum Master
  Elena     Responsable de IA responsable   Scrum Master / Técnica
## 2. Brief elegido y pregunta de negocio
-   Brief: **2 Cultivos**.
-   Pregunta de negocio en una frase: «¿Podemos clasificar fotografías
    de hojas de tomate para que agricultores y técnicos agrícolas puedan
    identificar posibles enfermedades y priorizar las plantas que
    necesitan una inspección profesional?»
## 3. Cliente y decisión que se apoyará
-   Quién usará el resultado: **Agricultores y técnicos agrícolas**.
-   Decisión concreta que mejorará (y qué pasa hoy sin el modelo):
    **Priorizar qué plantas revisar primero según la posible enfermedad
    detectada. Actualmente la identificación inicial depende de la
    inspección visual y de la experiencia de la persona; el sistema será
    una ayuda orientativa, no sustituirá el diagnóstico profesional.**
## 4. Datos
  -------------------------------------------------------------------------------------------------------------------------
  Fuente (enlace)                                               Licencia       Tamaño         Variables      Limitaciones
                                                                                              clave          previstas
  ------------------------------------------------------------- -------------- -------------- -------------- --------------
  [PlantVillage -- Hugging                                      CC BY-SA 3.0   54.305 rutas   image,         Desbalance
  Face](https://huggingface.co/datasets/mohanty/PlantVillage)   declarada en   en los         image_path,    entre clases;
                                                                el             ficheros de    label, crop,   imágenes de
                                                                repositorio;   partición;     disease,       laboratorio
                                                                verificación   18.160         leaf_id        que pueden no
                                                                de condiciones imágenes de                   representar
                                                                pendiente      tomate; ZIP                   condiciones
                                                                               indicado:                     reales;
                                                                               aprox. 2 GB                   comprobar
                                                                                                             licencia,
                                                                                                             imágenes y
                                                                                                             posibles fugas
                                                                                                             entre
                                                                                                             particiones
                                                                                                             mediante
                                                                                                             leaf_id.
  -------------------------------------------------------------------------------------------------------------------------
## 5. Métrica de éxito y baseline
-   Métrica de negocio: **Pendiente de acordar y cuantificar con el
    equipo/cliente; se propone medir la reducción del tiempo de
    priorización de inspecciones.**
-   Métrica técnica: **F1 macro como métrica principal; recall por clase
    y matriz de confusión como métricas complementarias.**
-   Umbral de éxito acordado: **Objetivo inicial propuesto: F1 macro ≥
    0,80; pendiente de validación por el docente.**
-   Baseline previsto: **Predicción de la clase mayoritaria.**
-   Partición de los datos: **PlantVillage incluye particiones
    train/test (43.596 / 10.709 registros según los ficheros
    descargados; 54.305 en total). Para tomate: 14.521 train y 3.639
    test. Revisar agrupación por leaf_id para evitar fuga de datos.**
## 6. Modelos previstos (≥ 3, incluyendo redes neuronales / LLM según el brief)
-   Enfoque elegido y por qué (mi dato · cuántos hay · ¿hay que
    explicar?; chuleta: «¿Qué enfoque uso?» del Atlas): 
    **Clasificación supervisada de imágenes. 
    Hay 18.160 imágenes de hojas de tomate
    distribuidas en 10 clases. Se compararán métodos clásicos y redes
    neuronales; se priorizará el rendimiento por clase y la posibilidad
    de explicar las limitaciones del resultado.**
1.  **Baseline de clase mayoritaria.**
2.  **HOG + SVM.**
3.  **CNN sencilla entrenada con las imágenes.**
4.  **Red neuronal con transferencia de aprendizaje: MobileNetV2.**
## 7. Demostrador previsto
-   Tecnología: **Streamlit. Permitirá cargar una fotografía de una hoja
    de tomate y mostrará la clase predicha, la confianza y un aviso de
    uso orientativo. Si la confianza no alcanza el umbral definido,
    mostrará «No concluyente».**
-   Plan B si falla la demo: vídeo de 90 s.
## 8. Riesgos y mitigación
  -----------------------------------------------------------------------
  Riesgo                  Tipo (datos / modelo /  Mitigación
                          uso / legal / técnico)  
  ----------------------- ----------------------- -----------------------
  Desbalance de clases    datos / modelo          Usar F1 macro, recall
                                                  por clase y matriz de
                                                  confusión; valorar
                                                  técnicas de
                                                  ponderación.

  Diferencias entre       datos / uso             Documentar la
  imágenes de laboratorio                         limitación y validar
  y campo                                         con imágenes reales
                                                  antes de un uso
                                                  operativo.

  Fuga de información     datos / modelo          Comprobar leaf_id y
  entre train y test                              separar por grupo
                                                  cuando corresponda.

  Licencia y condiciones  legal                   Verificar la licencia y
  de reutilización                                atribución antes de
                                                  redistribuir datos o
                                                  modelos.
  -----------------------------------------------------------------------
Clasificación preliminar AI Act: **Sistema de apoyo a la clasificación
de imágenes agrícolas; no se identifica inicialmente como sistema de
alto riesgo, sujeto a revisión de finalidad y normativa aplicable.** ·
¿Datos personales? **No se prevén; confirmar al revisar archivos y
metadatos.**
## 9. Backlog inicial (10-15 historias) y objetivo de cada sprint
-   Historias principales: **1) documentar el problema y usuarios; 2)
    verificar fuente y licencia; 3) descargar y comprobar datos; 4)
    analizar clases y desbalance; 5) revisar nulos y duplicados; 6)
    comprobar leaf_id y fugas; 7) preparar particiones; 8) crear
    baseline; 9) entrenar HOG + SVM; 10) entrenar CNN; 11) probar
    MobileNetV2; 12) comparar modelos; 13) evaluar errores por
    clase; 14) crear demo Streamlit; 15) documentar límites y preparar
    presentación.**
-   Objetivo S14: **Definir el proyecto, equipo, fuente de datos y plan
    inicial.** · Objetivo S15: **Preparar y explorar los datos,
    comprobar particiones y documentar limitaciones.** · Objetivo S16:
    **Entrenar, comparar y evaluar los modelos.** · Objetivo S17:
    **Construir y validar el demostrador y preparar la entrega final.**
------------------------------------------------------------------------
Firmas del equipo (nombres): **Montse, Cande, Marisol y Elena** ·
Respuesta del docente: ☐ GO ☐ GO con cambios ☐ NO-GO --- Comentarios:
