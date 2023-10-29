# connect with ssh #
ssh -p 5006 uwuser@72c90814cdee.westus.cloudapp.azure.com

# logout from the machine #
exit

# Generating a new SSH key #  
ssh-keygen -t ed25519 -C "name@email.com"

# start the ssh-agent in the background #
eval "$(ssh-agent -s)"

# Add your SSH private key to the ssh-agent. #
ssh-add .ssh/id_ed25519

# install the public key from your previously generated keypair for the user you just created on your VM #
ssh-copy-id -p 5006 -i .ssh/id_ed25519.pub jkuch@lab-7f2b540f-86ed-4cf1-8f5c-72c90814cdee.westus.cloudapp.azure.com

# create a ssh tunnel
ssh -L 8888:localhost:8888 -p '5006' 'piotreks@lab-7f2b540f-86ed-4cf1-8f5c-72c90814cdee.westus.cloudapp.azure.com'





