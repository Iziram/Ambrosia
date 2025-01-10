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


---

## AF_INET

...

---

## AF_UNIX
...

---

## AF_ VSOCK

...
