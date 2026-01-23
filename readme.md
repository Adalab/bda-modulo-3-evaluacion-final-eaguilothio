# 📊 Evaluación Final · Módulo 3  

## Análisis de Clientes en Programa de Fidelización de Aerolínea

**Autor:** eaguilothio  

---

## 📌 Descripción del Proyecto

Proyecto de **análisis de datos** enfocado en comprender el **perfil de los clientes y su comportamiento** dentro de un programa de fidelización de una aerolínea.

El objetivo principal es **explorar, limpiar, integrar y analizar** distintas fuentes de datos para **extraer conclusiones relevantes** sobre patrones, comportamiento de vuelos y características de los clientes.

---

# 📂 Fuentes de Datos

El análisis se basa en dos datasets complementarios:

### 1️⃣ Customer Flight Activity.csv  

Con este archivo se observa cómo vuela cada cliente mes a mes, cuántos vuelos realiza, si viaja acompañado y cómo utiliza sus puntos a lo largo del tiempo.

### **2. Customer Loyalty History.csv**

Con este archivo se entiende el perfil del cliente: dónde vive, su nivel de formación, su poder adquisitivo, su situación personal y el tipo de relación que mantiene con el programa de fidelización.


---

## 🔎 Fases del Análisis

### 🧹Fase 1: Exploración y Limpieza de Datos

- Antes de unir los dos archivos, revisamos por separado qué información contiene cada uno.  
- Cada dataset puede incluir problemas como valores nulos, duplicados u outliers.  
- Limpiar cada archivo individualmente evita errores y asegura una integración correcta.

### 📈 Fase 2: Análisis Estadístico Descriptivo

En esta fase se revisan los datos para entender cómo se comportan.  
El análisis se divide en dos partes:

- **Variables numéricas:** se observa cómo se distribuyen y cómo varían sus valores.  
- **Variables categóricas:** se revisa cuántas veces aparece cada categoría y qué proporción representa dentro del conjunto.

---

### 📊 Fase 3 · Visualización de Datos

En esta fase se utilizan gráficos para explorar los datos y detectar patrones que no se aprecian en tablas.  
Las visualizaciones permiten identificar tendencias, comparar grupos y observar relaciones entre variables.

Se trabaja a tres niveles:

- **Variables numéricas:** para ver cómo se distribuyen.  
- **Variables categóricas:** para conocer la composición de cada categoría.  
- **Relaciones entre variables:** para analizar cómo interactúan entre sí.


---

## Fase 4: Evaluación de Diferencias en Reservas de Vuelos por Nivel Educativo

Aunque no sea una “fase” operativa como las anteriores (limpieza, exploración, estadística o visualización), este apartado forma parte del análisis, ya que está orientado a responder preguntas específicas.

Aquí se evalúan diferencias entre grupos y se investiga si una característica del cliente —en este caso, el nivel educativo— está relacionada con su comportamiento de reserva.
 
---

## 🗂️ Estructura del Repositorio

- **README.md:** contiene las explicaciones del proyecto.  
- **pdf_evaluacion_final.pdf:** incluye el planteamiento del ejercicio.  
- **evaluacion-final-eaguilothio.ipynb:** notebook principal con el análisis completo.  
- **data/:** carpeta que almacena los archivos CSV utilizados en el proyecto.

## 🛠️ Tecnologías y Librerías

- **pandas** y **numpy**: manipulación y análisis de datos tabulares  
- **matplotlib** y **seaborn**: visualización de datos  

---