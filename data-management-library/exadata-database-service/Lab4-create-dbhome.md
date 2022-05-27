
<!-- Updated April 5, 2022 -->

# Create Oracle Database Home


## Introduction

This lab walks you through the steps to Create Oracle Database Home on Exadata Database Service on Dedicated Infrastructure <!--You will use this database in subsequent labs of this workshop.-->

Estimated Lab Time: 10 minutes



### Objectives

-   Create Oracle Database Home on Exadata Database Service on Dedicated Infrastructure


### Prerequisites

*Note: This lab requires completion of the following:*

* Completion of [Lab 3: Create a Cloud VM Cluster resource](?lab=Lab3-create-cloud-vmcluster) section.
* A correctly configured virtual cloud network (VCN) to launch the system in. Its related networking resources (gateways, route tables, security lists, DNS, and so on) must also be configured as necessary for the system
* The proper IAM policy is required to proceed See <a href="https://docs.oracle.com/en-us/iaas/exadatacloud/exacs/preparing-for-ecc-deployment.html#GUID-EA03F7BC-7D8E-4177-AFF4-615F71C390CD" target="\_blank">Required IAM Policy for Exadata Cloud Service</a>.


 <!-- add hyperlink for policies -->

 <!--
* The public key, in OpenSSH format, from the key pair that you plan to use for connecting to the system via SSH  -->

## Task 1: Create Oracle Database Home


1.  Click the navigation menu Click **Oracle Database**, then click **Exadata on Oracle Public Cloud**.

    ![](./images/Lab2/exacs.png " ")

2.  Choose your **Compartment**

    ![](./images/Lab4/compartment.png " ")


3.  Navigate to the cloud VM cluster or DB system you want to create the new Database Home on:

    Under **Oracle Exadata Database Service on Dedicated Infrastructure**, Click **Exadata VM Clusters**. In the list of VM clusters, find the VM cluster you want to access and click its highlighted name to view the details page for the cluster.

    ![](./images/Lab4/exavmclusters.png " ")

4.  Under Resources, click Database Homes. A list of Database Homes is displayed.

    ![](./images/Lab4/dbhomelist.png " ")

5.  Click Create Database Home.

    ![](./images/Lab4/createdbhome.png " ")

6.  In the **Create Database Home** dialog, enter the following:

    **Database Home display name**: The display name for the Database Home. Avoid entering confidential information.

    ![](./images/Lab4/displayname.png " ")

    **Database image**: Determines what Oracle Database version is used for the database. You can have databases with different minor versions the same database home. The major versions must remain the same. By default, the latest Oracle-published database software image is selected.

    Click **Change Database Image** to use an older Oracle-published image or a custom database software image that you have created in advance, then select an Image Type:

    ![](./images/Lab4/changedbimage.png " ")

       * **Oracle Provided Database Software Images**: These images contain generally available versions of Oracle Database software.

       * **Custom Database Software Images**: These images are created by your organization and contain customized configurations of software updates and patches.
       Use the **Select a compartment** and **Select a Database version** selectors to limit the list of custom database software images to a specific compartment or Oracle Database software major release version.

       ![](./images/Lab4/dbsoftwareimage.png " ")

       After choosing a software image, click **Select** to return to the Create Database dialog.

       ![](./images/Lab4/select.png " ")

    Click **Show Advanced Options** to specify advanced options for the Database Home

       **Tags**: If you have permissions to create a resource, then you also have permissions to apply free-form tags to that resource. To apply a defined tag, you must have permissions to use the tag namespace.

       ![](./images/Lab4/AOTags.png " ")

7. Click **Create**

   ![](./images/Lab4/clickcreate.png " ")


   When the Database Home creation is complete, the status changes from **Provisioning** to **Available**.

   ![](./images/Lab4/provisioning.png " ")

   ![](./images/Lab4/available.png " ")

   You may now **proceed to the next lab**

## Additional Lab: Create Custom Database Software Image

1.  Click the navigation menu Click **Oracle Database**, then click **Exadata on Oracle Public Cloud**.

    ![](./images/Lab2/exacs.png " ")

2.  Choose your **Compartment**

    ![](./images/Lab4/compartment.png " ")



<!--

## Want to Learn More?

Click [here](https://docs.oracle.com/en/cloud/paas/autonomous-data-warehouse-cloud/user/autonomous-workflow.html#GUID-5780368D-6D40-475C-8DEB-DBA14BA675C3) for documentation on the typical workflow for using Autonomous Data Warehouse.

## Acknowledgements

- **Author** - Leo Alvarado, Product Management
- **Last Updated By/Date** - Leo Alvarado, April 2022 -->
