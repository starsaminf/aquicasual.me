---
title: perdiendo el sudo
description: 
published: true
date: 2023-08-17T17:44:17.021Z
tags: 
editor: markdown
dateCreated: 2023-08-17T17:44:14.797Z
---

# Perdiendo acceso a sudo


Por un error fatal cambie el usuario del binario sudo, si lo se que verguenza!!! 😭😭😭😭😭

y si ejecutas **sudo bash** te saltara este error:

**/usr/bin/sudo must be owned by uid 0 and have the setuid bit set**

En este punto hay dos opciones:


1) Entrar modo recovery y cambiar los permisos
```bash
chown root:root sudo /usr/bin/sudo
chmod 4755 sudo
```

2) Si no hay forma de entrar modo recovery (mi caso), pero para mi suerte tengo mi usuario dentro del grupo docker.
```bash
docker run --rm -it -v /usr/bin/sudo:/tmp/sudo debian /bin/bash
chown -R root:root sudo
chmod 4755 sudo
```