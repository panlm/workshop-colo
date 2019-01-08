.. title:: LAB: Create Single Node Openshift Cluster (minishift)

.. _openshift:

-----------------------------------------
LAB: Create Openshift Cluster (minishift)
-----------------------------------------


Overview
++++++++

We will create a single node openshift cluster in this lab and add to project, 
so you could deploy pod in openshift cluster.


Prepare VM
++++++++++

- install ubuntu 14.40

- create ssh keys and login localhost without password

- download minishift 1.25 for openshift with kubernetes 1.10. `DOWNLOAD <https://github.com/minishift/minishift/releases>`_ 


Create Openshift Cluster
++++++++++++++++++++++++

- get localhost ip address

- using proxy to accelerate download (option)

    .. code-block:: bash
    
        export http_proxy=http://10.132.71.38:1080
        export https_proxy=${http_proxy}

- untar minishift and start to create openshift cluster

    .. code-block:: bash
    
        ./minishift start --vm-driver generic --remote-ipaddress 10.132.129.193 --remote-ssh-user root --remote-ssh-key ~/.ssh/id_rsa
    
    - vm-driver: using ``generic`` driver to create a cluster which you could access from local network
    - remote-ssh-user: **root**
    - remote-ssh-key: the ssh key you just created
    - remote-ipaddress: your minishift ip address

- login openshift UI, such as http://10.132.129.193:8443/


Role settings in Openshift
++++++++++++++++++++++++++

- login openshift with default user **developor**

    .. code-block:: bash
    
        /var/lib/minishift/bin/oc login

    - input **developor** as username
    - input **any string** as password

- create a project, it is a namespace in kubernetes. 

    .. code-block:: bash
    
        /var/lib/minishift/bin/oc create-project dev1

- create a test pod to verify it works (option)

- assign admin role to system:anonymous

    .. code-block:: bash
    
        /var/lib/minishift/bin/oc adm policy add-role-to-user admin system:anonymous

Deploy Pods in Openshift
++++++++++++++++++++++++

- add openshift cluster to project as kubernetes provider

    - Name: **your openshift cluster**
    - Type: Kubernetes
    - Server IP: **your openshift ip address**
    - Port: 8443
    - Auth Type: Basic Certificate
    - Username: **developor**
    - Password: **any string**
    - Click **Save** and **Verify**

- create blueprint and just like :ref:`podinbp`

- remeber to using ``bitnami/nginx:latest`` instead of ``nginx``

