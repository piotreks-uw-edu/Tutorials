### sleep
sudo systemctl suspend

# create a user account #
sudo adduser jkuch

# add (-a) the user jkuch to the group sudo #
sudo usermod -aG sudo jkuch

# get a detailed status report about the Docker service #
sudo systemctl status docker

# install the capability to fetch apt packages over HTTPS and the curl tool for data transfers #
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y

# apropos command takes as argument a keyword and will try to find all man pages in the system
# For example, if you wanted to delete something, type apropos delete
apropos delete

# man command which displays manual pages. For example, if I wanted to know about the man command itself, I could run8 “man man”  #
man man

# With no arguments, cd moves you to the home directory #
cd

# The pwd command prints the name of the current directory #
pwd

# copy #
cp

# move #
mv

# remove a file #
rm

# install Docker
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
apt-cache policy docker-ce

# display the contents of a file
cat file.txt

# run a script
sudo ./run.sh

