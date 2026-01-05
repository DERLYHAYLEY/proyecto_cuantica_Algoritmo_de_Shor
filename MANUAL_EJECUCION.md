# Manual de Ejecucion - Algoritmo de Shor

## OBJETIVO
Este manual te guiará paso a paso en la instalación y ejecución del proyecto de factorización RSA mediante el algoritmo de Shor.

---

## TABLA DE CONTENIDOS
1. [Requisitos Previos](#requisitos-previos)
2. [Instalación](#instalación)
3. [Ejecución del Notebook](#ejecución-del-notebook)
4. [Guía de Uso](#guía-de-uso)
5. [Solución de Problemas](#solución-de-problemas)
6. [Resultados Esperados](#resultados-esperados)

---

## 1. Requisitos Previos

### Sistema Operativo
- [OK] Windows 10/11
- [OK] macOS 10.15+
- [OK] Linux (Ubuntu 20.04+)

### Python
- **Versión requerida**: Python 3.8 o superior
- **Recomendado**: Python 3.10 o 3.11

#### Verificar versión de Python:
```bash
python --version
# o
python3 --version
```

Si no tienes Python instalado, descargalo desde:
--> https://www.python.org/downloads/

### Editor de Codigo
Elige una de estas opciones:

**Opción 1: Visual Studio Code (Recomendado)**
- Descargar: https://code.visualstudio.com/
- Instalar extensiones:
  - Python (Microsoft)
  - Jupyter (Microsoft)

**Opción 2: Jupyter Notebook**
```bash
pip install notebook
```

**Opción 3: JupyterLab**
```bash
pip install jupyterlab
```

---

## 2. Instalación

### Paso 1: Descargar el Proyecto
```bash
# Si usas Git:
git clone <URL_DEL_REPOSITORIO>
cd proyecto_ccuantica

# O descomprime el archivo ZIP del proyecto
```

### Paso 2: Crear Entorno Virtual (Opcional pero Recomendado)

#### En Windows:
```bash
python -m venv .venv
.venv\Scripts\activate
```

#### En macOS/Linux:
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Paso 3: Instalar Dependencias

#### Opción A: Usando requirements.txt (Recomendado)
```bash
pip install -r requirements.txt
```

#### Opción B: Instalación Manual
```bash
pip install qiskit qiskit-aer qiskit-ibm-runtime matplotlib numpy pandas
```

### Paso 4: Verificar Instalación
```bash
python -c "import qiskit; print('Qiskit version:', qiskit.__version__)"
```

**Salida esperada:**
```
Qiskit version: 1.x.x
```

---

## 3. Ejecución del Notebook

### Opcion A: Visual Studio Code

1. **Abrir VS Code**
   ```bash
   code .
   ```

2. **Abrir el notebook**
   - Haz clic en `SHOR -CCUANTICA.ipynb`

3. **Seleccionar Kernel**
   - Arriba a la derecha, clic en "Select Kernel"
   - Elige el entorno Python que creaste (.venv)

4. **Ejecutar celdas**
   - **Ejecutar una celda**: Shift + Enter
   - **Ejecutar todas**: "Run All" en la barra superior
   - **Ejecutar hasta aquí**: Click derecho → "Run Above"

### Opcion B: Jupyter Notebook

1. **Iniciar Jupyter**
   ```bash
   jupyter notebook
   ```

2. **Abrir el notebook**
   - Se abrirá tu navegador
   - Navega a `SHOR -CCUANTICA.ipynb`
   - Haz clic para abrir

3. **Ejecutar celdas**
   - **Una celda**: Shift + Enter
   - **Todas**: Cell → Run All

### Opcion C: JupyterLab

1. **Iniciar JupyterLab**
   ```bash
   jupyter lab
   ```

2. **Abrir y ejecutar** (similar a Jupyter Notebook)

---

## 4. Guía de Uso

### Estructura del Notebook

El notebook esta organizado en **13 secciones principales**:

#### * Seccion 1: Instalacion y Configuracion
- Instala dependencias automáticamente
- Importa librerías necesarias
- Tiempo: ~2-3 minutos

#### * Seccion 2: Implementacion de RSA Clasico
- Clase `RSA` para cifrado/descifrado
- Ejemplo con N=15 (p=3, q=5)
- Tiempo: instantaneo

#### * Seccion 3-4: Componentes Cuanticos
- Implementación de QFT (Transformada Cuántica de Fourier)
- Exponenciación modular controlada
- Construcción del circuito cuántico completo
- Tiempo: instantaneo (solo definiciones)

#### * Seccion 5-6: Algoritmo de Shor Completo
- Post-procesamiento clásico
- Función principal `shor_algorithm()`
- Tiempo: varia segun N

#### * Seccion 7-8: Comparaciones y Visualizaciones
- Factorización clásica vs cuántica
- Gráficos comparativos
- Tiempo: ~5-10 segundos

#### * Seccion 9: Experimentos
- **Experimento 1**: Factorizar N=15
  - Tiempo: ~5-10 segundos
  - Genera histograma de resultados
  
- **Experimento 2**: Factorizar N=21
  - Tiempo: ~10-15 segundos
  - Compara tiempos de ejecución

#### * Seccion 10-13: Analisis y Conclusiones
- Complejidad computacional
- Limitaciones actuales
- Impacto en seguridad
- Referencias bibliográficas

### Como Modificar Parametros

#### Cambiar el número a factorizar:
```python
# En la Seccion 9, modifica:
result = shor_algorithm(N=35, a=2, shots=2048, verbose=True)
#                         ^     ^        ^
#                         |     |        |
#                   Numero  Base  Mediciones
```

#### Parametros importantes:
- **N**: Numero a factorizar (prueba: 15, 21, 35, 77, 143)
- **a**: Base para exponenciacion (debe ser coprima con N)
- **shots**: Numero de mediciones cuanticas (recomendado: 1024-4096)
- **verbose**: Mostrar informacion detallada (True/False)

---

## 5. Solucion de Problemas

### [ERROR] ModuleNotFoundError: No module named 'qiskit'

**Solución:**
```bash
pip install qiskit qiskit-aer
```

### [ERROR] Kernel died unexpectedly

**Causa**: Notebook intentó usar demasiada memoria (N muy grande)

**Solución:**
- Reduce N a un valor más pequeño (≤ 35)
- Cierra otros programas
- Reinicia el kernel

### [ERROR] No module named 'qiskit_aer'

**Solución:**
```bash
pip install qiskit-aer
```

### [ERROR] Las graficas no se muestran

**Solución:**
```python
# Agrega al inicio del notebook:
%matplotlib inline
```

### [ERROR] ImportError: cannot import name 'Aer'

**Causa**: Version incompatible de Qiskit

**Solucion:**
```bash
pip uninstall qiskit qiskit-aer
pip install qiskit qiskit-aer
```

### [AVISO] La simulacion es muy lenta

**Normal para N grandes**. El simulador clasico crece exponencialmente:
- N=15: ~5-10 segundos [OK]
- N=21: ~10-20 segundos [OK]
- N=35: ~30-60 segundos [AVISO]
- N>77: varios minutos o inviable [NO RECOMENDADO]

**Recomendacion**: Usa N=15 o N=21 para demostraciones

---

## 6. Resultados Esperados

### [EXITO] Salida Exitosa - Experimento 1 (N=15)

```
================================================================================
EJECUTANDO ALGORITMO DE SHOR PARA N = 15
================================================================================

[PARAMETROS]
   N = 15 (numero a factorizar)
   a = 7 (base elegida)
   gcd(a, N) = 1

   [FASE CUANTICA]
   Construyendo circuito cuantico...
   * Qubits de conteo: 8
   * Qubits auxiliares: 4
   * Qubits totales: 12
   * Profundidad del circuito: 2034

   Ejecutando simulacion (2048 shots)...
   * Circuito transpilado con 2156 de profundidad
   [OK] Simulacion completada

   [POST-PROCESAMIENTO CLASICO]
   Analizando 256 resultados de medicion...

   Top 5 mediciones mas frecuentes:
   * |00000000> -> 0 -> fase~0.0000 (apariciones: 502)
   * |01000000> -> 64 -> fase~0.2500 (apariciones: 246)
   * |10000000> -> 128 -> fase~0.5000 (apariciones: 252)
   * |11000000> -> 192 -> fase~0.7500 (apariciones: 244)

   Analizando medicion 64:
   * Fase estimada: 0.250000
   * Fraccion: 1/4 -> periodo candidato r = 4
   * Periodo r = 4 es par [OK]
   * gcd(7^2 - 1, 15) = 3
   * gcd(7^2 + 1, 15) = 5

   *** FACTORES ENCONTRADOS! ***
   15 = 3 x 5

================================================================================
[EXITO] 15 = 3 x 5
Tiempo de ejecucion: 8.452 segundos
================================================================================
```

### Graficos Generados

1. **Histograma de Resultados Cuanticos**
   - Muestra las frecuencias de medicion
   - Picos visibles en fases 0, 0.25, 0.5, 0.75

2. **Comparacion Cuantico vs Clasico**
   - Grafico de barras con tiempos de ejecucion
   - Cuantico: ~8s, Clasico: <0.001s (para N=15)

3. **Analisis de Escalabilidad** (Celda 2)
   - Graficos log-log de operaciones vs N
   - Graficos log-log de tiempo vs N
   - Tabla comparativa de rendimiento

---

## Consejos y Mejores Practicas

### Para Presentaciones/Demostraciones
1. Ejecuta primero **solo N=15** (mas rapido, resultados claros)
2. Guarda las graficas generadas (clic derecho -> Guardar)
3. Toma screenshots de los resultados
4. Prepara explicacion de las mediciones

### Guardar Resultados
```python
# Al final de cada experimento, agrega:
plt.savefig('resultados/resultado_N15.png', dpi=300, bbox_inches='tight')
```

### Optimizar Tiempo de Ejecucion
- Reduce `shots` a 1024 para pruebas rápidas
- Usa `verbose=False` si solo necesitas resultados
- Ejecuta solo las secciones necesarias

### Documentar Experimentos
Crea una carpeta `resultados/` y guarda:
- Graficos generados
- Tiempos de ejecucion
- Notas sobre parametros usados

---

## Preguntas Frecuentes (FAQ)

### [Q] Cuanto tiempo tarda la ejecucion completa?
- **Celda 1 (Principal)**: 10-20 minutos
- **Celda 2 (Escalabilidad)**: 5-10 minutos
- **Total**: ~15-30 minutos

### [Q] Puedo factorizar numeros mas grandes?
Sí, pero con limitaciones:
- **N <= 77**: Recomendado [OK]
- **77 < N <= 143**: Lento pero posible [AVISO]
- **N > 143**: Muy lento o inviable en simulador [NO RECOMENDADO]

### [Q] Por que el simulador es tan lento?
El simulador clasico debe simular todos los estados cuanticos:
- **12 qubits**: 2^12 = 4,096 estados
- **Crece exponencialmente** con mas qubits
- Hardware cuantico real seria mucho mas rapido

### [Q] Que significa "shots"?
Numero de veces que se mide el circuito cuantico:
- Mas shots = resultados mas precisos
- Menos shots = ejecucion mas rapida
- Recomendado: 1024-4096

---

## Soporte

Si encuentras problemas no listados aqui:
1. Verifica que todas las dependencias esten instaladas
2. Revisa la version de Python (>=3.8)
3. Consulta la documentacion de Qiskit: https://qiskit.org/
4. Contacta al autor del proyecto

---



