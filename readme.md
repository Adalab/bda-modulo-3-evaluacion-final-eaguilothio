# Evaluación Final · Módulo 3

## Análisis del perfil de clientes y su comportamiento dentro de una Aerolínea

**Autor:** eaguilothio

---

## Tabla de Contenidos

1. [Descripción del Proyecto](#descripción-del-proyecto)  
2. [Fuentes de Datos](#fuentes-de-datos)  
3. [Fases del Análisis](#fases-del-análisis)  
   1. [Fase 1 — Exploración Inicial](#fase-1--exploración-inicial)  
   2. [Fase 1 — Limpieza y Preparación de Datos](#fase-1--limpieza-y-preparación-de-datos)  
   3. [Integración de Datos](#integración-de-datos)  
   4. [Fase 2 — Análisis Estadístico Descriptivo](#fase-2--análisis-estadístico-descriptivo)  
   5. [Fase 3 — Visualización de Datos](#fase-3--visualización-de-datos)  
   6. [Fase 4 — Evaluación de Diferencias por Nivel Educativo](#fase-6--evaluación-de-diferencias-por-nivel-educativo)  
4. [Estructura del Repositorio](#estructura-del-repositorio)  
5. [Librerías Principales](#librerías-principales)

---

## Descripción del Proyecto

Proyecto de **análisis de datos** enfocado en comprender el **perfil de los clientes y su comportamiento** dentro de un programa de fidelización de una aerolínea.

El objetivo principal es **explorar, limpiar, integrar y analizar** distintas fuentes de datos para **extraer conclusiones relevantes** sobre los patrones de vuelo, el uso del programa de fidelización y las características de los clientes.

---

## Fuentes de Datos

El análisis se basa en dos datasets complementarios:

### 1. Customer Flight Activity.csv

Este archivo permite analizar la **actividad de vuelo mensual** de cada cliente, incluyendo:
- Número de vuelos realizados
- Viajes acompañados
- Uso y acumulación de puntos
- Evolución del comportamiento a lo largo del tiempo

Se trata de un dataset con múltiples registros por cliente.

### 2. Customer Loyalty History.csv

Este archivo describe el **perfil del cliente** dentro del programa de fidelización:
- Lugar de residencia
- Nivel educativo
- Nivel de ingresos
- Situación personal
- Información relacionada con su relación con el programa

Cada cliente aparece una única vez en este dataset.

---

## Fases del Análisis

### Fase 1 — Exploración Inicial

**Objetivo**  
Comprender qué datos se tienen disponibles, su estructura, formato y posibles problemas antes de iniciar el análisis.

**Qué se hizo**

- **Revisión de dimensiones**
  - *Customer Flight Activity*:
    - Filas: **405.624**
    - Columnas: **10**
    - Muchas filas (actividad mensual) y pocas columnas.
  - *Customer Loyalty History*:
    - Filas: **16.737**
    - Columnas: **16**
    - Una fila por cliente y mayor detalle de variables.

- **Inspección de tipos de datos**
  - *Flight*: mayoritariamente numéricas.
  - *Loyalty*: mezcla de variables numéricas y categóricas.

- **Búsqueda de valores nulos**
  - *Flight*: no presenta valores nulos.
  - *Loyalty*: nulos informativos en `salary` (ingresos no declarados) y nulos en variables de cancelación.

- **Detección de duplicados**
  - *Flight*: pequeño porcentaje de filas duplicadas.
  - *Loyalty*: no presenta duplicados.

- **Detección de valores anómalos**
  - Se detecta salario negativo, atribuible a un error de signo.

---

### Fase 2 — Limpieza y Preparación de Datos

**Objetivo**  
Garantizar la coherencia y consistencia de los datos antes del análisis y la integración.

**Qué se hizo**

- Conversión de `loyalty_number` a string en ambos datasets.
- Corrección del valor negativo en `salary` mediante su valor absoluto.
- Eliminación de filas duplicadas en el dataset de actividad de vuelo.
- Homogeneización de nombres de columnas para mantener un formato uniforme.

---

### Fase 3 — Integración de Datos

**Objetivo**  
Unir la información de comportamiento de vuelo con el perfil del cliente.

**Método**

- Se utiliza `merge` como método de combinación.
- Tipo de combinación: **LEFT JOIN**, usando *Customer Flight Activity* como dataset principal.

**Justificación**
- Se conservan todas las observaciones de actividad de vuelo.
- Se añade información del perfil del cliente cuando existe.
- No se requieren perfiles sin actividad de vuelo para este análisis.

---

### Fase 4 — Análisis Estadístico Descriptivo

**Objetivo**  
Obtener una visión general del comportamiento de las variables numéricas y categóricas.

#### Variables numéricas

- **Total Flights**
  - Media muy superior a la mediana → asimetría positiva.
  - Alta dispersión y presencia de outliers.
  - La mayoría de clientes vuela poco; unos pocos concentran muchos vuelos.

- **CLV**
  - Media superior a la mediana → clientes de alto valor elevan la media.
  - Gran heterogeneidad.
  - Valores máximos muy elevados.

- **Salary**
  - Media y mediana similares → distribución casi simétrica.
  - Variabilidad moderada.
  - Presencia de algunos salarios altos.

**Conclusión**  
✔ Existen variables muy desiguales (`total_flights`, `CLV`) y otras más estables (`salary`).

#### Variables categóricas

- Análisis mediante `describe(include='object')`.
- Tablas de frecuencia absoluta y relativa (%) para país, género, nivel educativo, etc.

**Conclusión**  
✔ Las variables categóricas permiten segmentar y entender la composición de la clientela.

---

### Fase 5 — Visualización de Datos

**Objetivo**  
Detectar patrones y tendencias mediante representaciones gráficas.

**Gráficas principales**
- Barplot → categoría + numérica; usar horizontal si hay muchas categorías o nombres largos
- Scatterplot  → numérica + numérica; cada punto = un dato, ver correlación o dispersión
- Pie chart → categoría → proporción del total; ideal para ver distribuciones relativas, no para comparar valores exactos.

**Hallazgos relevantes**

- Fuerte estacionalidad:
  - Picos de reservas en verano (junio–agosto) y en diciembre.
  - Mínimos en enero y febrero.
- Ontario y British Columbia concentran la mayor cantidad de clientes.
- Los clientes casados representan el grupo más numeroso.
- La tarjeta **Star** concentra la mayoría de clientes.

**Conclusión**  
✔ Las visualizaciones refuerzan los resultados obtenidos en la estadística descriptiva.

---

### Fase 6 — Evaluación de Diferencias por Nivel Educativo

**Objetivo**  
Analizar si el nivel educativo influye en el número de vuelos reservados.

**Conclusiones**

- El nivel educativo **no parece influir de forma significativa** en la cantidad de vuelos reservados.
- El comportamiento de reserva es bastante homogéneo entre los distintos niveles educativos.

---

## Estructura del Repositorio

- **README.md:** documentación del proyecto.  
- **pdf_evaluacion_final.pdf:** enunciado del ejercicio.  
- **evaluacion-final-eaguilothio.ipynb:** notebook principal con el análisis completo.  
- **data/:** carpeta con los archivos CSV utilizados.

---

## Librerías Principales

### Manipulación y análisis de datos
- **pandas** → Carga, limpieza y análisis de datos tabulares.
- **numpy** → Cálculos numéricos y manejo de valores faltantes (`NaN`).
- **os** → Gestión de rutas y carga de archivos.

### Visualización
- **matplotlib** → Gráficos con alto nivel de personalización.
- **seaborn** → Visualizaciones estadísticas claras basadas en matplotlib.



