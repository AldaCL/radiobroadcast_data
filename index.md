# Análisis de datos abiertos de Radiodifusión en México 📈

En el presente repositorio se encuentran *Jupyter Notebooks* en las que se realizan análisis de datos del servicio de Radiodifusión en México. Esta serie de *Notebooks* tienen el objetivo de abarcar temas como **Radiodifusión Sonora en AM y FM** y  **Televisión Digital Terrestre (TDT)**  como los dos servicios principales, pero al mismo tiempo, exponer tecnicidades sobre el análisis de datos, visualización de datos así como el uso en conjunto  de bibliotecas enfocadas a tratar datos georreferenciados con el objetivo de aproximarse e interpretar los datos para generar y exponer información importante. 

El primera instancia, se busca una aproximación enfocada en el impacto de población, es decir, en las coberturas; la ubicación y mapeo de las coberturas y concentraciones de las estaciones de Radiodifusión en México; así como darle sentido e interpretación en la dimensión social y demográfica. 

Estas *notebooks* harán uso de tecnicidades, que, para quién resulte interesante, serán expuestas a mayor detalle en documentos posteriores , tales como análisis de datos, algoritmos de optimización para visualización de datos, datos georreferenciados y detalles sobre el tratamiento de datos con *Python*.

![alt text](/radio/Datos/results/mapa1.png)


# Descarga, instalación y funcionamiento 🐱‍👤

Este repositorio se encuentra sincronizado con un contenedor de *Docker* con el objetivo de no generar conflictos con las múltiples dependencias utilizadas; por lo tanto es altamente aconsejable que se cuente con *Docker* instalado.
Por otra parte, los datos empleados en en el análisis son **datos abiertos** (más adelante se listarán las fuentes, así como la estructura de los datos y cómo debes importarlos), por lo que únicamente se menciona la estructura de las carpetas de la forma como podrás organizar los datos, o bien puedes organizarlos a tu preferencia configurando el código debidamente. 


## TLDR
Abra una ventana de *Windows PowerShell* en la ruta en la que deseas descargar e iniciar el entorno; a continuación:

 1. Copie y pegue:  `git clone https://github.com/AldaCL/Radio_jupyter`
 2. Diríjase al directorio descargado con: `cd Radio_jupyter` 
 3. Inicialice el contenedor de *Docker* con `docker-compose up`
 4. Verá en la ventana, una dirección de red local que comienza con `http:\\127.0.0.1:8888:8888` seguido de un token, copia y pega todo en una ventana del navegador.
 5. Asegúrese  de  que los datos de coberturas y los datos de población se encuentran en su lugar y reinicié el *kernel* de la *Notebook* preferida.
 6. *voilá*  🐱‍🏍
  
# Lista de contenidos y guía: 

 1. [Análisis de datos de Radiodifusión Sonora en AM  y FM](#radio)
 2. Análisis de datos de Radiodifusión de Televisión Digital Terrestre (TDT)
 3. Algoritmos para clasificación y visualización de datos
 4. Interpretación de datos en la dimensión de las telecomunicaciones y las audiencias. *¿Qué nos dicen?*
 5. Principios de datos georreferenciados con *Geopandas*
 6. Principios técnicos sobre el tratamiento de datos con *Python*



### 1. Análisis de datos de Radiodifusión Sonora en AM  y FM  <a name="radio"></a>

 - **Datos requeridos**
	 - Polígonos *.shp* de capa de estados de la República Mexicana, **INEGI**, 2010: [Descarga](https://www.inegi.org.mx/app/biblioteca/ficha.html?upc=702825296520) (Estatal.shp)
	 - Lista de Localidades de México, **INEGI**, 2010: [Descarga](https://www.inegi.org.mx/contenidos/programas/ccpv/2010/datosabiertos/iter_nal_2010_csv.zip ) (Localidades_2010.csv)
	- Coberturas de radiodifusión sonora en AM y FM, **IFT**:  [Consulta CPCREL](http://mapasradiodifusion.ift.org.mx/CPCREL-web/consultaCoberturas/consultaCoberturas.xhtml;jsessionid=U-8eUGaEZNAYqrD8aTpGOYH0vn-6YGkZmI6KeQozd527haXDVzNQ!271094803?dswid=6870) (Coberturas.csv)
	
 - **Preparativos**
	a. Coloque los respectivos datos con la siguiente estructura (Ya contenida en el repositorio) : 
- **Datos**
	- */Localidades_2010.csv*
	- AM/*Coberturas AM .csv*
	- FM/*Coberturas FM.csv*
	- Geodata/*Estatal.shp*
	
- **Algunos resultados**
**Cobertura por número de estaciones sintonizables en cada localidad**
![mapa1](/radio/Datos/results/mapa1.png)
**Localidades sin cobertura del servicio de Radiodifusión Sonora en AM**
![mapa3](/radio/Datos/results/mapa3.png)

Si se replica el análisis para el servicio de Radiodifusión Sonora en FM

![mapa4](/radio/Datos/results/mapa4.png)
Es posible observar en  el mapa de localidades no atendidas por cada servicio, que existe un mayor número de localidades que no cuentan con el servicio de FM.**
**Por otra parte, observamos que la distribución de colores que representan un mayor número de estaciones sintonizables (Es decir los colores más claros) se encuentra mayormente distribuida y concentrica en las estaciones de AM; mientras que en el servicio de FM, se presentan manchas en las ubicaciones de las ciudades o capitales de cada estado con un área menor, respondiendo a una mayor concentración demográfica.
* **Existen 357 estaciones de radio AM autorizadas, que no  brindan servicio a un total de 31610 localidades**
* **Existen 1534 estaciones de radio FM autorizadas, que no brindan servicio a un total de 60643 localidades**

* **El servicio de AM, cuenta con un número menor de estaciones autorizadas, sin embargo debido a las características de propagación en esas frecuencias, su cobertura es mayor, lo cual habilita a un mayor número de personas a sintornizar al menos una estación de radio.**
* **Por otra parte, debido a la mayor cantidad de estaciones de FM, es posible decir que es más probable que las audiencias que tienen acceso al servicio de Radio FM, tengan acceso a al menos más de una estación de FM, lo cúal representa una mayor diversidad de contenidos para el público**

Finalmente, en un ejercicio de desagregación por estado, se obtiene el siguiente mapa interactivo
![mapa2](/radio/Datos/results/mapa2.png)

![pastel](/radio/Datos/results/pastel.png)

* **Los Estados ubicados en el centro del país cuentan con el mayor porcentaje de cobertura del servicio de radio (AM y FM) así como con una mayor cantidad de estaciones sintonizables, que a su vez coincide con la mayor densidad demográfica por km2, debido al tamaño de las entidades**
* **Durango es el estado con menor penetración del servicio de Radio FM, a su vez, Campeche es el estado con menor porcentaje de penetración de radio AM**

