TFG: Predicción del Riesgo de Inversión en Empresas del IBEX 35 mediante Indicadores Financieros y Bursátiles: Un Enfoque desde el Business Analytics

Autor: Alonso Gil Martín
Grado en Business Analytics | Facultad de Ciencias Jurídicas y Empresariales
Universidad Francisco de Vitoria (Curso 2025-2026)

Este repositorio contiene el ecosistema de datos, código y modelos analíticos desarrollados para mi Trabajo de Fin de Grado (TFG). El objetivo principal del proyecto es construir un sistema predictivo capaz de clasificar el nivel de riesgo de inversión (ALTO o BAJO) de las empresas no financieras del IBEX 35, integrando de forma sistemática el análisis fundamental clásico y el análisis cuantitativo de mercado.

La variable objetivo se operacionaliza mediante el Interest Coverage Ratio (ICR = EBIT / Gastos Financieros), que mide la capacidad de cada empresa para cubrir sus obligaciones de deuda con su beneficio operativo. El universo de análisis son las 29 empresas no financieras del índice (los 6 bancos quedan excluidos por incompatibilidad metodológica del ICR con su modelo de negocio).

Estructura del Repositorio (Distribución por Branches)

Para facilitar la corrección y mantener la trazabilidad metodológica del ciclo de vida del dato, el repositorio se encuentra estructurado en 4 ramas principales. Cada una de ellas responde a una fase crítica del proyecto:

1. anteproyecto


Contenido: Documentación inicial, planteamiento del problema, preguntas de investigación y los objetivos (general y específicos) que estructuran el trabajo.
Hito clave: Define el marco conceptual y justifica los cambios metodológicos respecto a la propuesta inicial. La operacionalización del riesgo evolucionó desde la volatilidad anualizada (descartada por generar circularidad trivial) hasta el ICR como variable objetivo definitiva, pasando por una fase intermedia de ampliación del universo a la totalidad del índice y la posterior exclusión de las 6 entidades financieras.


2. ingenieria-del-dato


Contenido: Script de Python (Ingenieria_del_Dato_ICR_FINAL.ipynb), extracción y procesamiento del dataset propio (datos de Yahoo Finance, Investing.com y la CNMV actualizados a abril de 2026).
Fases técnicas: Carga del archivo, construcción del ICR a partir de EBIT y Gastos Financieros, tratamiento de nulos mediante imputación por mediana (afecta únicamente a Redeia, Mapfre y Puig Brands), análisis de outliers (como Solaria o ArcelorMittal), transformaciones estadísticas (escalado StandardScaler), exportación del dataset final estructurado y visualizaciones de las variables predictoras y su correlación con el target.


3. analisis-del-dato


Contenido: El núcleo predictivo y analítico del TFG (Analisis_del_Dato_ICR_FINAL.ipynb).
Modelización y Validación: Implementación en Python (Scikit-Learn) de tres modelos de clasificación (Regresión Logística, Análisis Discriminante Lineal y Árbol de Decisión) bajo una estrategia de validación cruzada Leave-One-Out (LOOCV, k=29), necesaria por las limitaciones del tamaño muestral.
Hitos clave: Evaluación con métricas honestas (el Árbol de Decisión alcanza el mejor rendimiento con Accuracy 89,7% y AUC-ROC 0,895; la Regresión Logística, modelo de referencia por su interpretabilidad, obtiene Accuracy 79,3% y AUC-ROC 0,871) y el desarrollo de un Experimento de Robustez en 4 escenarios que descarta empíricamente cualquier atisbo de circularidad metodológica en la construcción del target.


4. analisis-de-negocio


Contenido: Propuesta comercial y de negocio orientada al mercado financiero español derivada de las conclusiones empíricas de los modelos.
Hito clave: Desarrollo estratégico de una plataforma web analítica de scoring de riesgo automatizado (modelo SaaS de suscripción mixta), denominada provisionalmente IBEX Risk Score. Incluye análisis de la jerarquía predictiva (donde se demuestra que el ratio Deuda/Capital está aproximadamente 4,6 veces más correlacionado con el riesgo ICR que la volatilidad bursátil anual) y la hoja de ruta con las limitaciones y líneas de desarrollo futuras del negocio.
