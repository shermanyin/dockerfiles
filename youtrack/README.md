# Youtrack-server based on Ubuntu

- based on latest ubuntu image
- downloads a specific Youtrack version directly from jetbrains

## Running this image

```bash
docker run -d \
           --rm \
           --name <container-name> \
           -h <hostname> \
           -p <host-http-port>:8080 \
           -v <youtrack-data-dir>:/home/ubuntu/youtrack-data \
           <image name>
```

where
- **container-name**: name of the container instead of a randomly generated name
- **hostname**: hostname of the container
- **host-http-port**: port of the host to map to Youtrack web interface of the container
- **youtrack-data-dir**: the directory to store youtrack data
- **image name**: name of this image

e.g.:

```bash
docker run -d --rm --name youtrack -h youtrack -p 80:8080 -v ~/youtrack-data:/home/ubuntu/youtrack-data shermanyin/youtrack
```

## Setting up Youtrack

Visit http://<host-ip>:<host-http-port> and start the setup
process.  During the "confirm settings" part of the setup, go to "Advanced
Settings" and ensure all directories are located within
/home/ubuntu/youtrack-data.
