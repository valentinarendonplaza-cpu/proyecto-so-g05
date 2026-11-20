# Ficha de Verificación de Versiones - Grupo 05

## Datos del Grupo
- **Grupo:** 05
- **Nomenclatura de VMs:** `g05-grafica` y `g05-consola`
- **Integrantes:**
  1. Valentina Rendón Plaza
  2. Carlos Alberto Loaiza Mosquera
  3. Matías Sánchez Erazo

## Especificaciones Técnicas Asignadas (Tabla Grupo 05)

| Componente | Distribución / Tecnología | Versión Oficial Vigente | Arquitectura / Familia | Gestor de Paquetes | Sistema de Archivos por Defecto | Fuente Oficial y Fecha de Consulta |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **VM Gráfica (`g05-grafica`)** | **Zorin OS** (Core) | Zorin OS 17.3 (Base Ubuntu 22.04.5 LTS) | x86_64 (64-bit) / Familia Debian-Ubuntu | `apt` / `dpkg` | `ext4` | [Zorin OS Official](https://zorin.com/os/) (Consultado: 19/11/2026) |
| **VM Consola (`g05-consola`)** | **Fedora Server** | Fedora Server 42 / 43 (Estable vigente) | x86_64 (64-bit) / Familia Fedora-RHEL | `dnf` / `rpm` | `XFS` (sobre LVM por defecto; particionado manual `ext4`/`XFS`) | [Fedora Server Docs](https://docs.fedoraproject.org/en-US/fedora-server/) (Consultado: 19/11/2026) |
| **Contenedor (Dockerfile)** | **Ubuntu** (Imagen oficial) | `ubuntu:24.04` (Noble Numbat LTS) | linux/amd64 / Familia Debian-Ubuntu | `apt` | `overlay2` (Docker) | [Docker Hub - Ubuntu](https://hub.docker.com/_/ubuntu) (Consultado: 19/11/2026) |
| **Orquestador** | **Kubernetes (Minikube)** | Minikube estable (`v1.34+`) con driver Docker | x86_64 | `kubectl` | N/A | [Minikube Docs](https://minikube.sigs.k8s.io/docs/start/) (Consultado: 19/11/2026) |

## Notas de Investigación Inicial
- **Zorin OS:** Al ser una derivada de Ubuntu LTS, utiliza el instalador gráfico Ubiquity (con opción de particionado manual *"Más opciones / Something else"*) y se administra con `apt` y `systemd`.
- **Fedora Server:** Utiliza el instalador **Anaconda** (opción de almacenamiento *"Custom / Personalizado"*), gestiona paquetes con `dnf`, servicios con `systemd` y firewall con `firewalld` (a diferencia de `ufw` en Ubuntu).
- **Requisitos de disco (VirtualBox):** Ambas máquinas se crearán con disco de 25 GB; `g05-consola` tendrá particionado manual obligatorio con `/`, `swap`, `/home` y `/var` (mínimos: `/` 5 GB, `/var` 10 GB, `swap` 1 GB, `/home` 1 GB).
