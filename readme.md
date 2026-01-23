# Evaluación Final · Módulo 3

## Análisis del perfil de clientes y su comportamiento dentro de una Aerolínea

**Autor:** eaguilothio  

---

## 📑 Tabla de Contenidos

1. [Descripción del Proyecto](#1-descripción-del-proyecto)  
2. [Fuentes de Datos](#2-fuentes-de-datos)  
   - [Customer Flight Activity.csv](#21-customer-flight-activitycsv)  
   - [Customer Loyalty History.csv](#22-customer-loyalty-historycsv)  
3. [Fases del Análisis](#3-fases-del-análisis)  
   1. [Fase 1 — Exploración y Limpieza de Datos](#31-fase-1--exploración-y-limpieza-de-datos)  
   2. [Integración de Datos](#32-integración-de-datos)  
   3. [Fase 2 — Análisis Estadístico Descriptivo](#33-fase-2--análisis-estadístico-descriptivo)  
   4. [Fase 3 — Visualización de Datos](#34-fase-3--visualización-de-datos)  
   5. [Fase 4 — Evaluación de Diferencias por Nivel Educativo](#35-fase-4--evaluación-de-diferencias-por-nivel-educativo)  
4. [Estructura del Repositorio](#4-estructura-del-repositorio)  
5. [Librerías Principales](#5-librerías-principales)  

---

## 1. Descripción del Proyecto

Proyecto de **análisis de datos** enfocado en comprender el **perfil de los clientes y su comportamiento** dentro de un programa de fidelización de una aerolínea.

**Objetivo principal:**  
Explorar, limpiar, integrar y analizar distintas fuentes de datos para **extraer conclusiones relevantes**.
 
---

## 2. Fuentes de Datos

### 2.1 Customer Flight Activity.csv

Analiza la **actividad de vuelo mensual** de cada cliente:

- Número de vuelos realizados  
- Viajes acompañados  
- Uso y acumulación de puntos  
- Evolución del comportamiento a lo largo del tiempo  

> Contiene múltiples registros por cliente.

---

### 2.2 Customer Loyalty History.csv

Describe el **perfil del cliente** dentro del programa de fidelización:

- Lugar de residencia  
- Nivel educativo  
- Nivel de ingresos  
- Situación personal  
- Información sobre la relación con el programa  

> Cada cliente aparece **una sola vez**.

---

## 3. Fases del Análisis

### 3.1 Fase 1 — Exploración y Limpieza de Datos

#### Exploración Inicial

**Objetivo:** Comprender los datos, su estructura y posibles problemas.

- **Revisión de dimensiones:**  
  - *Customer Flight Activity*: 405.624 filas × 10 columnas  
  - *Customer Loyalty History*: 16.737 filas × 16 columnas  

- **Inspección de tipos de datos:**  
  - Flight → mayormente numéricas  
  - Loyalty → mezcla de numéricas y categóricas  

- **Valores nulos:**  
  - Flight → ninguno  
  - Loyalty → `salary` y algunas variables de cancelación  

- **Duplicados:**  
  - Flight → pequeño porcentaje  
  - Loyalty → ninguno  

- **Valores anómalos:**  
  - Salarios negativos → error de signo  

#### Limpieza y Preparación de Datos

**Objetivo:** Garantizar coherencia y consistencia.

- Ambos → Conversión de `loyalty_number` a string  
- Homogeneización de nombres de columnas (snake_case)
- Loyalty → Corrección de `salary` (valores absolutos)  
- Flight →  Eliminación de duplicados en actividad de vuelo  

---

### 3.2 Integración de Datos

**Objetivo:** Unir comportamiento de vuelo y perfil del cliente.

- **Método:** `merge` → **LEFT JOIN** con Customer Flight Activity como base  
- **Justificación:**  
  - Se conservan todas las observaciones de vuelo  
  - Se agrega perfil de cliente cuando existe  
  - No se requieren perfiles sin actividad  

---

### 3.3 Fase 2 — Análisis Estadístico Descriptivo

**Objetivo:** Visión general de variables numéricas y categóricas.

#### Variables numéricas

| Variable        | Observaciones |
|-----------------|---------------|
| Total Flights   | Media > mediana → asimetría positiva, alta dispersión y outliers |
| CLV             | Media > mediana → heterogeneidad, valores máximos elevados |
| Salary          | Media ≈ mediana → distribución simétrica, algunos valores altos |

✔ Conclusión: algunas variables muy desiguales (`total_flights`, `CLV`), otras más estables (`salary`).

#### Variables categóricas

- Análisis mediante `describe(include='object')`  
- Tablas de frecuencia absoluta y relativa para país, género, nivel educativo, etc.

✔ Conclusión: permiten segmentar y comprender la composición de la clientela.

---

### 3.4 Fase 3 — Visualización de Datos

**Objetivo:** Detectar patrones y tendencias gráficas.

- **Tipos de gráficos:**  
  - Barplot horizontal → muchas categorías / nombres largos  
  - Barplot agrupado → subcategorías (hue)  
  - Scatterplot → correlación entre variables numéricas  
  - Pie chart → proporción relativa de categorías  

- **Hallazgos:**  
  - Estacionalidad → picos en verano y diciembre, mínimos en enero/febrero  
  - Ontario y British Columbia → mayor concentración de clientes  
  - Clientes casados → grupo más numeroso  
  - Tarjeta **Star** → mayoría de clientes  

---

### 3.5 Fase 4 — Evaluación de Diferencias por Nivel Educativo

**Objetivo:** Evaluar diferencias en número de vuelos según nivel educativo.

- El nivel educativo **no parece influir significativamente** en cantidad de vuelos.  
- El comportamiento de reserva es bastante homogéneo entre niveles educativos.  

---

## 4. Estructura del Repositorio

- **README.md:** documentación del proyecto  
- **pdf_evaluacion_final.pdf:** enunciado del ejercicio  
- **evaluacion-final-eaguilothio.ipynb:** notebook principal con el análisis completo  
- **data/**: carpeta con los archivos CSV utilizados  

---

## 5. Librerías Principales

### Manipulación y análisis de datos

- **pandas** → carga, limpieza y análisis de datos tabulares  
- **numpy** → cálculos numéricos y manejo de valores faltantes (`NaN`)  
- **os** → gestión de rutas y carga de archivos  

### Visualización

- **matplotlib** → gráficos personalizables  
- **seaborn** → visualizaciones estadísticas basadas en matplotlib  



