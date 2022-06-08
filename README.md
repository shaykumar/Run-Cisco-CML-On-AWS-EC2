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

# Step 4

Start the CML Lab installation on VMWare Fusion 


