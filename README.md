

## Quick Start

```bash
# 1. Clone and enter the repo
git clone https://github.com/firojbabu452/automate-ansible-terraform.git
cd automate-ansible-terraform

# 2. Generate SSH key pair
mkdir -p ~/keys
ssh-keygen -t rsa -b 4096 -f ~/keys/terra-key-ansible.pem -N ""
chmod 400 ~/keys/terra-key-ansible.pem
cp ~/keys/terra-key-ansible.pem.pub terraform/terra-key-ansible.pub

# 3. Provision infrastructure
cd terraform && terraform init && terraform apply -auto-approve && cd ..

# 4. Test connectivity
ansible all -m ping
```



## Infrastructure

Terraform creates **4 EC2 instances** in `us-west-2` (all `t2.micro`, free tier eligible):

| Host | OS | SSH User |
|------|----|----------|
| `master-ubuntu` | Ubuntu 24.04 | `ubuntu` |
| `worker-ubuntu` | Ubuntu 24.04 | `ubuntu` |
| `worker-redhat` | RHEL 9 | `ec2-user` |
| `worker-amazon` | Amazon Linux 2023 | `ec2-user` |

AMI IDs are region-specific — update them in `terraform/variables.tf` if you change regions.

Terraform auto-generates the Ansible inventory at `inventories/dev/hosts.ini`.

---





```bash
cd terraform && terraform destroy -auto-approve
```

