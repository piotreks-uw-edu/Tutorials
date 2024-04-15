### move WSL to another drive
https://github.com/LpCodes/Moving-WSL-Distribution-to-Another-Drive

#### Check the existing WSL 2 installations on your computer by running the following command in a WSL or Command Prompt window:
wsl --list -v

#### If the installation you want to move is currently running, you need to stop it. For example, if you want to move debian 22.04, terminate it using the following command:
wsl -t Debian

#### Export the WSL distribution to a folder. In this example, we will export debian 22.04 as debian-ex.tar to the D:\wsl\wsl_export directory. Run the following command:
wsl --export Debian "D:\wsl_export\debian-ex.tar"

#### Unregister the previous WSL installation. This step removes the debian 22.04 distribution from the WSL 2 list obtained in the previous step. Execute the following command:
wsl --unregister Debian

#### Import the WSL installation to a new folder and re-register it. In this example, we will import debian 22.04 to the D:\wsl_import\debian directory using the exported debian-ex.tar file. Run the following command:
wsl --import Debian "D:\wsl_import\debian" "D:\wsl_export\debian-ex.tar"

#### Set default user (optional): This step is only necessary if you're: Importing to a new machine or creating a new user for debian. Setting the default user avoids login prompts each time you launch the distribution.

Using multiple users on your Windows machine and want different defaults for each. This clarifies which user launches by default for each WSL environment.

To set the default user, run: debian.exe config --default-user me (replace "me" with your actual username).

Congratulations! You have successfully moved your WSL distribution (debian 22.04) to another drive. You can now start the distribution and continue using it on the new location.

# #####################################################################################
### move docker desktop data to another drive
wsl -l -v
wsl --shutdown
wsl --export docker-desktop-data D:\wsl_export\docker-desktop-data.tar
wsl --unregister docker-desktop-data
wsl --import docker-desktop-data D:\wsl_export\ D:\wsl_export\docker-desktop-data.tar --version 2
#### Restart the computer, up Docker and tests
rm D:\wsl_export\docker-desktop-data.tar
