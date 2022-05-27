
<!-- Updated April 5, 2022 -->

# Create Oracle Database on Exadata Database Service on Dedicated Infrastructure


## Introduction

This lab walks you through the steps to create Oracle Database on Exadata Database Service on Dedicated Infrastructure <!--You will use this database in subsequent labs of this workshop.-->

Estimated Lab Time: 10 minutes



### Objectives

-   Create a database in an existing Exadata Database Service on Dedicated Infrastructure


### Prerequisites

*Note: This lab requires completion of the following:*

* Completion of [Lab 4: Create Oracle Database Home on an Exadata Database Service on Dedicated Infrastructure](?lab=Lab4-create-dbhome) section.
* A correctly configured virtual cloud network (VCN) to launch the system in. Its related networking resources (gateways, route tables, security lists, DNS, and so on) must also be configured as necessary for the system
* The proper IAM policy is required to proceed See <a href="https://docs.oracle.com/en-us/iaas/exadatacloud/exacs/preparing-for-ecc-deployment.html#GUID-EA03F7BC-7D8E-4177-AFF4-615F71C390CD" target="\_blank">Required IAM Policy for Exadata Cloud Service</a>.


 <!-- add hyperlink for policies -->

 <!--
* The public key, in OpenSSH format, from the key pair that you plan to use for connecting to the system via SSH  -->

## Task 1: Create Oracle Database


1.  Click the navigation menu Click **Oracle Database**, then click **Exadata on Oracle Public Cloud**.

    ![](./Images/Lab2/exacs.png " ")

2.  Choose your **Compartment**

    ![](./Images/Lab4/compartment.png " ")


3.  Navigate to the cloud VM cluster you want to create the new Database on:

    Under **Oracle Exadata Database Service on Dedicated Infrastructure**, Click **Exadata VM Clusters**. In the list of VM clusters, find the VM cluster you want to access and click its highlighted name to view the details page for the cluster.

    ![](./Images/Lab4/exavmclusters.png " ")

4.  Under **Resources**, click **Databases**, Then Click **Create Database**.

    ![](./Images/Lab5/createdb.png " ")

5.  In the Create Database dialog, enter the following:

    ![](./Images/Lab5/dbname.png " ")

    **Database name**: The name for the database. The database name must meet the requirements:
    * Maximum of 8 characters
    * Contain only alphanumeric characters
    * Begin with an alphabetic character
    * Cannot be part of first 8 characters of a **DB\_UNIQUE_NAME** on the VM cluster
    * DO NOT use the following reserved names: grid, ASM

    **Database unique name suffix**:
    Optionally, specify a value for the **DB\_UNIQUE_NAME** database parameter. The value is case insensitive.

    The unique name must meet the requirements:

    * Maximum of 30 characters
    * Contain only alphanumeric or underscore (_) characters
    * Begin with an alphabetic character
    * Unique across the VM cluster. Recommended to be unique across the tenancy.

    If not specified, the system automatically generates a unique name value, as follows:

            <db_name>_<3_chars_unique_string>_<region-name>



    **Database version**: The version of the database. You can mix database versions on the Exadata DB system.

    ![](./Images/Lab5/dbversion.png " ")

    **PDB name**:*(Optional)* For Oracle Database 12c (12.1.0.2) and later, you can specify the name of the pluggable database. The PDB name must begin with an alphabetic character, and can contain a maximum of eight alphanumeric characters. The only special character permitted is the underscore ( _).

    ![](./Images/Lab5/PDBname.png " ")

    **Database Home**: The Oracle Database Home for the database. Choose the applicable option:

    *Note: For the Database Home, you can select an existing Database Home created from Lab 4 OR Create a new Database Home*
    *For this Lab, we will be using an existing Database Home created from Lab 4*

    ![](./Images/Lab5/dbhselect.png " ")

    * **Select an existing Database Home**: The Database Home display name field allows you to choose the Database Home from the existing homes for the database version you specified. If no Database Home with that version exists, you must create a new one.

    * **Create a new Database Home**: Use this option to provision a new Database Home for your database.


    **Create administrator credentials**: *(Read only)* A database administrator SYS user will be created with the password you supply.

       * **Username**: SYS
       * **Password**: Supply the password for this user. The password must meet the following criteria:

         A strong password for SYS, SYSTEM, TDE wallet, and PDB Admin. The password must be 9 to 30 characters and contain at least two uppercase, two lowercase, two numeric, and two special characters. The special characters must be _, #, or -. The password must not contain the username (SYS, SYSTEM, and so on) or the word "oracle" either in forward or reversed order and regardless of casing.

       * **Confirm password**: Re-enter the SYS password you specified.

    ![](./Images/Lab5/admincredentials.png " ")

    Using a TDE wallet password is optional. If you are using customer-managed encryption keys stored in a vault in your tenancy, the TDE wallet password is not applicable to your DB system.

    *Note on Customer-managed keys*: Use Show Advance Options at the end of the Create Database dialog to configure customer-managed keys.If you are using customer-managed keys, or if you want to specify a different TDE wallet password, uncheck the Use the administrator password for the TDE wallet box. If you are using customer-managed keys, leave the TDE password fields blank. To set the TDE wallet password manually, enter a password in the Enter TDE wallet password field, and then confirm by entering it into the Confirm TDE wallet password field.

    **Select workload type**: Choose the workload type that best suits your application:

       * **Transaction Processing** configures the database for a transactional workload, with a  
         bias towards high volumes of random data access.

       * **Data Warehouse** configures the database for a decision support or data warehouse
         workload, with a bias towards large data scanning operations.

    ![](./Images/Lab5/WT.png " ")

    **Configure database backups**: Specify the settings for backing up the database to Object Storage:

    * **Enable automatic backup**: Check the check box to enable automatic incremental backups for this database. If you are creating a database in a security zone compartment, you must enable automatic backups.

    *Note*: All [pre-requisites](https://docs.oracle.com/en-us/iaas/exadatacloud/exacs/ecs-managing-db-backup-and-recovery.html#GUID-41586B8E-FF2F-44B7-827B-D9122289C8AE) for backing up to Oracle Cloud Infrastructure Object Storage must be met for automatic backups to work

    ![](./Images/Lab5/enableautomatic.png " ")

    * **Backup retention period**: If you enable automatic backups, you can choose one of the following preset retention periods: 7 days, 15 days, 30 days, 45 days, or 60 days. The default selection is 30 days.

    ![](./Images/Lab5/retentionperiod.png " ")

    ![](./Images/Lab5/retentionperiod2.png " ")

    * **Backup Scheduling**: If you enable automatic backups, you can choose a two-hour scheduling window to control when backup operations begin. If you do not specify a window, the six-hour default window of 00:00 to 06:00 (in the time zone of the DB system's region) is used for your database.

    ![](./Images/Lab5/backupsched.png " ")

6. Click **Show Advanced Options** to specify advanced options for the database:

     **Management**:

     **Oracle SID prefix**: The Oracle Database instance number is automatically added to the SID prefix to create the INSTANCE_NAME database parameter. The INSTANCE_NAME parameter is also known as the SID. The SID is unique across the cloud VM cluster. If not specified, SID prefix defaults to the db_name.

     The SID prefix must meet the requirements:

     * Maximum of 12 characters
     * Contain only alphanumeric characters
     * Begin with an alphabetic character
     * Unique in the VM cluster
     * DO NOT use the following reserved names: grid, ASM

    **Character set**: The character set for the database. The default is AL32UTF8.

    ![](./Images/Lab5/sidprefix.png " ")

    **National character set**: The national character set for the database. The default is AL16UTF16.

    ![](./Images/Lab5/national.png " ")

    **Encryption**: If you are creating a database in an Exadata Cloud Service VM cluster, then you can choose to use encryption based on encryption keys that you manage. By default, the database is configured using Oracle-managed encryption keys.

     *Note: For this Lab we will use Oracle-Managed encryption keys*

     ![](./Images/Lab5/encryption.png " ")

     *Optional* To configure the database with encryption based on encryption keys you manage:

     * Select **Use customer-managed keys**. You must have a valid encryption key in Oracle Cloud Infrastructure Vault service. [See Let security admins manage vaults, keys, and secrets](https://docs.oracle.com/iaas/Content/Identity/Concepts/commonpolicies.htm#sec-admins-manage-vaults-keys)

     *Note:You must use AES-256 encryption keys for your database.*

     * Choose a **Vault**.
     * Select a **Master encryption key**.
     * To specify a key version other than the latest version of the selected key, check **Choose the key version** and enter the OCID of the key you want to use in the **Key version OCID** field.

    **Tags**: If you have permissions to create a resource, then you also have permissions to apply free-form tags to that resource. To apply a defined tag, you must have permissions to use the tag namespace.

     ![](./Images/Lab5/tags.png " ")

7. Click **Create Database**

     ![](./Images/Lab5/createdatabaseclick.png " ")


   After database creation is complete, the status changes from **Provisioning** to **Available**

   ![](./Images/Lab5/provisioning.png " ")

   ![](./Images/Lab5/available.png " ")

   You may now **proceed to the next lab**

<!--## Additional Lab: Create a Database from Backup -->

<!--

## Want to Learn More?

Click [here](https://docs.oracle.com/en/cloud/paas/autonomous-data-warehouse-cloud/user/autonomous-workflow.html#GUID-5780368D-6D40-475C-8DEB-DBA14BA675C3) for documentation on the typical workflow for using Autonomous Data Warehouse.

## Acknowledgements

- **Author** - Leo Alvarado, Product Management
- **Last Updated By/Date** - Leo Alvarado, April 2022 -->
