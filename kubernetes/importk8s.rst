.. title:: LAB: Import Kubernetes Blueprint

.. _importk8s:

--------------------------------
LAB: Import Kubernetes Blueprint
--------------------------------

Overview
++++++++

Import kubernetes cluster for yourself. (about 10 mins)

.. caution:: if you have good internet connection and no Great Fire Wall issue, please skip this chapter and use the default kubernetes blueprint in *market place* to create your own kubernetes cluster.

.. warning:: if you use default kubernetes blueprint, please refer chapter **How to use ssh keys in Calm** to use your own ssh key.



Import Blueprint
++++++++++++++++

- Ensure your PC version over 5.10

- Please download :download:`HERE <./COLO_kubernetes_cluster_BP.json>`

- Use **firefox** to open open Prism Central URL

    - open https://|PC_IP|!:9440
    - username: **nutanix**
    - password: **nutanix/4u**

- Upload blueprint

    .. figure:: images/imp1.png

    .. figure:: images/imp2.png
        :width: 50 %



Customize Blueprint
+++++++++++++++++++

- Using your private key as credentials for this blueprint

    .. figure:: images/imp3.png

- Using your public key

    .. figure:: images/imp4.png

- Ensure cluster information is correct

    .. figure:: images/imp5.png

    .. list-table::
        :widths: 30 40
        :header-rows: 1 

        *   - Name
            - Value
        *   - PE_CLUSTER_IP
            - ``10.132.129.37``
        *   - PE_DATA_SERVICE_IP
            - ``10.132.129.38``
        *   - PE_USERNAME
            - ``nutanix``
        *   - PE_PASSWORD
            - ``nutanix/4u``
        *   - PE_CONTAINER_NAME
            - ``SelfServiceContainer``

- Change image for each service. (using **panlm-img-xx**)

    .. figure:: images/imp6.png

- Change network interface for each service (using **Primary**)

    .. figure:: images/imp7.png

- Don't forget to save your blueprint




