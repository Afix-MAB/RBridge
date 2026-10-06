# Esborrany sobre el Projecte
### Context del projecte
Es creara una eina per poder fer monitoratge d'equips que estiguin debaix de un CG-NAT, es resoldra el problema de que els CG-NAT
no tenen cap manera tradicional per poder tenir ports oberts per a serveis o shells disponibles en xarxa que siguin disponibles desde 
una xarxa publica diferent, ja que té una forma de xarxa llogica d'aquesta manera.

```mermaid
graph TD;
    node1|10.162.114.201|-->ROUTER1;
    node2|10.162.114.202|-->ROUTER1;
    node3|10.162.114.201|-->ROUTER2;
    node4|10.162.114.202|-->ROUTER2;
    ROUTER1|20.40.20.1|-->CG-NAT;
    ROUTER2|20.40.20.2|-->CG-NAT;
    CG-NAT-->|PUBLIC IP| INTERNET;
```
 
```
sequenceDiagram
Alice->>John: Hello John, how are you?
loop HealthCheck
    John->>John: Fight against hypochondria
end
Note right of John: Rational thoughts!
John-->>Alice: Great!
John->>Bob: How about you?
Bob-->>John: Jolly good!

```
