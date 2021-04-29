# Análisis de datos abiertos de Radiodifusión en México 📈

En el presente repositorio se encuentran *Jupyter Notebooks* en las que se realizan análisis de datos del servicio de Radiodifusión en México. Esta serie de *Notebooks* tienen el objetivo de abarcar temas como **Radiodifusión Sonora en AM y FM** y  **Televisión Digital Terrestre (TDT)**  como los dos servicios principales, pero al mismo tiempo, exponer tecnicidades sobre el análisis de datos, visualización de datos así como el uso en conjunto  de bibliotecas enfocadas a tratar datos georreferenciados con el objetivo de aproximarse e interpretar los datos para generar y exponer información importante. 

El primera instancia, se busca una aproximación enfocada en el impacto de población, es decir, en las coberturas; la ubicación y mapeo de las coberturas y concentraciones de las estaciones de Radiodifusión en México; así como darle sentido e interpretación en la dimensión social y demográfica. 

Estas *notebooks* harán uso de tecnicidades, que, para quién resulte interesante, serán expuestas a mayor detalle en documentos posteriores , tales como análisis de datos, algoritmos de optimización para visualización de datos, datos georreferenciados y detalles sobre el tratamiento de datos con *Python*.

![alt text](https://github.com/AldaCL/radiobroadcast_data/tree/main/radio/Datos/results/mapa1.png)


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
 7. ***Caso de uso : Análisis de Must Carry/Must Offer (Repositorio y datos privados)***


### 1. Análisis de datos de Radiodifusión Sonora en AM  y FM  <a name="radio"></a>

 - **Datos requeridos**
	 - Polígonos *.shp* de capa de estados de la República Mexicana, **INEGI**, 2010: [Descarga](https://www.inegi.org.mx/app/biblioteca/ficha.html?upc=702825296520) (Estatal.shp)
	 - Lista de Localidades de México, **INEGI**, 2010: [Descarga](https://www.inegi.org.mx/contenidos/programas/ccpv/2010/datosabiertos/iter_nal_2010_csv.zip ) (Localidades_2010.csv)
	- Coberturas de radiodifusión sonora en AM y FM, **IFT**:  [Consulta CPCREL](http://mapasradiodifusion.ift.org.mx/CPCREL-web/consultaCoberturas/consultaCoberturas.xhtml;jsessionid=U-8eUGaEZNAYqrD8aTpGOYH0vn-6YGkZmI6KeQozd527haXDVzNQ!271094803?dswid=6870) (Coberturas.csv)
	
 - **Preparativos**
	a. Coloque los respectivos datos con la siguiente estructura (Ya contenida en el repositorio) : 
> -**Datos**
> --- */Localidades_2010.csv*
>	--- AM/*Coberturas AM .csv*
>--- FM/*Coberturas FM.csv*
>---Geodata/*Estatal.shp}

- **Previsualización**
![alt text](https://github.com/AldaCL/radiobroadcast_data/tree/main/radio/Datos/results/preview.png)
	

  	 
