# Access a folder in vm from local vscode

Generate SSH keys on your local machine (if you don't have them already):
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

Copy the public key to your GitHub account:

    Go to your GitHub settings.
    Navigate to "SSH and GPG keys".
    Click "New SSH key" and paste your public key.

Clone the repository on the VM:

SSH into your VM:
ssh azadmin@<VM_PUBLIC_IP>

Clone the repository:
git clone git@github.com:your_username/your_repository.git


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