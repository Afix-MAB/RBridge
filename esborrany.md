# Esborrany sobre el Projecte
### Context del projecte
Es creara una eina per poder fer monitoratge d'equips que estiguin debaix de un CG-NAT, es resoldra el problema de que els CG-NAT
no tenen cap manera tradicional per poder tenir ports oberts per a serveis o shells disponibles en xarxa que siguin disponibles desde 
una xarxa publica diferent, ja que té una forma de xarxa llogica d'aquesta manera.

```mermaid
graph TD;
    node1-->|10.162.114.201|ROUTER1;
    node2-->|10.162.114.202|ROUTER1;
    node3-->|10.162.114.201|ROUTER2;
    node4-->|10.162.114.202|ROUTER2;
    ROUTER1-->|20.40.20.1|CG-NAT;
    ROUTER2-->|20.40.20.2|CG-NAT;
    ROUTER1-->|PRIVATE IP|CG-NAT;
    ROUTER2-->|PRIVATE IP|CG-NAT;
    CG-NAT-->|PUBLIC IP|INTERNET;
```

### Abast del projecte
Es tindra en compte en la creació del projecte, els usuaris que neccesiten el servei de monitoratge (els clients), la forma de la xarxa de forma llogica, s'intentara possar en practica, el servidor privat en xarxa per poder establir la xarxa, els dispositius raspberry per  


### Diagrama de Projecte

Els agents en el projecte son els següents: 

1. Xarxa
 * Técnic - Amb el seu portatil es podrá connectar en el VPS. 
 * WireGuard pel admin - És el tunel del tecnic fins al VPS. 
 * WireGuard pel client - És el tunel que tindra cada client. 
 * FireWall -  Per tindre un minim de seguretat en la connexió, per només permetre la connexió a autoritzats.
 * Pasarela - Será la Raspberry en casa del client.
 * PC del client - On rebra l'accés.
 * VPS -  El servidor privat que tindrem, on resideix, WireGuard (els tunels), firewall, la base de dades, el reconciliador de peticions de la web amb la bdd, i possiblement la monitorització de connexions, memories...
 > S'utilitzara el VPS de forma simulada, també hauria d'estar el portal web per les peticions del reconciliador per la base de dades, es simulara tota l'estructura funcional pero no per llimitacions de hardware.

2. Gestió
 * Portal web - On el tecnic demana les sessions.
 * Base de dades - On es guarden els clients, sessions...
 * Reconciliador - Compara el que te la bdd amb el que tenim possat.
 > S'esta pensat utilitzar python de forma molt bàsica per crear el reconciliador.
 * Monitorització - Avisa si algun node falla.

3. Serveis
 * Web publica - Presenta el servei del tecnic.

```mermaid
flowchart LR
    T[Técnico] -->|túnel| V[VPS]
    H -->|túnel| P[Pasarela client]
    P --> PC[PC del cliente]

    H --> Portal[Portal web]
    H --> DB[(Base de datos)]
    H --> FW[Firewall]

    WPub[Web pública] --> DB
```
