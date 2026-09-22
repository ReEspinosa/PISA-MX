# Análisis de los Resultados de México en PISA 2025

Análisis estadístico de los microdatos oficiales de PISA 2025 (OCDE), enfocado en el
desempeño de México: evolución histórica, comparación con el promedio OCDE, niveles de
competencia, desigualdad socioeconómica, brecha de género y uso de inteligencia
artificial en el aprendizaje.

Todas las estimaciones se calculan con el método oficial de la OCDE: promedio
ponderado sobre los 10 valores plausibles de cada estudiante, y margen de error por
BRR con corrección de Fay (80 pesos replicados) combinado con las reglas de Rubin.

## Contenido del repositorio

```
.
├── analisis_pisa_2025.ipynb     Notebook de Python con el análisis completo
├── informe_pisa_2025.pdf        Reporte en formato paper (2 columnas, 2 páginas)
├── figuras/                     Las 6 gráficas generadas por el notebook
└── README.md
```

## Datos

Los microdatos no se incluyen en este repositorio por su tamaño (el archivo de
estudiantes pesa aproximadamente 2 GB). Se descargan directamente de la OCDE:

**Student Questionnaire Data File (SPSS)**
https://www.oecd.org/en/data/datasets/pisa-2025-database.html

Instrucciones de descarga y estructura de carpetas esperada dentro del propio
notebook.

## Metodología

PISA no reporta un puntaje único por estudiante, sino 10 estimaciones plausibles de su
desempeño. Cada estadístico se calcula 10 veces (una por cada valor plausible) y se
promedia el resultado.

El error estándar combina dos fuentes de incertidumbre:

1. **Varianza de muestreo**, estimada con BRR (Balanced Repeated Replication) y
   corrección de Fay, usando los 80 pesos replicados que trae el archivo oficial.
2. **Varianza de imputación**, derivada de la variación entre los 10 valores
   plausibles, combinada mediante las reglas de Rubin.

Una diferencia entre grupos se considera estadísticamente significativa cuando su
valor t supera 1.96 en valor absoluto.

Referencia metodológica completa: *PISA Data Analysis Manual*, OCDE.
https://doi.org/10.1787/9789264056275-en

## Gráficas incluidas

1. Puntaje de México por año (2003-2025)
2. México vs promedio OCDE (2025)
3. Niveles de competencia: ¿cuántos estudiantes no alcanzan el nivel básico?
4. Puntaje por nivel socioeconómico (índice ESCS)
5. Brecha de género por materia, con intervalos de confianza
6. Uso de inteligencia artificial y desempeño, controlando por nivel socioeconómico

## Cómo correr el notebook

Requiere Python 3.10 o superior.

```bash
pip install pandas numpy matplotlib pyreadstat
```

1. Descargar el Student Questionnaire Data File desde el link de la sección Datos.
2. Colocar el archivo `.sav` en una carpeta `datos/` junto al notebook.
3. Abrir `analisis_pisa_2025.ipynb` y correr las celdas en orden.

El notebook detecta automáticamente el archivo correcto entre los `.sav` que haya en
la carpeta, valida sus resultados contra las cifras oficiales publicadas por la OCDE,
y genera las 6 gráficas en la carpeta `figuras/`.

## Fuentes

- OECD (2026). *PISA 2025 Results (Volume I): Future-Ready Students*. OECD Publishing,
  Paris. https://doi.org/10.1787/73451bc5-en
- OECD (2026). *PISA 2025 Database*.
  https://www.oecd.org/en/data/datasets/pisa-2025-database.html
- Instituto Mexicano para la Competitividad (2026). *Resultados PISA 2025: México
  obtiene el puntaje más bajo en Matemáticas y Comprensión Lectora en 20 años*.
- Rubin, D. B. (1987). *Multiple Imputation for Nonresponse in Surveys*. John Wiley &
  Sons.

## Autora

Rebeca Espinosa 
Ciencias de la Computación, UNAM
