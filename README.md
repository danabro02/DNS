# practica dns

## ejercicio 1 

Crea un repositorio de Github para la práctica y sube los cambios de forma gradual. Si subes todos
los ficheros a la vez, en un solo commit, supondré que has copiado la práctica.
El repositorio deberá tener:

• Un fichero .gitignore No se deberá tener bajo control de versiones el directorio .vagrant ni los
ficheros de backup.

• Un fichero Vagrantfile para crear las máquinas virtuales del proyecto.

• Un fichero README.md dónde explique la práctica. Se incluirán capturas (ya sea en texto o en
gráfico) que muestren los puntos más importantes de la práctica y cómo ejecutarla.
Especialmente muestra como se produce la transferencia de zona.

• Un fichero de licencia LICENSE con una licencia de tu elección.


`vagrantfile:` he creado este archivo (commit)
`LICENCE:` he creado este archivo y a su vez le he añadido contenido sacado de internet (commit)
`gitignore:` he creado este archivo (commit)
`README.md:` he creado este archivo (commit)

## ejercicio 2

Todas las máquinas de la red (tanto reales como ficticias) estarán en la red 192.168.57.0/24.

Equipo                                                       FQDN                                IP
Linux gráfico (imaginario)                          mercurio.sistema.test                       .101
Debian texto                                        venus.sistema.test                          .102
Debian texto                                        tierra.sistema.test                         .103
Windows gráfico o server (imaginario)               marte.sistema.test                          .104

`vagrantfile:` he modificado este archivo para cumplir con lo anteior puesto, creando dos maquinas virtuales con las ips dadas

## ejercicio 3

Activa solamente la escucha del servidor para el protocolo IPv4.
