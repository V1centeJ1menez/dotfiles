# Guía de Configuración: Debian 13 + Sway

## 1. Configuración Inicial del Sistema

### Ajustar el tamaño del texto en consola (TTY)
Para mejorar la legibilidad en la terminal virtual durante la instalación:

1. 
   `su`
2. 
   `nano /etc/default/console-setup`
3. 
   `FONTSIZE="14x28"`

### Ajustar el PATH del sistema
Para asegurar que los binarios de administración estén accesibles:

1. Editar`~/.bashrc` y `~/.profile`:
   `nano ~/.bashrc`
   `nano ~/.profile`
2. Al final de ambos archivos:
   `export PATH=$PATH:/usr/local/sbin:/usr/sbin:/sbin`
3. Recargar cambios:
   `source ~/.bashrc`
   `source ~/.profile`

### Habilitar `sudo`
1. Instalar el paquete:
   `apt install sudo`
2. Añadir usuario al grupo:
   `usermod -aG sudo <tu_usuario>`
3. Verificar permisos con `visudo` (añade `usuario ALL=(ALL:ALL) ALL`).
4. Cerrar sesión y volver a entrar.

---

## 2. Instalación de Sway y Entorno


```bash

# Actualización del sistema
sudo apt update && sudo apt upgrade -y

# Herramientas esenciales
sudo apt install -y curl sway swaybg swaylock swayidle xdg-desktop-portal-wlr waybar pavucontrol blueman git wget build-essential kanshi network-manager network-manager-gnome pipewire pipewire-audio pipewire-pulse wireplumber

# Instalación de herramientas personalizadas (reemplazando por defecto)
sudo apt install -y alacritty rofi

# Capturas de pantalla y portapapeles
sudo apt install -y grim slurp wl-clipboard

# Fuentes
sudo apt install -y fonts-noto-color-emoji fonts-noto fonts-dejavu fonts-font-awesome
fc-cache -fv

# Aplicaciones básicas
sudo apt install -y xdg-user-dirs nautilus firefox-esr
xdg-user-dirs-update

---

## 3. Activar y generar archivos config/local