.. Adding labels to the beginning of your lab is helpful for linking to the lab from other pages

.. toctree::
  :maxdepth: 2
  :caption: Labs
  :name: _labs
  :hidden:

  kubernetes/kubernetes

.. toctree::
  :maxdepth: 2
  :caption: Appendix
  :name: _appendix
  :hidden:

  appendix/glossary
  appendix/otherstuff

.. _kubernetes:

------------------
LAB1: Create Kubernetes Cluster 
------------------

Overview
++++++++

create kubernetes cluster, 3 cotroller node and 3 work node

Create Kubernetes Cluster
+++++++++++++++++++++++++

- Open Prism Central

  open https://10.132.69.55:9440

    username: **nutanix**

    password: **nutanix/4u**

- Navigate to Calm UI, and open blueprint **COLO_Kubernetes_cluster_BP** in marketplace

  .. figure:: images/1.png

- open this blueprint and launch it from up-right corner 

  .. figure:: images/2.png

- give a name to this launch, such as **COLO-launch**

  .. figure:: images/3.png

- open application you launched and check it, until success

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



-----------------------------
LAB2: Persistent Storage on Nutanix
-----------------------------

Check Storage Class
+++++++++++++++++++

- open kubernetes dashboard, and navigate to **Storage Class** page

    - current storage class name is **silver**, we will use the name later.
  
    - and provider is **nutanix/abs**

    .. figure:: images/p1.png

- navigate to **Persistent Volume Claims** page, no PVC currently.

    .. figure:: images/p2.png


Create Peresistent Volume Claims
+++++++++++++++++++

- create a new PVC with following code

    .. code-block:: yml
    
        apiVersion: v1
        kind: PersistentVolumeClaim
        metadata:
          name: ntnx-pvc-demo
        spec:
          storageClassName: silver
          resources:
            requests:
              storage: 8Gi
          accessModes:
            - ReadWriteMany

    - will use the storage class named **silver**, we mentioned it before 

    - the PVC size is **8GiB**

    - the name of PVC is **ntnx-pvc-demo**, will be used in container

        .. figure:: images/p3.png

- you will find the Volume Group is created in Nutanix Cluster

    .. figure:: images/p4.png

    .. figure:: images/p5.png

    - and there is one 8GiB disk in this Volume Group

        .. figure:: images/p6.png
            :width: 50 %


Create Pod to use PVC
+++++++++++++++++++++

- use following code to deploy a POD and use the PVC we create before

    .. code-block:: yaml
    
        apiVersion: v1
        kind: Pod
        metadata:
          name: myapp-pod
          labels:
            app: myapp
          annotations:
        spec:
          containers:
          - name: myapp-nginx
            image: nginx
            ports:
              - name: web
                containerPort: 80
            volumeMounts:
              - name: abs
                mountPath: "/usr/share/nginx/html"
          volumes:
          - name: abs
            persistentVolumeClaim:
              claimName: ntnx-pvc-demo

- navigate to **Pods** page, and create a new pod

    - pod name is **myapp-pod**

    - pod will use pvc named **ntnx-pvc-demo**

    .. figure:: images/p7.png

- after pod create successfully, see the detail info of this pod

    .. figure:: images/p8.png

    .. figure:: images/p9.png

    - click **exec** to enter the pod and run ``df``

        .. figure:: images/p10.png



