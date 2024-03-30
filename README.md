# Setting up Docker Server

In this guide I will be showing and explaining a way to setup your own docker server. I'll be tackling on 2 type of webpage, one is HTML and the other is Nodejs.

## Requirements

- GitHub account

- GitHub Desktop installed

- Docker Desktop installed

- Visual Studio installed

- NodeJs installed

- Docker extension installed ( in Vs code)

## Preparation Phase

### Intalling Docker

- Download Docker from the link : https://www.docker.com/products/docker-desktop/ .
(Click on Download for Windows)

- Rress the install **Docker-Desktop-Installer.exe** icon and you will be pressing **next** all the way till you start installing. There isn't any configuration that needs to be change you will be using default settings.

- Restart your computer.

### Getting Resouce

- Fork the repository: https://github.com/eduluz1976/docker-challenge-template

- There is a lot of method to clone the repository (I assume you know how to clone through github desktop, if not just do your research).

- Open the repository through vs code or any preferred editor, but in this guide I'll be focusing on vs code.

## Challenge 1 : Starting up a HTML Server

- Open the "challenge1" folder.

- Create a new folder called public.

- Create a index.html file inside the public folder.

- Open the html file, make a simple code that shows your name and student.

- Create a Dockerfile in the challenge1 folder.

- Open the Dockerfile and type the following code.
```Dockerfile
FROM nginx:latest
COPY /public /usr/share/nginx/html
EXPOSE 8080
CMD [ "nginx", "-g", "daemon off;" ]
```
- This is what the code do.
  - Specify the base image with “FROM nginx:latest”.
  - Copy the “public” folder to the Nginx web directory with ‘COPY ./public /usr/share/nginx/html’.
  - Expose port 8080 with ‘EXPOSE 8080’.
  - Set the Nginx command to run in the foreground with ‘CMD [“nginx”, “-g”, “daemon off:”]’.

- Easy way to open CMD with the directory of challenge1 is by right clicking the challenge1 folder and then click on **Open in  Integrated Terminal**

- Build the Docker Image using the following command : "docker build -t challenge1 ."
  (**Don't forget to add space and then a dot to complete the command**. The dot tells Docker to look for the Dockerfile in the current directory)

- After the image is built, execute "docker run -d -p 8080:80 challenge1".
  - ‘-d’ runs the container in detacjed mode (in the background).
  - '-p' 8080:80 maps port 8080 on your host to port 80 in the container (where Nginx listens by default).
  - ‘challenge1’ is the name of the image to run.

- Check if the creating a container is successfull by using this command "docker ps".

- Open your preferred browser and navigate to http://localhost:8080 , you'll be able to see your static webpage.

  ## Challenge 2 : Starting up a NodeJS Server

- Download the "challenge2.zip" file
 
- Unzip and Open the challenge2 folder
 
- Drag the challenge2 files to the challenge2 folder ( don't create a new folder )
 
- Type in the following command "docker init". This command creates a CLI menu prompting you to answer.  

> Welcome to the Docker Init CLI!

> This utility will walk you through creating the following files with sensible defaults for your project:
> - .dockerignore
> - Dockerfile
> - compose.yaml
> - README.Docker.md

> Let's get started!

> WARNING: The following Docker files already exist in this directory:
> - .dockerignore
> - Dockerfile
> - compose.yaml
> - README.Docker.md

> ? Do you want to overwrite them? Yes
> ? What application platform does your project use? Node
> ? What version of Node do you want to use? (18.18.0)

> ? What version of Node do you want to use? 18.18.0
> ? Which package manager do you want to use? npm
> ? What command do you want to use to start the app? [tab for suggestions] (npm start)

> ? What command do you want to use to start the app? npm start
> ? What port does your server listen on? 3000

> ? What port does your server listen on? 3000

> CREATED: .dockerignore
> CREATED: Dockerfile
> CREATED: compose.yaml
> CREATED: README.Docker.md

> ✔ Your Docker files are ready!

> Take a moment to review them and tailor them to your application.

> When you're ready, start your application by running: docker compose up --build

> Your application will be available at http://localhost:3000

> Consult README.Docker.md for more information about using the generated files.

- After completing you will get a lot of files.

- The following files contain:
 - ‘.doncterignore’ to specify which files and directories should be ignored in the build context.
 - ‘.Dockerfile’ This contains instructions for building your Docker image.
 - ‘.compose.yaml’ for defining and running multi-container Docker applications.
 - ‘README.Docker.md' with information about the generated files.

- Build the Docker image using the command "docker-compose up --build"
  
- Open your preferred browser and navigate to "http://localhost:3000/api/books"

- Push your recent change to your GitHub repository fork.
