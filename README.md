# Proceso-ETL-y-Análisis-con-Python-y-Power-BI

## Introducción.

Este proyecto tiene como objetivo realizar un proceso completo de Extracción, Transformación y Carga (ETL) sobre una base de datos llamada BD_OPORTUNIDADES_23_24.csv que contiene registros de oportunidades de ventas de los últimos dos años. Posteriormente, se busca analizar los datos y responder preguntas clave mediante dashboards interactivos.

## Objetivo principal.

Realizar un flujo ETL que permita procesar datos crudos, limpiarlos, transformarlos e integrarlos en una base de datos secundaria.
Crear visualizaciones para responder preguntas analíticas clave relacionadas con el rendimiento por zonas, empresas y propietarios.

## Estructura del Proyecto.                                                                                                               
/
├── **DATA**
    - *BD_OPORTUNIDADES_23_24.csv*: Base de datos original con datos crudos (archivo .csv)
    - *Oportunidades_ETL*: Archivo .csv final con proceso ETL
    - *Reto*: Archivo .pdf con instrucciones del reto
├── **NOTEBOOKS**
    - *Proceso ETL BD Oportunidades*: Archivo Jupyter Notebook con código del proceso ETL en Python
├── **POWER BI**
    - *Reto Técnico Análisis*: Archivo .pbix con el dashboard en Power BI que muestra gráficos y resultados
    - *Respuestas Dashboard Power BI*: Archivo .pdf con las respuestas que explican los gráficos
├── **SQL**
    - *Oportunidadesdb.bak*: Base de datos en SQL Server después de aplicar el proceso ETL                           
                                                                       

## Requisitos Técnicos

El proyecto utiliza las siguientes herramientas y tecnologías:                                                                          
Python 3.8 o superior                                                                                                                 
Bibliotecas de Python:                                                                                                                  
pandas                                                                                                                                 
sqlalchemy                                                                                                                           
pyodbc                                                                                                                               
SQL Server: Para almacenar los datos procesados.                                                                                        
Power BI o Excel: Para la creación de dashboards.                                                                                      

## Descripción del Código

El archivo Proceso ETL BD Oportunidades.ipynb contiene un flujo organizado en tres etapas principales:

1. Extracción de Datos.                                                                                                               
Se conectan y cargan datos desde BD_OPORTUNIDADES_23_24.csv utilizando pandas para su manipulación inicial.

2. Transformación de Datos                                                                                                         
Limpieza de datos:                                                                                                                  
- Identificación y manejo de valores nulos.                                                                                           
- Normalización de formatos (fechas, texto, divisas).                                                                                 
- Eliminación de registros duplicados.                                                                                                 
                                                                                                                                       
Transformaciones.                                                                                                                       
Creación de nuevas columnas derivadas, como clasificaciones por zona o rangos de importes.                                             
Agrupaciones y segmentaciones para análisis específicos.                                                                              
                                                                                                                                         
3. Carga de Datos                                                                                                                       
Los datos transformados se cargan en una base de datos SQL Server, asegurando la integridad y consistencia de la información.                                                                                                                                                   
## Funciones Clave                                                                                                                    
def replace_values(df, column):                                                                                                        
* Se observa que hay valores de texto en una lomuna númerica, reemplazamos 'cero' por '0', 'diez' por '10', 'cien' por '100', 'diez mil' por '10000' de la columna Importe.                                                                                                       

def replace_val_sin_datos(df, column):                                                                                                   
* Función para reemplazar datos tipo texto en columna númerica. 'sin datos' se reemplaza por '0' en la columna 'Participantes'.                                                                                                                                                   
def fill_na_in_column(df, column, fill_value):                                                                                      
* Función para imputar datos faltantes de la tabla 'zona' se imputan tomando encuanta la Moda                                            

def remove_duplicates(df, column):                                                                                                     
* Funcion para eliminar duplicados de la columna 'IdOportunidad' ya que en esta columna son llaves primarias y no debe de haber valores  duplicados, esto garantixa integridad en los datos.                                                                                    
                                                                                                                                     
## Instrucciones de Configuración.
                                                                                                                                         
1.- Puedes Utilizar Anaconda para poder trabajar con archivos Jupiter Notebook                                                        
Link de instalación:                                                                                                                    
https://www-anaconda-com.translate.goog/download?_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es&_x_tr_pto=tc&_x_tr_hist=true                        
                                                                                                                                        
2.- Instalar Python y las bibliotecas necesarias:                                                                                       
Pandas                                                                                                                             
sqlalchemy                                                                                                                        
pyodbc                                                                                                                                   
Puedes abrir una terminal desde Jupyter y ejecutar el siguiente codigo:                                                                
pip install pandas sqlalchemy pyodbc                                                                                                   
                                                                                                                                        
3.- Restaurar la base de datos Oportunidadesdb.bak en SQL Server.                                                                        
4.- Configurar las credenciales de conexión a SQL Server                                                                                
                                                                                                                                        
## Guía de Uso                                                                                                                       
                                                                                                                                         
1. Ejecución del Proceso ETL                                                                                                             
Abrir el archivo Proceso ETL BD Oportunidades.ipynb en un entorno compatible como Jupyter Notebook(Anaconda) o VSCode.                   
Ejecutar las celdas de forma secuencial:                                                                                                 
La primera sección establece las conexiones y carga los datos iniciales.                                                                
La segunda sección limpia y transforma los datos según las reglas definidas.                                                             
La tercera sección almacena los datos procesados en SQL Server.                                                                          
Verificar los datos procesados en SQL Server ejecutando consultas para validar la correcta inserción.                                    
                                                                                                                                         
2. Creación de Dashboards                                                                                                               
Link de descarga de Power Bi Desktop:                                                                                                   
https://www.microsoft.com/es-es/power-platform/products/power-bi/desktop                                                                 
                                                                                                                                         
Abrir Power BI o Excel y conectar al servidor SQL Server donde se almacenaron los datos procesados.                                     
Cargar los datos relevantes desde la tabla procesada.                                                                                                                                                                       
Crear visualizaciones interactivas para responder preguntas clave:                                                                     
¿En qué zona (Zona) se ha dado la mejor venta en el último año? Identificar la región con mayor volumen de ventas en 2024, destacando    las tendencias por zona.                                                                                                                 
                                                                                                                                         
Top 3 de empresas (IdEmpresa) en crecimiento (%) del 2024 vs 2023. Mostrar las empresas con mayor incremento porcentual en ventas entre 
los años.                                                                                                                              
                                                                                                                                        
Top 3 de asesores (IdDueño_Oportunidad) en crecimiento (%) del 2024 vs 2023. Identificar los propietarios con mejor desempeño en         
crecimiento anual.                                                                                                                                                                                                                                                               
¿Cuál es la región (Zona) con mayor disminución en ventas (Importe) y su porcentaje comparando 2024 vs 2023? Evaluar las zonas que han   sufrido una caída significativa en ventas y calcular el porcentaje.                                                                     
                                                                                                                                        
¿De la región (Zona) de menos ventas (Importe), quién es el cliente (IdEmpresa) con mayor crecimiento comparando 2024 vs 2023? Resaltar clientes que han crecido significativamente en regiones con bajo desempeño.
                                                                                                                                        
¿Existe una relación entre el número de participantes (Participantes) y la zona (Zona), considerando el importe (Importe) promedio de las oportunidades por cada rango de participantes? Explorar sí los proyectos con más participantes tienen un impacto en el importe promedio dependiendo de la zona.                                                                                                         
                                                                                                                                        
Si ya tienes instalado Power Bi Desktop, solo abre el archivo CasoTecnicoTecMty.pbix para poder visualizar los gráficos.                 
Puedes personalizar el dashboards con filtros dinámicos, colores y etiquetas para mejorar la presentación.                               

## Autor
Isaac Heredia Diaz
[GitHub](https://github.com/IsaacHD86)


