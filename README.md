# Ejercicio_ML
## “All models are wrong, but some are useful.” George Box

*[Descripción del proyecto](#Descripción-del-proyecto)

*[Estado del proyecto](#Estado-del-proyecto)

*[Metodología](#Metodología)

*[Fases del proyecto](#Fases-del-proyecto)

*[Acceso al proyecto](#Acceso-al-proyecto)

*[Tecnologías utilizadas](#Tecnologías-utilizadas)

---
# Descripción-del-proyecto
El principal objetivo de este ejercicio es el de generar un acercamiento y experiencia en el uso de modelos de Machine Learning. Se plantea como caso de uso realizar un modelo de predicción de la Tasa de Inflación de USA. 


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
## Metodología CRISP DM
![Metodología CRISP_DM](https://raw.githubusercontent.com/gusper01/Ejercicio_ML/main/Archivos/CrispDM.PNG)
[Fuente Kenneth Jensen](https://commons.wikimedia.org/w/index.php?curid=24930610)
# Fases-del-Proyecto
 ## Comprensión del negocio
Muchas organizaciones  utilizan modelos para pronosticar variables económicas clave, como la inflación, el crecimiento del PBI, las tasas de interés, entre otras. Estos modelos pueden incorporar una amplia gama de variables y utilizar algoritmos sofisticados para mejorar la precisión de las predicciones. El objetivo es proporcionar pronósticos más precisos que respalden la toma de decisiones. Es este contexto se propone. Desarrollar un ejercicio que recorra todos los pasos necesarios para generar modelo de Machine Learning que pueda predecir la tasa de inflación de Estados Unidos. utilizando datos/variables macroeconómicas. En general este problema se aborda combinando técnicas de regresión y series de tiempo. En este caso se toman datos de series de tiempo con indicadores macroeconómicos publicadas por la Reserva Federal (USA FED). https://fred.stlouisfed.org/docs/api/fred/overview.html 
## Comprensión de los datos :chart_with_downwards_trend:
 Se toma como fuente de datos un conjunto de series de tiempo que contienen los siguientes indicadores de USA
* __CPIAUCSL:__ este el índice de precios al consumidor para todas las áreas urbanas de USA. y representa el cambio porcentual mensual de los precios de una canasta de bienes y servicios consumidos por los hogares urbanos.
https://fred.stlouisfed.org/series/CPIAUCSL
* __FEDFUNDS:__ Este es la serie de tiempo de la tasa de interés. Posee frecuencia mensual  
https://fred.stlouisfed.org/series/FEDFUNDS
* __UNRATE:__ Esta es la serie de tiempo de la tasa de desempleo, posee frecuencia mensual y 
representa la cantidad de desempleados como un porcentaje de la fuerza laboral. 
https://fred.stlouisfed.org/series/UNRATE
* __UMCSENT:__ Esta es la serie de tiempo del índice de sentimiento del consumidor, se basa en una encuesta realizada por la Universidad de Michigan a un grupo de consumidores para evaluar sus actitudes y expectativas hacia la economía, posee frecuencia mensual.
https://fred.stlouisfed.org/series/UMCSENT
* __MYAGM2USM052S:__ Esta es la serie de tiempo de la oferta monetaria M2 en los Estados Unidos. M2 es una medida amplia de la oferta monetaria que incluye el efectivo en circulación, los depósitos a la vista y los depósitos a plazo en instituciones financieras, así como ciertos instrumentos financieros de corto plazo. Posee frecuencia mensual. 
https://fred.stlouisfed.org/series/MYAGM2USM052S
* __WPUSI012011:__ Esta serie proporciona información sobre los cambios en los precios de los materiales utilizados en la industria de la construcción en los Estados Unidos. Posee frecuencia mensual. 
https://fred.stlouisfed.org/series/WPUSI012011
* __IPMAN:__ Esta es la serie de tiempo del índice de producción industrial de manufacturas de Estados Unidos. Posee frecuencia mensual 
https://fred.stlouisfed.org/series/IPMAN
* __MARTSMPCSM44000USS:__ Esta serie representa la variación porcentual mensual en las ventas minoristas en Estados Unidos
https://fred.stlouisfed.org/series/MARTSMPCSM44000USS
* __MICH:__ Esta serie proporciona información sobre las expectativas de inflación de los consumidores en Estados Unidos. Esta serie mide las percepciones y predicciones de los consumidores sobre la tasa de inflación futura en la economía. Posee frecuencia mensual.
https://fred.stlouisfed.org/series/MICH 
* __Fórmula Tasa de Inflación:__ Tasa de inflación = ((CPIAUCSL actual - CPIAUCSL mes anterior) / CPIAUCSL del mes anterior) * 100 
 ## Preparación de los datos
* A las series de tiempo se les aplicó [Test de Dickey-Fuller Aumentado](https://www.sciencedirect.com/topics/economics-econometrics-and-finance/dickey-fuller-test) 
* Se transformo el dataframe con las series de tiempo: eliminando valores nulos ```data2.dropna(inplace=True)``` y se aplican transformaciones log y diff(esta transformación calcula la diferencia entre observaciones 
 consecutivas) para eliminar tendencia o estacionalidad:  ```data2['Tasa Interes'] = np.log(data2['Tasa Interes']).diff()```
 ## Modelado
### Conjuntos de datos (entrenamiento y test)
En la construcción de los conjuntos de entrenamiento y test se aplicó la técnica de validación cruzada en series temporales (Time Series Cross-Validation). A diferencia de la validación cruzada tradicional, donde se asume que las observaciones son independientes entre sí, en la validación cruzada en series temporales se tiene en cuenta la dependencia temporal de los datos. que preserva la estructura temporal al realizar la validación cruzada. La idea principal detrás de la validación cruzada de series temporales es simular el escenario de predicción en el tiempo real, donde se cuenta con datos históricos hasta un momento determinado y se desea predecir los valores futuros. Para lograr esto, se divide el conjunto de datos en múltiples conjuntos de entrenamiento y prueba, de manera que las observaciones en los conjuntos de prueba siempre ocurren después de las observaciones en los conjuntos de entrenamiento.
<table><tr><td>
<pre>A los efectos de este ejercicio, si bien se genera el código para realizar la validación cruzada de la serie temporal y se aplica 
al conjunto de datos transformado. Se toman solo el primer par de conjuntos de entrenamiento y test generado. Se debe tener 
en cuenta que en un escenario productivo debería evaluarse el rendimiento del modelo en distintos puntos en el tiempo.
</pre>
</td></tr></table>

### Algoritmos de Modelado
Se seleccionaron 3 algoritmos de machine learning  para modelos de regresión, se determinó utilizar los algoritmos de Linear Regression, Random Forest y XGBoost para determinar el más adecuado para el problema de predicción de tasa de inflación de Estados Unidos. 

## Evaluación
### Métricas de evaluación :triangular_ruler:
Las métricas en la evaluación de modelos de Machine Learning permiten medir la precisión, el error y la capacidad de explicación del modelo. Al utilizar estas métricas en conjunto, se puede obtener una imagen completa del rendimiento del modelo y tomar decisiones sobre su utilidad y eficacia. Para evaluar los resultados del ejercicio se decide aplicar las siguientes métricas:
* MSE (Mean Square Error) Error Cuadrático Medio_
El MSE se calcula como el promedio de los cuadrados de las diferencias entre los valores predichos y los valores reales. Un MSE más bajo indica que las predicciones del modelo son más cercanas a los valores reales en promedio. Se considera que un MSE más bajo indica una mejor precisión en las predicciones debido a que: • El MSE penaliza más los errores grandes. Al elevar al cuadrado las diferencias, los errores más grandes tienen un impacto mayor en el resultado final. Esto significa que, si el modelo comete algunos errores significativos, el MSE aumentará rápidamente. Por lo tanto, un MSE más bajo indica que el modelo está cometiendo en promedio menos errores grandes.
* MAE (Mean Absolute Error) Error Absoluto Medio
El MAE mide el promedio de las diferencias absolutas entre los valores predichos y los valores reales. Se calcula sumando las diferencias absolutas y dividiendo por el número total de observaciones. El MAE también se utiliza para evaluar la precisión de un modelo de regresión. A diferencia del MSE, el MAE no penaliza de manera desproporcionada los errores grandes, lo que lo hace más útil cuando se desea evaluar el rendimiento de un modelo sin importar la magnitud de los errores. Al igual que el MSE, un valor de MAE más bajo indica un mejor ajuste del modelo. Al comparar modelos, se prefiere aquellos con un MAE más bajo. El MAE tiene una interpretación intuitiva y directa, ya que está en las mismas unidades que los datos originales. Por ejemplo, en una predicción de tasa de inflación si el MAE es 0.5, significa que, en promedio, la predicción difiere en 0.5 % de la inflación real.
* R2 Coeficiente de Determinación
Esta métrica se utiliza para evaluar la calidad de un modelo de regresión. Es una medida de qué tan bien se ajustan los valores predichos por el modelo a los valores reales. El R2 se interpreta de la siguiente manera:
Un valor cercano a 1 indica que el modelo explica una gran parte de la variabilidad de los datos y se ajusta bien a los datos. Un valor cercano a 0 indica que el modelo no explica mucha variabilidad y no se ajusta bien a los datos. Es importante tener en cuenta que un valor negativo de R2 no es una situación común y, en general, si se obtiene un valor negativo, es una señal de que el modelo no es apropiado para los datos.

 ## Despliegue :rocket:
<table><tr><td>
<pre>Los datos y el código se actualizan de forma regular, lo que puede llevar a variaciones en algunos resultados y visualizaciones.
</pre>
</td></tr></table> 

![Predicciones](https://raw.githubusercontent.com/gusper01/Ejercicio_ML/main/Archivos/Predicciones.png)
 

 # Acceso-al-proyecto
 
  | Carpeta              | Contenido |
| -------------------- | --------- |
| [Archivos](./Archivos) | Archivos generados con Python,  Pandas, pickle, predicciones, etc.. |
| [Notebooks](./Notebooks) | Notebooks Colab con el código fuente generado |

# Tecnologías-utilizadas
* Python
* [Google_Colaboratory](https://colab.research.google.com/notebooks/welcome.ipynb?hl=es)
* API KEY - FRED
  Se debe generar una cuenta en el sitio de FRED https://fred.stlouisfed.org/ previamente 


