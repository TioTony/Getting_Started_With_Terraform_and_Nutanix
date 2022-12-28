# Getting_Started_With_Terraform_and_Nutanix

## What you need to get started:
1. A Nutanix Cluster running AHV and Prism Central
2. A subnet named "Primary"

## Here is what it does:
1. Uploads a CentOS7 image
2. Builds a VM
3. Runs cloudinit script to setup the following:
    - git
    - terraform
    - download the terraform scripts

## How to use these files:
1. Login to the CentoOS VM that was created
2. ? CD to some directory?
3. At the command prompt run 'terraform init'.  This will download the provider to your machine.
4. Run 'terrform plan'
    It should list a bunch of stuff with this at the end:
    
    Plan: 3 to add, 0 to change, 0 to destroy.

4. Run 'terraform apply -auto-approve'
    Sit back and watch everything get built in Prism Central.
    In Prism Central:
        Compute & Storage -> Images: Look for the "Terraform-CentOS7" image
        Comptue & Storage -> VMs: Look for "terraform-vm".  The console login is user:root password: nutanix/4u

NOTE: There may be a time gap between the time all items are built in Prism Central and the time Terraform thinks it is done.
    Give it a while, it will eventually figure it out.  This can take as long as 30 minutes.

5. Run 'terraform destroy -auto-approve' and everthing created by Terraform will be removed.  
    Reconfirm by looking for the entities in Prism Central and they should no longer be present:
        Compute & Storage -> Images: Look for the "Terraform-CentOS7" image
        Comptue & Storage -> VMs: Look for "terraform-vm".  
    This should run much faster than the "apply".

Nice work!  The examples in the github repo are a great next step now that you have the basics figured out.

## Other Notes

This was created by Tony Hughes (aka TH in the comments) to provide a quick introduction to using Terraform with Nutanix in less than 100 lines of code.
