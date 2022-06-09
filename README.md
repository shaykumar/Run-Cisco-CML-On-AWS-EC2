# Instructions on setting up CML on EC2

**Note** 

Running CML on EC2 is going to require you to run a baremetal instance on EC2 - The pricing for this can be found on this page 
https://calculator.aws/#/createCalculator/EC2DedicatedHosts

! You cannot run CML on regular EC2 instances as nested virtualization is not supported on these instances. Direct access to CPU cores is required for
CML to function properly. Note the pricing for baremetal instances and check if it is right for you.



# Step 1 - Download the CML OVA  

1. Purchase a license for the Cisco Modeling Lab based on your requirements.
2. Visit the myaccount page https://learningnetworkstore.cisco.com/myaccount
3. Download 
    - Download the stable version release 
    - Use the download link with the file ending in .ova 
    - This is the right file format for running an installation on Vmware Workstation or VMWare Fusion
    - We will need to install CML on Fusion / Workstation first in order to convert the format from OVA to OVF to be able to import this into EC2

# Step 2 - Download the refplat ISO

The refplan ISO contains .qcow image files for network device images. This is necessary for CML to instantiate these devices. We will use this later as an attached disk 
when installing CML 
- Download file named refplat*.iso 

# Step 3 - Get a VMWare Fusion Pro License 

You cannot run CML on VMWare Fusion Player. VMWare Fusion Player has limited features that disable nested virtualisaton which is a requirement to start the CML labs.
You will be able to install the CML OVA on VMWare Fusion Player but the device images will not start and you will get the "KVM Domain cannot be started" error.

Vmware Fusion Player also does not support exporting the image from OVA to OVF - which is required to be able to import the image as an EC2 image. 

# Step 4 - Install CML on Fusion Pro

- Create a new virtual machine by importing the downloaded OVA file from Cisco in step 1
- While the machine is shut down, ensure to attach the refplat ISO as a disk to the Virtual Machine
- Start the CML Lab installation on VMWare Fusion Pro
- Follow the prompts and setup the admin and sysadmin accounts
- Once installation is complete, you will be able to browse to the <IP-Address>:9090 to get to the admin console. Use the sysadmin username / password here 
- You can browse the CML GUI on port 443.
- Login for CML here - https://ip-address:443 
- Use the admin/password account here for login

    
# Step 5 - Export VM to OVF Format
    
- Once the installation is complete, shut down the VM and export the VM as an OVF file.
- File -> Export to OVF...
    
# Step 6 - Install AWS CLI 

- You need to have the AWS cli installed locally on your machine to be able to import images into EC2
     
# Step 7 - Get the Acceess Key and Token from AWS Console
    
    
# Step 8 - Configure AWS CLI
    

# Step 9 - Upload .vmdk file to S3 
    
# Step 10 - Create Policy and Role 
       
`aws iam create-role --role-name vmimport --assume-role-policy-document "file://<file-path>/trust-policy.json"`

`aws iam put-role-policy --role-name vmimport --policy-name vmimport --policy-document "file://<file-path>/role-policy.json"`
    
`aws ec2 import-image --description "Cisco CML" --disk-containers "file://<file-path>/containers.json"`
    
`aws ec2 describe-import-image-tasks --import-task-ids import-ami-0143a066d6e195d3b`

