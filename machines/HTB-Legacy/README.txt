# HTB - Legacy

Máquina Windows vulnerable enfocada en SMB y exploits clásicos.
El objetivo de esta máquina es aprender a identificar servicios antiguos
y explotar vulnerabilidades conocidas en sistemas Windows.

## Información básica

- Plataforma: Hack The Box
- Sistema operativo: Windows
- Dificultad: Easy

## Enumeración

Se realizó un escaneo completo de puertos para identificar los servicios activos.

Servicios relevantes encontrados:
- SMB (puertos 139 y 445)
- Sistema Windows antiguo

## Análisis de vulnerabilidades

El servicio SMB expuesto en un sistema Windows antiguo es un indicador
claro de posibles vulnerabilidades conocidas.

Tras investigar la versión del servicio y el sistema operativo,
se identificó una vulnerabilidad crítica que permite ejecución remota
de código sin autenticación.

## Explotación

Se utilizó un exploit conocido para SMB que permite obtener acceso remoto
al sistema objetivo.

El exploit permite ejecutar código de forma remota y obtener una shell
con privilegios elevados.

Resultado:
- Acceso obtenido como: NT AUTHORITY\SYSTEM

## Post-explotación

Una vez obtenida la shell se verificó el nivel de privilegios
y se confirmó el control total del sistema.

## Lecciones aprendidas

- La enumeración correcta es clave para identificar vectores de ataque.
- Los servicios antiguos suelen tener exploits públicos bien documentados.
- Comprender por qué funciona un exploit es más importante que ejecutarlo.

## Disclaimer

Este contenido es únicamente educativo y se ha realizado en un entorno
controlado con fines de aprendizaje.

