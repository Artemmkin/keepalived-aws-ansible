### What should I change to run it?

First, you need to spin up 2 EC2 instances and assign a ```secondary``` IP address to one of them.

Then change the following variables inside **defaults**:
```
# private IP addresses of ec2 instances
master_ip_address:
slave_ip_address:

VIP:  # instance's secondary IP address
VIP_subnet: 20 # CIDR netmask of a subnet the VIP belongs to
```
You'll alsoe need to change variables in **var/main.yml**:
```
aws_access_key:
aws_secret_key:
region:
```
But before you do this, create an IAM user with appropriate access policy. You can create a custom policy using contents of **aws_policy_example** file in this repo, then attach this policy to a new user.

Of course, don't forget to change the path to your private key in ansible.cfg:
```
private_key_file = ~/.ssh/express42
```
and change IP address of freeradius host in ```hosts``` file.

### How to run?

You can use the following command:
```
ansible-playbook site.yml
```
