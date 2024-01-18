# Ansible Project: WordPress Deployment

This Ansible project automates the deployment of a WordPress application using Vagrant. The project consists of three VMs:

1. **Ansible Controller**: Responsible for managing and configuring the other VMs.
2. **MySQL Server**: Database server for the WordPress application.
3. **WordPress**: Web server hosting the WordPress application.

## Requirements

- [Vagrant](https://www.vagrantup.com/)
- [VirtualBox](https://www.virtualbox.org/)

## Usage

1. Clone the repository:

    ```bash
    git clone https://github.com/AbderrahmaneOd/ansible-vagrant-wordpress
    cd ansible-vagrant-wordpress
    ```

2. Spin up the VMs using Vagrant:

    ```bash
    vagrant up
    ```
3. Generate an SSH key pair on the Ansible Controller VM
    ```bash
    ssh-keygen
    ```
    Follow the prompts to generate the key pair. By default, the keys will be stored in the `~/.ssh/` directory.
    Then, copy the public key to the other VM.

   ```bash
    ssh vagrant@192.168.33.11
    ssh vagrant@192.168.33.10
    ```
      Note: Ensure that you can connect to both VMs without entering a password.

5. Connect to the Ansible Controller VM:

    ```bash
    vagrant ssh ansible-controller
    ```

6. Navigate to the Ansible project directory:

    ```bash
    cd /ansible
    ```
7. Install requirements:

    ```bash
    ansible-galaxy install -r requirements.yml
    
8. Run the Ansible playbook to configure the MySQL Server and deploy WordPress:

    ```bash
    ansible-playbook -i hosts wordpress.yml
    ```

9. Access WordPress in your web browser:

    - URL: [http://localhost:8080](http://localhost:8080)

## Directory Structure
- `hosts`: Ansible inventory file specifying VM details.
- `wordpress.yml`: Main Ansible playbook orchestrating the deployment.
- `roles/`: Ansible roles containing tasks for WordPress.
- `Vagrantfile`: Vagrant configuration file for VM setup.

## Author
- Abderrahmane Ouaday
