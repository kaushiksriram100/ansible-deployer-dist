
1. Deploy a neat ansible deployment environment (install ansible software, keys and users)
2. compile and deploy the slaveworker to the deployment environments
3. Deploy a dispatcher env (any VM) and compile the dispatcher code and copy there. 

To run the code: 

```
./masterdeployer -playbookpath "/Users/skaush1/Documents/my_dev_env/github_uploads_final/ansible-playbooks/wm-splunk-universal-forwarder/" --logfile "/tmp/" -playbookaction main.yml -targettype "<path to github path" -slaves "localhost:3001,localhost:3002"

./slaveworker -port "3002"

```
You can start with nohup also.

**Dependency:**
 
1. Make sure secgroups/firewalls are configured properly in the workers so that port can be reached from the master.
2. Master deployer opens a layer4 TCP connection with the workers and picks a random node to send the request. Max retries to 5 attempts. 
3. Worker will receive the message from the tcp stream and decode it and process it to run the ansible playbook

**Pre-requisites:**

1. Clone oo-inventory code (https://github.com/oneops/oneops-inventory) to your deployment VM. 


Author: Sriram Kaushik
