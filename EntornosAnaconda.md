# 🐍 Anaconda Cheatsheet - Gestión de Entornos Virtuales

> **Guía de referencia rápida para estudiantes**  
> Comandos esenciales para trabajar con entornos virtuales en Anaconda

---

## 📚 Tabla de Contenidos

- [¿Qué es un entorno virtual?](#qué-es-un-entorno-virtual)
- [Crear Entornos](#crear-entornos)
- [Activar y Desactivar](#activar-y-desactivar)
- [Listar Entornos](#listar-entornos)
- [Gestión de Paquetes](#gestión-de-paquetes)
- [Exportar e Importar](#exportar-e-importar)
- [Eliminar Entornos](#eliminar-entornos)
- [Comandos de Mantenimiento](#comandos-de-mantenimiento)
- [Buenas Prácticas](#buenas-prácticas)

---

## ¿Qué es un entorno virtual?

Un **entorno virtual** es un espacio aislado donde puedes instalar paquetes de Python sin afectar tu instalación global. Esto te permite:

- ✅ Trabajar en múltiples proyectos con diferentes versiones de paquetes
- ✅ Evitar conflictos entre dependencias
- ✅ Compartir fácilmente tu configuración con otros
- ✅ Mantener tu sistema limpio y organizado

---

## 🆕 Crear Entornos

### Crear entorno básico
```bash
conda create --name mi_entorno
```

### Crear con versión específica de Python
```bash
conda create --name mi_entorno python=3.11
```

### Crear con paquetes incluidos
```bash
conda create --name mi_entorno python=3.11 numpy pandas matplotlib
```

### Crear desde archivo `environment.yml`
```bash
conda env create -f environment.yml
```

### Crear en ubicación específica
```bash
conda create --prefix ./mi_entorno python=3.11
```

---

## ▶️ Activar y Desactivar

### Activar un entorno
```bash
conda activate mi_entorno
```

### Desactivar el entorno actual
```bash
conda deactivate
```

> **💡 Tip:** Cuando activas un entorno, verás su nombre entre paréntesis al inicio de tu línea de comandos:  
> `(mi_entorno) usuario@computadora:~$`

---

## 📋 Listar Entornos

### Ver todos los entornos disponibles
```bash
conda env list
```

### Alternativa
```bash
conda info --envs
```

### Ver información del entorno actual
```bash
conda info
```

---

## 📦 Gestión de Paquetes

### Instalar paquetes

```bash
# Instalar un paquete
conda install numpy

# Instalar versión específica
conda install numpy=1.24.0

# Instalar desde un canal específico
conda install -c conda-forge scikit-learn

# Instalar múltiples paquetes
conda install pandas matplotlib seaborn jupyter
```

### Actualizar paquetes

```bash
# Actualizar un paquete específico
conda update numpy

# Actualizar todos los paquetes
conda update --all
```

### Remover paquetes

```bash
conda remove numpy
```

### Listar paquetes instalados

```bash
# Ver todos los paquetes en el entorno actual
conda list

# Buscar si un paquete está disponible
conda search numpy
```

---

## 💾 Exportar e Importar

### Exportar entorno a archivo YAML (Recomendado)

```bash
# Exportar todo el entorno
conda env export > environment.yml

# Exportar sin información de build (más portable)
conda env export --no-builds > environment.yml

# Exportar solo paquetes instalados manualmente
conda env export --from-history > environment.yml
```

### Exportar lista simple de paquetes

```bash
conda list --export > requirements.txt
```

### Importar/Recrear entorno

```bash
# Desde archivo environment.yml
conda env create -f environment.yml

# Desde requirements.txt
conda create --name mi_entorno --file requirements.txt
```

### Ejemplo de archivo `environment.yml`

```yaml
name: proyecto_datos
channels:
  - conda-forge
  - defaults
dependencies:
  - python=3.11
  - numpy
  - pandas
  - matplotlib
  - scikit-learn
  - jupyter
  - pip
  - pip:
    - paquete-solo-disponible-en-pip
```

---

## 🗑️ Eliminar Entornos

### Eliminar un entorno completo

```bash
conda env remove --name mi_entorno
```

### Alternativa

```bash
conda remove --name mi_entorno --all
```

> **⚠️ Advertencia:** Esta acción es irreversible. Asegúrate de exportar tu entorno antes si quieres conservar su configuración.

---

## 🔧 Comandos de Mantenimiento

### Limpiar caché

```bash
# Limpiar paquetes y caché no utilizados
conda clean --all
```

### Actualizar Conda

```bash
# Actualizar conda a la última versión
conda update conda

# Actualizar Anaconda completo
conda update anaconda
```

### Ver información del sistema

```bash
conda info
```

### Configuración de canales

```bash
# Ver canales configurados
conda config --show channels

# Agregar un canal
conda config --add channels conda-forge

# Ver toda la configuración
conda config --show
```

---

## 🔄 Clonar Entornos

### Crear una copia exacta de un entorno

```bash
conda create --name nuevo_entorno --clone entorno_existente
```

> **💡 Uso:** Útil para experimentar sin afectar tu entorno de trabajo principal.

---

## ✨ Buenas Prácticas

### 1. **Usa un entorno por proyecto**
Cada proyecto debe tener su propio entorno para evitar conflictos.

```bash
conda create --name proyecto_tesis python=3.11
conda create --name curso_ml python=3.10
```

### 2. **Nombra tus entornos descriptivamente**
```bash
# ❌ Evita nombres genéricos
conda create --name test

# ✅ Usa nombres descriptivos
conda create --name analisis_ventas_2024
```

### 3. **Documenta tus entornos**
Siempre exporta tu entorno antes de compartir tu proyecto:

```bash
conda env export --from-history > environment.yml
```

### 4. **Mantén actualizado Conda**
```bash
conda update conda
```

### 5. **Limpia regularmente**
```bash
conda clean --all
```

---

## 📖 Atajos y Comandos Resumidos

| Acción | Comando |
|--------|---------|
| Crear entorno | `conda create -n nombre python=3.11` |
| Activar | `conda activate nombre` |
| Desactivar | `conda deactivate` |
| Listar entornos | `conda env list` |
| Instalar paquete | `conda install paquete` |
| Listar paquetes | `conda list` |
| Exportar | `conda env export > environment.yml` |
| Importar | `conda env create -f environment.yml` |
| Eliminar | `conda env remove -n nombre` |
| Clonar | `conda create -n nuevo --clone viejo` |
| Limpiar | `conda clean --all` |

---

## 🆘 Solución de Problemas Comunes

### El comando `conda` no se reconoce
**Solución:** Asegúrate de que Anaconda esté en tu PATH o usa Anaconda Prompt.

### Error al activar entorno
**Solución:** Inicializa conda para tu shell:
```bash
conda init bash  # o zsh, powershell, etc.
```

### Conflictos de paquetes
**Solución:** Crea un nuevo entorno limpio e instala solo lo necesario.

### Espacio en disco lleno
**Solución:** Limpia archivos innecesarios:
```bash
conda clean --all
```

---

## 📚 Recursos Adicionales

- [Documentación oficial de Conda](https://docs.conda.io/)
- [Conda Cheat Sheet (PDF oficial)](https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html)
- [Anaconda Package List](https://docs.anaconda.com/free/anaconda/reference/packages/pkg-docs/)

---

## 📝 Notas para Estudiantes

- **Siempre activa tu entorno antes de trabajar** en un proyecto
- **Exporta tu entorno** antes de entregar tareas o proyectos
- **No instales todo en el entorno `base`** - crea entornos específicos
- Si trabajas en equipo, comparte tu archivo `environment.yml`

---

**¿Encontraste útil esta guía?** ⭐ Dale una estrella al repositorio y compártela con tus compañeros.

---

*Última actualización: Noviembre 2025*  
*Contribuciones y sugerencias son bienvenidas* 🚀