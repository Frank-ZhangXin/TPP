# LEM lab automation tool guide

*Note: This is only the guide of automation tool, please vist https://one.rackspace.com/display/~denn8098/LEM+-+Under+the+Hood to lean lab other knowledge.


### What is this tool:

This automation is made to help user to fast and guard free Openstack deployment on lab host clusters.

### Tool functions intros:

This tool include two kinds of automations:

1. Web based fast Rekick function

    'Rekick' function can help you to do a quick rebuilding on all your hosts in a lab you owned. Fresh OS will  be installed on each host, all the old setting, and the pre-configs would be wiped out. Hostname and (vlan) IPs will stay as they were.
    

2. Integrated native All-in-One config script

    User checked in labs, then they always need to pre-config a lot of stuff for Openstack deployment. This script is going to do every setting for user, which include 'openstack_user_config.yml' and 'swift.yml' generation, swfit drives fromatting, pre-config of 'f5' log system, installing all necessary packages from apt, download and checking out appropriate version of RPC-O and OSA, then do the deployment automatically without guard. Please note, this script is only applied on default deployment. 

 ### How to use:
 
 1. Web page Rekick function:
 
     * Log in your lab account with URL: https://lem.withoutaclue.com
     * For first time to use this lab, you should 'Check-in' your lab on the left side menu bar. If you've already checked-in and owned a lab, see below instruction.
     * Click 'Rekick a Lab' button on your left menu bar, then you will see a list of all labs you owned which are able to be performed 'Rekick'. It roughly will take 1 hour to finish, and you can check rebuilding status in 'Lab rebuilds' on left menu bar.

        ![alt tag](http://i.imgur.com/AwQk3Ab.png)
    
    
 2. Integrated native All-in-One script:
    
    For typical deployment:
    
     * Log into infra host as root.
     * Go to '/opt/rpc_lem/user-tools' directory
     * Execute 'do_the_deploy.sh' script. And whole pre-config and deploy work will start.
     
    ```bash
    ./opt/rpc_lem/user-tools/do_the_deploy.sh
    ```

    For pre-config 'openstack_user_config.yml' and 'swift.yml':
    
    * Before this step we assume you've already installed 'git' like necessary tools and clone down RPC-O repo with certain branch.
    * Log into infra host as root.
    * Execute 'cp -r /opt/rpc-openstack/etc/openstack_deploy /etc/openstack_deploy'
    * Go to '/opt/rpc_lem/user_tools/generate_ouc' directory
    * Execute 'python generate_ouc.py --swift --print-out' to generate 'openstack_user_config.yml' and 'swift.yml' in place. '--swift / -s' flag indicates generation of 'swift.yml' script, and '--print-out / -p' flag will print out all generated scipt on screen.

    ```bash
    python /opt/rpc_lem/user-tools/generate_ouc/generate_ouc.py -s -p
    ```
    
