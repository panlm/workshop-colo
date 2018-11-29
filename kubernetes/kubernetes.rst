.. title:: kubernetes

.. _kubernetes:

------------------
LAB1: Create Kubernetes Cluster 
------------------

Overview
++++++++

create kubernetes cluster, 3 cotroller node and 3 work node ( about 5 mins )

Create Kubernetes Cluster
+++++++++++++++++++++++++

- Open Prism Central

  open https://10.132.69.55:9440

    username: **nutanix**

    password: **nutanix/4u**

- Navigate to Calm UI, and find blueprint **COLO_Kubernetes_cluster_BP** in blueprint page

  .. figure:: images/1.png

- open this blueprint and launch it from up-right corner 

  .. figure:: images/2.png

- give a name to this launch, such as **COLO-launch**

  .. figure:: images/3.png

- open application you launched and check it after success

  - status is **running**

  - total vm is **6**

  .. figure:: images/4.png

- open **service** tab of this launch

  - k8sc - controller node

    - you will find **AHV_Centos_K8SC** means it is Controller node

    - all controller node ip listed blow

    .. figure:: images/6.png

  - k8sm - work node

    - you will find **AHV_Centos_K8SM** means it is Minion node ( or work node )

    - all work node ip listed blow

    .. figure:: images/5.png

- find the first controller node and **open terminal** 

    .. figure:: images/7.png

- run command to verify, ``kubectl get node -o wide -n kube-system``

    .. figure:: images/8.png


Access Kubernetes Dashboard
+++++++++++++++++++++++++++

- open browser, and access ``https://<any_ip_address_in_your_cluster>:30443/``, it is the default **dashboard** of kubernetes. Click **Skip** to skip certifications (using **firefox** if your chrome has some issue)

    .. figure:: images/9.png

- now you could create your first container application  :)

    .. figure:: images/10.png


Scale Out Work Node
+++++++++++++++++++

- navigate to **application** page, in **manage** tab, click **ScaleOut** when you want to add more work node to your cluster. in this case we add 4 more node to cluster.

    .. figure:: images/11.png

    .. figure:: images/12.png
        :width: 50 %

- you will find totally 7 work nodes in this cluster

    .. figure:: images/13.png

- you could do scale in as you wish




Others
++++++

if you got any BP issue, please download :download:`HERE <./COLO_kubernetes_cluster_BP.json>`
or contact Leiming.pan@nutanix.com



