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

```mermaid
flowchart LR
    T[Técnico] -->|túnel| H[Hub VPS]
    H -->|túnel| P[Pasarela cliente]
    P --> PC[PC del cliente]

    H --> Portal[Portal web]
    H --> DB[(Base de datos)]
    H --> FW[Firewall]

    Pub[Web pública] --> DB
```
