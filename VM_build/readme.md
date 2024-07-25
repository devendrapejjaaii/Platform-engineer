# Access a folder in vm from local vscode

Generate SSH keys on your local machine (if you don't have them already):
ssh-keygen -t rsa -b 4096 -C "<your_email@example.com>"

Copy the public key to your GitHub account:

    Go to your GitHub settings.
    Navigate to "SSH and GPG keys".
    Click "New SSH key" and paste your public key.

Clone the repository on the VM:

SSH into your VM:
ssh azadmin@<VM_PUBLIC_IP>

Clone the repository:
git clone <git@github.com>:your_username/your_repository.git

Part 3: Connect the Repository to Your Local Laptop and VSCode

    Clone the repository on your local machine:
    git clone git@github.com:your_username/your_repository.git
Open the repository in VSCode:

    Open VSCode.
    Use the menu: File -> Open Folder and select the cloned repository folder.


    Initialize and apply the Terraform configuration:

    terraform init
terraform apply
Access the VM and verify the configuration:
ssh azadmin@<VM_PUBLIC_IP>

Manage the GitHub repository from both the VM and your local machine.

---------------------------------

## IDEA 1

1. Manually Create a Virtual machine using ubuntu 22.04 OS and install backstage application.
2. Use already deployed VM template and deploy a VM and configure backstage application.
3. Once you installed and configured application, now create a docker image for the application.
4. Verify if you docker image created can run container and access the application locally.
5. Next intital docker image created worked, push that working docker image to a azure container resgistry or any container registry of our choice.
6. For demo purpose we can use azure container registry , in order to push the images created in linux vm , we need to connect to container regisrty from linux vm.
7. In order to connect to registry we should have a username and password generated in ACR access key tab.
8. Next to push image once conncted to ACR, use docker push command
9. Finally create the container instace and check if your application is accessible over internet.

### IDEA 1 Implementation

1. Deploy a Azure Virtual machine manually or using ARM template with pre installed packages(like configureing backstage).
    1.1 Install Curl or wget

    ```
    sudo apt-get update sudo apt-get install curl #OR sudo apt-get install wget
    ````

    1.2 Install Node.js LTS version using NVM

    ```
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
    nvm install 20
    nvm use 20
    nvm alias default 20
    ```

    1.3 Install Yarn

    ```
    npm install --global yarn
    #To check the version 
    yarn --version
    ```

    1.4 Install docker

    ```
    sudo apt-get update
    sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    sudo apt-get update
    sudo apt-get install docker-ce docker-ce-cli containerd.io
    docker --version
    sudo systemctl start docker
    ```

    1.5 Install git

    ```
    sudo apt-get install git-all
    ```

2. Create backstage app using command 

```
npx @backstage/create-app@latest
```
