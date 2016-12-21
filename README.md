# Setting up and Using CoreNLP

CoreNLP is an open source, state-of-the-art server for use in Natural Language Processing tasks. The server can perform basic NLP tasks such as tokenizing and lemmatizing to high standards, while also performing extremely well on more advanced use cases such as recognizing entities and sentiment.

### Setup

#### Local Setup

To set up CoreNLP locally, follow the instructions to install Docker here: [https://www.Docker.com/products/overview#/install_the_platform](https://www.Docker.com/products/overview#/install_the_platform). Once Docker is installed, run the following command in your terminal to start the CoreNLP server on Port 9000. The container will require more than 2 GB of free space and run CoreNLP version 3.6 with full functionality. The files may take a few minutes to download and extract.

``` bash
docker run -itd -p 9000:9000 --name corenlp graham3333/corenlp-complete-custom
```

The server is up and running locally and ready to accept requests! You can test that it's up by going to `http://localhost:9000` in your web browser, where the server is accepting requests. 

#### Remote Setup

To set up CoreNLP for general access in the cloud, first spin up an AWS instance with at least 4 GB of RAM - any instance will do, but I provide instructions for the Amazon Linux AMI here. When launching the AMI, be sure to create a Custom TCP Rule that allows traffic on Port 9000. For testing purposes, a t2.medium with 10 GB EBS storage should be fine. Once the instance is up and running, SSH in, update, install Docker, change Docker's user permissions, and reboot using the following code.

``` bash
sudo yum update -y
sudo yum install docker -y
sudo usermod -aG docker ec2-user
sudo reboot
```

Once the instance restarts, SSH back in and run the following command to start the CoreNLP server on Port 9000. The container will require more than 2 GB of free space and run CoreNLP version 3.6 with full functionality. The files may take a few minutes to download and extract.

``` bash
docker run -itd -p 9000:9000 --name corenlp graham3333/corenlp-complete-custom
```

The server is up and running and ready to accept requests! You can test that it's up by going to `http://[Your instance IP]:9000` in your web browser, where the server is accepting requests. 

### Using CoreNLP

#### Interactive Use

You can use CoreNLP interactively by going to the address on your web browser specified in the Setup section. Either `http://localhost:9000` for local setup or `http://[Your instance IP]:9000` for remote setup. Use the web form to enter text and click Submit to get the results from the server.

#### Access via API

You can get results from CoreNLP via API or command line using the instructions from the [CoreNLP Page](http://stanfordnlp.github.io/CoreNLP/corenlp-server.html). If you are running CoreNLP on a remote server, just replace `localhost:9000` with `[Your instance IP]:9000` and you're ready to go. For a complete list of CoreNLP annotators and functionality, see the [CoreNLP Page](http://stanfordnlp.github.io/CoreNLP/annotators.html).