# What it is

<div style="text-align: justify">
LTV Extension is a solution that provides LTV addition and re-sealing. LTV Extension API is the way to preserve your documents guaranteeing performance and legal security of your electronically signed documents.
<br></br>
A turnkey system that can be easily integrated with any business application without altering the user experience through a high-level web API based on the HTTP RESTful paradigm.
</div>

# How it works

<div style="text-align: justify">
An API is given with a module called LTV Optimizer, a server system that exposes our LTV Extension HTTP RESTful API through which business applications are able to process their electronic signatures extensions and re-sealings.
<br></br>
The documents to be extended are processed in the customer business layer and are not send to Uanataca Services since a hash of the document is sent, created from a hash algorithm.
<br></br>
For the execution of signature requests, all the data has to be sent along the credentials of the Billing account which will be used to authenticate the user. All the  computationally expensive workload operations are performed by our side and the result will be a document with its signatures extended by Uanataca which is a Qualified Trusted Service Provider.
</div>
<br></br>

<img src="https://raw.githubusercontent.com/UANATACA/LTV-REPO/main/img/graf_LTV.png">


# Configuration

This configuration requires a server with Linux distribution.

The steps shown below are for CentOS 7 but you can find the steps for your linux distribution in official docker docs.
https://docs.docker.com/engine/install/

> STEP 1: Install Docker

Run the following commands in this order.

	sudo yum update -y
	sudo yum install -y yum-utils
	sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
	sudo yum install docker-ce docker-ce-cli containerd.io docker-compose-plugin
	sudo systemctl start docker

Installation check:

    sudo docker run hello-world

    Unable to find image 'hello-world:latest' locally
    latest: Pulling from library/hello-world
    2ez49280125e: Pull complete
    Digest: sha256:c78be1d3a47d0caf71z82de806ee61xe01f32fc748091a6ec4cf1389848ib833
    Status: Downloaded newer image for hello-world:latest

    Hello from Docker!
    This message shows that your installation appears to be working correctly.

    To generate this message, Docker took the following steps:
    1. The Docker client contacted the Docker daemon.
    2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
        (amd64)
    3. The Docker daemon created a new container from that image which runs the
        executable that produces the output you are currently reading.
    4. The Docker daemon streamed that output to the Docker client, which sent it
        to your terminal.

    To try something more ambitious, you can run an Ubuntu container with:
    $ docker run -it ubuntu bash

    Share images, automate workflows, and more with a free Docker ID:
    https://hub.docker.com/

    For more examples and ideas, visit:
    https://docs.docker.com/get-started/

</br>

> STEP 2: Load provided LTV docker image 

Run the following command:

    docker image load -i uanataca_ltv.tar

Remove image file:

    rm -rf uanataca_ltv.tar

> STEP 3: Launch the service

For SandBox run:

    docker run -ti -e ENVIRONMENT=sandbox -p 80:16100 uanatacaltvserver

For Production run:

    docker run -ti -p 80:16100 uanatacaltvserver

Check service status:

    docker ps

    CONTAINER ID   IMAGE                         COMMAND                  CREATED        STATUS        PORTS                                             NAMES                                                                     
    149136458ed3   uanatacaltvserver             "/docker-entrypoint.…"   4 weeks ago    Up 4 weeks    0.0.0.0:16100->16100/tcp, :::16100->16100/tcp     upbeat_bassi


# Logs

Service logs are not stored locally, to consult them execute one of the following commands:

    docker logs <container_id>
<br>

    docker logs <container_id> > logs.txt           #For file output

# Postman Collection

A postman collection is available as a support for a quick start.<br>

<a href="https://cdn.bit4id.com/es/uanataca/public/signbox/Uanataca_SignBox_Postman.zip"> LTV Extension collection download</a>

<div id="APIReference" style="padding-top: 60px;color: #585856;"><h1>API Reference</h1></div>
