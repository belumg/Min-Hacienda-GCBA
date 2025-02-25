# Min-Hacienda-GCBA

**Disclaimer:** Ningún dato sensible o confidencial ha sido expuesto sin el consentimiento correspondiente.


### Motivación
<p align="justify"> Desde la Subgerencia Operativa de Proyecciones y Estadísticas Presupuestarias, perteneciente al Ministerio de Hacienda y Finanzas del Gobierno de la Ciudad de Buenos Aires, se busca generar un modelo de datos que relacione diferentes tablas y datasets para su análisis y proyección a futuro.

Particularmente, en esta demo se requerirá extraer y "cruzar" tres datasets, a saber: índices, estructuras y resultados.

En primer lugar, la idea será visualizar cada concepto mostrando:
- El acumulado del 2023 de cada uno de los índices que componen la estructura.
- El porcentaje de ponderación de cada índice multiplicado por el acumulado del 2023.

Por otra parte, y conforme a dichos conceptos habrá de determinarse:
- Cuánto representa su devengado mensual dentro del total de los devengados de la base. 
- Qué porcentaje de ejecución debería tener cada uno (Dato del área a devengar / Monto mensual proyectado).
</p>

### Idea de resolución
Me fueron proporcionados los datasets de índices, estructuras y resultados:
- En el de índices figuran los nombres, montos acumulados mes a mes y tanto el número como el código alfabético identificatorio.
- En el de estructuras se muestran, por cada concepto, los índices que lo componen (columna "nombre" de la tabla de índices) como así también su código (combinación de las columnas índice y código de la tabla de índices) y ponderación.
- Por último, en el de resultados se especifica por cada concepto su devengamiento mensual, lo que el área devenga y el monto proyectado.

<p align="justify"> Básicamente, relacioné indices.csv y estructuras.csv en función de sus columnas nombre e índice, respectivamente.
Habiendo almacenado previamente las tablas en formato DataFrame, recorrí cada una y generé un diccionario en el que se guardara el total acumulado de 2023 o bien su ponderación, en ambos casos con su nombre/índice como clave. Para calcular el acumulado 2023 según su ponderación, bastó con acceder a los datos del diccionario correspondiente y por último, trasladar todo a un nuevo DataFrame. Adicionalmente, este fue filtrado por "Concepto" y se expuso visualmente como tabla (PrettyTable). </p>
  
<p align="justify"> En cuanto a resultados.csv, el único dato extra necesario fue la suma del total devengado de la base y la división del devengado mensual de cada concepto por esta. En relación al porcentaje de ejecución, la cuenta fue efectuada directamente entre los campos correspondientes de cada concepto. Nuevamente, toda la información se cargó como tabla. </p>


### Mejoras
- Exporté las tablas del Excel original a archivos .csv separados para mayor flexibilidad.
- Automaticé su lectura y procesamiento con Python.
- Los datos se cargan como DataFrames (librería Pandas), lo cual permite manipularlos, buscarlos y filtrarlos más fácilmente.
- Los conceptos se agrupan y se van mostrando en tablas, intentando reproducir el formato de tabla dinámica de Excel.   
