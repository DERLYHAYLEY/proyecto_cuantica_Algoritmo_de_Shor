# Algoritmo de Shor para Factorizacion de Claves RSA

## Descripcion del Proyecto

Este proyecto implementa el **algoritmo de Shor** utilizando computacion cuantica simulada con **Qiskit** para demostrar la vulnerabilidad del sistema criptografico **RSA** frente a computadoras cuanticas.

### Objetivo General
Demostrar la vulnerabilidad del sistema criptografico RSA frente a la computacion cuantica mediante la implementacion del algoritmo de Shor utilizando un simulador cuantico (Qiskit).

### Universidad
**Universidad Nacional de San Antonio Abad del Cusco**  
Departamento Academico de Informatica - Computacion Cuantica  
Enero 2026

---

## Caracteristicas Principales

- Implementacion completa del algoritmo de Shor en Qiskit  
- Simulacion de factorizacion de numeros semiprimos (RSA)  
- Comparacion cuantica vs clasica (Trial Division, Pollard's Rho)  
- Analisis de escalabilidad hasta RSA-2048  
- Visualizaciones interactivas de resultados  
- Documentacion exhaustiva con referencias academicas  

---

## Estructura del Repositorio

```
proyecto_ccuantica/
|
+-- SHOR -CCUANTICA.ipynb       # Notebook principal con implementacion
+-- README.md                    # Este archivo
+-- MANUAL_EJECUCION.md         # Guia paso a paso de ejecucion
+-- requirements.txt             # Dependencias del proyecto
+-- resultados/                  # Carpeta para graficos (generados al ejecutar)
```

---

## Componentes Implementados

### 1. **RSA Clasico**
- Generacion de claves publicas/privadas
- Cifrado y descifrado de mensajes
- Demostracion de funcionamiento

### 2. **Algoritmo de Shor - Componentes Cuanticos**
- **QFT (Transformada Cuantica de Fourier Inversa)**
- **Exponenciacion Modular Controlada** (`a^x mod N`)
- **Post-procesamiento Clasico** (Fracciones continuas)
- **Busqueda de factores** mediante GCD

### 3. **Experimentos y Comparaciones**
- Factorizacion de N=15 (3 x 5)
- Factorizacion de N=21 (3 x 7)
- Analisis de escalabilidad (hasta N=30,137)
- Proyecciones para RSA-2048

### 4. **Visualizaciones**
- Histogramas de resultados cuanticos
- Graficas de comparacion cuantico vs clasico
- Analisis de operaciones y tiempos de ejecucion

---

## Requisitos Tecnicos

### Software Necesario
- **Python**: 3.8 o superior
- **Jupyter Notebook** o **VS Code** con extension de Jupyter
- Librerias Python (ver `requirements.txt`)

### Dependencias Principales
```
qiskit >= 1.0.0
qiskit-aer >= 0.13.0
numpy >= 1.24.0
matplotlib >= 3.7.0
pandas >= 2.0.0
```

---

## Instalacion Rapida

### Opcion 1: Instalacion Manual
```bash
# Instalar dependencias
pip install qiskit qiskit-aer matplotlib numpy pandas

# Abrir el notebook
jupyter notebook "SHOR -CCUANTICA.ipynb"
```

### Opcion 2: Usando requirements.txt
```bash
# Instalar todas las dependencias
pip install -r requirements.txt

# Ejecutar en VS Code o Jupyter
code "SHOR -CCUANTICA.ipynb"
```

---

## Resultados Principales

### Experimento 1: Factorizacion de N=15
- **Metodo Cuantico (Shor)**: Factorizacion exitosa en ~5-10 segundos
- **Metodo Clasico**: < 1 segundo (numero pequeno)
- **Factores encontrados**: 3 x 5 [OK]

### Experimento 2: Factorizacion de N=21
- **Metodo Cuantico (Shor)**: Factorizacion exitosa
- **Factores encontrados**: 3 x 7 [OK]

### Proyecciones para Numeros Grandes

| Tamano | N (aprox) | Trial Division (Clasico) | Shor (Cuantico) |
|--------|-----------|-------------------------|-----------------|
| RSA-64 | 2^64 | ~10^10 anos | ~0.01 segundos |
| RSA-128 | 2^128 | ~10^19 anos | ~0.16 segundos |
| RSA-256 | 2^256 | ~10^38 anos | ~2.6 segundos |
| RSA-512 | 2^512 | ~10^77 anos | ~41 segundos |
| RSA-1024 | 2^1024 | ~10^154 anos | ~11 minutos |
| **RSA-2048** | **2^2048** | **~10^308 anos** | **~1.5 horas** |

> **Conclusion Clave**: El algoritmo de Shor ofrece una **aceleracion EXPONENCIAL** sobre metodos clasicos, convirtiendo un problema intratable en uno resoluble en tiempo polinomial.

---

## Fundamentos Teoricos

### Complejidad Computacional

#### Metodos Clasicos:
- **Division de Prueba**: O(raiz(N)) - Exponencial en bits
- **Pollard's Rho**: O(N^1/4) - Mas eficiente pero aun exponencial

#### Algoritmo de Shor (Cuantico):
- **Complejidad**: O((log N)^3) - **Polinomial**
- **Ventaja**: Exponencial sobre metodos clasicos

### Por que Shor Rompe RSA?

RSA se basa en la dificultad de **factorizar numeros grandes** en tiempo razonable.

**Clasicamente**: Factorizar RSA-2048 tomaria ~10^308 anos  
**Con Shor**: Una computadora cuantica podria hacerlo en ~1.5 horas

---

## Impacto en Seguridad Actual

### Sistemas Vulnerables:
- **RSA** (usado en HTTPS, SSL/TLS, firmas digitales)
- **Diffie-Hellman** (intercambio de claves)
- **Curvas Elipticas** (variantes tambien vulnerables)

### Estado Actual (2026):
- IBM tiene ~1,000 qubits fisicos
- Se necesitan ~4,000 qubits **logicos** para romper RSA-2048
- Estimacion: **10-15 anos** para amenaza real

### Recomendaciones:
1. Transicion a **criptografia post-cuantica** (NIST esta estandarizando)
2. Implementar **crypto-agility** (capacidad de cambiar algoritmos)
3. Monitorear avances en hardware cuantico

---

## Limitaciones Actuales

### Del Simulador:
- Limitado a ~30-40 qubits (limitacion de memoria)
- No modela ruido/decoherencia real
- Simulacion es exponencialmente mas lenta que hardware real

### De Hardware Cuantico Real:
- Tasa de error alta (~0.1-1% por puerta)
- Correccion de errores requiere muchos qubits fisicos
- Ratio actual: ~1000 qubits fisicos -> 1 qubit logico

---

## Referencias Bibliograficas

1. **Shor, P. W.** (1997). "Polynomial-Time Algorithms for Prime Factorization and Discrete Logarithms on a Quantum Computer". *SIAM Journal on Computing*.

2. **Nielsen, M. A., & Chuang, I. L.** (2010). "Quantum Computation and Quantum Information". Cambridge University Press.

3. **Qiskit Development Team** (2024). "Qiskit Documentation". https://qiskit.org/documentation/

4. **Rivest, R. L., Shamir, A., & Adleman, L.** (1978). "A Method for Obtaining Digital Signatures and Public-Key Cryptosystems". *Communications of the ACM*.

5. **NIST** (2024). "Post-Quantum Cryptography Standardization". https://csrc.nist.gov/projects/post-quantum-cryptography

6. **IBM Quantum** (2024). "IBM Quantum Experience". https://quantum-computing.ibm.com/

---

## Autores

**[Tu Nombre Aqui]**  
Universidad Nacional de San Antonio Abad del Cusco  
Departamento de Informatica - Computacion Cuantica

---

## Licencia

Este proyecto es de código abierto con fines educativos y de investigación.

---

## Contribuciones

Este es un proyecto educativo. Para sugerencias o mejoras:
1. Revisa el codigo en el notebook
2. Prueba las implementaciones
3. Documenta cualquier hallazgo

---

## Contacto
**[Tu Email]**  
Universidad Nacional de San Antonio Abad del Cusco

---

## Reconocimientos

- **Qiskit Team** por el excelente framework de computacion cuantica
- **IBM Quantum** por recursos educativos
- **Universidad Nacional de San Antonio Abad del Cusco** por el apoyo academico

---


