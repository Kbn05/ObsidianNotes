Partición de disco

Al hacer partición de disco, se deben crear mín 3: SWAP, Boot y /(contiene los demás archivos del sistema)

Partición Grub/Boot: máx 1GB
Se le asocia la Fat32
En caso de error con distro al momento de seleccionar Fat32, algunas pedirán en su lugar mínimo Ext2
Punto de montaje /boot
Bootable flag: on
Mount options recommended: noatime - nodiratime

Partición SWAP:
Mismo proceso pero se escoge tipo lógica y asociado a Swap.

Partición /:
Primaria
Ext4

Kali default file system: ext4
# Instalación Arch

```Bash
loadkeys es
echo "es_ES.UTF-8 UTF-8" > /etc/locale.gen
locale-gen
export LANG=es_ES.UTF-8
ls /sys/firmware/efi/efivars (comprobación uefi-bios)
ping 8.8.8.8
timedatectl status
timedatectl set-zone /America/Bogota
fdisk -l
```
## Configuración wifi (en caso de no tener conexión Ethernet)
```bash
ip link (ver NICS)
ip link set $(network interface) up
iwlist $(network interface) scan
##En caso de estar bloqueada la interfaz por error RF-kill usa:
rfkill unblock all
"Dependiendo de la seguridad de la red (WEP/WPA/WPA-2) será diferente el modo de conexión"
#WEP
iwconfig $(network interface) essid $(SSID) key s:$(password)
#WPA-WPA2
wpa_passphrase $(SSID) $(password) > /etc/wifi
wpa_supplicant -B -i $(network interface) -D wext -c /etc/wifi 
(o también)
wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf -D nl80211


#WEP-WPA-WPA2
dhclient

ping 8.8.8.8
```
## Particionado BIOS
```bash
cfdisk /ruta/disco (ej:/dev/sda)
Seleccionar etiqueta:
BIOS - Dos
UEFI - GPT
'boot'
300M
primaria
inciable
'swap'
4G
primaria
tipo: Linux SWAP/solaris
'root'
30-40G
primaria

Escribir

fdisk -l

FORMATEAR
mkfs.ext4 -L 'BIOS' /ruta/particion/boot

mkswap /ruta/particion/swap
swapon /ruta/particion/swap (Encender SWAP)

mkfs.ext4 -L 'root' /ruta/particion/root

fdisk -l

lsblk (ver particiones montadas)
mount /ruta/particion/root /mnt/

mkdir -p /mtn/boot
mount /ruta/particion/boot /mnt/boot
```

## Particionado UEFI
```bash
cfdisk /ruta/disco (ej:/dev/sda)
Seleccionar etiqueta:
BIOS - Dos
UEFI - GPT
'Partición EFI'
150-300M
primaria
tipo: Sistema EFI
'SWAP'
4G
tipo: Linux SWAP
'Root'
30-40G
ext4

Escribir

fdisk -l

mkfs.fat -F32 /ruta/particion/efi

mkfswap /ruta/particion/swap
swapon /ruta/particion/swap

mkfs.ext4 /ruta/particion/root

mount /ruta/particion/root /mnt
mount /ruta/particion/efi /mnt/boot/efi

lsblk
```

Propuesta partición de mi equipo

Disco total = 235G

EFI: 300M
SWAP: 4G
Root: 65G
Home: lo demás (165G apróx)

## Instalación sistema
```bash
pacstrap /mnt base base-devel nano (base + base 4 development)

'Ahora instalamos kernel (leer documentación arch)'
pacstrap /mnt linux linux-firmware linux-headers mkinitcpio

```

Los puntos de montaje los hicimos manualmente, para que sean automático debemos tener el archivo de fstab configurado para que se inicie. Cuando se inicia el SO, la primera capa BIOS/UEFI, pasa al GRUB y luego al SO.

```bash
cat /mnt/etc/fstab

'Si está vacío'
genfstab -p /mnt >> /mnt/etc/fstab
```
Entrar al sistema arch
```bash
arch-chroot /mnt
nano /etc/locale.gen
'Seleccionar es_CO.UTF-8'
locale-gen
export LANG= es_CO.UTF-8
echo "LANG= es_CO.UTF-8" > /etc/locale.conf
```
## Zona horaria
```bash
ls /usr/share/zoneinfo
ln -sf /usr/share/zoneinfo/America/Bogota /etc/localtime

pacman -S curl

ln -sf /usr/share/zoneinfo/$(curl https://ipapi.co/timezone) /etc/localtime

hwclock -w
hwclock --systohc

date

echo "KEYMAP=es" > /etc/vconsole.conf

echo "$(hostname)" > /etc/hostname

passwd root
(clave: 123456)

useradd -m -g users -G wheel -s /bin/bash $(username)

passwd $(username)
(123456)

nano /etc/sudoers

('Agregar usuario donde se encuentra root')
$(username) ALL=(ALL:ALL) ALL

pacman -S dhcp dhcpcd networkmanager iwd

systemctl enable dhcpcd NetworkManager

pacman -S reflector

reflector --verbose --latest 10 --sort rate --save /etc/pacman.d/mirrorlist
```
## Grub para UEFI
```bash
pacman -S grub efibootmgr os-prober

grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=Arch

grub-install --target=x86_64-efi --efi-directory=/boot/efi --removable

ls /boot/efi
```
## Grub para BIOS
```bash
pacman -S grub os-prober

grub-install /ruta/disco/particionado

ls /boot
```
## Configuración de GRUB
```bash
nano /etc/default/grub
"Modificar"
GRUB_TIMEOUT=10
GRUB_DISABLE_OS_PROBER=true(sin #)
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=3 quiet" (remover quiet)

grub-mkconfig -o /boot/grub/grub.cfg
```
## Configuración de Pacman
```Bash
nano /etc/pacman.conf
"Modificar"
(Sin #)
Color
VerbosePkgLists
ParallelDownloads = 5
ILoveCandy
[multilib]
Include = /etc/pacman.d/mirrorlist

pacman -Sy

```
## Configuraciones finales
```bash
ls /root/

pacman -S xdg-user-dirs

xdg-user-dirs-update

ls /root/

su $(username) -c "xdg-user-dirs-update"

ls /home/$(username)

pacman -S gnu-free-fonts ttf-hack ttf-inconsolata noto-fonts-emoji

pacman -S neofetch lsb-release git wget openssh

##mkinitcpio -P

exit

umount -R /mnt

lsblk

swapoff /ruta/partición/swap

lsblk

reboot
```

## Aspectos personalización
- Terminal: Alacritty
- Gestor de ventanas: Mosaico[Qtile, spectrum, hyperland], Flotante[openbox]
- Escritorio: xorg
```bash
sudo pacman -S xorg-server xorg-apps xorg-xinit xterm (graphical drivers)

("Login Options")
sudo pacman -S lightdm lightdm-gtk-greeter
lightdm-gtk-greeter-settings
sudo systemctl enable lightdm.service

("Desktop Options")
mkdir -p ~/.config/qtile
sudo pacman -S qtile
cp /usr/share/doc/qtile/ default_config.py ~/.config/qtile/config.py

reboot

"En xterm"
setxkbmap es
sudo pacman -S kitty pulseaudio pavucontrol xorg-xinit volumeicon feh rofi picom cbatticon udisks2 udiskie network-manager-applet vlc imv scrot lxappereance notification-daemon libnotify lsd 

##Listar fuentes disponibles
fc-list

git clone https://github.com/arcolinuxd/arco-qtile
```

```bash
"Configuración HyperLand"

sudo pacman -S hyprland firefox kitty ranger

Hyprland

sudo pacman -S waybar
```

### AUR Install

``` Shell
"AUR Command installation"
git clone https://aur.archlinux.org/paru-bin.git

cd paru-bin/

makepkg -si

```

### Gnome install

``` Shell
sudo pacman -S xorg xorg-server
sudo pacman -S gnome
sudo systemctl enable gdm.service
sudo pacman -S kitty
#comprobar este
sudo pacman -S gtkmm
```
## Anotaciones

Por ahora con el Tiling Manager Qtile tengo problemas para la configuración de entorno de escritorio y reproducción multimedia y drivers de sonido. En caso de continuar revisar los enlaces:

- https://wiki.archlinux.org/title/Intel_graphics
- https://blog.desdelinux.net/instalar-drivers-de-video-intel-ati-y-nvidia-en-arch-linux/
- https://codigocristo.github.io/driver_intel.html
- https://docs.qtile.org/en/stable/manual/config/default.html#default-config

Neofetch está descontinuado, en su lugar usar fastfetch

#### Lo siguiente es una conversación con ChatGPT que me ayudó a solucionar un problema con la conexión:

estoy en el instalador de archlinux y requiero conectarme al wifi por comandos

###### ChatGPT dijo:

ChatGPT

¿Estás usando un entorno con acceso a la terminal y tienes el nombre de tu red Wi-Fi?

4o mini

##### Dijiste:

si

###### ChatGPT dijo:

ChatGPT

Primero, ejecuta `iwctl` para entrar en el modo interactivo. Luego, usa `station device scan` para buscar redes, seguido de `station device get-networks` para ver la lista. Finalmente, con `station device connect nombre_de_red`, conéctate a tu Wi-Fi. Asegúrate de reemplazar "device" con el nombre de tu adaptador, como `wlan0`.

4o mini

##### Dijiste:

me encuentro en la interfaz de instalación de arch, he ejecutado el comando: ip link Para ver ñas interfaces de red, al hacerlo me aparecen 2 enp2s0 y wlan0, al querer hacer el up a wlan0 me aparece el siguiente error: RTNETLINK answers: Operation not possible due to RF-kill El problema es que al hacer el comando up con la otra interfaz me permite hacerlo, pero al querer escanear redes con el comando: iwlist $(network interface) scan Me aparece el error: enp2s0 Interface doesn't support scanning

###### ChatGPT dijo:

ChatGPT

El error de RF-kill indica que la interfaz inalámbrica está desactivada. Puedes intentar habilitarla con el comando `rfkill unblock all`. Luego, verifica el estado con `rfkill list`. Después, prueba nuevamente `ip link set wlan0 up` y realiza el escaneo.

4o mini

##### Dijiste:

ahora que escanee la red y pude detectar la mia, como puedo conectarme a ella, lei que para redes con seguridad WPA es con los comandos: wpa_passphrase $(SSID) $(password) > /etc/wifi wpa_supplicant -B -i $(network interface) -D wext -c /etc/wifi dhclient Pero para mi red que es WPA-2 como sería?

###### ChatGPT dijo:

ChatGPT

Para conectarte a una red WPA2, puedes seguir los mismos pasos que mencionaste, ya que `wpa_passphrase` y `wpa_supplicant` son compatibles con WPA2. Aquí tienes los pasos:

1. **Genera el archivo de configuración**:
    
    bash
    
    Copiar código
    
    `wpa_passphrase "SSID" "password" | sudo tee /etc/wpa_supplicant.conf`
    
2. **Conéctate a la red**:
    
    bash
    
    Copiar código
    
    `sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf -D wext`
    
3. **Obtén una dirección IP**:
    
    bash
    
    Copiar código
    
    `sudo dhclient wlan0`
    

Asegúrate de reemplazar `"SSID"` y `"password"` con el nombre de tu red y la contraseña, respectivamente. Si `wext` no funciona, también puedes intentar con `nl80211`:

bash

Copiar código

`sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf -D nl80211`

¡Intenta esto y verifica tu conexión!

4o mini

##### Dijiste:

Al hacerlo con este: sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf -D nl80211 Me aparece el mensaje Succesfully initialized wpa_supplicant El problema es que al hacer 'dhclient' wlan0 y comprobar mi conexión no me toma ip ni me deja hacer ping 8.8.8.8 ya que aparece 'Network is unreachable'

###### ChatGPT dijo:

ChatGPT

Si `wpa_supplicant` se inicializó correctamente pero no obtienes una dirección IP, puede ser un problema con el proceso de DHCP. Aquí hay algunos pasos para solucionar el problema:

1. **Verifica la conexión**: Asegúrate de que `wpa_supplicant` esté ejecutándose correctamente:
    
    bash
    
    Copiar código
    
    `sudo wpa_cli status`
    
2. **Intenta reiniciar `dhclient`**: A veces, reiniciar `dhclient` puede ayudar:
    
    bash
    
    Copiar código
    
    `sudo dhclient -r wlan0  # Libera la dirección IP sudo dhclient wlan0      # Solicita una nueva dirección IP`
    
3. **Verifica el estado de la conexión**: Ejecuta:
    
    bash
    
    Copiar código
    
    `ip addr show wlan0`
    
    Comprueba si se asignó alguna dirección IP.
    
4. **Verifica el router**: Asegúrate de que tu router esté funcionando correctamente y que no haya límites en el número de dispositivos conectados.
    
5. **Revisa logs de errores**: Puedes revisar los logs del sistema para ver si hay algún error relacionado:
    
    bash
    
    Copiar código
    
    `journalctl -xe`
    

Si aún no puedes conectarte, prueba desconectar y volver a conectar `wpa_supplicant` y `dhclient` para ver si eso resuelve el problema.

4o mini

##### Dijiste:

Al hacer el comando wpa_cli status me aparece lo siguiente: Failed to connect to non-global ctrl_iframe: (nil) error: No such file or directory Al intentar sudo dhclient -r wlan0 # Libera la dirección IP sudo dhclient wlan0 # Solicita una nueva dirección IP Y comprobar si me tomo ip me aparece igual, no toma Cuando verifico los logs con: journalctl -xe Me aparece lo siguiente: recieve_packet failed on wlan0: Network is down Could not register frame watch type 00d0: -114

###### ChatGPT dijo:

ChatGPT

Parece que `wpa_supplicant` no está gestionando correctamente la interfaz. Vamos a intentar algunos pasos adicionales:

1. **Detén `wpa_supplicant`**:
    
    bash
    
    Copiar código
    
    `sudo killall wpa_supplicant`
    
2. **Asegúrate de que `wlan0` esté activa**:
    
    bash
    
    Copiar código
    
    `sudo ip link set wlan0 up`
    
3. **Vuelve a iniciar `wpa_supplicant`**: Asegúrate de usar el modo correcto para tu driver:
    
    bash
    
    Copiar código
    
    `sudo wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf -D nl80211`
    
4. **Intenta obtener una dirección IP nuevamente**:
    
    bash
    
    Copiar código
    
    `sudo dhclient wlan0`
    

Si el problema persiste, verifica si hay un controlador específico que necesites para tu adaptador de red. También asegúrate de que no haya bloqueos de hardware en el adaptador (como un interruptor físico en la laptop).