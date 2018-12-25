.. title:: LAB: Manage Pod in Blueprint

.. _podinbp:

----------------------------
LAB: Manage Pod in Blueprint
----------------------------

Overviews
+++++++++

Enable Container in blueprint . (about 10 mins)

Add Kubernetes as Provider
++++++++++++++++++++++++++

- Use **firefox** to open open Prism Central URL
    - Open https://10.132.129.39:9440
    - Username: **nutanix**
    - Password: **nutanix/4u**

- Get credential from your current kubernetes cluster
    - Using putty to connect the first controller (**K8SC-0-XXX**)
    - We will use the private key saved in putty to login
    - Use username **centos**
    - Client Certificate: ``cat ~/CA/admin.pem``
    - Client Key: ``cat ~/CA/admin-key.pem``

- Click **Setting** icon, add Kubernetes Cluster's Credentials

    .. figure:: images/pod1.png

    - Name: **your kubernetes cluster**
    - Type: Kubernetes
    - Server IP: the first controller ip (**K8SC-0-XXX**)
    - Port: 6443
    - Auth Type: Client Certificate
    - Client Certificate:  ``cat ~/CA/admin.pem``
    - Client Key: ``cat ~/CA/admin-key.pem``
    - Click **Save** and **Verify**

- Click **Projects** icon, and click your project, and add kubernetes cluster you just added.

    .. figure:: images/pod2.png

    - Kubernetes: **your kubernetes cluster**
    - Save all your settings


Create Blueprint for POD
++++++++++++++++++++++++

- Click **Blueprints** icon, choose **Multi VM/Pod Blueprint** to create a new blueprint
- Put the blueprint in **your project**

    .. figure:: images/pod3.png

    .. figure:: images/pod4.png

    - In **Deployment** tab

        .. figure:: images/pod5.png
            :width: 50 %

        - Account: **your kubernetes cluster**
        - Namespace: **default**
        - (Option) Replicas: 2
        - SELECTOR: app:myapp


        .. figure:: images/pod6.png
            :width: 50 %

        - LABELS: app:myapp

    - In **Containers** tab

        .. figure:: images/pod7.png
            :width: 50 %

        - Image: nginx
        - (Option) Image Pull Policy: IfNotPresent

    - In **Service** tab

        .. figure:: images/pod8.png
            :width: 50 %

        .. figure:: images/pod9.png
            :width: 50 %

        - Service Type: NodePort
        - (Option) Port: 8888
        - (Option) Target Port: 8888
        - SELECTOR: app:myapp

- Click **Save** and **Launch** your blueprint



Check POD is running
++++++++++++++++++++

- Click **Applications** and choose the application you just launched

    .. figure:: images/pod10.png

    .. figure:: images/pod11.png

- Check POD is running in kubernetes dashboard

    - open dashboard with **firefox** browser ``https://<controller0_ip_addr>:30443``
    - click **skip** when you got login page

    .. figure:: images/pod12.png

    .. figure:: images/pod13.png
