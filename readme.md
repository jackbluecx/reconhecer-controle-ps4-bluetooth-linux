<span style="font-size:21px;">Achei esse codigo na internet em um forum, demorei horrores para achar, não dou o credito porque nãolembro onde foi.
    Aqui tem algumas soluções para conexão de dispositivos, principalmente controle dualshock 4, use as variaveis que quiser.</span>


<hr/>


# grave os comandos abaixo em 
# "/lib/udev/rules.d/99-steam-controller-perms.rules",
"sudo nano /lib/udev/rules.d/99-steam-controller-perms.rules".

<hr/>

```bash
# Essa regra é necessária para o funcionamento básico do
# controle no Steam e para a emulação de teclado/mouse.
SUBSYSTEM=="usb", ATTRS{idVendor}=="28de", MODE="0666"

# Essa regra é necessária para a emulação de gamepad;
# certifique-se de substituir 'pgriffais' por um grupo ao qual o usuário 
# que executa o Steam pertença.
KERNEL=="uinput", MODE="0660", GROUP="pgriffais", OPTIONS+="static_node=uinput"

#Dispositivos Valve HID via Bluetooth Hidraw
KERNEL=="hidraw*", ATTRS{idVendor}=="28de", MODE="0666"

#Valve HID devices over bluetooth hidraw
KERNEL=="hidraw*", KERNELS=="*28DE:*", MODE="0666"

#DualShock 4 via USB hidraw
KERNEL=="hidraw*", ATTRS{idVendor}=="054c", ATTRS{idProduct}=="05c4", MODE="0666"

#Adaptador sem fio DualShock 4 via USB hidraw
KERNEL=="hidraw*", ATTRS{idVendor}=="054c", ATTRS{idProduct}=="0ba0", MODE="0666"

#DualShock 4 Slim sobre USB hidraw
KERNEL=="hidraw*", ATTRS{idVendor}=="054c", ATTRS{idProduct}=="09cc", MODE="0666"

#DualShock 4 via Bluetooth Hidraw
KERNEL=="hidraw*", KERNELS=="*054C:05C4*", MODE="0666"

#DualShock 4 Slim via Bluetooth Hidraw
KERNEL=="hidraw*", KERNELS=="*054C:09CC*", MODE="0666"
```

<hr/>

# de permissão para a pasta "/dev/uinput" 
sudo chmod 666 /dev/uinput

<hr/>

# instale "python3-autopilot"
sudo apt-get install python3-autopilot

<hr/>

# rode esse comando
sudo udevadm trigger

<hr/>

# reinicie a steam, e reconecte o controle, se não for reinicie o sistema.

<hr/>


