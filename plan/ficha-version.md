# Ficha de Verificación de Versiones - Grupo 04

**Fecha de consulta:** 17 de noviembre de 2026

## 1. Máquina Virtual Gráfica (`g04-grafica`)
* **Distribución asignada:** Debian (con entorno de escritorio)
* **Versión elegida:** Debian 13 (Trixie) - Estable
* **Arquitectura:** x86_64 (`amd64`)
* **Familia / Gestor de paquetes:** Debian / APT (`apt`)
* **Fuente oficial de descarga:** https://www.debian.org/distrib/
* **Verificación de integridad:** Archivo `SHA256SUMS` / `SHA512SUMS` desde el servidor oficial de Debian.

## 2. Máquina Virtual de Consola (`g04-consola`)
* **Distribución asignada:** AlmaLinux (instalación mínima / sin entorno gráfico)
* **Versión elegida:** AlmaLinux 9.6 / 10 (Estable)
* **Arquitectura:** x86_64
* **Familia / Gestor de paquetes:** RHEL (Red Hat Enterprise Linux) / DNF (`dnf`)
* **Fuente oficial de descarga:** https://almalinux.org/get-almalinux/
* **Verificación de integridad:** Archivo `CHECKSUM` (SHA256) desde el espejo oficial de AlmaLinux.

## 3. Imagen Base para Contenedores (`Dockerfile`)
* **Imagen asignada:** Rocky Linux
* **Etiqueta (Tag) elegida:** `rockylinux:9`
* **Arquitectura:** `linux/amd64`
* **Gestor de paquetes interno:** DNF / Microdnf
* **Fuente oficial:** https://hub.docker.com/_/rockylinux
