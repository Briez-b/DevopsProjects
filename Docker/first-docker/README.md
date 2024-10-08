## Practice with Docker 

First register on docker hub

Creating my first container:
**1) Install docker**
``` bash
sudo pacman -S docker
```
**2) Add user to docker group**
``` bash
sudo usermod -aG docker ebryyau
```
For some reason I still wasn't able to run images even after log out. Reboot helped me
**3) Run simple hello world image to check if all work correctly:**
``` bash
docker run hello-world
```

Run our own image:
**1) Create Dockerfile and needed app code:**

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020240906072432.png)

1. **FROM ubuntu:latest**: This line sets the base image to the latest version of Ubuntu.
2. **WORKDIR /app**: Sets the working directory inside the container to `/app`.
3. **COPY . /app**: Copies all the files from the current directory on the host system into the `/app` directory in the container.
4. **RUN apt-get update && apt-get install -y python3 python3-pip**: Updates the package list and installs Python 3 and pip.
5. **ENV NAME World**: Sets an environment variable `NAME` with the value `World`.
6. **CMD ["python3", "app.py"]**: Specifies the command to run when the container starts, which is to execute the `app.py` script using Python 3.

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020240906072608.png)

App is a simple python hello-world
**2) Run build:**

``` bash
docker build -t ebryyau/first-ubuntu-image:v1 .
```
![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020240906074540.png)

**3) Run to be sure it works. And then you can push it to docker hub. Then this image will be accesible for everyone:**

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020240906075056.png)

![](https://github.com/Briez-b/DevOpsNotes/blob/main/Attachments/Pasted%20image%2020240906075115.png)

To remove images use this:
``` bash
docker rmi image-name
```
I can also remove multiple images or use image id

- **Check for Running Containers**: Make sure no running or stopped containers are using the image you want to delete. You can check with:
``` bash
docker ps -a # all, even stopped
docker ps # running containers
```
To check how many memories images take use:
```bash
docker system df
```

Here's a concise list of useful Docker commands for quick reference, covering common tasks such as managing containers, images, volumes, and more:

### **Some additional commands**
- **Start a Container:**
  ```bash
  docker start container-name-or-id
  ```
- **Stop a Container:**
  ```bash
  docker stop container-name-or-id
  ```
- **Remove a Container:**
  ```bash
  docker rm container-name-or-id
  ```
- **Run a New Container:**
  ```bash
  docker run -d --name container-name image-name
  ```
### **Images**
- **List All Images:**
  ```bash
  docker images
  ```
- **Build an Image from Dockerfile:**
  ```bash
  docker build -t image-name .
  ```
- **Remove an Image:**
  ```bash
  docker rmi image-name-or-id
  ```
- **Remove Unused Images:**
  ```bash
  docker image prune
  ```
- **Pull an Image from a Registry:**
  ```bash
  docker pull image-name
  ```

These commands will help you efficiently manage your Docker environment. Feel free to save or expand on this list based on your needs! Let me know if you need more details or examples for any command
