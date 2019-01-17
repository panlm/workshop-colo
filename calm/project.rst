.. title:: LAB: Create Your Own Project

.. _project:

----------------------------
LAB: Create Your Own Project
----------------------------

Overview
++++++++

Create your own project for following labs. (about 1 mins)


Create
++++++

- Use **firefox** to open open Prism Central URL

  - open https://10.132.129.39:9440
  - username: **nutanix**
  - password: **nutanix/4u**

- Open **Projects** page from **Administration** menu

- Click **Create Project**

  .. figure:: images/proj1.png

  .. figure:: images/proj2.png

  - Project Name: **your project name**
  - Description: **your project desc**
  - Cluster: **AHV-2**
  - Users, Groups and Roles: 

    .. list-table::
      :widths: 30 40
      :header-rows: 1 

      * - Username
        - Role
      * - SSP Admins
        - Project Admin

  - Network: **Primary**
  - **Save**

- Open **Calm** page from **Services** menu

- Navigate to **Projects** and find the project you just added

  - Infrastructure: **Local and Cloud resources**
  - AHV Cluster: **AHV-2**
  - Network: **Primary**
  - (option)Kubernetes: **your kubernetes cluster**
  - Save all your settings

