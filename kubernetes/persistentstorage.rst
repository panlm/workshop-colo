.. title:: persistentstorage

.. _persistentstorage:


----------------------------------
LAB: Persistent Storage on Nutanix
----------------------------------

Check Storage Class
+++++++++++++++++++

- open kubernetes dashboard, and navigate to **Storage Class** page

    - current storage class name is **silver**, we will use the name later.

    - and provider is **nutanix/abs**

    .. figure:: images/per1.png

- navigate to **Persistent Volume Claims** page, no PVC currently.

    .. figure:: images/per2.png


Create Peresistent Volume Claims
++++++++++++++++++++++++++++++++

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

        .. figure:: images/per3.png

- you will find the Volume Group is created in Nutanix Cluster

    .. figure:: images/per4.png

    .. figure:: images/per5.png

    - and there is one 8GiB disk in this Volume Group

        .. figure:: images/per6.png
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

    .. figure:: images/per7.png

- after pod create successfully, see the detail info of this pod

    .. figure:: images/per8.png

    .. figure:: images/per9.png

    - click **exec** to enter the pod and run ``df``

        .. figure:: images/per10.png


