# Openssh-server based on Ubuntu

- user "ubuntu" added with passwordless sudo priviledge
- root SSH login disabled
- password SSH login disabled

To run this image in detached state, execute:

```bash
docker run -d \
           --rm \
           --name <container-name> \
           -h <hostname> \
           -p <host-port>:22 \
           -v <ssh-dir>:/home/ubuntu/.ssh \
           <image name>
```

where:
- **container-name**: name of the container instead of a randomly generated name
- **hostname**: hostname of the container
- **host-port**: port of the host to map to port 22 of the container
- **ssh-dir**: the directory with the SSH "authorized_keys" file which contains
acceptable public keys for SSH login.
- **image name**: name of this image

e.g.:

```bash
docker run -d --rm --name sshd -h sshd -p 10022:22 -v ~/.ssh:/home/ubuntu/.ssh shermanyin/sshd
```

To login via SSH:

```bash
ssh -i <private-key> ubuntu@<container-ip> -p <host-port>
```

e.g.:

```bash
ssh -i ~/.ssh/id_rsa ubuntu@localhost -p 10022
```
