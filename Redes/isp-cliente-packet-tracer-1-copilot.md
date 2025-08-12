¡Entendido! Aquí tienes la configuración para cada router con las redes especificadas y su debido enrutamiento estático según la topología de la red que has compartido.

### Router0 (TU OTRO VECINO)
```plaintext
interface FastEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown

interface FastEthernet0/1
 ip address 10.0.0.1 255.255.255.0
 no shutdown

ip route 0.0.0.0 0.0.0.0 10.0.0.2
```

### Router1 (TU CASA)
```plaintext
interface FastEthernet0/0
 ip address 192.168.2.1 255.255.255.0
 no shutdown

interface FastEthernet0/1
 ip address 10.0.0.2 255.255.255.0
 no shutdown

ip route 0.0.0.0 0.0.0.0 10.0.0.1
```

### Router2 (TU VECINO)
```plaintext
interface FastEthernet0/0
 ip address 192.168.3.1 255.255.255.0
 no shutdown

interface FastEthernet0/1
 ip address 10.0.1.1 255.255.255.0
 no shutdown

ip route 0.0.0.0 0.0.0.0 10.0.1.2
```

### Router3 (Central Router)
```plaintext
interface FastEthernet0/0
 ip address 10.0.0.3 255.255.255.0
 no shutdown

interface FastEthernet0/1
 ip address 10.0.1.2 255.255.255.0
 no shutdown

interface FastEthernet1/0
 ip address 150.102.0.1 255.255.0.0
 no shutdown

ip route 192.168.1.0 255.255.255.0 10.0.0.1
ip route 192.168.2.0 255.255.255.0 10.0.0.2
ip route 192.168.3.0 255.255.255.0 10.0.1.1
```

### Notas Adicionales:
- **Router0, Router1 y Router2** están configurados con sus respectivas redes locales y rutas estáticas hacia el Router3 (Central Router).
- **Router3 (Central Router)** tiene rutas estáticas hacia todas las redes locales conectadas a los otros routers.

Con esta configuración, cada router debe ser capaz de comunicarse con las redes específicas de los otros routers a través del Router3 (Central Router). Si tienes más preguntas o necesitas más ajustes en la configuración, ¡házmelo saber! 😊🚀