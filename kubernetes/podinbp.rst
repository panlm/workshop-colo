.. title:: podinbp

.. _podinbp:

----------------------------
LAB: Manage Pod in Blueprint
----------------------------

Overviews
+++++++++

Enable Container in blueprint . (about 10 mins)

Add Kubernetes as Provider
++++++++++++++++++++++++++

- Open Prism Central

    - open https://10.132.129.39:9440

        username: **nutanix**

        password: **nutanix/4u**


- Click **Setting** icon, add Kubernetes Cluster's Credentials

    .. figure:: images/pod1.png

    - type: Kubernetes
    - Server IP: controller0 ip
    - Port: 6443
    - Auth Type: Client Certificate
    - Client Certificate: 
        - login to your controller0 and ``cat ~/CA/admin.pem``
    - Client Key:
        - login to your controller0 and ``cat ~/CA/admin-key.pem``
    - Click **Save** and **Verify**

- Click **Projects** icon, click your project name

    .. figure:: images/pod2.png

    - ensure you have select **Local and Cloud resources**, and choose the kubernetes proider name

Create Blueprint for POD
++++++++++++++++++++++++

- Click **Blueprints** icon, choose **Multi VM/Pod Blueprint** to create a new blueprint

    .. figure:: images/pod3.png

    .. figure:: images/pod4.png

    - In **Deployment** tab

        .. figure:: images/pod5.png
            :width: 50 %

        - Account: kubernetes
        - Namespace: default
        - Replicas: 2
        - SELECTOR: app:myapp

        .. figure:: images/pod6.png
            :width: 50 %

        - LABELS: app:myapp

    - In **Containers** tab

        .. figure:: images/pod7.png
            :width: 50 %

        - Image: nginx
        - (Option)Image Pull Policy: IfNotPresent

    - In **Service** tab

        .. figure:: images/pod8.png
            :width: 50 %

        .. figure:: images/pod9.png
            :width: 50 %

        - Service Type: NodePort
        - Port: 8888
        - Target Port: 8888
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
