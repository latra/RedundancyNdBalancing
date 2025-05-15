# Redundancia y Balanceo

## NAT

## Redundancia

## Balanceo
[Revisen la documentación oficial - RTFM](https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/ipapp_fhrp/configuration/12-2sx/fhp-12-2sx-book/fhp-glbp.html)
### Round-Robin
1. Elegimos una V-IP para nuestros routers: `192.168.1.100`
2. Configuramos R1 con una prioridad superior
```
config t
interface FastEthernet 1/0
glbp 10 ip 192.168.1.100
glbp 10 priority 200
glbp 10 load-balancing round-robin
```
3. Configuramos R7 con una prioridad más baja
```
config t
interface FastEthernet 1/0
glbp 10 ip 192.168.1.100
glbp 10 priority 200
glbp 10 load-balancing round-robin
```
4. En H1 y H2, configuramos la puerta de enlace predeterminada hacia la V-IP:
```
config t
ip route 0.0.0.0 0.0.0.0 192.168.1.100
```
