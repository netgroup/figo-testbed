Preparation for Onboarding
==========================

This guide provides step-by-step instructions to prepare a server for onboarding into FIGO.

1. **Install SSH**
-------------------
To install the OpenSSH server, run:
   
.. code-block:: bash

    sudo apt update
    sudo apt install -y openssh-server

Ensure that the SSH service is running:

.. code-block:: bash

    sudo systemctl enable ssh
    sudo systemctl start ssh
    sudo systemctl status ssh

2. **Disable Password Authentication and Enable Pubkey Authentication**
------------------------------------------------------------------------
To improve security, disable password authentication and enforce key-based authentication.

Edit the SSH configuration file:

.. code-block:: bash

    sudo nano /etc/ssh/sshd_config

Find and modify the following lines:

.. code-block:: none

    PasswordAuthentication no
    PubkeyAuthentication yes

Then restart the SSH service to apply changes:

.. code-block:: bash

    sudo systemctl restart ssh

3. **Enable Passwordless Sudo for the `ubuntu` User**
------------------------------------------------------
To allow the `ubuntu` user to run `sudo` commands without a password:

Edit the sudoers file:

.. code-block:: bash

    sudo visudo

Add the following line at the end:

.. code-block:: none

    ubuntu ALL=(ALL) NOPASSWD:ALL

Alternatively, create a dedicated sudoers file:

.. code-block:: bash

    echo "ubuntu ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/ubuntu
    sudo chmod 0440 /etc/sudoers.d/ubuntu

Verify that passwordless sudo works:

.. code-block:: bash

    sudo -l -U ubuntu

You should see:

.. code-block:: none

    (ALL) NOPASSWD: ALL

To test it:

.. code-block:: bash

    sudo whoami

If it prints `root` without asking for a password, it is correctly configured.

4. **Add the Public Key of the Main FIGO Node**
------------------------------------------------
To allow secure access from the FIGO main node, add its public SSH key to the `authorized_keys` file of the remote user (e.g., `ubuntu`).

Edit the `authorized_keys` file:

.. code-block:: bash

    sudo nano /home/ubuntu/.ssh/authorized_keys

Copy and paste the following key into the file:

.. code-block:: none

    ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIDUaONS6eu014yRBE+6LzKZeFkmQiSiwQUdVBQEVmQmK gpuserver_stefano.salsano@uniroma2.it

Ensure the correct file permissions:

.. code-block:: bash

    sudo chmod 600 /home/ubuntu/.ssh/authorized_keys
    sudo chown ubuntu:ubuntu /home/ubuntu/.ssh/authorized_keys

This step ensures that the FIGO main node can securely access the server via SSH.

---

Following these steps ensures that the server is properly prepared for onboarding into FIGO.
