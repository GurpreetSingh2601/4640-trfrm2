####
Instructions to replicate provided configuration on a new machine.
###

*Note - Terraform should be installed to automate the droplet creation process.

To install Terraform you can visit the link below:

https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli 

Step 1:

To connect to your digital ocean account we need an API token which should be available as a variable to use it in our droplet configuration.

We will start by creating a .env file which contains token in the following format:

```bash
export TF_VAR_do_token=<your digital ocean API token>
```
after exporting the token as a variable we will source the .env file and make our token available as an environment variable. use the following command to source:

```bash
source .env
```
Now, you can check by running the following command that the token is exported properly by typing :

```bash
echo $TF_VAR_do_token
```
You should see the token available as a varibale.

Next, we will run :
```bash
terraform init
```
to initialize the terraform.

After Initializing terraform, you will need to clone the repository and get the configuration file.
Make all the required necessary changes such as droplet name, region, tags, etc.

Note* - Make sure to change the name of your ssh key file in main.tf file if the name is different from the one which is used.

Next, run:

```bash
terraform apply
```

You should see resources created on your Digital Ocean platform.

####
Configuring Ansible
####

In this step we installed nginx on the droplets which we created in the previous step.
nginx_setup.yml file has the configuration in it.

You will need DO_API_TOKEN to run the ansible playbook
Next, Run command

```bash
ansible-playbook nginx_setup.yml -u root
```

To confirm you can go to the ipv4 address of your Load Balancer configured in first step

*Note - If you ever wish to store your code on github don't forget to add a .gitignore file and write the name of the file in it which is used to source authentication token which is .env in this case.
