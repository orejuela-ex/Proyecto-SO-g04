---
layout: default
title: Sprint 1 · Montaje
---

# Sprint 1 · Montaje

Grupo 4 · VM gráfica: Debian · VM consola: AlmaLinux

## 1. VM gráfica (g04-grafica)

Creamos la máquina virtual g04-grafica en VirtualBox usando la imagen ISO de Debian 13 y un disco duro virtual de 25 GB (desactivando la instalación automática). Dentro del instalador configuramos el idioma en español, el nombre del equipo (g04-grafica), la clave de administrador (root) y el usuario laura. Por último, entramos al particionado manual y dividimos el disco (sda) en tres partes: el sistema (/), la  memoria de intercambio (swap) y los archivos personales (/home).

| Partición | Tamaño | Por qué |
|---|---|---|
| / | 15 G | Almacena el sistema operativos base Debian 13, los paquetes del sistema y el entorno gráfico  |
| swap | 2 G  | Respalda la memoria RAM cuando aumenta la carga |
| /home | 9.8 G | Separa los archivos y configuraciones del usuario en este caso Laura |


Anexos:
Particiones
<img width="800" height="600" alt="image" src="https://github.com/user-attachments/assets/a1dce653-748b-4675-a27c-3318f79cccf5" />


Comandos: `lsblk`, `df -h`, `cat /etc/fstab`

<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/7831d53a-4a28-4977-a8bd-cbd70eb58433" />
Date
<img width="1280" height="800" alt="g04" src="https://github.com/user-attachments/assets/22ea51e1-10c9-4968-97e2-bd02f2cc4aae" />

Primero iniciamos en el usuario que ingresamos manualmente, despues inicilizamos la termminal para ingresar los comandos, primero ingresamos clear && lsblk && echo "--- df -h ---" && df -h / /home && echo "--- /etc/fstab ---" && grep -v '^#' /etc/fstab para ejecutar todos de primero, pero nos falto el date entonces lo ejecutamos por si solo 

<img width="1280" height="800" alt="g04" src="https://github.com/user-attachments/assets/22ea51e1-10c9-4968-97e2-bd02f2cc4aae" />
Instalamos los navegadores y editores con el siguiente comando (sudo apt update && sudo apt install -y chromium geany) y el prompt root@g04-grafica
<img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/54470570-f437-4d13-b482-80826a47946d" />



## 2. VM de consola (g04-consola)

(Qué hicimos, con nuestras palabras)

| Partición | Tamaño | Por qué |
|---|---|---|
| / |  |  |
| /var |  |  |
| swap |  |  |
| /home |  |  |

Herramientas: make, rsync, curl, git y wget.

Comandos: `lsblk`, `df -h`, `cat /etc/fstab`, `make --version`, `rsync --version`, `curl --version`, `git --version`, `wget --version`

(Aquí van las capturas y la explicación)

## 3. Red

(Aquí van las capturas de ip a y de los dos ping, y la explicación)

## 4. SSH

(Aquí va la captura de la sesión SSH y la explicación)

## 5. Instantáneas

(Aquí van las dos capturas y la explicación)

## Código del sprint

(Comandos usados para guardar el código)

## Video del sprint

(Enlace de YouTube)

## Lo que hizo cada integrante

| Integrante | Qué hizo | Commits |
|---|---|---|
| Juan Orejuela |subió las capturas al sitio y modifico la información  |  |
