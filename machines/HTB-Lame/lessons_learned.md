# Lessons Learned — HTB Lame

Este documento recoge las principales lecciones aprendidas durante la resolución de la máquina **Lame**, tanto a nivel técnico como metodológico.

---

##  Enumeración es la fase más importante

La fase de enumeración permitió identificar:
- Servicios expuestos
- Versiones concretas
- Posibles vectores de ataque

Una enumeración incompleta o incorrecta puede llevar a conclusiones erróneas.  
Repetir escaneos y ajustar parámetros fue clave para detectar correctamente el servicio vulnerable.

---

##  Re-enumerar no es un error

Durante el laboratorio:
- Un vector de ataque (FTP) parecía viable
- El exploit no funcionó en este entorno
- Se decidió **volver a enumerar**

Esto permitió descubrir un servicio alternativo vulnerable (**Samba**).

Re-enumerar no significa retroceder, sino **refinar la información**.

---

##  No obsesionarse con un único vector

Aunque una versión pueda ser conocida como vulnerable:
- El exploit puede estar parcheado
- El binario puede no ser el original
- El entorno puede bloquear el ataque

Saber **descartar un vector** es tan importante como saber explotarlo.

---

##  Diferencia entre bind shell y reverse shell

Durante la explotación se estudiaron ambos conceptos:

- **Bind shell**:
  - El objetivo abre un puerto
  - El atacante se conecta
  - Más simple, pero más visible

- **Reverse shell**:
  - El objetivo inicia la conexión
  - Más común en entornos reales
  - Menos dependiente de firewalls

Entender cuándo usar cada una es clave en escenarios reales.

---

##  Metasploit como herramienta profesional

Aunque se intentó la explotación manual:
- La explotación fue finalmente realizada con **Metasploit**
- Esto permitió confirmar la vulnerabilidad de forma estable

---

## 🎯 Impacto real de una mala configuración

La vulnerabilidad explotada (**CVE-2007-2447**) demuestra que:
- Servicios antiguos representan un riesgo crítico
- La falta de validación de entradas puede provocar RCE
- Un solo servicio mal configurado puede comprometer todo el sistema

---

##  Conclusión personal

Esta máquina permitió reforzar conceptos clave:
- Metodología de pentesting
- Análisis de servicios
- Toma de decisiones técnicas
- Importancia de documentar el proceso completo

---

##  Próximos pasos

Tras completar esta máquina:
- Seguir practicando con máquinas de nivel similar
- Profundizar en explotación manual
- Mejorar la documentación técnica
- Construir un portfolio sólido y progresivo

