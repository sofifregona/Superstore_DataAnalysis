> El presente análisis se ha desarrollado en el marco del proyecto final del curso de Data Science de la plataforma de e-learning "Coderhouse". Los datos han sido extraídos de Kaggle https://www.kaggle.com/datasets/ahsan81/superstore-marketing-campaign-dataset. El nombre de la compañía es ficticio. By sofifregona.<br>

# **Análisis de comportamiento de clientes para predicción**
## **Abstract**
Con el advenimiento del aprendizaje automático y la inteligencia artificial, son cada vez más las compañías que buscan incorporar estos campos a la planeación empresarial para poder lograr una mayor eficiencia en la toma de decisiones estratégicas. Las tiendas no son una excepción a ello y, con el paso de los años, han comenzado a incorporar dichas tecnologías para predecir el comportamiento de sus clientes y, de esta manera, enfocar sus campañas de Marketing hacia la dirección más oportuna. <br>

El presente trabajo está destinado al departamento de Marketing de la compañía 'Superstore!', el cual pretende predecir el comportamiento de sus clientes. Asimismo, éste se encuentra a disposición de todo el público que pudiera tener interés en él. Los datos han sido relevados y puestos a disposición por parte de la compañía.

### *Contexto*
La superstore 'Supercompras!' está planeando otorgar membresías doradas de 200 USD con descuentos especiales para sus clientes. La campaña se realizará a través de llamadas telefónicas y sólo a usuarios que ya sean clientes de la empresa. Para poder minimizar los costos de la campaña se pretende realizar un modelo predictivo para seleccionar aquellos clientes que tienen mayor probabilidad de aceptar la oferta.

### *Objetivo*
El objetivo del presente análisis es descubrir si existen factores que se relacionen con la decisión de aceptar la membresía por parte de los clientes y, en caso de ser afirmativo, descubrir cuáles son dichos factores y en qué medida cada uno de ellos contribuye a la decisión final. De esta manera se pretende poder predecir el comportamiento futuro de los clientes para, así, enfocar las campañas de marketing en aquellos a los que se les asocie una mayor probabilidad de aceptar la membresía.

## **Desarrollo**
### *Variables*
* `Response` (objetivo) - 1 si el cliente aceptó la oferta de la campaña, 0 si no.
* `ID` - Identificador único del cliente.
* `Year_Birth` - Edad.
* `Complain` - 1 si el cliente realizó alguna queja en los últimos 2 años, 0 si no.
* `Dt_Customer` - Fecha de inscripción del cliente a la compañía.
* `Education` - Nivel de educación.
* `Marital_Status` - Estado civil.
* `Kidhome` - Número de niños en el hogar.
* `Teenhome` - Número de adolescentes en el hogar.
* `Income` - Salario anual.
* `MntFishProducts` - Cantidad gastada en pescados en los últimos 2 años.
* `MntMeatProducts` - Cantidad gastada en carnes en los últimos 2 años.
* `MntFruits` - Cantidad gastada en frutas en los últimos 2 años.
* `MntSweetProducts` - Cantidad gastada en productos con azúcares en los últimos 2 años.
* `MntWines` - Cantidad gastada en vinos en los últimos 2 años.
* `MntGoldProds` - Cantidad gastada en productos de oro en los últimos 2 años.
* `NumDealsPurchases` - Número de compras con descuento realizadas.
* `NumCatalogPurchases` - Número de compras realizadas por catálogo (comprar productos para ser enviados por correo).
* `NumStorePurchases` - Número de compras realizadas directamente en la tienda.
* `NumWebPurchases` - Número de compras realizadas a través del sitio web de la compañía.
* `NumWebVisitsMonth` - Número de visitas al sitio web de la compañía en el último mes.
* `Recency` - Número de días desde la última compra.

### *Datos*
Se ha realizado limpieza y tratamiento de los datos para lograr una mayor estandarización y coherencia.
|index|Id|Year\_Birth|Education|Marital\_Status|Income|Kidhome|Teenhome|Dt\_Customer|Recency|MntWines|MntFruits|MntMeatProducts|MntFishProducts|MntSweetProducts|MntGoldProds|NumDealsPurchases|NumWebPurchases|NumCatalogPurchases|NumStorePurchases|NumWebVisitsMonth|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|0|1826|1970|Graduation|Divorced|84835\.0|0|0|6/16/2014|0|189|104|379|111|189|218|1|4|4|6|1|
|1|1|1961|Graduation|Single|57091\.0|0|0|6/15/2014|0|464|5|64|7|0|37|1|7|3|7|5|
|2|10476|1958|Graduation|Married|67267\.0|0|1|5/13/2014|0|134|11|59|15|2|30|1|3|2|5|2|
|3|1386|1967|Graduation|Together|32474\.0|1|1|11/5/2014|0|10|0|1|0|0|0|1|1|0|2|7|
|4|5371|1989|Graduation|Single|21474\.0|1|0|8/4/2014|0|6|16|24|11|0|34|2|3|1|2|7|
|5|7348|1958|PhD|Single|71691\.0|0|0|3/17/2014|0|336|130|411|240|32|43|1|4|7|5|2|
|6|4073|1954|2n Cycle|Married|63564\.0|0|0|1/29/2014|0|769|80|252|15|34|65|1|10|10|7|6|
|7|1991|1967|Graduation|Together|44931\.0|0|1|1/18/2014|0|78|0|11|0|0|7|1|2|1|3|5|
|8|4047|1954|PhD|Married|65324\.0|0|1|11/1/2014|0|384|0|102|21|32|5|3|6|2|9|4|
|9|9477|1954|PhD|Married|65324\.0|0|1|11/1/2014|0|384|0|102|21|32|5|3|6|2|9|4|

> <i>Muestra de los primeros 10 datos de la tabla</i>

### *Análisis exploratorio de datos* 
#### ► 1. **¿Es el salario anual un factor influyente en la decisión de acptar la membresía?**
***1.1. INTRODUCCIÓN*** <br>
Para responder esta pregunta debemos evaluar si existen diferencias significativas entre la media salarial anual de las personas que aceptaron la membresía y la media salarial anual de las personas que no la aceptaron. Así nuestra variable respuesta será `Response` y nuestra variable predictora será `Income`.<br>

*• Parámetro poblacional de interés:* <br>
$\mu_{1} - \mu_{2}$ <br>
donde: <br>
$\mu_{1}$ : salario medio anual de las personas que no aceptaron la membresía. <br>
$\mu_{2}$ : salario medio anual de las personas que aceptaron la membresía. <br>

*• Hipótesis:* <br>
$H_{0}: \mu_{0} - \mu_{1} = 0$ <br>
$H_{1}: \mu_{0} - \mu_{1} ≠ 0$ <br>

*• Estadístico muestral para realizar la estimación:* <br>
$T={x̄_{1}-x̄_{2}}{\sqrt{\frac{s_{1}^{2}}{n_{1}}+\frac{s_{2}^{2}}{n_{1}}}}$ <br>
donde: <br>
$x̄_{1}$ : media muestral del salario anual de las personas que no aceptaron la membresía. <br>
$x̄_{2}$ : media muestral del salario anual de las personas que aceptaron la membresía. <br>
$s_{1}$ : desvío estándar muestral del salario anual de las personas que no aceptaron la membresía. <br>
$s_{2}$ : desvío estándar muestral del salario anual de las personas que aceptaron la membresía. <br>
$n_{1}$ : tamaño de la muestra de los salarios anuales de las personas que no aceptaron la membresía. <br>
$n_{2}$ : tamaño de la muestra de los salarios anuales de las personas que no aceptaron la membresía. <br>

*• Valor T crítico:* <br>
Sea $t_{\frac{\alpha}{2},\nu}$ el valor $t_{critico}$ que deja un área de $\frac{\alpha}{2}$ a derecha y un área de $\frac{\alpha}{2}$ a izquierda con $\nu$ grados de libertad. La hipótesis nula se rechazará si: $T < -t_{\frac{\alpha}{2},\nu}$ o $T > t_{\frac{\alpha}{2},\nu}$ <br>

*• Intervalo de confianza:* <br>
$IC = (x̄_{1} - x̄_{2}) - t_{\frac{\alpha}{2},\nu}\sqrt{\frac{s_{1}^{2}}{n_{1}} + \frac{s_{2}^{2}}{n_{1}}}$ , $(x̄_{1} - x̄_{2}) + t_{\frac{\alpha}{2},\nu}\sqrt{\frac{s_{1}^{2}}{n_{1}} + \frac{s_{2}^{2}}{n_{1}}}$ <br>
Utilizaremos un nivel de confianza del 95% (es decir, un nivel de significancia $\alpha$ del 5%). <br>

***1.2. ANÁLISIS*** <br>
Se realizó el análisis exploratorio y se obtuvo el resumen numérico y el resumen gráfico. <br>

|Response|count|mean|std|min|25%|50%|75%|max|
|---|---|---|---|---|---|---|---|---|
|0|1881\.0|50832\.62519936204|25263\.91308080881|1730\.0|34421\.0|50150\.0|66313\.0|666666\.0|
|1|331\.0|60187\.752265861025|23231\.596312029622|7500\.0|39723\.5|64090\.0|80676\.0|105471\.0|

> <i>Resumen numérico del salario anual en función de la respuesta (siendo 0: negativo, 1: afirmativo)</i><br>
<p align=left><image src="https://github.com/sofifregona/Superstore_DataAnalysis/blob/main/assets_readme/g_1.png" alt="Boxplot de la distribución del salario anual agrupado por la respuesta" width=400><image src="https://github.com/sofifregona/Superstore_DataAnalysis/blob/main/assets_readme/g_2.png" alt="Boxplot de la distribución del salario anual agrupado por la respuesta, sin outliers" width=400></p>
  
> <i>Boxplot de la distribución del salario anual agrupado por la respuesta con outliers (izquierda) y sin ellos (derecha). </i>
  
Se observa que la mediana de los salarios anuales de las personas que decidieron aceptar la membresía es ligeramente superior a la mediana de los salarios anuales de las personas que no lo hicieron. La variabilidad es ligeramente superior en los casos de las personas que no aceptaron la membresía y, además, esta distribución presenta outliers. <br>
  
Se aplicó la prueba de Levene para determinar si existen diferencias significativas entre las varianzas de ambos grupos, y se concluyó que se puede suponer que ambas varianzas son significativamente diferentes. Con esto se obtuvo $t_{critico} = 1.965$. <br>

Luego obtuvimos $T = -6.665$ y se confirma que $T < -t_{critico}$ por lo que tenemos evidencia para rechazar la hipótesis nula. <br>
                                                                 
El intervalo de confianza está dado por $IC = (-12112.951, -6597.303)$. Observamos que el mismo no contiene al 0, por lo que nuevamente confirmamos que tenemos evidencia para descartar la hipótesis nula. Además, todos los valores del intervalo son negativos, lo que indica que la media del salario anual de las personas que aceptaron la membresía es mayor que la media del salario anual de las personas que no lo hicieron. <br>
  
***1.3. CONCLUSIÓN*** <br>
Con un 95% de confianza podemos concluir que existen evidencias suficientes para afirmar que las personas que optaron por aceptar la membresía poseen mayores ingresos anuales que aquellas personas que no la aceptaron. <br>
<br>  
#### ► 2. ¿Es el nivel educativo un factor que influye en la decisión de aceptar la membresía?
***2.1. INTRODUCCIÓN*** <br>
Para responder esta pregunta debemos evaluar si existen diferencias significativas entre las proporciones de personas que aceptaron la membresía en función de su nivel educativo. Así nuestra variable respuesta será `Response` y nuestra variable predictora será `Education`.<br>

*• Parámetro poblacional de interés:* <br>
$p_{i} - p_{j}$ <br>
donde: <br>
$p_{i}$ : proporción de personas con nivel educativo $ i $ que aceptaron la membresía sobre el total de personas con nivel educativo $ i $. <br>
$p_{j}$ : proporción de personas con nivel educativo $ j $ que aceptaron la membresía sobre el total de personas con nivel educativo $ j $. <br>
siendo: <br>
${i,j}$ : {Basic, 2n Cycle, Graduate, Master, PhD}<br>
  
*• Hipótesis:*
$H_{0}: p_{i} - p_{j} = 0$ para algún $i,j$<br>
$H_{1}: p_{i} - p_{j} ≠ 0$ para algún $i,j$<br>
  
*• Estadístico muestral para realizar la estimación:* <br>
$Z = \frac{p̂_{i} - p̂_{j}}{\sqrt{\frac{p̂_{i}(1-p̂_{i})}{n_{i}} + \frac{p̂_{j}(1-p̂_{j})}{n_{j}}}}$ <br>
donde: <br>
$p̂_{i}$ : proporción muestral de personas con nivel educativo $i$ que aceptaron la membresía. <br>
$p̂_{j}$ : proporción muestral de personas con nivel educativo $j$ que aceptaron la membresía. <br>
$n_{i}$ : total de personas con nivel educativo $i$. <br>
$n_{j}$ : total de personas con nivel educativo $j$. <br>
  
*• Valor Z crítico:* <br>
Sea $z_{\frac{\alpha}{2}}$ el valor $z_{critico}$ que deja un área de $\frac{\alpha}{2}$ a derecha y un área de $\frac{\alpha}{2}$ a izquierda. La hipótesis nula se rechazará si: $Z < -z_{\frac{\alpha}{2}}$ o $Z > z_{\frac{\alpha}{2}}$ <br>

*• Intervalo de confianza:* <br>
$IC = (p̂_{i} - p̂_{j}) - z_{\frac{\alpha}{2}}\sqrt{\frac{p̂_{i}(1-p̂_{i})}{n_{i}} + \frac{p̂_{j}(1-p̂_{j})}{n_{j}}}$ , $(p̂_{i} - p̂_{j}) + z_{\frac{\alpha}{2}}\sqrt{\frac{p̂_{i}(1-p̂_{i})}{n_{i}} + \frac{p̂_{j}(1-p̂_{j})}{n_{j}}}$ <br>
Utilizaremos un nivel de confianza del 95% (es decir, un nivel de significancia $ \alpha $ del 5%). <br>
  
***2.2. ANÁLISIS*** <br>
Se realizó el análisis exploratorio y se obtuvo el resumen numérico y el resumen gráfico. <br>

|Education|0|1|
|---|---|---|
|2n Cycle|0\.89|0\.11|
|Basic|0\.9629629629629629|0\.037037037037037035|
|Graduation|0\.8645739910313901|0\.13542600896860987|
|Master|0\.8461538461538461|0\.15384615384615385|
|PhD|0\.791231732776618|0\.20876826722338204|
  
> <i>Tabla de frecuencias relativas de la respuesta en función del nivel educativo</i><br>
<image src="https://github.com/sofifregona/Superstore_DataAnalysis/blob/main/assets_readme/g_3.png" alt="Boxplot de la distribución del salario anual agrupado por la respuesta" width=400>
  
> <i>Barplot de la proporción de respuestas afirmativas y negativas en función del nivel educativo. </i>
<br>  
Tomando en cuenta el orden jerárquico de los niveles académicos (en orden creciente esto es: básico, secundario, graduado, máster y PhD) observamos que a medida que el nivel aumenta pareciera ser mayor la proporción de personas que se dispuesieron a aceptar la membresía. <br>

Se obtuvo el $z_{critico}$ para cada comparación de niveles y se obtuvo lo siguiente: <br>
  
|Niveles|Básico|Secundario|Graduado|Máster|Postdoctoral|
|--|--|--|--|--|--| 
|Básico|0|-2.152|-3.556|-3.661|-5.416|
|Secundario|-2.152|0|-1.043|-1.506|-3.419|
|Graduado|-3.556|-1.043|0|-0.856|-3.458|
|Máster|-3.661|-1.506|-0.856|0|-2.072|
|Postdoctoral|-5.416|-3.419|-3.458|-2.072|0|
  
***2.3. CONCLUSIÓN*** <br>
