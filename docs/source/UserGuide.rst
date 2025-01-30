User Guide
==========

.. _installation:

You will receive a .zip file that includes among the other:

- username.conf : your local wireguard configuration file
- username.key_ssh_ed25519 : your private ssh key for accessing your compute instances
- username.pfx : your client certificate to access the FIGO webGUI

Wireguard Installation
-----------------------

Download and install wireguard (see https://www.wireguard.com/install/) on your PC

Configure a wireguard tunnel using the provided .conf file

Access your compute instances (containers and/or VMs)
------------------------------------------------------

You can log in into your instances (VMs or containers) using the private key usename.key_ssh_ed25519

either you install the key in your $HOME/.ssh so that you can run

.. code-block:: shell

   ssh ubuntu@10.202.x.y

where 10.202.x.y is the address of the instance

or you provide the path to the key:

.. code-block:: shell

   ssh -i /path/to/username.key_ssh_ed25519 ubuntu@10.202.x.y

File Permissions: Ensure your private key file has the correct permissions. The file must not be readable by others:

.. code-block:: shell

   chmod 600 /path/to/username.key_ssh_ed25519

If you encounter issues, use the -v option for verbose output:

.. code-block:: shell

   ssh ubuntu@10.202.x.y
   ssh -i /path/to/username.key_ssh_ed25519 ubuntu@10.202.x.y

Accessing the FIGO webGUI
------------------------------------------------------

Configure your browser with the provided client certificate (.pfx file) to access the webGUI at 
https://figo.netgroup.uniroma2.it (see below)

Adding the certificate to the browser
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Instruction for adding the certificate into chrome 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: text
   
   Save the attached .pfx file
   Paste into the address bar:
   chrome://settings/security
   Scroll down to the Advanced settings and click Manage device certificates...

   (Chrome on Windows)
   ... this opens a certificate management dialog. Click Import...then Next and select the .pfx file you just saved.
   Do not enter any password. Click Next.
   Select Automatically select the certificate store and click Next, then click Finish.
   Restart the browser and open the GUI https://figo.netgroup.uniroma2.it/
   Select the saved certificate.

   (Chrome on Linux)
   ... this opens a certificate management dialog. Click Import and select the .pfx file you just saved.
   Do not enter any password. Click Next.
   Restart the browser (chrome://restart) and open the GUI https://figo.netgroup.uniroma2.it/
   Select the saved certificate.

Instruction for adding the certificate into firefox browser
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: text

   Paste this link into the address bar:
   about:preferences#privacy
   Scroll down to the certificates section and click the View Certificates button.
   In the popup click Your certificates and then Import.
   Select the incus-ui.pfx file you just downloaded. Enter your password, or leave the field empty if you have not set one.
   Restart Firefox (about:profiles) and open  the GUI https://figo.netgroup.uniroma2.it/. Select the Incus-UI certificate.

