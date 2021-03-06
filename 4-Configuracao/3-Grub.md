# 03 - Grub, Xorg, Drivers de Vídeo e Áudio

## Grub

Para instalarmos o grub nós temos duas alternativas, uma pra modo de boot BIOS e outra para UEFI.

### BIOS

Para instalar o grub em modo de boot bios é bem simples, basta seguir os seguintes comandos.

```console
# pacman -S grub
# grub-install --target=i386-pc --recheck /dev/sda
```

_obs: se a sua partição não for a /dev/sda você tem que substituí-la._

### UEFI

Para instalarmos o grub em UEFI nós temos que instalar outro tipo de pacote e passar mais umas opções.

```console
# pacman -S grub-efi-x86_64 efibootmgr
# grub-install --target=x86_64-efi --efi-directory=/boot/efi  --bootloader-id=arch_grub --recheck
```

E agora vamos gerar nosso arquivo de configurações do boot:

```console
# grub-mkconfig -o /boot/grub/grub.cfg
```

E pronto já temos nosso grub instalado com sucesso. Se você deseja fazer dual boot com outro OS você precisa instalar o pacote `os-prober`.

## Xorg

Para instalarmos qualquer interface gráfica nós precisaremos instalar o Xorg e fazer isto é bem simples.

```console
# pacman -S xorg xorg-server xorg-drivers mesa libgl
```

Pronto, já instalamos o Xorg.

## Drivers de vídeo

Vamos instalar os drivers de vídeo agora.

### Intel

```console
# pacman -S xf86-video-intel
```

### Nvidia

```console
# pacman -S nvidia nvidia-libgl
```

### AMD

```console
# pacman -S xf86-video-amdgpu
```

### Virtual box

```console
# pacman -S virtualbox-guest-utils virtualbox-guest-modules-arch mesa-libgl
```

## Áudio

Vamos instalar pacote que vai cuidar do nosso áudio o `pulseaudio`.

```console
# pacman -S pulseaudio pulseaudio-alsa
```

Se você tiver problemas com chiados ou ruídos instale o pacote `pulseeffects` e habilite a função de inicializar junto ao sistema.

E pronto, já temos nosso sistema instalado e configurado mas antes de reiniciarmos nossa máquina vamos instalar um display manager e uma interface gráfica! Confira o [próximo arquivo](../5-GUI/1-GUI.md)
