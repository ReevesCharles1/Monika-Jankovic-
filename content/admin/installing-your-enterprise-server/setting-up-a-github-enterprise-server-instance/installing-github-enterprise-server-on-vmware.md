---
title: Installing GitHub Enterprise Server on VMware
intro: 'To install {% data variables.product.prodname_ghe_server %} on VMware, you must download the VMware vSphere client, and then download and deploy the {% data variables.product.prodname_ghe_server %} software.'
redirect_from:
  - /enterprise/admin/articles/getting-started-with-vmware
  - /enterprise/admin/articles/installing-vmware-tools
  - /enterprise/admin/articles/vmware-esxi-virtual-machine-maximums
  - /enterprise/admin/guides/installation/installing-github-enterprise-on-vmware
  - /enterprise/admin/installation/installing-github-enterprise-server-on-vmware
  - /admin/installation/installing-github-enterprise-server-on-vmware
  - /admin/installation/setting-up-a-github-enterprise-server-instance/installing-github-enterprise-server-on-vmware
versions:
  ghes: '*'
type: tutorial
topics:
  - Administrator
  - Enterprise
  - Infrastructure
  - Set up
shortTitle: Install on VMware
---
## Prerequisites

* {% data reusables.enterprise_installation.software-license %}
* You must have a VMware vSphere ESXi Hypervisor, applied to a bare metal machine that will run {% data variables.location.product_location %}s. We support versions 5.5 to 8.0. The ESXi Hypervisor is free and does not include the (optional) vCenter Server. For more information, see [the VMware ESXi documentation](https://www.vmware.com/products/esxi-and-esx.html).
* You will need access to a vSphere Client. If you have vCenter Server you can use the vSphere Web Client. For more information, see the VMware guide [Log in to vCenter Server by Using the vSphere Web Client](https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/8-0/vcenter-server-installation-and-setup-8-0.html).

## Hardware considerations

{% data reusables.enterprise_installation.hardware-considerations-all-platforms %}

## Downloading the {% data variables.product.prodname_ghe_server %} image

{% data reusables.enterprise_installation.download-license %}
{% data reusables.enterprise_installation.download-appliance %}
1. Under "{% data variables.product.prodname_dotcom %} On-premises", select the "Select your hypervisor" dropdown menu and click **VMware ESXi/vSphere (OVA)**.
1. Click **Download for VMware ESXi/vSphere (OVA)**.

## Creating the {% data variables.product.prodname_ghe_server %} instance

{% data reusables.enterprise_installation.create-ghe-instance %}

1. Using the vSphere Windows Client or the vCenter Web Client, import the {% data variables.product.prodname_ghe_server %} image you downloaded. For instructions, see the VMware guide [Deploy an OVF or OVA Template](https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/6-5/vsphere-virtual-machine-administration-guide-6-5/deploying-ovf-templates/deploy-an-ovf-template-flex-and-h5.html).
    * When selecting a datastore, choose one with sufficient space to host the VM's disks. For the minimum hardware specifications recommended for your instance size, see [Hardware considerations](#hardware-considerations). We recommend thick provisioning with lazy zeroing.
    * Leave the **Power on after deployment** box unchecked, as you will need to add an attached storage volume for your repository data after provisioning the VM.
{% data reusables.enterprise_installation.create-attached-storage-volume %} For instructions, see the VMware guide [Add a New Hard Disk to a Virtual Machine](https://techdocs.broadcom.com/us/en/vmware-cis/vsphere/vsphere/6-5/add-a-new-hard-disk-to-a-virtual-machine.html).

## Configuring the {% data variables.product.prodname_ghe_server %} instance

{% data reusables.enterprise_installation.new-instance-config-summary %}

{% data reusables.enterprise_installation.new-instance-attack-vector-warning %}

{% data reusables.enterprise_installation.copy-the-vm-public-dns-name %}
{% data reusables.enterprise_installation.upload-a-license-file %}
{% data reusables.enterprise_installation.save-settings-in-web-based-mgmt-console %} For more information, see [AUTOTITLE](/admin/configuration/configuring-your-enterprise).
{% data reusables.enterprise_installation.instance-will-restart-automatically %}
{% data reusables.enterprise_installation.visit-your-instance %}

## Further reading

* [AUTOTITLE](/admin/overview/system-overview)
* [AUTOTITLE](/admin/overview/about-upgrades-to-new-releases)
