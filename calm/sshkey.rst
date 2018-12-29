.. title:: LAB: Create Your Own SSH Key

.. _sshkey:

----------------------------
LAB: Create Your Own SSH Key
----------------------------

Overview
++++++++

Create your own ssh keys. (about 5 mins)


Sample Key
++++++++++

Here are the sample key will be used in our labs:

- private key

    .. code-block:: rsa

        -----BEGIN RSA PRIVATE KEY-----
        MIIEowIBAAKCAQEAsBZimX9Q761H4d3uH95kQ6eqCsIxuVNnp8w2Pj9DQ34WRPjx
        EGY23oRigu3rmxOCESuljitBlCTEQKqYsfWi9FfyzZXFtJEf5eyM6aSA9c7ijvUv
        5QlrCovSTZBPfZD1NlHL0BEu46KLKnEDX6O2Wc1irdCVfNxHhl8KcipEShxlii1l
        8XP/HrnfPHb85T4n6e8D55A2+kolDVjENSn8zOvxY0a7ERaaSu2a3JuxH8BPuMaj
        dN9ni9/w+qrWbs6SUzyWJDTNOofZgh+mTPHz5Fe/cGsG+vs1EpXucsxqlR6j2n+H
        sBthg8GG1KQTwf0XeQIoOsRo3bwfkMOqEWHXsQIDAQABAoIBADhzVLTE3huYP50n
        WrmYwCf4TkkYrHwvQuHGU/VsrpGqkFUYQZ/yRNDdO/+hapDSljYO+gozz9hAWTIp
        /r2+c7lFoK9Lvo/+nm1Fgn88n6Mt6e/OpsYUWN6OqKL5CqLEn/gEDQTtHU0YxOic
        RmqYv1LWxzXV0raun7dyLJUg+7eODokBEmXpKLAJXjg4vgsjclKeHsgUDPDcMSgV
        ND436leczwyUzRCTN4JcycoDWTldQb72TdGznP2nDCddfKf+DLKLb86EUMmlX1o4
        9KmGbflrj4BxU7u96AWpGc0LYzca+dyCLzcX7TtRFdcQmlmDBZg+lnybhPkKhRpy
        K2zCOuECgYEA4tzI21xCTviMwLTi7OUu/VG4cxHVAH+bWEcYYq5lp9zoub/58PK9
        e4QGL+YFE4b2u51laOnwGK69po7GQKOWsClJ+9YZWMi0HHJ9hEmQnKf1fPU9FATH
        0n9vMmJ9+gEFQWrvgbSLWre3ilg3g42yDZEFZ4KdI6XH+sZkkNBEy6UCgYEAxrQf
        m5SjlUePw2SrdC8fZybRMlQAzJuRUBK31eWow2KbisToOLbZG2UOswm6kdeU1Go9
        B9q6GfFJdGFk47V/IYqSDA/RVO9/dQe74Wd56UJDM7BeIAgwj6OWQVy9Esyb/hCS
        ACrNBOGNo8efWyzYAHv0rXo02WbYs7q1+hlYzh0CgYEAku1lVNTKyTSmjERa2AyS
        w1PC/xukdT8wEBtziq3ifrZPL8ZLDSdZWv6lty3lScFWWSpWPH2Ol53MjGvZsJGC
        jbMgDG+cWOkb5XStIBk5BIyvLG/0T9vMwuLv1JT/fARfMAAfAEU7H9TulTYPNi92
        Ct1Kv8BTH3xGKX+GMFgCxlUCgYAJ1FtD7QRynAmmltJMexBIoAj1PmaTuJZlqadi
        c2v3zmb3ZGpAc/slechSXwbVtB5uq5q9SrquEduaYD8HbLEPTbWP1zB5zSc2+Nz4
        d4/2VArTAcSGPSF52ZPTQ+0uguSsmtE+JN/jf+zrzzI45m0BCSC/fC4lGwtZSME7
        0AkumQKBgDSLUHa5JMLjcDY1EekkBekQbkjxnF2IKhiPETdVoSeIjzNXWr1DdGg+
        v+wX7Z7zPLaQ7S8IHCx0UVKz3uWSlJJahXra8DuEAuNU+xif1jFljogNO2OYLjfw
        gPTTk52+1CTE1rCKljb3ru5u3wgXrTI2PfSJtj7l13CXi6Gx1wwY
        -----END RSA PRIVATE KEY-----

- Public key

    .. code-block:: rsa

        ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCwFmKZf1DvrUfh3e4f3mRDp6oKwjG5U2enzDY+P0NDfhZE+PEQZjbehGKC7eubE4IRK6WOK0GUJMRAqpix9aL0V/LNlcW0kR/l7IzppID1zuKO9S/lCWsKi9JNkE99kPU2UcvQES7joosqcQNfo7ZZzWKt0JV83EeGXwpyKkRKHGWKLWXxc/8eud88dvzlPifp7wPnkDb6SiUNWMQ1KfzM6/FjRrsRFppK7Zrcm7EfwE+4xqN032eL3/D6qtZuzpJTPJYkNM06h9mCH6ZM8fPkV79wawb6+zUSle5yzGqVHqPaf4ewG2GDwYbUpBPB/Rd5Aig6xGjdvB+Qw6oRYdex centos@controller0


Load sample key in putty
------------------------

- save the private key (before) in text
- open ``PUTTYGEN``
- Click menu ``Conversions`` --> ``Import key``, choose the private key you just saved
- You will find public key in UI 
- If you need ppk file (putty format), click ``Save private key`` button



Or you could create your key as following
+++++++++++++++++++++++++++++++++++++++++

Create key in putty
-------------------

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


Create key in Linux
-------------------

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

In Putty
--------

- Open putty, load the private you saved in last step
    .. figure:: images/key9.png
        :width: 70 %

- Save change to default
    .. figure:: images/key10.png
        :width: 70 %


In Linux
--------

- save private key to  ``~/.ssh/id_rsa`` and change mode to ``chmod 600 ~/.ssh/id_rsa``
- save public key to ``~/.ssh/id_rsa.pub`` and change mode to ``chmod 644 ~/.ssh/id_rsa.pub``
- Put your public key string in destination host, in specified **user**'s home direcotry ``~/.ssh/authorized_keys``
- Now you could login as that **user** without password prompt 


In Calm
-------

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




