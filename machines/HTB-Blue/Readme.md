## HTB-Blue
---

## Resumen

Blue, aunque posiblemente sea la máquina más simple en Hack The Box, demuestra la gravedad del exploit EternalBlue, que se ha utilizado en múltiples ataques de ransomware y criptominería a gran escala desde que se filtró públicamente.

---

## Enumeracion 

- Se hizo un escaneo con nmap encontrando una vulnerabilidad en el puerto 445 por SMB
- se busco vulnerabilidades con nmap

---

## Analisis

Se encontro una vulnerabilidad con nmap y el siguiente paso fue buscar informacion en internet sobre dicha vulnerabilidad y buscar exploits disponibles con metaexploit

---

## Explotacion

Se encontro la siguiente vulnerabilidad ms17-010 y se busco el exploit en metaexploit.
Acto seguido se exploto usando el siguiente exploit: exploit/windows/smb/ms17_010_eternalblue

---

## Resultado

Obtuve una sesion meterpreter.
Abri una shell y comprobe mis privilegios
Entre a los escritorios de administrador y de usuario y obtuve las flags.
