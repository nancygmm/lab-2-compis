# Laboratorio 2 - Sistema de Tipos con ANTLR

Este laboratorio implementa un sistema de análisis sintáctico y de tipos usando ANTLR y Python, ejecutado en un contenedor Docker.

## Estructura del Proyecto

- `SimpleLang.g4`: gramática en ANTLR para un lenguaje simple.
- `Driver.py`: analizador basado en Visitor.
- `DriverListener.py`: analizador basado en Listener.
- `program_test_pass.txt`: archivo de entrada válido.
- `program_test_no_pass.txt`: archivo con errores de tipo.
- `Dockerfile`: para levantar el entorno fácilmente.
- `README.md`: este archivo.

---

## Comandos utilizados

### Movernos a la carpeta del proyecto

```bash
cd /Users/nancymazariegos/Documents/Repos/lab-2-compis
```

### Levantar el contenedor con Docker

```bash
docker build --rm -t lab2-image . && docker run --rm -ti -v "$(pwd)/program":/program lab2-image
```

### Generar archivos de Lexer y Parser con ANTLR

Dentro del contenedor:

```bash
cd /program
antlr -Dlanguage=Python3 -visitor SimpleLang.g4
antlr -Dlanguage=Python3 -listener SimpleLang.g4
```

---

## Pruebas realizadas

### Archivo que **sí pasa**

```bash
python3 Driver.py program_test_pass.txt
python3 DriverListener.py program_test_pass.txt
```

Resultado esperado:
```
Type checking passed
```

---

### Archivo que **no pasa**

```bash
python3 Driver.py program_test_no_pass.txt
python3 DriverListener.py program_test_no_pass.txt
```

Resultado esperado: errores de tipo, por ejemplo:

```
Error: type mismatch at line X
```

---


## 📹 Video

🔗 [Video de YouTube (no listado)](https://youtu.be/2ieL55P4EVA)  

---
