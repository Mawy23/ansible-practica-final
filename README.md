# Práctica Final - Ansible (Vagrant + Apache + Usuarios)

Esta práctica final demuestra el uso de Ansible para automatizar la configuración de servidores virtualizados con Vagrant. Se crean usuarios, se despliega un servidor web Apache personalizado con plantillas y se verifica el estado final.

## 🔧 Requisitos

- Vagrant (3 máquinas: `control`, `vagrant1`, `vagrant2`)
- Ansible ejecutándose en `control`
- Conexión SSH entre nodos
- Docker (para `ansible-navigator`, opcional)

## 📁 Estructura del proyecto

ansible-practica-final/
├── ansible.cfg
├── inventory
├── users.yml
├── verify_user.yml
├── dev_deploy.yml
├── get_web_content.yml
├── site.yml
├── templates/
│   ├── vhost.conf.j2
│   └── index.html.j2

## 🚀 Ejecución de los playbooks

### 1. Crear usuarios

    ansible-playbook users.yml

### 2. Desplegar Apache con contenido personalizado

    ansible-playbook dev_deploy.yml

### 3. Verificar contenido web

    curl http://192.168.10.20
    curl http://192.168.10.30

### 4. Verificar usuarios con SSH

    ssh vagrant@192.168.10.20 "id carlos && id marta"
    ssh vagrant@192.168.10.30 "id carlos && id marta"

    o

    ssh vagrant1 "id carlos && id marta"
    ssh vagrant2 "id carlos && id marta"

## ✅ Verificación alternativa con Ansible

    ansible all -i inventory -b -m shell -a "id carlos && id marta"



