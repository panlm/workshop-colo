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

- create vm from centos7 images

- create ssh keys and login localhost without password

    .. code-block:: bash
    
        ssh-keygen -t rsa

- download minishift 1.25 for openshift with kubernetes 1.10. `DOWNLOAD <https://github.com/minishift/minishift/releases>`_ 


Prepare Openshift Cluster
+++++++++++++++++++++++++

- get localhost ip address

    .. code-block:: bash
    
        ifconfig eth0 |grep -w inet |awk '{print $2}'

- using proxy to accelerate download 

- untar minishift and start to create openshift cluster

    .. code-block:: bash
    
        MYIP="<your_ip_address>"
        ./minishift start --vm-driver generic --remote-ipaddress ${MYIP} --remote-ssh-user root --remote-ssh-key ~/.ssh/id_rsa
    
    - vm-driver: using ``generic`` driver to create a cluster which you could access from local network
    - remote-ssh-user: **root**
    - remote-ssh-key: the ssh key you just created
    - remote-ipaddress: your minishift ip address

    - if you get error, maybe due to download to slow and reach the timeout, please re-run last command again.

        .. code-block:: log
        
            E0110 20:20:00.846466    7391 run_self_hosted.go:542] API server error: Get https://10.132.129.228:8443/healthz?timeout=32s: dial tcp 10.132.129.228:8443: connect: connection refused ()
            Error: timed out waiting for the condition

    - if you get this information, means you create minishift cluster successfully.

        .. code-block:: log
        
            The server is accessible via web console at:
                https://10.132.129.228:8443

            You are logged in as:
                User:     developer
                Password: <any value>

            To login as administrator:
                oc login -u system:admin

- login openshift Web UI, such as ``http://<your_ip_address>:8443/``

- login openshift CLI, if you got ``TLS handshake timeout`` error, please ``unset`` proxy environment variables

    .. code-block:: bash
    
        cd /var/lib/minishift/bin/
        ./oc login -u system:admin

- create the first project **proj1** for this lab from up-right corner button, or following CLI

    .. code-block:: bash
    
        ./oc new-project proj1

- create a test pod to verify it works (option)

- assign admin role to system:anonymous

    .. code-block:: bash
    
        /var/lib/minishift/bin/oc adm policy add-role-to-user admin system:anonymous

Deploy Pods in Openshift
++++++++++++++++++++++++

- add openshift cluster as a kubernetes provider

    - Name: **your openshift cluster**
    - Type: Kubernetes
    - Server IP: **your openshift ip address**
    - Port: 8443
    - Auth Type: Basic Certificate
    - Username: **developor**
    - Password: **any string**
    - Click **Save** and **Verify**

- create project in calm to use kubernetes provider before

- create blueprint and just like :ref:`podinbp`

- remeber to using ``bitnami/nginx:latest`` instead of ``nginx``

    - use **proj1** as namespace in **deployment** tab and **service** tab


Errors
++++++

- if you get following error message, please restart your openshift cluster

    .. code-block:: log
    
        deployments.apps is forbidden: User "system:anonymous" cannot create deployments.apps in the namespace "dev1": User "system:anonymous" cannot create deployments.apps in project "dev1"

    .. code-block:: bash
    
        cd ~/minishift-1.25.0-linux-amd64
        ./minishift stop
        ./minishift start

