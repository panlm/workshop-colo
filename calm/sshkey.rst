.. title:: LAB: Create Your Own SSH Key

.. _sshkey:

----------------------------
LAB: Create Your Own SSH Key
----------------------------

Overview
++++++++

Create your own ssh keys. (about 5 mins)

Windows
+++++++

- Open share folder ``\\10.132.71.50\share``

- Copy ``tools\putty_64bit`` to you local directory

- Run ``PUTTYGEN``

    .. figure:: images/key1.png
        :width: 70 %

- Click ``Generate`` and keep moving your mouse
    .. figure:: images/key2.png
        :width: 70 %

- After create completed, here is your public key. Please copy paste to your file
    .. figure:: images/key3.png
        :width: 70 %

- Export your private key (Openssh format)
    .. figure:: images/key4.png
        :width: 70 %

    .. figure:: images/key5.png
        :width: 70 %

    .. figure:: images/key6.png
        :width: 70 %

- Save private in putty format ``priv.ppk``, will be used in putty
    .. figure:: images/key7.png
        :width: 70 %

    .. figure:: images/key8.png
        :width: 70 %

- Open putty, load the private you saved in last step
    .. figure:: images/key9.png
        :width: 70 %

- Save change to default
    .. figure:: images/key10.png
        :width: 70 %



Linux
+++++

- Check you already have ``id_rsa`` key or not
    .. code-block:: bash

        cd ~/.ssh

- Backup your existed rsa key
- Create your rsa key
    .. code-block:: bash

        ssh-keygen -t rsa

    .. figure:: images/key11.png
        :width: 70 %

- Your public key is ``cat ~/.ssh/id_rsa.pub``
- Your private key is ``cat ~/.ssh/id_rsa``



How to use ssh keys
+++++++++++++++++++

- Put your public key string in destination host, in specified **user**'s home direcotry ``~/.ssh/authorized_keys``
- Now you could login as that **user** without password prompt 



How to use ssh key in Calm
++++++++++++++++++++++++++

- Create user and put your private key
    .. figure:: images/key12.png

- Set public key variable
    .. figure:: images/key13.png

- Ingest public key when create VM with ``cloud-init`` service
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
          sudo: ['ALL=(ALL) NOPASSWD:ALL']




