# Openssh-server based on Ubuntu

- user "ubuntu" added with passwordless sudo priviledge
- root SSH login disabled
- password SSH login disabled

To this image in detached state, execute:

```bash
docker run -d -p <host-port>:22 -v <ssh-dir>:/home/ubuntu/.ssh <image name>
```

, where *<ssh-dir>* is the directory with the SSH "authorized_keys" file which
contains acceptable public keys for SSH login.  e.g.:

```bash
docker run -d -p 10022:22 -v ~/.ssh:/home/ubuntu/.ssh sshd
```

To login via SSH:

```bash
ssh -i <private-key> ubuntu@<container-ip> -p <host-port>
```

e.g.:

```bash
ssh -i ~/.ssh/id_rsa ubuntu@localhost -p 10022
```
