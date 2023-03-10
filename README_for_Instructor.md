# Getting started with Terraform and Nutanix

## What you need to get started
1. A workstation with Terraform installed
2. A Nutanix cluster running AHV 
      - NOTE: The PHX HPOC is assumed.  Changes to the code may be required for other locations
3. The cluster must have a "Primary" subnet
4. The cluster needs to be attached to Prism Central
5. The worksation needs to have network access to Prism Central

## How to use these files
1. Clone this repo to your Terraform workstation
2. Edit the main.tf
   - Update the cluster IP, password and other details
   - Commit the changes to git so the values are correct for the attendees
3. Continue editing main.tf but do not commit changes after this point
   - change the "prefix_for_created_entities = " to a value that will be prepended to all VMs created 
   - change the "count = " to match the number of participants
         NOTE: The Nutanix HPOC "Primary" subnet has approximately 50 usable IP addresses.  Each participant will spin up at least 3 VMs.  A practical limit is 10 users per cluster (10 IPs for VMs created by the instructor for participants to use + 3 VMs * 10 Partipants = 40 IPs)
4. At the command prompt run 'terraform init'.  
5. Run 'terrform plan'
6. Run 'terraform apply -auto-approve'
NOTE: At this step it is ready for use by the participants who should follow README.md
NOTE: Check the comments in the code if any errors are encountered.  Open a bug if the issue is not documented in the code.
7. To clean up at the end of the class, run 'terraform destroy -auto-approve' and everthing created by Terraform will be removed. 