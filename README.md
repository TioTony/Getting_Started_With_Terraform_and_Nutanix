# Getting started with Terraform and Nutanix

## What you need to get started
1. A Nutanix Cluster running AHV and Prism Central
2. A subnet named "Primary"

## Here is what it does
1. Uploads a CentOS7 image
2. Builds a VM
3. Runs cloudinit script to setup the following:
    - git
    - terraform
    - download the terraform scripts

## How to use these files
1. Login to the CentoOS VM that was created
    - ssh nutanix@xxx.xxx.xxx.xxx
    - Password is "nutanix/4u"
2. cd /home/nutanix/Getting_Started_With_Terraform_and_Nutanix
3. Edit the main.tf and change the "prefix_for_created_entities = " entry to your initials
4. At the command prompt run 'terraform init'.  
5. Run 'terrform plan'
6. Run 'terraform apply -auto-approve'

NOTE: There may be a time gap between the time all items are built in Prism Central and the time Terraform thinks it is done.
    Give it a while, it will eventually figure it out.  This can take as long as 30 minutes.

6. To clean up, run 'terraform destroy -auto-approve' and everthing created by Terraform will be removed.  

Nice work!  The examples in the my other github repos are a great next step now that you have the basics figured out.

## Other Notes

This was created by Tony Hughes (aka TH in the comments) to provide a quick introduction to using Terraform with Nutanix in about 100 lines of code.
