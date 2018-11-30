.. title:: lamp

.. _lamp:

-----------------------------
LAB3: Create LAMP Application
-----------------------------

Overview
++++++++

create LAMP application, including 1 haproxy, 2 php-apache and 1 mysql. (about 8 mins)

Create LAMP
+++++++++++

- Open Prism Central

    - open https://10.132.69.55:9440

        username: **nutanix**

        password: **nutanix/4u**

- Navigate to Calm UI, and find blueprint **COLO_lamp_BP** in blueprint page

     .. figure:: images/1.png

- open this blueprint and launch it from up-right corner 

    .. figure:: images/2.png

- give a name to this launch, such as **COLO_launch_lamp**

      .. figure:: images/3.png

- open application you launched and check it after success

     - status is **running**

     - total vm is **4**

    .. figure:: images/4.png

- open **service** tab of this launch

    - haproxy, it is an entry for this application, record it's **ip address**, we will use it later.

        .. figure:: images/5.png

    - apache, it is endpoint beind haproxy, we will find their ip address in haproxy statistics page

        .. figure:: images/6.png


Access haproxy stat page
++++++++++++++++++++++++

- open browser, and access ``http://<hapryxo_ip_address>:8080/stats``, put the haproxy ip address here.

    .. figure:: images/7.png

    - you could find the apache ip addresses in the buttom of the page 


Scale Out apache node 
+++++++++++++++++++++

- navigate to **application** page, in **manage** tab, click **ScaleOut** when you want to add more apache nodes.

    .. figure:: images/10.png

    .. figure:: images/11.png
        :width: 50 %

- refresh statistics page, and we find number of http server change to 3

    .. figure:: images/12.png

    .. figure:: images/13.png

- you could do scale in as you wish



Others
++++++

if you got any BP issue, please download :download:`HERE <./COLO_lamp_BP.json>`
or contact Leiming.pan@nutanix.com



