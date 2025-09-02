# Hola, soy Fernando Valencia! <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="25px">

## Acerca de mí

Soy ingeniero industrial con experiencia en la gestión de indicadores y en el desarrollo de proyectos de analítica enfocados en la visualización para el seguimiento de KPIs a lo largo de la cadena de suministro.

Mi primera experiencia fue como practicante en la farmacéutica **Genfar**, donde mi principal logro fue desarrollar un **dashboard en Power BI**, automatizando el proceso de **Extracción, Transformación y Carga (ETL)** para monitorear producción, paradas y limpiezas de todos los procesos productivos. Esto permitió visualizar las principales causales de improductividad y facilitar su detección, **contribuyendo a mejorar el indicador OEE** de la compañía.

Luego, en **Carval de Colombia**, continué desarrollando soluciones analíticas para **producción, logística, compras y planeación**. Además, construí una **aplicación en Power Apps** para automatizar la toma de datos de producción y dar seguimiento en Power BI a los tiempos en planta.

A raíz de este camino, decidí cursar la **Maestría en Analítica e Inteligencia de Negocios** en la **Universidad del Valle**, donde profundicé en **Machine Learning** y **Deep Learning**. He complementado mi formación con cursos en **Coursera** y **Platzi**.

## 🚀 Proyectos destacados
### 🔷 NER clínico en historias de cáncer de pulmón (fine-tuning XLM-RoBERTa)

Realicé **fine-tuning de `xlm-roberta-base`** para **Reconocimiento de Entidades Nombradas (NER)** en historias clínicas de **cáncer de pulmón**, partiendo de un dataset **anotado en formato BIO**. El objetivo fue construir un **dataset limpio y consistente** para análisis estadístico/ML, manteniendo una taxonomía clínica clara (p. ej., `CANCER_CONCEPT`, `TNM`, `STAGE`, `DRUG`, etc.).

**Modelo en Hugging Face.**   
[![HF NER model — xlm-roberta-base (finetuned)](https://img.shields.io/badge/Hugging%20Face-NER%20model%20%E2%80%94%20xlm--roberta--base%20(finetuned)-orange?logo=huggingface)](https://huggingface.co/FernandoValencia/xlm-roberta-base-finetuned-ner-pulmon)


**Datos:** Corpus clínico en español, **anotado BIO**; división train/valid; entidades clínicas (entre otras): `CANCER_CONCEPT`, `DRUG`, `CHEMOTHERAPY`, `RADIOTHERAPY`, `TNM`, `STAGE`, `DATE`, `SURGERY`, `SMOKER_STATUS`, `FAMILY`, `METRIC`, `QUANTITY`, `OCURRENCE_EVENT`, `IMPLICIT_DATE`.

**Pipeline:** Tokenización XLM-R → etiquetado BIO → entrenamiento NER → evaluación → **export a CSV/JSON**.

**Entrenamiento (validación).**
| Época | Val. Loss | Precisión | Recall | F1     | Accuracy |
|:----:|:----------:|:---------:|:------:|:------:|:--------:|
| 1    | 0.1183     | 0.9034    | 0.9135 | 0.9084 | 0.9701   |
| 2    | 0.0894     | 0.9160    | 0.9537 | 0.9345 | 0.9768   |
| 3    | 0.0773     | 0.9264    | 0.9557 | 0.9409 | 0.9802   |
| 4    | 0.0764     | 0.9272    | 0.9605 | 0.9436 | 0.9804   |
| **5**| **0.0772** | **0.9255**| **0.9631**| **0.9439**| **0.9804** |

**Desempeño por entidad (muestra).**
- **Sobresaliente (F1 ≥ 0.96):** `CHEMOTHERAPY` 0.98 · `DATE` 0.98 · `FAMILY` 0.99 · `QUANTITY` 0.96 · `STAGE` 0.97 · `TNM` 0.96
- **Buen desempeño (0.90–0.95):** `CANCER_CONCEPT` 0.92 · `DRUG` 0.94 · `RADIOTHERAPY` 0.95
- **A mejorar:** `OCURRENCE_EVENT` 0.80 · `SURGERY` 0.86 · `SMOKER_STATUS` 0.87
- **Bajo soporte/dificultad:** `IMPLICIT_DATE` 0.46 *(frecuencia baja, ~26 muestras; fechas implícitas son más complejas)*

👉 **Repositorio:** https://github.com/FernandoValencia-DS/PLN_SALUD/tree/main/Taller1  

<details>
<summary>Ejemplo de salida</summary>

**Texto**: “El paciente fue diagnosticado con adenocarcinoma de pulmón estadio IV el 12 de marzo de 2022, con metástasis en cerebro y hueso, y presentó un TNM de T3N2M1.”

- **OCURRENCE_EVENT** → “fue” *(0.50)*
- **OCURRENCE_EVENT** → “diagnosticado” *(0.99)*
- **CANCER_CONCEPT** → “adenocarcinoma de pulmón” *(1.00)*
- **STAGE** → “estadio IV” *(1.00)*
- **DATE** → “12 de marzo de 2022” *(1.00)*
- **CANCER_CONCEPT** → “metástasis en cerebro y hueso” *(0.97)*
- **TNM** → “T3N2M1” *(1.00)*
</details>

### 🔷 Reconocimiento de Entidades Nombradas en Historias Clínicas de Cáncer de Mama
En este proyecto extraigo entidades clínicas de historias clínicas de cáncer de mama y, mediante un pipeline que encadena dos modelos preentrenados (uno para NER y otro para detección de negación/incertidumbre), asigno a cada entidad su **estatus** (Afirmativa/Negada/Sospechosa). El resultado es un **dataset estructurado y consistente** listo para análisis estadístico y de ML, minimizando ambigüedades del texto libre.



**Modelos (Hugging Face).**  
[![NER · extracción de entidades — anvorja/breast-cancer-biomedical-ner-sp-1](https://img.shields.io/badge/NER%20%C2%B7%20extracci%C3%B3n%20de%20entidades-anvorja%2Fbreast--cancer--biomedical--ner--sp--1-orange?logo=huggingface)](https://huggingface.co/anvorja/breast-cancer-biomedical-ner-sp-1)
[![Negación/Incertidumbre · estatus — JuanSolarte99/bert-base-uncased-finetuned-ner-negation_detection_NUBES](https://img.shields.io/badge/Negaci%C3%B3n%2FIncertidumbre%20%C2%B7%20estatus-JuanSolarte99%2Fbert--base--uncased--finetuned--ner--negation__detection__NUBES-orange?logo=huggingface)](https://huggingface.co/JuanSolarte99/bert-base-uncased-finetuned-ner-negation_detection_NUBES)


**Datos:** 106 historias clínicas **anonimizadas** (ES).

**Pipeline:** NER → normalización de etiquetas → detección de **negación/incertidumbre** → **export** a CSV (lista para análisis).
 
👉 **Repositorio:** https://github.com/FernandoValencia-DS/PLN_SALUD/tree/main/Taller2

<details>
<summary>Ejemplo de salida (incluye afirmaciones y negaciones) — ID paciente = 1</summary>

> *El texto proviene del documento original y puede contener errores de digitación propios de la fuente.*

| ID | Fragmento                                                                                                                     | Span                                              | Entidad NER          | Estatus    |
|---:|-------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------|----------------------|------------|
| 1  | RIMERA CONSULTA DE ONCOLOGÍA MÉDICA.                                                                                          | ONCOLOGÍA MÉDICA                                  | CLINICAL_SERVICE     | Afirmativa |
| 1  | Antecedentes Personales:- Alergia a Fluconazol.                                                                               | Alergia a Fluconazol                              | ALLERGIES            | Afirmativa |
| 1  | - No HTA.                                                                                                                     | No HTA                                            | COMORBIDITY          | Negada     |
| 1  | No DM.                                                                                                                        | No DM                                             | COMORBIDITY          | Negada     |
| 1  | No DL.                                                                                                                        | No DL                                             | COMORBIDITY          | Negada     |
| 1  | - Niega habitos toxicos.- Candidiasis recurrentes- Iqx: ninguna.                                                              | Candidiasis recurrentes                           | GINECOLOGICAL_HISTORY| Afirmativa |
| 1  | Muje de 59 años remitida desde oncología con Adenocarcinoma ductal infiltrante de mama izquierda…                             | 59 años                                           | AGE                  | Afirmativa |
| 1  | Muje de 59 años remitida desde oncología con Adenocarcinoma ductal infiltrante de mama izquierda…                             | remitida                                          | OCURRENCE_EVENT      | Afirmativa |
| 1  | Muje de 59 años remitida desde oncología con Adenocarcinoma ductal infiltrante de mama izquierda…                             | oncología                                         | CLINICAL_SERVICE     | Afirmativa |
| 1  | Muje de 59 años remitida desde oncología con Adenocarcinoma ductal infiltrante de mama izquierda…                             | Adenocarcinoma ductal infiltrante de mama izquierda | CANCER_CONCEPT     | Afirmativa |
| 1  | Muje de 59 años remitida desde oncología con Adenocarcinoma ductal infiltrante de mama izquierda…                             | intervenido                                       | OCURRENCE_EVENT      | Afirmativa |
| 1  | Muje de 59 años remitida desde oncología con Adenocarcinoma ductal infiltrante de mama izquierda…                             | mastectomía radical izquierda                     | SURGERY              | Afirmativa |
| 1  | Muje de 59 años remitida desde oncología con Adenocarcinoma ductal infiltrante de mama izquierda…                             | 20/06/1991                                        | DATE                 | Afirmativa |

</details>

### 🔷 Modelos predictivos de diabetes (resampling + comparativa de algoritmos)

En este proyecto clasifico riesgo de **diabetes** en un dataset **desbalanceado**. Para mitigar el sesgo del entrenamiento, aplico **RandomUnderSampler + SMOTE** **solo en el set de entrenamiento** (para evitar *data leakage*) y luego comparo varios modelos clásicos y de *deep learning*.

**Datos (clase objetivo `diabetes`).**
- **Distribución original:** 0 = 64 037 · 1 = 5 950  
- **Distribución tras resampling (solo train):** 0 = 14 875 · 1 = 11 900

**Modelos comparados:** Árbol de Decisión · Random Forest · XGBoost · SVM · MLP

**Resultados (validación).**
| Modelo                       | Accuracy | Precision | Recall | F1-score |   AUC |
|-----------------------------|:--------:|:---------:|:------:|:--------:|------:|
| Árbol de Decisión           |  0.863   |   0.375   | 0.920  |  0.533   | 0.960 |
| Random Forest               |  0.939   |   0.604   | 0.822  |  0.696   | 0.972 |
| XGBoost                     |  0.927   |   0.542   | 0.880  |  0.671   | 0.977 |
| Máquina de Soporte Vectorial|  0.934   |   0.580   | 0.814  |  0.677   | 0.955 |
| Multi-Layer Perceptron (MLP)|  0.950   |   0.651   | 0.827  |  0.729   | 0.976 |

**Conclusiones clave.**
- **Accuracy:** el mejor es **MLP (95%)**, pero **accuracy** por sí solo no es fiable con clases desbalanceadas.  
- **Recall (sensibilidad):** **Árbol de Decisión (92%)** maximiza verdaderos positivos —útil si priorizas **no perder casos**.  
- **Precision:** **MLP (≈65%)** reduce falsos positivos frente a otros modelos; **Árbol** sacrifica precisión por alta sensibilidad.  
- **F1-score (balance):** **MLP** ofrece el mejor compromiso entre detectar diabetes y contener falsos positivos.  
- **AUC:** **XGBoost (0.977)** es el más alto, muy cercano a **MLP (0.976)** y **RF (0.972)**.

👉 **Notebook:** https://github.com/FernandoValencia-DS/data-science-portfolio/blob/main/Clasificaci%C3%B3n/Diabetes.ipynb




## Mira mis publicaciones en Linkedin
<a href= "https://www.linkedin.com/in/fernando-valencia-mar%C3%ADn-5a915b1a5/">
  <img src="https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white">
</a>

## Cursos
[![Static Badge](https://img.shields.io/badge/Data%20Science-Specialization-%20?style=flat&logo=coursera&color=blue)
](https://coursera.org/share/01dfcf9b32c8e5530b7afa2b7310b5a9)

## Credly Badges
[<img src='https://images.credly.com/size/340x340/images/42ce4209-8839-431a-9046-f2ce2e72e04b/Coursera_20Data_20Science_20Professional_20Certificate.png' width="120" height="120"/>](https://www.credly.com/badges/e5b00a01-00f5-4a50-a070-d114da68826a/public_url)
[<img src='https://images.credly.com/size/340x340/images/169512d3-cef6-43e3-bec8-e6af2723a076/image.png' width="120" height="120"/>](https://www.credly.com/badges/7b2b7bee-1f37-478c-9417-54555cb22dbc/public_url)
[<img src='https://images.credly.com/size/340x340/images/950038fc-2519-4f79-8827-f71caf0f5095/image.png' width="120" height="120"/>](https://www.credly.com/badges/ec6dfd3a-8802-471c-97c9-5a3e0742bb6f/public_url)
[<img src='https://images.credly.com/size/340x340/images/f2573aac-d21c-483d-acda-afaa366b4f51/image.png' width="120" height="120"/>](https://www.credly.com/badges/2bf77e72-985e-4bdd-8219-2e214c4d2727/public_url)
[<img src='https://images.credly.com/size/340x340/images/56c60565-e945-4bcd-b8a6-9b2f43e1b0d9/Coursera_20Machine_20Learning_20with_20Python_20V2.png' width="120" height="120"/>](https://www.credly.com/badges/aa89a5f0-b5fc-4115-8246-ad2b6d1d965d/public_url)
[<img src='https://images.credly.com/size/340x340/images/4dd14b9d-2750-43bc-a5f6-27970c0de0fa/image.png' width="120" height="120"/>](https://www.credly.com/badges/e1b26a50-7ed9-4e08-aa94-ef6d3d6db64a/public_url)
[<img src='https://images.credly.com/size/340x340/images/1447954e-9923-4703-a647-eac80e5f0682/image.png' width="120" height="120"/>](https://www.credly.com/badges/201278fe-5924-4eb3-8031-89783c029290/public_url)
[<img src='https://images.credly.com/size/340x340/images/46defa53-a922-47bd-94ea-b43488f5cd8a/Data_Science_Methodology_Foundational.png' width="120" height="120"/>](https://www.credly.com/badges/07eec1db-7033-4ddb-bcbf-81b4e420be4b/public_url)

