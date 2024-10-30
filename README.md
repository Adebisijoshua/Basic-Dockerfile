https://roadmap.sh/projects/basic-dockerfile


This is a project to build a basic Dockerfile to create a Docker image and belows are the requirements and the steps I took in solving the problem.

Requirements
--------------------
    The Dockerfile should be named Dockerfile.

    The Dockerfile should be in the root directory of the project.

    The base image should be alpine:latest.

    The Dockerfile should contain a single instruction to print “Hello, Captain!” to the console before exiting.

a) Step 1---------
I opened my  terminal and I created a directory (folder) for the project:
     (mkdir hello-docker && cd hello-docker)
------------------------------------------------

b) Step 2------------
I opened the dockerfile in a text editor (Vim) and added the following code inside

  # Use Alpine as the base image
FROM alpine:latest

# Run a command to print "Hello, Captain!" and exit
CMD ["echo", "Hello, Captain!"]

c) Step 3...
I exit the docker file in the editor and saved with :wq....
I make sure I was  inside the hello-docker directory and run:
  docker build -t hello-captain .
-------------------------------------
Explanation:

    docker build creates a Docker image.
    -t hello-captain tags the image with the name hello-captain.
    The dot (.) tells Docker to look for the Dockerfile in the current directory.
 
d) Step 4......
I ran the docker container from the Image I built using the command ::
    docker run hello-captain
---------------------------------------------
 And I got this output
   Hello, Captain!
-------------------------

     Advanced Version: Pass My  Name as an Argument
-------------------------------------------------------

e) Step 5............................

I modified the docker file and replaced the content with::
# Use Alpine as the base image
FROM alpine:latest

# Define an argument to pass a name during the build
ARG NAME="Captain"

# Set an environment variable to use it inside the container
ENV NAME=${NAME}

# Use the environment variable to print "Hello, [name]!"
CMD ["sh", "-c", "echo Hello, $NAME!"]

f) Step 6........................

I rebuit the Image with my name (Joshua) by running the following command::
docker build -t hello-joshua --build-arg NAME=Joshua .

g) Step 7-------- 

Then I ran the conatainer again.....
  docker run hello-joshua
--------------------

And the expected output is...
Hello, Joshua!
--------------

This is the end of the proejct

