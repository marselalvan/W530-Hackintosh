# W530-Hackintosh Sequoai
Esta es una guia con su carpeta EFI la cual te ayudara espesificamente con esta Laptop, hay mucho de esta Efi que esta hecho por otra guia de T530, ya que basicamente son las mismas laptos.

Funciona todo menos la tarjeta grafica Nvidia Quadro K1000m
Investigando no es algo que puedas activar pues no es compatible la forma en como se proyectan los graficos en la pantalla, asi que hay que conformarse con los graficos integrados de intel.
WiFi y Bluetooth pero hay que hacer un paso extra post Instalacion para que funcione. 

Componente	Detalles
Modelo	Lenovo ThinkPad W530, modelo n.° 2429-62G
Conjunto de chips	Intel QM77 Express
Versión del BIOS	2.77, desbloqueado con 1vyRain
Procesador	Intel(R) Core(TM) i7-3740QM CPU @ 2.70GHz
Memoria	8 GB
Mínimo: 8 GB
Gráficos integrados	Gráficos Intel HD 4000, 2048 MB de RAM asignados
Mostrar	Pantalla TFT HD+ de 15,6" (1600 x 900 píxeles)
Audio	Realtek ALC269VC Rev.3 (ID de diseño: 39)
Ethernet	Conexión de red Gigabit Intel 82579LM
WiFi y Bluetooth	Centrino Ultimate-N 63000
Lector de múltiples tarjetas	Lector 4 en 1 de Ricoh (MMC, SD, SDHC, SDXC)
Ranura para ExpressCard/34	desactivado

Pasos a Seguir
Esta guia esta hecha para aquellas personas que tienen conocimiento previo de OpenCore y como realizar una USB
Remplace la carpeta EFI en su Unidad USB, no deberia tener problemas de instalacion, lo unico importante es quitar cambiar ciertos parametros de la Bios, que basicamente son los mismos en casi todas las laptops
Te dejo este video de Youtube donde alguien enseña la configuracion de la Bios, el video empieza exactamente donde empieza a modificar.


https://youtu.be/TnnrpA0Q0_4?si=EYmbBrZWVP2BKMSX&t=407

Una vez procedes con la instalacion es muy posible que arroje alguna clase de error en la instalacion donde tiene un problema para actulizar el sistema, pero no te preocupes solo acepta todo reinicia y continua la instalacion, seguira de forma correcta, muy probablemente no te pasara, pero si lo hace no te asustes.

Una vez se a instalado correctamente es importante que tengas en cuenta lo siguiente, el archivo SSDT esta configurado exactamente para el procesador mencionado, si tienes otro, es importante generar este archivo, en mi experiencia cuando tienes el correcto es mucho mas fluido el sistema.
Si no sabes generarlo porfavor sigue esta breve guia.

Abrir terminal

Introduzca el siguiente comando para descargar el script ssdtPRGen:
 curl -o ~/ssdtPRGen.sh https://raw.githubusercontent.com/Piker-Alpha/ssdtPRGen.sh/Beta/ssdtPRGen.sh

Hazlo ejecutable:
 chmod +x ~/ssdtPRGen.sh

Ejecute el script:
 sudo ~/ssdtPRGen.sh

El generado SSDT.amlse ubicará en~/Library/ssdtPRGen
Renombrarlo a SSDT-PM.aml(opcional, pero es una buena práctica)
Cópielo EFI/OC/ACPIy enumérelo en la ACPI/Addsección de suconfig.plist
En ACPI/Delete, deshabilitar Delete CpuPmy Delete Cpu0Istnuevamente
Guarde la configuración y reinicie.

Y despues de esto viene algo muy importante tenemos que usar OPEN CORE PARCHER pero tenemos que usar un version modificada, esta nos ayudara a que el WiFi y Bluetooth funcionen correctamente si es que tienes la misma tarjeta de red o similar. La version modificada estara en este repositorio.
Ademas de eso intalara los Drivers de los grafico de Intel.

Una vez temines con esto reinicia y listo.


Si tienes una tarjeta de red diferente te recomendaria consultar el siguiente repositorio https://github.com/5T33Z0/Lenovo-T530-Hackintosh-OpenCore?tab=readme-ov-file

aqui te ayuda a configurar, la cuestion es que necesitas tener una Bios modificada, la cual es relativamente sensillo hacerlo, sin miedo al exito.
Me parece que la ventaja de hacer esto es que es compatible con Airplay y las demas funciones inalambricas.

Asi que debes de saber que esta configuracion con intel no es capaz de hacerlo, pero funcionara correctamente el wifi y dispositivos Bluetooth.

En general es estable y no deberias tener muchos problemas.
