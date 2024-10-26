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

## ejercicio 3 (en este ejercicio se ve lo realizado en github y sus subidas paso a paso)

Activa solamente la escucha del servidor para el protocolo IPv4.

Establecer la opción dnssec-validation a yes

Los servidores permitirán las consultas recursivas sólo a los ordenadores en la red 127.0.0.0/8
y en la red 192.168.57.0/24, para ello utilizarán la opción de listas de control de acceso o acl.

El servidor maestro será tierra.sistema.test y tendrá autoridad sobre la zona directa e inversa.

El servidor esclavo será venus.sistema.test y tendrá como maestro a tierra.sistema.test.

El tiempo en caché de las respuestas negativas de las zonas (directa e inversa) será de dos horas
(se pone en segundos).

Aquellas consultas que reciba el servidor para la que no está autorizado, deberá reenviarlas
(forward) al servidor DNS 208.67.222.222 (OpenDNS).

Se configurarán los siguientes alias:
a. ns1.sistema.test. será un alias de tierra.sistema.test.
b. ns2.sistema.test. será un alias de venus.sistema.test..

mail.sistema.test. será un alias de marte.sistema.test.

El equipo marte.sistema.test. actuará como servidor de correo del dominio de correo
sistema.test.

## ejercicio 4

Puedes resolver los registros tipo A.

dig A sistema.test

Comprueba que se pueden resolver de forma inversa sus direcciones IP.

dig -x 192.168.57.103

Puedes resolver los alias ns1.sistema.test y ns2.sistema.test.

dig CNAME ns1.sistema.test
dig CNAME ns2.sistema.test

Realiza la consulta para saber los servidores NS de sistema.test. Debes obtener
tierra.sistema.test y venus.sistema.test.

dig NS sistema.test

Realiza la consulta para saber los servidores MX de sistema.test.

dig MX sistema.test

Comprueba que se ha realizado la transferencia de la zona entre el servidor DNS maestro y el
esclavo. Revisa los logs o realiza una consulta del registro AXFR.

dig AXFR sistema.test @192.168.57.102

Comprueba que tanto maestro como esclavo pueden contestar a las mismas preguntas.

dig A sistema.test
