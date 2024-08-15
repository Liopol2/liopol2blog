+++
title = 'Flats.sh'
date = 2024-08-13T23:21:02-03:00
draft = false
+++

Nada como un nuevo inicio, ya sea un nuevo dia, nuevo trabajo, nuevo auto, o porque no nuevo sistema.

Pero desgraciadamente, siempre que empezamos de 0 hay cosas que cambiar, para dejar todo a nuestro gusto, 
Este es mi caso cada que decido probar una nueva distro o cuando mi sistema lleva demasiado tiempo sin un buen reset. 

Durante los años descubri un par de cosas para hacer mi vida un poco mas facil reinstalando linux, aqui voy a compartir mis experiencias practicas y una de mis herramientas. 

### Particiones
> Crear una particion aparte para `~/home`.

Por mucho tiempo no le preste la atencion necesaria a esto y verdaderamente me arrepiento de no haber implementado esto antes.

Pero, ¿Por que esto es tan importante?
De hecho es sumamente simple, al tener una particion aparte para tus archivos, sabes que si queres hacer algun cambio radical en el sistema, como por ejemplo un passthrough pci-e, o cambiar algo en fstab, y no logras revertir los cambios, simplemente sobreescribes el sistema.

Y al no tocar la particion home no estas en peligro de perder nada de tus datos. 

Supongamos que tenes un disco hd0 con esta estructura:
```
|-sd0   / 
|-sd1   /home 
|-sd2   /boot
```
Entonces solo tenemos que reescribir `sd0` y recargar el bootloader, lo cual por lo general es echo por el propio instalador si seleccionaste, las particiones manualmente.
esto tambien nos habilita a encriptar solamente nuestros datos, para que de esa manera no perdamos el acceso al sistema ~~si es que~~ cuando perdamos la contraseña.
### Flatpak
Genial ahora tenemos un sistema completamente independiente de nuestros datos, podemos volar todo las veces que queramos, ¿Pero que pasa si no tenemos ni idea de como usar el package manager de la distro nueva?

Ahi es donde flatpak brilla, 
dependiendo de tu distro la instalacion va a variar, en algunos casos puede que la omitas completamente. 
y con un par de comandos independientemente de la distro podes instalar con el mismo comando el programa de tu eleccion.
ej:
`flatpak install flathub org.mozilla.firefox`

### Flats.sh
Flatpak es excelente de por si, pero ¿No seria mejor si puedo simplemente instalar todo de una vez?

Para eso hice este [script](https://github.com/Liopol2/flats.sh), que se encarga de leer un archivo `flatpacks.txt` donde puedo copiar y pegar los programas que quiera y ejecutar una a una las lineas el archivo.
Por ejemplo:
> flatpacks.txt
```
flatpak install flathub org.mozilla.firefox
flatpak install flathub com.visualstudio.code
flatpak install flathub me.kozec.syncthingtk
```
Instalando todo de una vez, y permitiendome trabajar en otras cosas como por ejemplo configurar syncthing o configurar otras partes del sistema. 

Espero que esto pueda ser de algun uso, y si deberia agregar o cambiar algo dejamelo saber.

Esto es todo por ahora, gracias por leer.