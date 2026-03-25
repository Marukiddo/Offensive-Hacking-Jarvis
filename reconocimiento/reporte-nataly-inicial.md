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

## 🛡️ Recomendaciones del Red Team
Se recomienda el cierre inmediato de los puertos 111, 139, 445 y 6566 mediante reglas de Firewall (UFW) en el servidor objetivo, ya que no son necesarios para la administración remota segura.

---
*Documentado por Maru Barreto (Offensive Hacking Lab).*
