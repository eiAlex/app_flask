# app_flask
Building a Flask app with Docker Nginx and uwsgi 

# # Setting Up Docker for Windows and WSL to Work Flawlessly ##

In the general settings, you’ll want to expose the daemon without TLS.

Docker for Windows has been recently renamed to Docker Desktop, so if your settings look slightly different than the screenshot, no worries. It’s the same thing.

# Update the apt package list.
sudo apt-get update -y

# Install Docker's package dependencies.
sudo apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

 # Download and add Docker's official public PGP key.
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add   


# Verify the fingerprint.
sudo apt-key fingerprint 0EBFCD88

# Add the `stable` channel's Docker upstream repository.
#
# If you want to live on the edge, you can change "stable" below to "test" or
# "nightly". I highly recommend sticking with stable!
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

   # Update the apt package list (for the new apt repo).
sudo apt-get update -y


# Install the latest version of Docker CE.
sudo apt-get install -y docker-ce

# Allow your user to access the Docker CLI without needing root access.
sudo usermod -aG docker $USER

Install Docker Compose

We’re going to install Docker Compose using PIP instead of the pre-compiled binary on GitHub because it runs a little bit faster (both are still Python apps).

# Install Python and PIP.
sudo apt-get install -y python python-pip

# Install Docker Compose into your user's home directory.
pip install --user docker-compose

# Connect to a remote Docker daemon with this 1 liner:

echo "export DOCKER_HOST=tcp://localhost:2375" >> ~/.bashrc && source ~/.bashrc

export DOCKER_HOST=tcp://127.0.0.1:2375

# Verify Everything Works

# You should get a bunch of output about your Docker daemon.
# If you get a permission denied error, close + open your terminal and try again.
docker info

# You should get back your Docker Compose version.
docker-compose --version

# # Installing uWSGI ##

apt-get install build-essential python

apt-get install python-dev

# Install the latest stable release:
pip install uwsgi
# ... or if you want to install the latest LTS (long term support) release,
pip install https://projects.unbit.it/downloads/uwsgi-lts.tar.gz


Install Compose on Linux systems

sudo curl -L "https://github.com/docker/compose/releases/download/1.25.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

Test the installation.

docker-compose --version

# Install Virtualenv
apt-get install python-virtualenv

$ source activate
