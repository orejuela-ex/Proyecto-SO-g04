

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

También verificamos que quedaran instaladas las herramientas básicas pedidas para el proyecto (`make`, `rsync`, `curl`, `git` y `wget`):
(ARRASTRA AQUÍ TU CAPTURA: 04-g04-grafica-entorno-paq.png)

## 2. VM de consola (g04-consola)

Creamos la máquina virtual `g04-consola` en VirtualBox usando la imagen ISO minimal de AlmaLinux 9. La dejamos únicamente en modo texto (sin pantalla gráfica) para que gaste menos recursos del computador. Durante la instalación pusimos el idioma en español, le dimos el nombre `g04-consola`, creamos la clave de administrador (`root`) y nuestro usuario `lguetio`. Al final entramos al particionado manual para dividir el disco en cuatro partes bien organizadas:

| Partición | Tamaño | Por qué |
|---|---|---|
| / | 15 G | Guarda el sistema operativo base AlmaLinux 9 y los programas principales |
| /var | 4 G | Separa los registros y archivos que cambian seguido para no llenar el sistema |
| swap | 2 G | Ayuda a la memoria RAM cuando el equipo tiene mucho trabajo |
| /home | 4 G | Guarda los archivos y carpetas personales del usuario `lguetio` |

Herramientas: make, rsync, curl, git y wget.

Comandos: `lsblk`, `df -h`, `cat /etc/fstab`, `make --version`, `rsync --version`, `curl --version`, `git --version`, `wget --version`

(ARRASTRA AQUÍ TU CAPTURA: 01-g04-consola-particionado.png)
(ARRASTRA AQUÍ TU CAPTURA: 02-g04-consola-hostname-p.png)

Una vez encendido el sistema, revisamos en la terminal que las particiones hubieran quedado bien creadas y montadas automáticamente al prender el equipo (`lsblk`, `df -h` y `cat /etc/fstab`). Después confirmamos el nombre de la máquina (`g04-consola`) e instalamos las cinco herramientas obligatorias (`make`, `rsync`, `curl`, `git` y `wget`), comprobando la versión de cada una para asegurarnos de que funcionaran bien.

## 3. Red

(ARRASTRA AQUÍ TU CAPTURA: 05-g04-grafica-red-ssh.png)
(ARRASTRA AQUÍ TU CAPTURA: 06-g04-consola-red-ssh.png)

Revisamos la conexión de red en ambas máquinas usando el comando `ip a`. Comprobamos que tanto `g04-grafica` como `g04-consola` tienen su tarjeta de red encendida y recibieron una dirección IP automática (`10.0.2.15`) gracias a VirtualBox, lo que les permite conectarse entre sí y tener salida a Internet para descargar actualizaciones y programas.

## 4. SSH

(ARRASTRA AQUÍ TU CAPTURA: 05-g04-grafica-red-ssh.png)
(ARRASTRA AQUÍ TU CAPTURA: 06-g04-consola-red-ssh.png)

Activamos y encendimos el servicio SSH en los dos sistemas operativos (`ssh` en Debian y `sshd` en AlmaLinux) para poder conectarnos a las máquinas de forma remota desde otra terminal. Con el comando `systemctl status` confirmamos que el servicio aparece en verde (`active (running)`), que arranca solo cada vez que prendemos las máquinas y que está listo para recibir conexiones por el puerto 22.

## 5. Instantáneas

(ARRASTRA AQUÍ TU CAPTURA: 07-virtualbox-instantaneas.png)

Cuando ya teníamos las dos máquinas listas, actualizadas y con todos los programas instalados, expulsamos los discos de instalación (`.iso`) para que no volvieran a arrancar desde el instalador y apagamos ambos equipos correctamente. Luego entramos a VirtualBox y guardamos una instantánea llamada `Estado-Base-Sprint1` en cada máquina (`g04-grafica1` y `g04-consola`). Esto nos sirve como copia de seguridad para volver a este punto limpio si algo sale mal en los próximos sprints.

## Código del sprint

```bash
# Comandos que usamos dentro de las máquinas para revisar discos, red y servicios
lsblk
df -h
cat /etc/fstab
ip a
systemctl status ssh --no-pager   # En Debian (g04-grafica)
systemctl status sshd --no-pager  # En AlmaLinux (g04-consola)

# Comandos de Git para subir y guardar los avances en el repositorio
git status
git add .
git commit -m "Documentacion y evidencias oficiales Sprint 1"
git push origin main
