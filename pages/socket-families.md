# Les sockets les plus utilisés

<div v-click="1">

```py
import socket

def list_address_families():
    families = {getattr(socket, attr): attr for attr in dir(socket) if attr.startswith('AF_')}
    return families

def main():
    families = list_address_families()
    print("Available Address Families:")
    for family, name in families.items():
        print(f"{name} ({family})")

if __name__ == "__main__":
    main()

```

</div>

<div v-click="2">
Available Address Families:
AF_APPLETALK (16),
AF_DECnet (12),
AF_INET (2),
AF_INET6 (30),
AF_IPX (23),
AF_LINK (18),
AF_ROUTE (17),
AF_SNA (11),
AF_SYSTEM (32),
AF_UNIX (1),
AF_UNSPEC (0)
</div>

> <mdi-warning/> Attention, les valeurs peuvent changer suivant les systèmes.

---

## AF_INET

- IPv4 (TCP/UDP)
- Le plus utilisé / courant

<div v-click.hide="3">

````md magic-move

```c
struct sockaddr_in {
    sa_family_t    sin_family;    // Famille d'adresses : AF_INET (2 octet)
    in_port_t      sin_port;      // Port du service (2 octets)
    struct in_addr sin_addr;      // Adresse IPv4 (4 octets)
    char           sin_zero[8];   // Remplissage pour compatibilité avec struct sockaddr (8 octets)
};
```

```c

server_addr.sin_port = htons(PORT); // host to network short

```

````

</div>

<div v-click="'+1'">

```js {monaco-run}
function htons(number) {
    // Ensure the number is a 16-bit unsigned integer
    number = number & 0xFFFF;  // Mask to 16 bits (0xFFFF)
    
    // Swap the bytes: 16-bit number, where 0xABCD -> 0xCDAB
    return ((number << 8) & 0xFF00) | ((number >> 8) & 0x00FF);
}

// Example usage:
const port = 4444;
const portNetwork = htons(port);

console.log(`Before (little endian) : ${port} / 0x${port.toString(16)}`)
console.log(`After (big endian): ${portNetwork} / 0x${portNetwork.toString(16)}`)
```

</div>



---

## AF_UNIX

- Unix domain sockets (IPC local)
- Utilisé pour la communication entre processus locaux (sans réseau)

````md magic-move

```c
struct sockaddr_un {
    sa_family_t sun_family;     // Famille d'adresses : AF_UNIX (2 octets)
    char        sun_path[108];  // Chemin du fichier du socket Unix (108 octets)
};
```

```c
struct sockaddr_un server_addr;
server_addr.sun_family = AF_UNIX;
strncpy(server_addr.sun_path, "/tmp/my_unix_socket", sizeof(server_addr.sun_path) - 1); // Chemin du socket
server_addr.sun_path[sizeof(server_addr.sun_path) - 1] = '\0'; // Terminateur nul
```
````

> <mdi-warning/> Attention, bien qu'un fichier soit créé sur le système. Aucune donnée ne transite dessus.



---

## AF_ VSOCK

...
