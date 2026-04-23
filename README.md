# 📘 COMANDOS DE LINUX – Guía Completa

> Una guía exhaustiva de comandos Linux con explicaciones detalladas, ejemplos prácticos y casos de uso reales para DevOps, administración de sistemas y desarrollo.

![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=flat-square&logo=ubuntu&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-blue.svg)

---

## 📋 Tabla de Contenidos

1. [Descripción General](#descripción-general)
2. [Requisitos](#requisitos)
3. [Estructura del Proyecto](#estructura-del-proyecto)
4. [Comandos por Categoría](#comandos-por-categoría)
   - [Información del Sistema](#1-información-del-sistema)
   - [Navegación y Directorios](#2-navegación-y-directorios)
   - [Gestión de Archivos](#3-gestión-de-archivos)
   - [Visualización de Contenido](#4-visualización-de-contenido)
   - [Búsqueda y Filtrado](#5-búsqueda-y-filtrado)
   - [Procesamiento de Texto](#6-procesamiento-de-texto)
   - [Redirección y Tuberías](#7-redirección-y-tuberías)
   - [Variables de Entorno](#8-variables-de-entorno)
   - [Permisos de Archivos](#9-permisos-de-archivos)
   - [Ayuda y Documentación](#10-ayuda-y-documentación)
   - [Gestión de Paquetes](#11-gestión-de-paquetes)
   - [Procesos](#12-procesos)
   - [Compresión y Archivos](#13-compresión-y-archivos)
   - [Editores de Texto](#14-editores-de-texto)
   - [Networking](#15-networking)
   - [Almacenamiento y Disco](#16-almacenamiento-y-disco)
   - [Systemd y Servicios](#17-systemd-y-servicios)
   - [Cron - Tareas Programadas](#18-cron---tareas-programadas)
   - [Alias - Atajos Personalizados](#19-alias---atajos-personalizados)
   - [TMUX - Multiplexor de Terminal](#20-tmux---multiplexor-de-terminal)
5. [Mejores Prácticas](#mejores-prácticas)
6. [Contribuciones](#contribuciones)
7. [Licencia](#licencia)

---

## Descripción General

Este repositorio contiene una referencia completa de comandos Linux organizados por categorías temáticas. Cada comando incluye:

- **Descripción clara** del propósito y funcionalidad
- **Sintaxis correcta** con opciones comunes
- **Ejemplos prácticos** con entrada y salida
- **Casos de uso reales** en administración de sistemas y DevOps
- **Notas de seguridad** donde corresponda

Ideal para:
- Estudiantes de Linux y administración de sistemas
- Desarrolladores que trabajan en entornos Linux/Unix
- Profesionales de DevOps y Cloud
- Principiantes en la línea de comandos

---

## Requisitos

- Sistema operativo Linux/Unix o macOS
- Terminal Bash, Zsh, o compatible
- Permiso de usuario (sudo cuando sea necesario)
- Conexión a internet (para algunos comandos de red)

### Versiones Compatibles

- **Ubuntu:** 20.04 LTS en adelante
- **Debian:** 10 en adelante
- **CentOS/RHEL:** 7 en adelante
- **macOS:** 10.14 en adelante (con Brew)
- **Alpine Linux:** 3.12 en adelante

---

## Estructura del Proyecto

```
.
├── README.md                          # Este archivo
├── COMANDOS_DE_LINUX.md              # Guía completa con ejemplos
├── CHEATSHEET.md                     # Referencia rápida (próximamente)
├── examples/
│   ├── scripts_basicos/
│   ├── automatizacion/
│   └── monitoreo/
├── CONTRIBUIR.md                     # Guía para contribuidores
└── LICENSE                           # Licencia MIT
```

---

## Comandos por Categoría

### 1. INFORMACIÓN DEL SISTEMA

Comandos para obtener información sobre el sistema operativo y hardware.

#### `whoami`
**Descripción:** Muestra el usuario actual que ha iniciado sesión.

```bash
$ whoami
root
```

---

#### `pwd`
**Descripción:** Imprime el directorio de trabajo actual (ruta completa).

```bash
$ pwd
/home/usuario/proyectos/linux-commands
```

---

#### `uname`
**Descripción:** Muestra información del sistema operativo.

```bash
# Información completa del sistema
$ uname -a
Linux servidor 5.15.0-56-generic #62-Ubuntu SMP Tue Nov 23 19:47:48 UTC 2021 x86_64 GNU/Linux

# Solo versión del kernel
$ uname -r
5.15.0-56-generic

# Máquina (arquitectura)
$ uname -m
x86_64
```

---

#### `date`
**Descripción:** Muestra la fecha y hora actual del sistema.

```bash
$ date
Wed Apr 22 14:35:22 UTC 2024

# Formato personalizado
$ date "+%Y-%m-%d %H:%M:%S"
2024-04-22 14:35:22
```

---

### 2. NAVEGACIÓN Y DIRECTORIOS

Comandos para moverse entre directorios y explorar la estructura de archivos.

#### `ls`
**Descripción:** Lista el contenido del directorio actual. Variantes: `-l` (largo), `-a` (ocultos), `-h` (tamaño legible), `-R` (recursivo).

```bash
# Listado simple
$ ls
archivo.txt  directorio1  directorio2

# Listado detallado con permisos
$ ls -la
total 32
drwxr-xr-x  5 usuario grupo  4096 Apr 22 14:30 .
drwxr-xr-x 18 usuario grupo  4096 Apr 22 10:00 ..
-rw-r--r--  1 usuario grupo   256 Apr 22 14:30 archivo.txt
drwxr-xr-x  2 usuario grupo  4096 Apr 22 14:25 directorio1

# Tamaños legibles (K, M, G)
$ ls -lh
total 32K
-rw-r--r-- 1 usuario grupo 256K Apr 22 14:30 archivo.txt
drwxr-xr-x 2 usuario grupo 4.0K Apr 22 14:25 directorio1

# Listado recursivo
$ ls -R
.:
archivo.txt  directorio1

./directorio1:
archivo2.txt
```

---

#### `cd`
**Descripción:** Cambia el directorio actual. `cd ~` va al home, `cd ..` sube un nivel, `cd -` vuelve al anterior.

```bash
# Cambiar a directorio específico
$ cd /var/www/html

# Ir al home del usuario
$ cd ~

# Subir un nivel
$ cd ..

# Volver al directorio anterior
$ cd -

# Cambiar a raíz
$ cd /
```

---

#### `pushd / popd`
**Descripción:** Maneja una pila de directorios. `pushd` cambia y guarda la posición. `popd` vuelve a la anterior.

```bash
# Cambiar a /tmp y guardar ubicación anterior en la pila
$ pushd /tmp
/tmp ~/proyectos/aplicacion

# Ver la pila
$ dirs
~/proyectos/aplicacion /tmp

# Volver al directorio anterior
$ popd
~/proyectos/aplicacion
```

---

#### `clear`
**Descripción:** Limpia la pantalla de la terminal.

```bash
$ clear
# Borra todo lo visible en la terminal
```

---

### 3. GESTIÓN DE ARCHIVOS

Comandos para crear, copiar, mover y eliminar archivos y directorios.

#### `touch`
**Descripción:** Crea un archivo vacío o actualiza su fecha de modificación.

```bash
# Crear archivo vacío
$ touch archivo.txt
$ ls -la archivo.txt
-rw-r--r-- 1 usuario grupo 0 Apr 22 15:30 archivo.txt

# Crear múltiples archivos
$ touch archivo1.txt archivo2.txt archivo3.txt

# Actualizar fecha de modificación
$ touch archivo.txt
```

---

#### `mkdir`
**Descripción:** Crea directorios. `-p` crea directorios padres si no existen.

```bash
# Crear directorio simple
$ mkdir proyectos

# Crear estructura completa de directorios
$ mkdir -p /var/www/html/app/config

# Crear múltiples directorios
$ mkdir dir1 dir2 dir3
```

---

#### `cp`
**Descripción:** Copia archivos o directorios. `-r` copia directorios recursivamente. `-i` pide confirmación.

```bash
# Copiar archivo
$ cp archivo.txt copia.txt

# Copiar a otro directorio
$ cp archivo.txt ~/backup/

# Copiar directorio completo
$ cp -r directorio/ copia_directorio/

# Copiar con confirmación si existe
$ cp -i archivo.txt destino/
```

---

#### `mv`
**Descripción:** Mueve o renombra archivos y directorios.

```bash
# Renombrar archivo
$ mv archivo.txt nuevo_nombre.txt

# Mover archivo a otro directorio
$ mv archivo.txt ~/backup/

# Mover y renombrar
$ mv archivo.txt ~/backup/nuevo_nombre.txt

# Mover directorio
$ mv directorio_viejo/ directorio_nuevo/
```

---

#### `rm`
**Descripción:** ⚠️ **Elimina archivos de forma permanente.** `-r` elimina directorios recursivamente. `-f` fuerza sin confirmación. **¡Sin papelera de reciclaje!**

```bash
# Eliminar archivo individual
$ rm archivo.txt

# Eliminar directorio y contenido
$ rm -r directorio/

# Eliminar sin confirmación (peligroso)
$ rm -rf directorio/

# Eliminar múltiples archivos
$ rm archivo1.txt archivo2.txt archivo3.txt

# Eliminar archivos de forma segura (pide confirmación)
$ rm -i archivo.txt
```

**⚠️ ADVERTENCIA:** No hay forma de recuperar archivos eliminados con `rm`. Usa con cuidado en producción.

---

### 4. VISUALIZACIÓN DE CONTENIDO

Comandos para ver el contenido de archivos.

#### `cat`
**Descripción:** Imprime el contenido completo de un archivo.

```bash
$ cat archivo.txt
Línea 1 del archivo
Línea 2 del archivo
Línea 3 del archivo

# Mostrar números de línea
$ cat -n archivo.txt
     1  Línea 1 del archivo
     2  Línea 2 del archivo
     3  Línea 3 del archivo

# Concatenar múltiples archivos
$ cat archivo1.txt archivo2.txt > archivo_combinado.txt
```

---

#### `less / more`
**Descripción:** Visualiza archivos página por página. `less` es más moderno y permite navegación hacia atrás.

```bash
# Abrir archivo con navegación interactiva
$ less archivo.txt
# Dentro de less:
#   q = salir
#   Space = siguiente página
#   b = página anterior
#   /patron = buscar
#   n = siguiente coincidencia

$ more archivo.txt
# Dentro de more:
#   Space = siguiente página
#   q = salir
```

---

#### `head / tail`
**Descripción:** Muestra las primeras o últimas líneas. `-n` especifica la cantidad.

```bash
# Primeras 20 líneas
$ head -n 20 archivo.txt

# Últimas 10 líneas
$ tail -n 10 archivo.txt

# Últimas 5 líneas (por defecto)
$ tail -5 archivo.txt

# Seguir archivo en tiempo real (útil para logs)
$ tail -f /var/log/syslog
# Ctrl+C para detener

# Primeras 20 líneas de múltiples archivos
$ head -n 20 archivo1.txt archivo2.txt
```

---

#### `nl`
**Descripción:** Numera las líneas de un archivo.

```bash
$ nl archivo.txt
     1  Primera línea
     2  Segunda línea
     3  Tercera línea
     4  Cuarta línea

# Sin numerar líneas vacías
$ nl -ba archivo.txt
```

---

### 5. BÚSQUEDA Y FILTRADO

Comandos para buscar patrones y archivos.

#### `grep`
**Descripción:** Busca patrones en archivos.

**Opciones principales:**
- `-i`: Ignora mayúsculas/minúsculas
- `-v`: Invierte la búsqueda (líneas que NO coinciden)
- `-c`: Cuenta las coincidencias
- `-n`: Muestra número de línea
- `-l`: Solo muestra nombres de archivos

```bash
# Búsqueda simple
$ grep "error" log.txt
Error en línea 42
Error crítico en línea 105

# Búsqueda sin importar mayúsculas
$ grep -i "ERROR" log.txt
Error en línea 42
ERROR crítico en línea 105
error menor en línea 200

# Contar coincidencias
$ grep -c "error" log.txt
3

# Líneas que NO contienen el patrón
$ grep -v "debug" log.txt

# Con número de línea
$ grep -n "error" log.txt
42:Error en línea 42
105:ERROR crítico en línea 105
200:error menor en línea 200

# Buscar en múltiples archivos
$ grep -r "función" ~/proyecto/
```

---

#### `find`
**Descripción:** Busca archivos por nombre, tipo, tamaño o fecha.

```bash
# Encontrar todos los archivos PDF
$ find . -type f -name "*.pdf"
./documentos/manual.pdf
./documentos/guia.pdf

# Encontrar directorios
$ find . -type d -name "config*"
./config
./app/config

# Archivos mayores a 1MB
$ find . -size +1M
./videos/intro.mp4

# Archivos modificados hace menos de 1 día
$ find . -type f -mtime -1

# Encontrar archivos sin permisos de lectura
$ find . -type f ! -readable

# Ejecutar comando en resultados
$ find . -name "*.log" -delete
$ find . -name "*.tmp" -exec rm {} \;
```

---

#### Patrones y Wildcards
**Descripción:** Caracteres especiales para búsquedas rápidas.

```bash
# * = cualquier carácter (0 o más)
$ ls *.txt
archivo.txt  documento.txt  notas.txt

# ? = exactamente un carácter
$ ls file?.txt
file1.txt  fileA.txt

# [AB] = A o B
$ ls *[AB].*
archivoA.txt  documentoB.pdf

# Rango [a-z]
$ ls *[a-m].*
archivo.txt  documento.txt

# Múltiples extensiones
$ ls *.{md,txt,log}
README.md  notas.txt  error.log
```

---

### 6. PROCESAMIENTO DE TEXTO

Comandos para manipular y analizar contenido de texto.

#### `echo`
**Descripción:** Imprime texto. `>` redirige a archivo (sobrescribe). `>>` concatena al archivo.

```bash
# Imprimir simple
$ echo "Hola mundo"
Hola mundo

# Escribir en archivo (sobrescribe si existe)
$ echo "Primera línea" > archivo.txt
$ cat archivo.txt
Primera línea

# Añadir al final del archivo
$ echo "Segunda línea" >> archivo.txt
$ cat archivo.txt
Primera línea
Segunda línea

# Usar variables
$ echo "Usuario: $USER"
Usuario: root

# Desactivar interpretación de variables
$ echo 'Usuario: $USER'
Usuario: $USER
```

---

#### `wc`
**Descripción:** Cuenta líneas, palabras o caracteres.

**Opciones:**
- `-l`: Líneas
- `-w`: Palabras
- `-c`: Caracteres
- `-m`: Caracteres (multibyte)

```bash
# Contar líneas, palabras y caracteres
$ wc archivo.txt
 10  50  250 archivo.txt

# Solo líneas
$ wc -l archivo.txt
10 archivo.txt

# Solo palabras
$ wc -w archivo.txt
50 archivo.txt

# Contar líneas de múltiples archivos
$ wc -l *.txt
 10 archivo1.txt
 20 archivo2.txt
 30 total

# Contar líneas totales en directorio
$ wc -l *.py | tail -1
```

---

#### `awk`
**Descripción:** Procesa archivos columna por columna. Muy potente para análisis de datos y reportes.

```bash
# Imprimir primera columna (espacio delimitado)
$ awk '{print $1}' datos.txt
nombre1
nombre2
nombre3

# Imprimir columnas 1 y 3
$ awk '{print $1, $3}' datos.txt

# Usar delimitador diferente (CSV)
$ awk -F ',' '{print $1}' datos.csv

# Imprimir líneas donde columna 2 > 100
$ awk '$2 > 100 {print $1, $2}' datos.txt
item1 150
item3 200

# Contar líneas
$ awk 'END {print NR}' archivo.txt
10

# Sumar columna
$ awk '{sum += $2} END {print sum}' datos.txt

# Contar ocurrencias
$ awk '{count[$1]++} END {for (word in count) print word, count[word]}' archivo.txt
```

---

### 7. REDIRECCIÓN Y TUBERÍAS

Redirige entrada/salida y encadena comandos para procesamiento de datos.

```bash
# > Redirige salida a archivo (sobrescribe)
$ ls > lista_archivos.txt

# >> Redirige salida a archivo (añade)
$ ls >> lista_archivos.txt

# 2> Redirige solo errores a archivo
$ comando_invalido 2> error.log

# 2>&1 Redirige errores Y salida normal al mismo archivo
$ comando > salida.log 2>&1

# | (pipe) Encadena comandos
$ cat archivo.txt | grep "patrón"
$ ps aux | grep "proceso"
$ ls -la | wc -l

# Múltiples pipes
$ cat archivo.txt | grep "error" | wc -l

# &> Redirige todo (salida y errores)
$ comando &> todo.log

# < Redirige entrada desde archivo
$ sort < archivo.txt

# << Heredoc (entrada multilínea)
$ cat << EOF
Primera línea
Segunda línea
EOF
```

---

### 8. VARIABLES DE ENTORNO

Accede y configura variables del sistema.

#### `echo $VAR`
**Descripción:** Imprime el valor de una variable de entorno.

```bash
# Ver todas las variables
$ env

# Variables comunes predefinidas
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin

$ echo $HOME
/root

$ echo $USER
root

$ echo $PWD
/root/proyectos

$ echo $SHELL
/bin/bash
```

---

#### Crear y Exportar Variables
**Descripción:** Define variables permanentes en `.bashrc` o `.zshrc`

```bash
# Crear variable (sesión actual solo)
$ VARIABLE="valor"
$ echo $VARIABLE
valor

# Exportar variable (disponible en subprocesos)
$ export MI_VAR="valor_exportado"

# Hacer variable permanente en .bashrc
$ echo "export MI_VAR='valor_permanente'" >> ~/.bashrc
$ source ~/.bashrc
$ echo $MI_VAR
valor_permanente

# Ver variables definidas
$ set | grep MI_VAR
```

---

### 9. PERMISOS DE ARCHIVOS

Gestiona permisos de lectura, escritura y ejecución.

#### `chmod`
**Descripción:** Cambia permisos de archivos y directorios.

**Sintaxis:**
- `+x`: Añade permiso de ejecución
- `+r`: Añade permiso de lectura
- `+w`: Añade permiso de escritura
- `-x`: Quita permiso de ejecución

**Números:**
- `7 = rwx` (lectura + escritura + ejecución)
- `5 = r-x` (lectura + ejecución)
- `4 = r--` (solo lectura)
- `0 = ---` (sin permisos)

```bash
# Hacer archivo ejecutable
$ chmod +x script.sh
$ ls -la script.sh
-rwxr-xr-x 1 root root 1024 Apr 22 15:30 script.sh

# Dar permisos 700 (solo propietario)
$ chmod 700 archivo_privado
$ ls -la archivo_privado
-rwx------ 1 root root 256 Apr 22 15:30 archivo_privado

# Dar permisos 644 (r/w propietario, r otros)
$ chmod 644 documento.txt

# Aplicar permisos recursivamente
$ chmod -R 755 directorio/

# Copiar permisos de otro archivo
$ chmod --reference=archivo1 archivo2

# Explicación de 755:
# 7 (propietario) = rwx
# 5 (grupo)       = r-x
# 5 (otros)       = r-x
```

---

### 10. AYUDA Y DOCUMENTACIÓN

Obtén información sobre comandos y funciones del sistema.

#### `man / whatis / type / which`

```bash
# Manual completo (interactivo)
$ man ls
# Dentro de man:
#   q = salir
#   Space = siguiente página
#   / = buscar
#   n = siguiente coincidencia

# Descripción corta
$ whatis grep
grep (1)    - print lines matching a pattern

# Ver si es comando interno o externo
$ type ls
ls is aliased to 'ls --color=auto'

$ type cd
cd is a shell builtin

# Ver ruta completa del ejecutable
$ which python
/usr/bin/python

$ which ls
/bin/ls

# Ayuda integrada del comando
$ ls --help
$ grep --help
```

---

### 11. GESTIÓN DE PAQUETES

Instala, actualiza y elimina software en el sistema.

#### APT (Debian/Ubuntu)

```bash
# Buscar un paquete
$ apt search python3
python3/focal 3.8.2-3 all

# Ver información del paquete
$ apt show git
Package: git
Version: 1:2.25.1-1ubuntu3
...

# Instalar paquete
$ sudo apt install git

# Instalar múltiples paquetes
$ sudo apt install curl wget vim

# Desinstalar paquete
$ sudo apt remove git

# Desinstalar paquete y archivos de configuración
$ sudo apt purge git

# Actualizar lista de paquetes
$ sudo apt update

# Actualizar programas instalados
$ sudo apt upgrade

# Limpiar archivos descargados
$ sudo apt clean

# Limpiar en profundidad
$ sudo apt autoclean
```

#### Brew (macOS)

```bash
# Instalar paquete
$ brew install git

# Actualizar lista
$ brew update

# Actualizar programas instalados
$ brew upgrade

# Desinstalar paquete
$ brew uninstall git

# Ver información
$ brew info git

# Listar paquetes instalados
$ brew list
```

---

### 12. PROCESOS

Monitorea y gestiona procesos en ejecución.

#### `ps / top / htop`

```bash
# Listar todos los procesos
$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY   STAT START   TIME COMMAND
root         1  0.0  0.2 168396 10324 ?     Ss   10:00   0:01 /sbin/init
www-data  2345  0.2  1.5 456789 123456 ?    Sl   10:00   0:45 nginx

# Buscar proceso específico
$ ps aux | grep nginx
www-data  2345  0.2  1.5 456789 123456 ?    Sl   10:00   0:45 nginx

# Listar solo procesos del usuario actual
$ ps -u $USER

# Monitor interactivo en tiempo real
$ top
# Opciones en top:
#   q = salir
#   M = ordenar por memoria
#   P = ordenar por CPU
#   k = matar proceso

# Monitor mejorado (más colorido)
$ htop
# Interfaz más amigable que top
```

---

#### `jobs / fg / bg`

Gestiona trabajos en segundo plano (background) y primer plano (foreground).

```bash
# Ejecutar comando en background
$ sleep 100 &
[1] 2345

# Listar trabajos en background
$ jobs
[1]+  Running                 sleep 100 &

# Listar con PID
$ jobs -l
[1]+ 2345 Running                 sleep 100 &

# Traer trabajo a foreground
$ fg %1
sleep 100

# Pausar proceso (Ctrl+Z)
$ sleep 100
^Z
[1]+  Stopped                 sleep 100

# Continuar en background
$ bg %1
[1]+ sleep 100 &

# Continuar en foreground
$ fg %1
```

---

#### `kill`

Termina procesos de forma controlada o forzada.

```bash
# Terminar proceso (SIGTERM - terminación normal)
$ kill 2345

# Forzar terminación (SIGKILL)
$ kill -9 2345

# Terminar por nombre
$ killall firefox

# Ver todas las señales disponibles
$ kill -l
 1) SIGHUP      2) SIGINT      3) SIGQUIT
 9) SIGKILL    15) SIGTERM    19) SIGSTOP
18) SIGCONT

# Señales comunes:
# -1  SIGHUP   = reinicia el proceso
# -2  SIGINT   = interrumpe (Ctrl+C)
# -9  SIGKILL  = termina forzadamente
# -15 SIGTERM  = termina normalmente (default)
# -19 SIGSTOP  = pausa el proceso
# -18 SIGCONT  = reanuda el proceso
```

---

#### `sleep`

Pausa la ejecución durante un tiempo especificado.

```bash
# Esperar 10 segundos
$ sleep 10

# Encadenar comandos con espera
$ sleep 10 && echo "¡Listo!"

# Ejecutar en background
$ sleep 30 &
[1] 5678

# Verificar con jobs
$ jobs
[1]+  Running                 sleep 30 &

# Diferentes unidades
$ sleep 5     # 5 segundos
$ sleep 1m    # 1 minuto
$ sleep 2h    # 2 horas
```

---

### 13. COMPRESIÓN Y ARCHIVOS

Empaqueta y comprime archivos para respaldo y distribución.

#### `tar`

Empaqueta múltiples archivos en un solo archivo TAR.

```bash
# Empaquetar directorio
$ tar -cvf backup.tar directorio/
directorio/
directorio/archivo1.txt
directorio/archivo2.txt

# Desempaquetar
$ tar -xvf backup.tar

# Empaquetar Y comprimir con gzip
$ tar -czvf backup.tar.gz directorio/

# Descomprimir Y desempaquetar
$ tar -xzvf backup.tar.gz

# Ver contenido sin extraer
$ tar -tvf backup.tar
drwxr-xr-x 0/0              0 2024-04-22 15:30 directorio/
-rw-r--r-- 0/0            256 2024-04-22 15:30 directorio/archivo1.txt

# Comprimir con bzip2
$ tar -cjvf backup.tar.bz2 directorio/

# Opciones:
# -c = crear
# -x = extraer
# -v = verbose
# -f = archivo
# -z = gzip
# -j = bzip2
# -t = listar contenido
```

---

#### `gzip / gunzip`

Comprime y descomprime archivos individuales.

```bash
# Comprimir archivo
$ gzip archivo.tar
$ ls
archivo.tar.gz

# Descomprimir
$ gunzip archivo.tar.gz
$ ls
archivo.tar

# Comprimir manteniendo original
$ gzip -k archivo.tar
$ ls
archivo.tar  archivo.tar.gz

# Nivel de compresión (1-9, default 6)
$ gzip -9 archivo.tar
```

---

### 14. EDITORES DE TEXTO

Edita archivos desde la terminal.

```bash
# NANO - Fácil para principiantes
$ nano archivo.txt
# Ctrl+X = salir
# Ctrl+O = guardar
# Ctrl+W = buscar

# VIM - Muy potente pero complejo
$ vim archivo.txt
# i = insertar
# ESC = comando
# :w = guardar
# :q = salir
# :wq = guardar y salir
# :q! = salir sin guardar

# VI - Versión clásica
$ vi archivo.txt

# Atajos básicos de Vim/Vi:
# i = insertar
# a = insertar después del cursor
# o = nueva línea
# dd = borrar línea
# yy = copiar línea
# p = pegar
# / = buscar
# n = siguiente coincidencia
# :set number = mostrar números
# :syntax on = resaltado de sintaxis
```

---

### 15. NETWORKING

Herramientas para red, diagnóstico y conectividad.

#### `ip / ping / curl / wget`

```bash
# Ver todas las interfaces de red
$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536
    inet 127.0.0.1/8 scope host lo
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500
    inet 192.168.1.100/24 brd 192.168.1.255 scope global eth0

# Ver solo IPv4
$ ip -4 a

# Ver tabla de rutas
$ ip r
default via 192.168.1.1 dev eth0
192.168.1.0/24 dev eth0 proto kernel scope link

# Verificar conectividad (4 paquetes por defecto)
$ ping -c 4 google.com
PING google.com (142.250.185.46) 56(84) bytes of data.
64 bytes from 142.250.185.46: icmp_seq=1 ttl=59 time=15.3 ms

# Descargar contenido web
$ curl -s www.example.com

# Guardar en archivo
$ curl www.example.com > index.html

# Con cabeceras
$ curl -i www.example.com

# Descargar archivo
$ wget https://ejemplo.com/archivo.zip
--2024-04-22 15:30:00--  https://ejemplo.com/archivo.zip
Guardando a: 'archivo.zip'
100%[=============================>] 1,024,000 1.0M/s in 1s

# Con barra de progreso
$ wget -q --show-progress https://ejemplo.com/archivo.zip
```

---

### 16. ALMACENAMIENTO Y DISCO

Información sobre espacio en disco y memoria.

#### `df / du / free / lsblk`

```bash
# Espacio libre/usado en particiones (legible)
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       100G   50G   50G  50% /
/dev/sda2       500G  250G  250G  50% /home
tmpfs           7.9G     0  7.9G   0% /dev/shm

# Con tipo de sistema de archivos
$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda1      ext4      100G   50G   50G  50% /

# Tamaño de un directorio
$ du -sh directorio/
4.5G    directorio/

# Subdirectorios ordenados por tamaño
$ du -sh directorio/* | sort -h

# Memoria RAM disponible
$ free -h
              total        used        free      shared  buff/cache   available
Mem:          15Gi       4.5Gi       8.2Gi       512Mi       2.3Gi      10.0Gi
Swap:         2.0Gi          0       2.0Gi

# Dispositivos de bloques y particiones
$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk
├─sda1   8:1    0   512M  0 part /boot/efi
├─sda2   8:2    0   100G  0 part /
└─sda3   8:3    0 830.5G  0 part /home

# Información detallada
$ lsblk -f
NAME FSTYPE FSVER LABEL UUID
sda1 vfat   FAT32       1234-5678
sda2 ext4   1.0         abcd-efgh
```

---

### 17. SYSTEMD Y SERVICIOS

Gestiona servicios del sistema mediante systemd.

#### `systemctl`

```bash
# Ver estado de un servicio
$ systemctl status nginx
● nginx.service - A high performance web server
   Loaded: loaded (/lib/systemd/system/nginx.service; enabled)
   Active: active (running) since Mon 2024-04-22 10:00:00 UTC
   
# Iniciar servicio
$ sudo systemctl start nginx

# Detener servicio
$ sudo systemctl stop nginx

# Reiniciar servicio
$ sudo systemctl restart nginx

# Recargar configuración sin detener
$ sudo systemctl reload nginx

# Habilitar al arrancar
$ sudo systemctl enable nginx

# Deshabilitar del arranque
$ sudo systemctl disable nginx

# Ver servicios habilitados
$ systemctl list-unit-files | grep enabled

# Recargar configuración de systemd
$ sudo systemctl daemon-reload

# Ver logs del servicio (últimas 20 líneas)
$ journalctl -u nginx -n 20

# Seguir logs en tiempo real
$ journalctl -u nginx -f
```

---

### 18. CRON - TAREAS PROGRAMADAS

Programa comandos para ejecutarse automáticamente en horarios específicos.

#### Gestión de Cron

```bash
# Editar tareas cron del usuario actual
$ crontab -e
# Se abre el editor de texto

# Ver tareas cron del usuario
$ crontab -l
0 15 * * * /usr/local/bin/backup.sh
0 9 * * 1-5 /usr/local/bin/reminders.sh

# Editar tareas de otro usuario (como root)
$ sudo crontab -u usuario -l

# Eliminar todas las tareas cron
$ crontab -r

# Ver cron logs (en algunos sistemas)
$ grep CRON /var/log/syslog
```

#### Formato de Cron

```
* * * * * comando
│ │ │ │ │
│ │ │ │ └─ Día de la semana (0=Domingo, 6=Sábado)
│ │ │ └──- Mes (1-12)
│ │ └───── Día del mes (1-31)
│ └─────── Hora (0-23)
└───────── Minuto (0-59)
```

#### Ejemplos de Cron

```bash
# A las 3 PM (15:00) todos los días
0 15 * * * /usr/local/bin/backup.sh

# Cada lunes a las 9 AM
0 9 * * 1 /usr/local/bin/report.sh

# Cada 30 minutos
*/30 * * * * /usr/local/bin/check.sh

# A las 2 AM del 1 de enero
0 2 1 1 * /usr/local/bin/newyear.sh

# De lunes a viernes a las 8 AM
0 8 * * 1-5 /usr/local/bin/work.sh

# Cada hora
0 * * * * /usr/local/bin/hourly.sh

# Cada 15 minutos
*/15 * * * * /usr/local/bin/frequent.sh

# Últimos minutos de cada hora
59 * * * * /usr/local/bin/end_hour.sh
```

---

### 19. ALIAS - ATAJOS PERSONALIZADOS

Crea comandos cortos para operaciones frecuentes.

#### Crear Alias Temporales

```bash
# Crear alias temporal (solo sesión actual)
$ alias ll='ls -lah'
$ ll
total 48K
drwxr-xr-x  5 root root 4.0K Apr 22 15:30 .

# Alias con parámetros
$ alias mkcd='mkdir -p "$1" && cd "$1"'
$ mkcd nuevo_directorio

# Ver todos los alias definidos
$ alias

# Ver un alias específico
$ alias ll
alias ll='ls -lah'

# Eliminar alias
$ unalias ll
```

#### Hacer Alias Permanentes

```bash
# Añadir alias a .bashrc
$ echo "alias ll='ls -lah'" >> ~/.bashrc

# Para que surta efecto inmediatamente
$ source ~/.bashrc

# Verificar que funciona
$ ll

# Alias comunes recomendados
alias ll='ls -lah'
alias la='ls -la'
alias l='ls -CF'
alias ..='cd ..'
alias ...='cd ../..'
alias cd..='cd ..'
alias mkcd='mkdir -p "$1" && cd "$1"'
alias grpe='grep'  # Corrección de typo
alias duu='du -sh *'
```

---

### 20. TMUX - MULTIPLEXOR DE TERMINAL

Crea múltiples sesiones y ventanas de terminal en una sola conexión SSH.

#### Comandos Básicos

```bash
# Iniciar nueva sesión
$ tmux
# Sesión 0 creada

# Listar sesiones activas
$ tmux ls
0: 1 windows (created Tue Apr 22 15:30)
1: 1 windows (created Tue Apr 22 15:31)

# Crear sesión con nombre
$ tmux new-session -s desarrollo
$ tmux new-s trabajo

# Conectarse a sesión existente
$ tmux attach -t desarrollo
$ tmux attach -t 0

# Desconectarse sin cerrar (Ctrl+b d)
# La sesión sigue corriendo en background

# Matar sesión
$ tmux kill-session -t desarrollo
```

#### Dentro de TMUX (Prefijo: Ctrl+b)

```
CTRL+b %          Divide panel verticalmente
CTRL+b "          Divide panel horizontalmente
CTRL+b c          Crea nueva ventana
CTRL+b ,          Renombra ventana actual
CTRL+b n          Va a siguiente ventana
CTRL+b p          Va a ventana anterior
CTRL+b [0-9]      Va a ventana específica
CTRL+b d          Desconecta sesión (keep-alive)
CTRL+b x          Cierra panel actual
CTRL+b &          Cierra ventana actual
CTRL+b [          Modo copy (navegar con arrow keys)
CTRL+b ]          Pegar contenido copiado
CTRL+b {          Rotar paneles
CTRL+b }          Rotar paneles al revés
CTRL+b o          Cambiar a siguiente panel
CTRL+b ;          Cambiar al panel anterior
```

#### Ejemplo Práctico de TMUX

```bash
# Crear sesión de desarrollo
$ tmux new-s desarrollo

# Dentro de TMUX:
# Ctrl+b c → Nueva ventana "servidor"
# Ctrl+b c → Nueva ventana "editor"
# Ctrl+b c → Nueva ventana "logs"

# Renombrar ventanas (Ctrl+b ,)
# Cambiar entre ventanas (Ctrl+b n/p)

# Dividir panel (Ctrl+b %)
# Navegar entre paneles (Ctrl+b arrow keys)

# Desconectar (Ctrl+b d)
# Reconectar después:
$ tmux attach -t desarrollo
```

---

## Mejores Prácticas

### Seguridad

- ✅ Usa `sudo` solo cuando sea necesario
- ✅ Evita usar `rm -rf` en directorios de producción
- ✅ Revisa scripts antes de ejecutarlos
- ✅ Usa `chmod` para restringir permisos
- ✅ Mantén copias de seguridad de archivos importantes

### Productividad

- ✅ Aprende y crea alias para comandos frecuentes
- ✅ Usa `history` para recordar comandos previos
- ✅ Aplica autocompletado con Tab
- ✅ Usa `Ctrl+R` para búsqueda inversa en historial
- ✅ Encadena comandos con `&&` para dependencias

### Automatización

- ✅ Usa `cron` para tareas repetitivas
- ✅ Crea scripts bash para automatizar procesos
- ✅ Usa `systemd` para servicios persistentes
- ✅ Documenta scripts para futuras referencias

### Performance

- ✅ Monitorea procesos con `top` o `htop`
- ✅ Revisa uso de disco con `df` y `du`
- ✅ Analiza memoria con `free`
- ✅ Usa tuberías (`|`) para procesar datos eficientemente

---

## Contribuciones

Las contribuciones son bienvenidas. Para contribuir:

1. Fork el repositorio
2. Crea una rama para tu feature (`git checkout -b feature/nueva-caracteristica`)
3. Commit tus cambios (`git commit -am 'Añade nueva característica'`)
4. Push a la rama (`git push origin feature/nueva-caracteristica`)
5. Abre un Pull Request

Por favor, asegúrate de:
- Seguir el mismo formato y estructura
- Incluir ejemplos prácticos claros
- Revisar ortografía y gramática
- Probar los comandos antes de enviar

---

## Recursos Adicionales

- [Linux Man Pages Online](https://man7.org/)
- [Bash Scripting Guide](https://www.gnu.org/software/bash/manual/)
- [Cron Expression Generator](https://crontab.guru/)
- [Regular Expressions Tester](https://regex101.com/)
- [OverTheWire - Linux Wargames](https://overthewire.org/)
