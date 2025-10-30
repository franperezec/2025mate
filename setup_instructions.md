# 🔧 Guía de Configuración del Entorno

## Gestión de Entornos con Anaconda

### 1. Instalación de Anaconda

Si no tienes Anaconda instalado:
- Descarga desde: https://www.anaconda.com/download
- Sigue las instrucciones para tu sistema operativo

### 2. Crear el entorno mate2025

#### Opción A: Usando el archivo environment.yml (Recomendado)
```bash
# Navegar al directorio del curso
cd 2025MATECSCGITHUB

# Crear el entorno desde el archivo
conda env create -f environment.yml

# Activar el entorno
conda activate mate2025
```

#### Opción B: Creación manual desde terminal
```bash
# Crear entorno con Python 3.12
conda create -n mate2025 python=3.12

# Activar el entorno
conda activate mate2025

# Instalar paquetes esenciales
conda install numpy pandas matplotlib seaborn sympy scipy ipykernel jupyter

# Instalar widgets interactivos
conda install -c conda-forge ipywidgets

# Instalar paquetes adicionales
conda install plotly networkx openpyxl

# Registrar el kernel para Jupyter
python -m ipykernel install --user --name mate2025 --display-name "Python (mate2025)"
```

### 3. Comandos útiles de Anaconda
```bash
# Ver todos los entornos
conda env list

# Activar el entorno
conda activate mate2025

# Desactivar el entorno actual
conda deactivate

# Ver paquetes instalados
conda list

# Actualizar un paquete
conda update numpy

# Instalar un paquete adicional
conda install scikit-learn

# Exportar entorno actual
conda env export > environment.yml

# Eliminar un entorno (si necesario)
conda remove -n mate2025 --all
```

### 4. Configuración de Jupyter
```bash
# Con el entorno activado
conda activate mate2025

# Iniciar Jupyter Lab
jupyter lab

# O Jupyter Notebook clásico
jupyter notebook
```

### 5. Configuración de VS Code

1. Instala la extensión de Python
2. Abre la paleta de comandos (Ctrl+Shift+P)
3. Busca "Python: Select Interpreter"
4. Selecciona el entorno `mate2025`

### 6. Verificación de la instalación
```python
# Ejecuta este script para verificar
import sys
print(f"Python: {sys.version}")

import numpy as np
print(f"NumPy: {np.__version__}")

import pandas as pd
print(f"Pandas: {pd.__version__}")

import sympy as sp
print(f"SymPy: {sp.__version__}")

import matplotlib
print(f"Matplotlib: {matplotlib.__version__}")

print("\n✅ Todas las librerías están instaladas correctamente!")
```

### 7. Solución de problemas comunes

**Error: "conda is not recognized"**
- Asegúrate de haber agregado Anaconda al PATH durante la instalación
- En Windows: reinicia la terminal o usa Anaconda Prompt

**Error al crear el entorno**
```bash
# Actualiza conda primero
conda update conda
conda update anaconda
```

**Jupyter no encuentra el kernel mate2025**
```bash
# Reinstala ipykernel
conda activate mate2025
conda install ipykernel
python -m ipykernel install --user --name mate2025
```

### 8. Widgets interactivos en Jupyter

Para habilitar widgets interactivos:
```bash
# Instalar extensiones
jupyter nbextension enable --py widgetsnbextension

# Para JupyterLab
jupyter labextension install @jupyter-widgets/jupyterlab-manager
```

Ejemplo de uso:
```python
import ipywidgets as widgets
from IPython.display import display

slider = widgets.IntSlider(value=5, min=0, max=10, description='Valor:')
display(slider)
```