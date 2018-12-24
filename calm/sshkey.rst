.. title:: sshkey

.. _sshkey:

----------------------------
LAB: Create Your Own SSH Key
----------------------------

Overview
++++++++

Create your own ssh keys. (about 5 mins)

Windows
+++++++

- open share folder ``\\10.132.71.50\share``
- copy ``tools\putty_64bit`` to you local directory
- run ``PUTTYGEN``
    .. figure:: images/key1.png

- Click ``Generate`` and keep moving your mouse
    .. figure:: images/key2.png

- After create completed, here is your public key. Please copy paste to your file
    .. figure:: images/key3.png

- export your private key
    .. figure:: images/key4.png

    .. figure:: images/key5.png

    .. figure:: images/key6.png

- save private in putty format ``priv.ppk``, will be used in putty
    .. figure:: images/key7.png

    .. figure:: images/key8.png

- open putty, load the private you saved in last step
    .. figure:: images/key9.png

- save change to default
    .. figure:: images/key10.png

Linux
+++++

- check you already have ``id_rsa`` key or not
    .. code-block:: bash
    
        cd ~/.ssh

- backup your existed rsa key
- create your rsa key
    .. code-block:: bash

        ssh-keygen -t rsa

    .. figure:: images/key11.png

- your public key is ``cat ~/.ssh/id_rsa.pub``
- your private key is ``cat ~/.ssh/id_rsa``


How to use ssh keys
+++++++++++++++++++

- put your public key string in destination host, in specified **user**'s home direcotry ``~/.ssh/authorized_keys``
- now you could login as that **user** without password prompt 

How to use ssh key in Calm
++++++++++++++++++++++++++

- create user with key certification
    .. figure:: images/key12.png

- set public key variable
    .. figure:: images/key13.png

- ingest public key when create VM with ``cloud-init`` service
    .. figure:: images/key14.png

    .. code-block:: config

        #cloud-config
        disable_root: False
        ssh_enabled: True
        ssh_pwauth: True
        users:
        - name: centos
          ssh-authorized-keys:
            - @@{INSTANCE_PUBLIC_KEY}@@
          sudo -E: ['ALL=(ALL) NOPASSWD:ALL']

