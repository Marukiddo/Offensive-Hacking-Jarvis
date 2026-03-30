# 🚩 Offensive Hacking Jarvis (Red Team)

Laboratorio dedicado al aprendizaje de auditoría de seguridad ofensiva, pruebas de penetración y hacking ético.

- **Enfoque:** Reconocimiento, explotación y post-explotación controlada.
- **Objetivo:** Poner a prueba las defensas de Jarvis y Nataly en un entorno controlado.

## 🏗️ Arquitectura del Laboratorio
- **Mando Central (Jarvis):** Estación de trabajo principal para la gestión de auditorías.
- **Servidor de Ataque (Nataly):** Nodo ligero (Compaq/Debian) dedicado a la ejecución de exploits y escaneos de red.
- **Entorno Unificado:** Segmento de red `192.168.100.0/24` (Modo Puente) para visibilidad total entre dispositivos.

## 🛠️ Herramientas de Ataque
- [x] **Nmap:** Escaneo de red, enumeración de servicios y descubrimiento de SO.
- [x] **Impacket:** Ejecución remota de comandos (RCE) mediante `wmiexec` y `smbexec`.
- [ ] **Metasploit Framework:** (Próximamente).
- [x] **SmbClient:** Interacción con recursos compartidos SMB/CIFS.

## 📖 Metodologías y Casos de Estudio
- [x] **Escaneo y Enumeración:** Identificación de activos y servicios en red local.
- [x] **Bypass de Políticas de Seguridad:** Configuración de objetivos Windows 11 para pruebas de Red Team.
- [x] **Movimiento Lateral:** Ejecución de comandos visuales y administrativos en objetivos remotos.

---
*Este repositorio documenta el progreso de Maru Barreto en el mundo del Hacking Ético.*
