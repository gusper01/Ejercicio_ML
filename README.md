# Ejercicio_ML
## “All models are wrong, some are useful.” George Box

*[Descripción del proyecto](#Descripción-del-proyecto)

*[Estado del proyecto](#Estado-del-proyecto)

*[Metodología](#Metodología)

*[Fases del proyecto](#Fases-del-proyecto)

*[Acceso al proyecto](#acceso-proyecto)

*[Tecnologías utilizadas](#tecnologías-utilizadas)

---
# Descripción-del-proyecto
Este ejercicio tiene como principal objetivo es generar un acercamiento y experiencia en el uso de modelos de Machine Learning. Se plantea como caso de uso realizar un modelo de predicción de la Tasa de Inflación de USA. 


# Estado-del-proyecto
:construction: En construcción :construction:

# Metodología
En este ejercicio se decide aplicar la metodología __CRISP-DM__ (Cross-Industry Standard Process for Data Mining) esta es una metodología ampliamente utilizada en el campo de la minería de datos y el desarrollo de proyectos de análisis de datos. Proporciona un marco estructurado y sistemático para el desarrollo de proyectos de minería de datos, incluyendo el proceso de construcción de modelos de machino e Learning.
La metodología CRISP-DM define 6 fases en un proyecto de minería de datos o machine Learning
* Comprensión del negocio: En esta fase, se busca comprender los objetivos del negocio y los requerimientos del proyecto de minería de datos. Se definen los objetivos específicos y se establece un plan inicial.
*	Comprensión de los datos: Se recopila y analiza el conjunto de datos disponible. Se realiza una exploración inicial de los datos para identificar patrones, tendencias y posibles problemas de calidad de los datos.
*	Preparación de los datos: Se realiza el procesamiento y la transformación de los datos necesarios para el análisis. Esto puede incluir la limpieza de datos, la selección de variables relevantes y la creación de nuevas variables derivadas.
*	Modelado: En esta fase se construyen los modelos de minería de datos utilizando técnicas como regresión, clasificación, clustering(agrupamiento), etc. Se selecciona el modelo más adecuado y se entrena con los datos disponibles.
*	Evaluación: Se evalúa el rendimiento de los modelos construidos utilizando métricas apropiadas. Se realiza una validación cruzada y se ajustan los modelos según sea necesario para mejorar su desempeño.
*	Despliegue: Se implementa el modelo seleccionado en un entorno operativo. Se documenta el proceso y se crea un plan de seguimiento y mantenimiento del modelo. Se realiza un seguimiento continuo para evaluar su rendimiento y realizar ajustes si es necesario.


# Fases-del-Proyecto
 ##Comprensión del negocio
Muchas organizaciones  utilizan modelos para pronosticar variables económicas clave, como la inflación, el crecimiento del PBI, las tasas de interés, entre otras. Estos modelos pueden incorporar una amplia gama de variables y utilizar algoritmos sofisticados para mejorar la precisión de las predicciones. El objetivo es proporcionar pronósticos más precisos que respalden la toma de decisiones. Es este contexto se propone. Desarrollar un ejercicio que recorra todos los pasos necesarios para generar modelo de Machine Learning que pueda predecir la tasa de inflación de Estados Unidos. utilizando datos/variables macroeconómicas. En general este problema se aborda combinando técnicas de regresión y series de tiempo. En este caso se toman datos de series de tiempo con indicadores macroeconómicos publicadas por la Reserva Federal (USA FED). https://fred.stlouisfed.org/docs/api/fred/overview.html
 ## Comprensión de los datos
 Se toma como fuente de datos un conjunto de series de tiempo que contienen los siguientes indicadores macroeconómicos de ESTADOS UNIDOS
 
 ## Preparación de los datos
 ## Modelado
 ## Evaluación
* Métricas de evaluación 
Las métricas en la evaluación de modelos de Machine Learning permiten medir la precisión, el error y la capacidad de explicación del modelo. Al utilizar estas métricas en conjunto, se puede obtener una imagen completa del rendimiento del modelo y tomar decisiones sobre su utilidad y eficacia. Para evaluar los resultados del ejercicio se decide aplicar las siguientes métricas:
* MSE (Mean Square Error) Error Cuadrático Medio_
El MSE se calcula como el promedio de los cuadrados de las diferencias entre los valores predichos y los valores reales. Un MSE más bajo indica que las predicciones del modelo son más cercanas a los valores reales en promedio. Se considera que un MSE más bajo indica una mejor precisión en las predicciones debido a que: • El MSE penaliza más los errores grandes. Al elevar al cuadrado las diferencias, los errores más grandes tienen un impacto mayor en el resultado final. Esto significa que, si el modelo comete algunos errores significativos, el MSE aumentará rápidamente. Por lo tanto, un MSE más bajo indica que el modelo está cometiendo en promedio menos errores grandes.
* MAE (Mean Absolute Error) Error Absoluto Medio
El MAE mide el promedio de las diferencias absolutas entre los valores predichos y los valores reales. Se calcula sumando las diferencias absolutas y dividiendo por el número total de observaciones. El MAE también se utiliza para evaluar la precisión de un modelo de regresión. A diferencia del MSE, el MAE no penaliza de manera desproporcionada los errores grandes, lo que lo hace más útil cuando se desea evaluar el rendimiento de un modelo sin importar la magnitud de los errores. Al igual que el MSE, un valor de MAE más bajo indica un mejor ajuste del modelo. Al comparar modelos, se prefiere aquellos con un MAE más bajo. El MAE tiene una interpretación intuitiva y directa, ya que está en las mismas unidades que los datos originales. Por ejemplo, en una predicción de tasa de inflación si el MAE es 0.5, significa que, en promedio, la predicción difiere en 0.5 % de la inflación real.
* R2 Coeficiente de Determinación
Esta métrica se utiliza para evaluar la calidad de un modelo de regresión. Es una medida de qué tan bien se ajustan los valores predichos por el modelo a los valores reales. El R2 se interpreta de la siguiente manera:
Un valor cercano a 1 indica que el modelo explica una gran parte de la variabilidad de los datos y se ajusta bien a los datos. Un valor cercano a 0 indica que el modelo no explica mucha variabilidad y no se ajusta bien a los datos. Es importante tener en cuenta que un valor negativo de R2 no es una situación común y, en general, si se obtiene un valor negativo, es una señal de que el modelo no es apropiado para los datos.

 ## Despliegue
 
