.. title:: LAB: Import Kubernetes Blueprint

.. _importk8s:

--------------------------------
LAB: Import Kubernetes Blueprint
--------------------------------

Overview
++++++++

Import kubernetes cluster for yourself. (about 10 mins)

Import Blueprint
++++++++++++++++

- ensure your PC version over 5.10
- please download :download:`HERE <./COLO_kubernetes_cluster_BP.json>`
- Upload blueprint
    .. figure:: images/imp1.png

    .. figure:: images/imp2.png
        :width: 50 %

Customize Blueprint
+++++++++++++++++++

- change credentials for this blueprint
    using your private key
- change public key
- change image for each service. (using **panlm-img-xx**)
- change network interface for each service (using **Secondary**)

Launch Blueprint
++++++++++++++++

- refer lab :ref:`kubernetes`

