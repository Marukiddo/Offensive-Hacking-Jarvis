# 🚩 Informe de Laboratorio: Control Remoto en Windows 11 (Red Team)

**Fecha:** 28/03/2026
**Atacante:** Nataly (Servidor de Ataque Compaq) - 192.168.100.29
**Objetivo:** Windows 11 Pro - 192.168.100.22
**Herramientas:** Nmap, Impacket (wmiexec.py), SMBClient

## 📋 Resumen Ejecutivo
Se ha configurado con éxito un entorno de laboratorio unificado eliminando el "Doble NAT" entre dos routers. Se ha logrado la ejecución remota de comandos (RCE) desde un servidor Linux (Nataly) hacia una estación de trabajo Windows 11 moderna mediante el uso de credenciales administrativas y ajustes en las políticas de seguridad del objetivo.

## 🛠️ Fase 1: Reconfiguración de Infraestructura
- **Problema:** Doble NAT (Router de salida + Router secundario) impedía la visibilidad entre atacante y objetivo.
- **Solución:** Configuración del router secundario en modo "Wired Repeater" (Modo Puente).
- **Resultado:** Red plana unificada en el segmento `192.168.100.0/24`.

## 🔍 Fase 2: Reconocimiento y Enumeración
Se utilizó `Nmap` para identificar los servicios activos en el objetivo:
- **Puerto 135/tcp (MSRPC):** Abierto.
- **Puerto 139/445 (SMB):** Abierto (Protocolo SMBv2/v3 detectado).
- **Puerto 137 (NetBIOS):** Se extrajo el nombre de la máquina objetivo.

## 🔓 Fase 3: Bypass de Seguridad en Windows 11
Para permitir la administración remota desde el servidor de ataque, se aplicaron los siguientes ajustes en el objetivo (Hardening Bypass):
1. **Registro:** Habilitación de `LocalAccountTokenFilterPolicy` (REG_DWORD 1) para permitir tokens de administrador remotos.
2. **Firewall:** Apertura de las reglas de "Administración remota de Windows" e "Instrumental de administración de Windows (WMI)".
3. **Red:** Cambio del perfil de red de "Público" a "Privado".

## 🚀 Fase 4: Prueba de Concepto (PoC)
Se utilizó la herramienta `wmiexec.py` de la suite Impacket para obtener una shell semi-interactiva:
- **Comando:** `python3 wmiexec.py <USER>:<PASS>@<TARGET_IP>`
- **Acción Visual:** Ejecución remota del comando `schtasks` para lanzar un mensaje visual y la apertura de una URL en el navegador de la sesión del usuario activo.

---
*Documentado por Maru Barreto (Offensive Hacking Lab).*
