# Hack The Box — Lame

## 🧠 Descripción
Lame es una máquina de **Hack The Box** enfocada a la enumeración de servicios y explotación de vulnerabilidades conocidas en servicios antiguos.  
El objetivo de esta máquina es obtener acceso **root** entendiendo el proceso completo de análisis, explotación y toma de decisiones durante un pentest.

---

## 🎯 Objetivo
- Enumerar los servicios expuestos
- Identificar versiones vulnerables
- Probar vectores de ataque
- Obtener acceso como **root**
- Documentar tanto los intentos fallidos como el vector final

---

## 🔍 Enumeración inicial

Se realizó un escaneo de puertos y servicios para identificar la superficie de ataque:

- FTP (vsFTPd 2.3.4)
- SSH
- Samba (puertos 139 / 445)
- Otros servicios de red

Durante esta fase se detectaron versiones antiguas que podían ser potencialmente vulnerables.

Los escaneos de Nmap utilizados se encuentran documentados en la carpeta `/nmap`.

---

## ❌ Vector descartado — FTP (vsFTPd 2.3.4)

El servicio FTP parecía vulnerable a una backdoor conocida en la versión **vsFTPd 2.3.4**.  
Se realizaron intentos de explotación manual utilizando clientes FTP y `netcat`.

Sin embargo:
- El exploit no funcionó correctamente en este entorno
- El puerto esperado para la backdoor no se abrió
- Se decidió **descartar este vector** tras comprobar que no era viable

👉 Este proceso se documenta en detalle en `exploitation/ftp_vsftpd_234.md`.

---

## ✅ Vector exitoso — Samba (CVE-2007-2447)

Durante la re-enumeración se identificó el servicio:

- **Samba smbd 3.0.20 (Debian)**

Esta versión es vulnerable a **CVE-2007-2447**, que permite **Remote Command Execution (RCE)** debido a una mala sanitización del nombre de usuario en el parámetro `username map script`.

Se confirmó:
- Ejecución remota de comandos
- Ejecución con privilegios **root**
- Compromiso total del sistema

La explotación se realizó mediante **Metasploit**, utilizando el módulo:

exploit/multi/samba/usermap_script


👉 El proceso completo está documentado en `exploitation/samba_cve_2007_2447.md`.

---

## 🧪 Resultado final

- Acceso obtenido: **root**
- Tipo de vulnerabilidad: **Remote Command Execution**
- Servicio comprometido: **Samba**
- Escalada de privilegios: **No necesaria**

---

## 📚 Lecciones aprendidas

- No todos los exploits funcionan aunque la versión coincida
- Re-enumerar es parte esencial del proceso
- Documentar intentos fallidos aporta valor
- Metasploit es una herramienta válida cuando se usa con criterio
- Entender el *por qué* es más importante que llegar rápido al resultado

Las conclusiones completas se encuentran en `lessons_learned.md`.

---

## ⚠️ Disclaimer
Este laboratorio ha sido realizado con fines **educativos** en un entorno controlado.  
No debe aplicarse en sistemas sin autorización explícita.

