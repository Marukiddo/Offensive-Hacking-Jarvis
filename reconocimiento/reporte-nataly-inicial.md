# 🚩 Informe de Reconocimiento Inicial: Nataly Server

**Fecha:** 25/03/2026
**Objetivo:** Nataly (192.168.31.185)
**Herramienta:** Nmap v7.94

## 🔍 Hallazgos (Puertos Abiertos)

| Puerto | Servicio | Estado | Riesgo |
| --- | --- | --- | --- |
| 22/tcp | SSH | Abierto | Bajo (Protegido con llaves Ed25519) |
| 111/tcp | rpcbind | **Abierto** | Medio (Exposición innecesaria de servicios RPC) |
| 139/tcp | netbios-ssn | **Abierto** | Alto (Posible fuga de información de carpetas compartidas) |
| 445/tcp | microsoft-ds | **Abierto** | Alto (Protocolo SMB - Potencial vector de exploits como EternalBlue) |
| 6566/tcp | sane-port | **Abierto** | Bajo (Servicio de escáner innecesario) |

## 🛡️ Mitigación y Verificación (Blue Team)

**Fecha de Mitigación:** 25/03/2026
**Acción:** Implementación de reglas de Firewall (UFW) en Nataly Server.

### Verificación Post-Hardening
Escaneo final realizado tras el blindaje:
- **Puertos Filtrados:** 999 (No responden a escaneos).
- **Puertos Abiertos:** Solo 22/tcp (SSH).

**Estado Final:** ✅ **SEGURO**. La superficie de ataque se ha reducido al mínimo necesario para la administración remota.

---
*Documentado por Maru Barreto (Offensive Hacking Lab).*
