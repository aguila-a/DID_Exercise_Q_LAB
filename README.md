# Problem Set - Differences-in-Differences (DID)

## Descripción
Este repositorio contiene la solución al Problem Set sobre Differences-in-Differences (DID) en el curso de Econometría Aplicada Avanzada. Se incluyen análisis de los efectos de la entrada de China en la OMC en 2001 sobre el empleo manufacturero en EE.UU. y la evaluación del impacto del EITC en la oferta laboral de mujeres solteras.

## Contenido del Repositorio
- `Problem_Set_DID.ipynb`: Notebook de Jupyter con la implementación de los ejercicios y análisis.
- `data/`: Carpeta con los datos descargados y preprocesados.
- `README.md`: Este archivo, que explica la estructura del repositorio.
- `results/`: Carpeta con los resultados generados, incluyendo tablas y gráficos.

## Problemas Resueltos
### **Problema 1: Impacto de la Entrada de China en la OMC**
#### **Datos**
- Se descargan los datos del Census County Business Patterns (CBP) para los años 1998-2006.
- Se mantienen las variables: `FIPSTATE`, `YEAR`, `NAICS`, `EMP`, `QP1`, `AP`, `EST`.

#### **Pasos del Análisis**
1. **Nivel de observación**: Se identifica que la unidad de observación es el sector NAICS-3 por estado y año.
2. **Creación de variables**:
   - `post_china`: Dummy que toma valor 1 si `YEAR >= 2001`, 0 en caso contrario.
   - `manuf`: Dummy que toma valor 1 si `NAICS` comienza con '3' (sector manufacturero), 0 en caso contrario.
3. **Cálculo de la matriz 2x2 para DID**: Se define el grupo de tratamiento (`manuf == 1`) y el grupo de control (`manuf == 0`). Se calcula la diferencia antes y después de 2001.
4. **Estimación del modelo DID**: Se realiza una regresión de `EMP` con la interacción `post_china * manuf`.
5. **DID para otros resultados**: Se extiende el análisis a `EST` y `QP1/EMP`.
6. **Regresión con logaritmos**: Se evalúa `log(EMP)` para verificar la necesidad de transformación.
7. **Estudio de eventos**: Se crean dummies de año y sus interacciones con `manuf`.
8. **Estimación del estudio de eventos**: Se evalúa el efecto a lo largo del tiempo sobre `log(EMP)`, `log(EST)`, y `QP1/EMP`.

### **Problema 2: Impacto del EITC en la Oferta Laboral**
#### **Datos**
- Se utiliza el archivo `eitc.dta` con datos de mujeres solteras de 20-54 años con menos de secundaria.

#### **Pasos del Análisis**
1. **Tabla resumen de datos**.
2. **Cálculo de medias por grupo**: Se comparan mujeres sin hijos, con 1 hijo y con 2+ hijos.
3. **Creación de variables**:
   - `anykids`: Dummy que toma 1 si tiene al menos 1 hijo, 0 en caso contrario.
   - `post93`: Dummy que toma 1 si `YEAR >= 1994`, 0 en caso contrario.
4. **Estimación de DID**: Se realiza una regresión de ingresos en función de `post93 * anykids`.
5. **Inclusión de efectos fijos por estado y año**.
6. **Incorporación de controles adicionales (`urate`, `nonwhite`, `age`, `ed`, `unearn`)**.
7. **Estimación diferenciada por número de hijos**.
8. **Análisis de placebo (1992-1993 como periodo tratado)**.

## Requisitos
Para ejecutar el código es necesario tener instalado Python y las siguientes librerías:
```bash
pip install pandas numpy statsmodels matplotlib seaborn
```

## Uso
1. Clona el repositorio:
   ```bash
   git clone https://github.com/tu_usuario/tu_repositorio.git
   ```
2. Accede al directorio:
   ```bash
   cd tu_repositorio
   ```
3. Abre el notebook en Jupyter:
   ```bash
   jupyter notebook Problem_Set_DID.ipynb
   ```

## Resultados Principales
- Se encuentra que la entrada de China en la OMC tuvo un efecto negativo significativo en el empleo manufacturero de EE.UU., con impactos de largo plazo.


## Autores
- Integrantes del equipo: Anderson Aguila y Zarit de la Cruz

---
Repositorio para el curso de **Econometría Aplicada Avanzada**, Profesor(a): **Cristina Tello-Trillo**.

