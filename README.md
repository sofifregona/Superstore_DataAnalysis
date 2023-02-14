# **Análisis de Superstore para campaña de marketing**
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

<p align=center><i>Muestra de los primeros 10 datos de la tabla</i></p>

### *Análisis exploratorio de datos* 
#### ¿Es el salario anual un factor influyente en la decisión de aceptar la membresía? 
Para responder esta pregunta debemos evaluar si existen diferencias significativas entre la media salarial anual de las personas que aceptaron la membresía y la media salarial anual de las personas que no la aceptaron. Así nuestra variable respuesta será `Response` y nuestra variable predictora será `Income`.<br>

* Parámetro poblacional de interés: <br>
$\mu_{1} - \mu_{2}$ <br>
donde: <br>
$\mu_{1}$ : salario medio anual de las personas que no aceptaron la membresía. <br>
$\mu_{2}$ : salario medio anual de las personas que aceptaron la membresía. <br>

* HIPÓTESIS: <br>
$H_{0}: \mu_{0} - \mu_{1} = 0$ <br>
$H_{1}: \mu_{0} - \mu_{1} ≠ 0$ <br>

* Estadístico muestral para realizar la estimación: <br>
$T = \frac{x̄_{1} - x̄_{2}}{\sqrt{\frac{s^{2}_{1}}{n_{1}} + \frac{s^{2}_{2}}{n_{1}}}}$ 
<br>
donde: <br>
$x̄_{1}$ : media muestral del salario anual de las personas que no aceptaron la membresía. <br>
$x̄_{2}$ : media muestral del salario anual de las personas que aceptaron la membresía. <br>
$s_{1}$ : desvío estándar muestral del salario anual de las personas que no aceptaron la membresía. <br>
$s_{2}$ : desvío estándar muestral del salario anual de las personas que aceptaron la membresía. <br>
$n_{1}$ : tamaño de la muestra de los salarios anuales de las personas que no aceptaron la membresía. <br>
$n_{2}$ : tamaño de la muestra de los salarios anuales de las personas que no aceptaron la membresía. <br>
<br>

* Valor T crítico: <br>

Sea $ t_{\frac{\alpha}{2},\nu} $ el valor $ t_{critico} $ que deja un área de $ \frac{\alpha}{2} $ a derecha y un área de $ \frac{\alpha}{2} $ a izquierda con $ \nu $ grados de libertad. La hipótesis nula se rechazará si: <br>
$ T < -t_{\frac{\alpha}{2},\nu} $ o $ T > t_{\frac{\alpha}{2},\nu} $
<br>

* INTERVALO DE CONFIANZA: <br>

$ (x̄_{1} - x̄_{2}) - t_{\frac{\alpha}{2},\nu}\sqrt{\frac{s^{2}_{1}}{n_{1}} + \frac{s^{2}_{2}}{n_{1}}} $ , $ (x̄_{1} - x̄_{2}) + t_{\frac{\alpha}{2},\nu}\sqrt{\frac{s^{2}_{1}}{n_{1}} + \frac{s^{2}_{2}}{n_{1}}} $ <br>
Utilizaremos un nivel de confianza del 95% (es decir, un nivel de significancia $ \alpha $ del 5%). <br>
<br>

* Interpretación del intervalo de confianza: <br>

Si el 0 está contenido dentro del intervalo, entonces podremos afirmar con un 95% de confianza que existen diferencias significativas entre las medias de los salarios anuales de quienes aceptaron la membresía y quienes no lo hicieron. Por el contrario, si el 0 no está contenido, entonces no podremos afirmar que existan diferencias significativas.
