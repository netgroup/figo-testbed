User Guide
==========

.. _installation:

Installation
------------

Download and install wireguard (see https://www.wireguard.com/install/) on your PC

Configure a wireguard tunnel using the provided .conf file

Configure your browser with the provided client certificate (.pfx file) to access the webGUI at 
https://figo.netgroup.uniroma2.it (see below)

Log in into your instances (VMs or containers), where 10.202.9.x is the address of the instance

.. code-block:: shell

   ssh ubuntu@10.202.9.x

Adding the certifica to the browser
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Instruction for adding the certificate into chrome 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: text
   
   Save the attached .pfx file
   Paste into the address bar:
   chrome://settings/security
   Scroll down to the Advanced settings and click Manage device certificates

   (Chrome on Windows)
   This opens a certificate management dialog. Click Import...then Next and select the .pfx file you just saved. Do not enter any password. Click Next.
   Select Automatically select the certificate store and click Next, then click Finish.
   Restart the browser and open the GUI https://figo.netgroup.uniroma2.it/
   Select the saved certificate.

   (Chrome on Linux)
   This opens a certificate management dialog. Click Import and select the .pfx file you just saved. Do not enter any password. Click Next.
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

