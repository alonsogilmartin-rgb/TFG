# TFG: Predicción del Riesgo de Inversión en Empresas del IBEX 35 mediante Indicadores Financieros y Bursátiles: Un Enfoque desde el Business Analytics

**Autor:** Alonso Gil Martín  
**Grado en Business Analytics** | Facultad de Ciencias Jurídicas y Empresariales  
**Universidad Francisco de Vitoria** (Curso 2025-2026)

Este repositorio contiene el ecosistema de datos, código y modelos analíticos desarrollados para mi Trabajo de Fin de Grado (TFG). El objetivo principal del proyecto es construir un sistema predictivo capaz de clasificar el nivel de riesgo de inversión (ALTO o BAJO) de las 35 empresas componentes del IBEX 35, integrando de forma sistemática el análisis fundamental clásico y el análisis cuantitativo de mercado.

## Estructura del Repositorio (Distribución por Branches)
Para facilitar la corrección y mantener la trazabilidad metodológica del ciclo de vida del dato, el repositorio se encuentra estructurado en **4 ramas principales**. Cada una de ellas responde a una fase crítica del proyecto:

### 1. `anteproyecto`
* **Contenido:** Documentación inicial, planteamiento del problema, preguntas de investigación y los objetivos (general y específicos) que estructuran el trabajo. 
* **Hito clave:** Define el marco conceptual y justifica los cambios metodológicos respecto a la propuesta inicial (como la ampliación a las 35 empresas del índice para eliminar sesgos muestrales).

### 2. `ingenieria-del-dato`
* **Contenido:** Scripts de Python (`Ingenieria_del_Dato_Alonso_Gil.ipynb`), extracción y procesamiento del dataset propio (datos de Yahoo Finance, Investing.com y la CNMV actualizados a abril de 2026).
* **Fases técnicas:** Carga del archivo, tratamiento de nulos mediante imputación crítica por mediana, análisis de outliers (como Solaria o ArcelorMittal), transformaciones estadísticas (escalado `StandardScaler`), exportación del dataset final estructurado y primeras visualizaciones de las variables predictoras.

### 3. `analisis-del-dato`
* **Contenido:** El núcleo predictivo y analítico del TFG (`Analisis_del_Dato_Alonso_Gil.ipynb`).
* **Modelización y Validación:** Implementación en Python (Scikit-Learn) de los tres modelos de clasificación bajo una robusta estrategia de validación cruzada *Leave-One-Out* (LOOCV), obligatoria por las limitaciones del tamaño muestral ($n = 35$).
* **Hitos clave:** Evaluación con métricas honestas (destacando la Regresión Logística con un *Accuracy* del 80,0% y un AUC-ROC de 0,876) y el desarrollo de un **Experimento de Robustez en 4 escenarios** que descarta empíricamente cualquier atisbo de circularidad o sesgo en la construcción del target.

### 4. `analisis-de-negocio`
* **Contenido:** Propuesta comercial y de negocio orientada al mercado financiero español derivada de las conclusiones empíricas de los modelos.
* **Hito clave:** Desarrollo estratégico de una plataforma web analítica de *scoring* de riesgo automatizado (modelo SaaS de suscripción mixta). Incluye análisis de la jerarquía predictiva (donde se demuestra que los ratios contables como Deuda/Capital pesan aproximadamente 2,7 veces más que la volatilidad bursátil diaria para la monitorización continua) y la hoja de ruta con las limitaciones y líneas de desarrollo futuras del negocio.
