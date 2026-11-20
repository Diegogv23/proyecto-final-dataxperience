# ¿Qué decide si un empleo será automatizado en 2030?

Proyecto final del curso de Ciencia de Datos.

**Integrantes:** Alejandra Vera · Diego Gutierrez

## 🎥 Video de la presentación

👉 **[[Video](https://youtu.be/5nLZ3Rqu1hM)]**

## Pregunta de investigación

¿Qué factores se asocian más con la probabilidad de que un empleo sea automatizado en 2030: la profesión, la experiencia, la educación, el salario o la exposición a la IA?

## Dataset

- **Nombre:** AI Impact on Jobs 2030
- **Fuente:** [Kaggle](https://www.kaggle.com/) (buscar "AI Impact on Jobs 2030")
- **Tamaño:** 3.000 registros, 18 variables, 20 profesiones
- **Variable objetivo:** `Automation_Probability_2030`
- **Aviso:** es un dataset **sintético**. El valor del proyecto está en el método, no en las cifras como estadísticas reales.

## Estructura del repositorio

| Carpeta | Contenido |
|---|---|
| `datos/` | `AI_Impact_on_Jobs_2030.csv` |
| `notebook/` | Cuaderno de Colab con todo el análisis (`.ipynb`) |
| `presentacion/` | Presentación en PDF/PPTX |
| `README.md` | Este archivo |

**Cuaderno en Colab:** [[COLAB](https://colab.research.google.com/drive/1k9q2fvhPLnWDxaUUR5WGVOsDUnIkNvAm?usp=sharing)]

## Metodología (3 etapas)

1. **Exploración y limpieza.** Sin nulos, duplicados ni valores imposibles (3.000 registros conservados). Dos hallazgos: una regla genérica "entre 0 y 1" habría borrado 1.486 filas válidas (49,5 %) porque `Tech_Growth_Factor` es un multiplicador de 0,5 a 1,5; y `Risk_Category` se excluyó del modelo por fuga de información (es la variable objetivo agrupada).
2. **Análisis de causas.** El riesgo promedio es 50 %, pero con desviación estándar de casi 25 puntos. Se midió cuánta variación explica cada variable (η²).
3. **Visualización y modelo.** Regresión lineal con validación cruzada de 5 particiones, comparada contra una línea base.

## Resultados principales

- La **profesión explica el 85,7 %** de la variación del riesgo; experiencia, salario, educación y exposición a la IA explican menos del 0,2 % cada una.
- La correlación entre exposición a la IA y riesgo es **r = 0,014**: prácticamente nula.
- Las 20 profesiones forman **tres niveles**: bajo (5–30 %), medio (30–70 %) y alto (70–95 %).
- Sin la profesión, el modelo no supera a la línea base (R² ≈ 0, error de 21 puntos). Con ella, R² ≈ 0,85 y error de 8 puntos; en datos de prueba acierta el nivel de riesgo en el 99,3 % de los casos.

## Limitaciones

- Datos sintéticos: las conclusiones no describen el mercado laboral real.
- El modelo predice el nivel de la profesión, no distingue entre personas de una misma profesión.
- Las habilidades son anónimas y no hay dimensión temporal.
- No debe usarse para tomar decisiones sobre personas.

## Cómo reproducirlo

1. Abrir el cuaderno de `notebook/` en [Google Colab](https://colab.research.google.com/).
2. Cargar el CSV desde `datos/` (el cuaderno indica cómo).
3. Ejecutar todo: *Entorno de ejecución → Ejecutar todas*.

Librerías: pandas, numpy, matplotlib, seaborn, scikit-learn.