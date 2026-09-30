# RemoteBridge - Plataforma d'accés remot
![Linux](https://img.shields.io/badge/SO-Linux-FCC624?logo=linux&logoColor=black)
![WireGuard](https://img.shields.io/badge/VPN-WireGuard-88171A?logo=wireguard&logoColor=white)
## Idea de servei

RemoteBridge serà un servei de control remot per a xarxes que funcionen amb [CG-NAT](https://www.xataka.com/basics/cg-nat-que-que-problemas-puede-provocar-como-saber-tienes-tu-conexion-a-internet), on una IP pública és compartida per més d'un router privat per usuari, és a dir, és un NAT en diferents xarxes privades, compartint així una mateixa IP pública.

El servei està pensat per poder tenir un accés remot segur per a un tècnic informàtic, que dona servei a petits negocis que tinguin una IP pública compartida. Es pensa tenir un servidor cloud (VPS), que fa de punt de connexió, i una passarel·la a casa del client. S'utilitzarà [WireGuard](https://www.wireguard.com/) per a la connexió.

El tècnic podrà accedir al dispositiu des d'una web, sense que el client hagi d'obrir ports o configurar qualsevol protocol. Cada usuari tindrà una Raspberry Pi per poder tenir aquesta connexió.

## Problemes

Hi ha la possibilitat que un grup d'empreses en un edifici estiguin darrere d'una CG-NAT, ja que alguns [operadors](https://www.redeszone.net/tutoriales/redes-cable/operadores-usan-cg-nat-internet/) n'utilitzen aquesta, com per exemple, MasOrange, Digi, Movistar o O2.

Per això, des de fora de la xarxa no es podria arribar a accedir als equips. Teòricament es podrien obrir ports al router, però seria molt insegur, ja que s'exposaria un servei directament a internet.

## Objectiu

Dissenyar i desplegar un sistema que ens deixi accedir de forma segura a les xarxes dels nostres clients, amb cada client aïllat dels altres, on principalment tot estarà en una web, que ens permetrà controlar el túnel per poder accedir als dispositius dels clients.

## Contingut

El projecte incorpora un VPS, 3 clients, 3 dispositius Raspberry, i un portal web amb un formulari de seleccions. També hi haurà una web per poder demanar els serveis del tècnic i una base de dades dels dispositius dels clients.
