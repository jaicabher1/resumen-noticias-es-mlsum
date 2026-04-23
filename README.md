# Comparación de técnicas de resumen automático (noticias en español)

## Resumen del proyecto
Este proyecto estudia y compara técnicas de **resumen automático** aplicadas a **noticias en español**, con el objetivo de entender las diferencias entre enfoques **extractivos** (seleccionan frases del texto original) y **generativos** (redactan un resumen nuevo). Para ello se utiliza el dataset **MLSUM (Multilingual Summarization)**, filtrando la partición en español.

La idea del trabajo **no es entrenar modelos desde cero**, sino realizar experimentos con **modelos preentrenados** y baselines clásicos, analizar su rendimiento con métricas estándar y discutir sus limitaciones, especialmente en términos de **calidad**, **coherencia** y posibles **errores de factualidad** (p. ej., omitir información clave o introducir detalles no presentes en el texto).

## Objetivos
- Comparar métodos **extractivos** vs **generativos** para el resumen de noticias en español.
- Implementar baselines extractivos (por ejemplo **Lead-k** y **TextRank**) y evaluar su comportamiento.
- Evaluar varios modelos generativos preentrenados de **Hugging Face** (mínimo dos), ajustando el proceso de inferencia a textos largos (p. ej., mediante **chunking** si es necesario).
- Medir el rendimiento con métricas automáticas (p. ej., **ROUGE-1/2/L**) y con indicadores auxiliares de calidad (longitud, ratio de compresión, repetición, cobertura de entidades, etc.).
- Realizar un análisis cualitativo con ejemplos representativos para identificar patrones: cuándo funciona mejor cada enfoque, errores típicos y casos difíciles.
- Extraer conclusiones y proponer líneas de **trabajo futuro** (mejores métricas de coherencia/factualidad, evaluación humana, modelos para contexto largo, etc.).

## Dataset
- **MLSUM — Multilingual Summarization Dataset**
- Se utilizará la porción en **español (es)** para tareas de resumen monodocumento (artículo → resumen de referencia).

> Nota: en el repositorio no se suben los datos crudos si la licencia o el tamaño no lo permiten; en su lugar, se documenta cómo descargarlos y preprocesarlos.

## Metodología (visión general)
1. **EDA y preprocesado**: análisis de longitudes, limpieza mínima, selección de subconjuntos y ejemplos.
2. **Modelos extractivos**: construcción de resúmenes a partir de selección de frases.
3. **Modelos generativos**: generación de resúmenes con modelos preentrenados (con control de longitud).
4. **Evaluación**:
   - Métricas con referencia: ROUGE.
   - Indicadores de calidad y coherencia: compresión, repetición, cobertura de entidades, chequeos simples de números/fechas (exploratorio).
5. **Discusión**: análisis cuantitativo + ejemplos cualitativos + limitaciones.

## Estructura del repositorio (plan)
- `notebooks/` — notebooks del proyecto:
  - `01_eda_dataset.ipynb`
  - `02_extractive_baselines.ipynb`
  - `03_generative_models.ipynb`
  - `04_evaluation.ipynb`
- `src/` — código reutilizable (carga de datos, preprocesado, evaluación).
- `reports/` — memoria del proyecto (informe final).
- `slides/` — guion/diapositivas para la presentación.

## Resultados esperados
Se espera observar diferencias claras entre enfoques:
- Los métodos extractivos pueden funcionar bien en noticias con estructura de “pirámide invertida”, pero suelen producir resúmenes menos fluidos.
- Los modelos generativos suelen mejorar fluidez y condensación, pero pueden cometer errores de factualidad o perder detalles específicos.
- El rendimiento puede variar según longitud del texto, tema y estilo del resumen de referencia.

## Autores
- Trabajo en pareja (2 integrantes).
