# 📖 Guía de Configuración: Servidor de Ataque Nataly

**Descripción:** Metodología paso a paso para la configuración del acceso seguro y optimizado entre la estación de mando (Jarvis) y el servidor de ataque (Nataly).

## 🔐 1. Configuración de Llaves SSH (Ed25519)
Para evitar el uso de contraseñas y mejorar la seguridad, se utiliza criptografía de curva elíptica:

```bash
# Generar llave en Jarvis
ssh-keygen -t ed25519 -C "Jarvis-to-Nataly"

# Copiar llave pública a Nataly
ssh-copy-id -i ~/.ssh/id_ed25519.pub <USER>@<NATALY_IP>
```

## 🚀 2. Optimización de Acceso (SSH Alias)
Configuración del archivo `~/.ssh/config` en Jarvis para permitir conexiones rápidas mediante alias:

```text
Host Nataly
    HostName <NATALY_IP>
    User <NATALY_USER>
    IdentityFile ~/.ssh/id_ed25519
```
*Uso: `ssh Nataly`*

## 🛠️ 3. Preparación del Arsenal (Herramientas Base)
Comandos ejecutados en Nataly para preparar el entorno de auditoría:

```bash
sudo apt update
sudo apt install -y nmap git curl python3-impacket smbclient cifs-utils exploitdb
```

## 🕵️ 4. Verificación de Seguridad (Hardening Inicial)
Nataly fue configurada originalmente para reducir su superficie de ataque:
- **Firewall (UFW):** Solo puerto 22/tcp abierto para administración.
- **Acceso:** Solo mediante llaves públicas (PasswordAuthentication no recomendado).

---
*Documentado por Maru Barreto (Offensive Hacking Lab).*
