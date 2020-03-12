# Recetas JETBOT


## 1. Reducir la Memoria RAM usada por Ubuntu, instalando LUbuntu

Con estos pasos reducimos 1GB de Memoria RAM, tomado de este [enlace](https://www.zaferarican.com/post/how-to-save-1gb-memory-on-jetson-nano-by-installing-lubuntu-desktop)

* Remover ubuntu-desktop
    
            sudo apt remove --purge ubuntu-desktop

* Instalar lxdm display manager. Puede aparecer un dialogo para seleccionar el display manager, Seleccione **lxdm**

            sudo apt install lxdm

* Remover el display manager de Ubuntu por defecto, gdm3

            sudo apt remove --purge gdm3

* Ubuntu 18.04 no tiene a Lubuntu-desktop en los repositorioes. Por esta razón, instale el escritorio LXDE si está en 18.04.

            sudo apt install lxde

* Para 18.10 y superiores, puede instalar Lubuntu-desktop usando

            sudo apt install lubuntu-desktop

* Es recomendado reinstalar lxdm para reconfigurar lubuntu-desktop

            sudo apt install --reinstall lxdm

Después de REINICIAR, notará un consumo de memoria cercano a los 400Mb.


## 2. Rotar la cámara 180° en JetBot

En algunos casos al activar la cámara del vehiculo esta puede aparecer al revés, siga los siguientes pasos para solucionarlo:

* Abra el código fuente de la cámara

            cd ~/jetbot/jetbot/camera.py

* Busque el método `_gst_str` de la clase `Camera`

* Modifique `nvvidconv` por `nvvidconv flip-method=2`

* Recompile las fuentes de jetbot

            cd ~/jetbot
            sudo python3 setup.py install


## 3. Conectar la JetBot a WiFi

* Conecte la JetBot al router usando un cable de Ethernet, y conecta su PC a la misma Red/Router

* Ingrese por SSH a la JetBot usando la Ip mostrada en la PioLed, ej (192.168.1.3)

            ssh jetbot@192.168.1.3

* En la terminal, use el siguiente comando para listar las redes WiFi disponibles.

            sudo nmcli device wifi list

* Conectese a la red WiFi 

            sudo nmcli device wifi connect <ssid_name> password <password>

