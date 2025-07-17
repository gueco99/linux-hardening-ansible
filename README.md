# 🔐 Linux Hardening Automatizado con Ansible

Este proyecto implementa un playbook de **Ansible** para realizar un **hardening básico y automatizado** sobre servidores Linux.  
Aplica buenas prácticas de ciberseguridad para reforzar el sistema frente a accesos no autorizados, escaneos, fuerza bruta y servicios obsoletos.

---

## 🧰 Tecnologías utilizadas

- **Ansible**
- Linux (Debian/Ubuntu)
- OpenSSH
- UFW (Firewall)
- fail2ban
- Lynis (auditoría de seguridad)

---

## 📦 Roles incluidos

| Rol       | Función principal |
|-----------|--------------------|
| `common`  | Actualiza el sistema y elimina servicios inseguros |
| `ssh`     | Configura el acceso SSH seguro (puerto, root, autenticación) |
| `ufw`     | Activa el firewall y permite el nuevo puerto |
| `fail2ban`| Protege contra ataques de fuerza bruta SSH |
| `lynis`   | Ejecuta auditoría de seguridad y genera un informe |

---

## 🚀 ¿Cómo usar este playbook?

### 1. Clona el repositorio

```bash
git clone https://github.com/tu_usuario/linux-hardening-ansible.git
cd linux-hardening-ansible

2. Configurá tu inventario
Editá inventory.ini con los datos de tu servidor:
[servers]
mi_servidor ansible_host=<TUIP> ansible_user=<TUNOMBRE> ansible_ssh_private_key_file=/home/usuario/.ssh/id_rsa

3. Ejecutá el playbook
ansible-playbook -i inventory.ini playbook.yml --ask-become-pass

💡 Te pedirá la passphrase de tu clave privada y la contraseña sudo del servidor.




📂 Resultado final
SSH en puerto 2222 (no root login, solo clave)

Firewall UFW activo y restrictivo

fail2ban protegiendo SSH

Servicios obsoletos desinstalados

Reporte generado en /var/log/lynis-report.txt
