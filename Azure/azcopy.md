### check and see if azcopy is already instaled on your VM by running:
which azcopy

### Inside your Ubuntu VM download AzCopy by running
wget https://aka.ms/downloadazcopy-v10-linux -O azcopy_linux_amd64.tar.gz
tar zxf azcopy_linux_amd64.tar.gz

### Edit the ‘.bashrc’ file5 in your user directory and add the following line at the very bottom of the file:
echo 'export PATH=azcopy_linux_amd64_10.22.2:$PATH' >> ~/.bashrc

### Now that azcopy is installed, get it authorized to talk to Azure. Run the command:
azcopy login --tenant-id f6b6dd5b-0000-441a-99a0-162ac5060bd2

### Copy to Azure
azcopy copy ~/tmp https://sdsdsfall23.blob.core.windows.net/container1--recursive