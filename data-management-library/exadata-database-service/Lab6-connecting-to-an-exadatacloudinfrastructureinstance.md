
<!-- Updated April 5, 2022 -->

# Connecting to an Exadata Database Service Instance


## Introduction

This lab walks you through the steps on how to connect to an Exadata Cloud Infrastructure instance using SSH or SQL Developer. <!--You will use this database in subsequent labs of this workshop.-->

Estimated Lab Time: 10 minutes



### Objectives

-   Connect to an Exadata Cloud Infrastructure instance using SSH


### Prerequisites

*Note: This lab requires completion of the following:*

* Completion of [Lab 5: Create Oracle Database on Exadata Database Service on Dedicated Infrastructure](?lab=Lab5-create-database) section.
* A correctly configured virtual cloud network (VCN) to launch the system in. Its related networking resources (gateways, route tables, security lists, DNS, and so on) must also be configured as necessary for the system
* The proper IAM policy is required to proceed See <a href="https://docs.oracle.com/en-us/iaas/exadatacloud/exacs/preparing-for-ecc-deployment.html#GUID-EA03F7BC-7D8E-4177-AFF4-615F71C390CD" target="\_blank">Required IAM Policy for Exadata Cloud Service</a>.
* The full path to the file that contains the private key associated with the public key used when the system was launched.
* The public or private IP address of the Exadata Cloud Infrastructure instance.

  


 <!-- add hyperlink for policies -->

 <!--
* The public key, in OpenSSH format, from the key pair that you plan to use for connecting to the system via SSH  -->

## Task 1: View the Exadata VM Cluster Details to find the IP addresses in the OCI Console


1.  Click the navigation menu Click **Oracle Database**, then click **Exadata on Oracle Public Cloud**.

    ![](./images/Lab2/exacs.png " ")

2.  Choose your **Compartment**

    ![](./images/Lab4/compartment.png " ")


3.  Navigate to the cloud VM cluster you want to view the IP addresses:

    Under **Oracle Exadata Database Service on Dedicated Infrastructure**, Click **Exadata VM Clusters**. In the list of VM clusters, find the VM cluster you want to access and click its highlighted name to view the details page for the cluster.

    ![](./images/Lab4/exavmclusters.png " ")

4.  Under **Resources**, click **Virutal Machines**.

    ![](./images/Lab6/viewvmcluster.png " ")

    Find the public or private IP address of the Exadata Cloud Infrastructure instance.

    The values are displayed in the **Public IP Address** and **Private IP Address & DNS Name** columns of the table displaying the **Virtual Machines** of the Exadata Cloud Infrastructure instance.

    Use the private IP address to connect to the system from your on-premises network, or from within the virtual cloud network (VCN). This includes connecting from a host located on-premises connecting through a VPN or FastConnect to your VCN, or from another host in the same VCN. Use the public IP address to connect to the system from outside the cloud (with no VPN).

## Task 2: Connecting to a Virtual Machine with SSH

You can connect to the virtual machines in an Exadata Cloud Infrastructure system by using a Secure Shell (SSH) connection.

1.  To access a virtual machine on an Oracle ExaDB-D system from a Unix-style system using SSH, use this procedure.

    Enter the following SSH command to access the virtual machine:     

    > ssh –i  < *private-key* > < *user* >@*node*



    In the preceding syntax:

    * *<code>  private-key  </code>* is the full path and name of the file that contains the SSH private key that corresponds to a public key that is registered in the system.
    * *<code>  user  </code>* is the operating system user that you want to use to connect:
         * To perform operations as the Oracle Database software owner, connect as as *<code>  opc  </code>* and *<code>  su oracle  </code>*. The *<code>  oracle  </code>* user does not have root user access to the virtual machine.
         * To perform operations that require *<code>  root  </code>* access to the virtual machine, such as patching, connect as *<code>  opc  </code>*. The *<code>  opc  </code>* user can use the *<code>  sudo -s  </code>* command to gain *<code>  root  </code>* access to the virtual machine.
    * *<code>  node  </code>* is the host name or IP address for the virtual machine that you want to access.

    ![](./images/Lab6/sshnew.png " ")

    ![](./images/Lab6/sqlplus.png " ")


    *Note*: Follow this procedure if you want to access a virtual machine from a Microsoft Windows system using PuTTY.  
    See <a href="https://docs.oracle.com/en-us/iaas/exadatacloud/exacs/ecs-connecting-to-service-inst.html#GUID-8D940FEF-2705-4502-95EA-665906606F3C" target="\_blank">Connecting to a Virtual Machine from a Microsoft Windows System Using PuTTY</a>



## Want to Learn More?


Click [here](https://docs.oracle.com/en-us/iaas/exadatacloud/exacs/ecs-connect-to-service-instance.html) for documentation on Connecting to an Exadata Cloud Infrastructure Instance.


## Acknowledgements

* **Author** - Leo Alvarado, Product Management

* **Contributors** - Tammy Bednar, Eddie Ambler, Product Management

* **Last Update** - May 2022.
