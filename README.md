playbook for perfSONAR deployment and config

**Quick Start**:

You must have an account on each of the MiServers and be in the not2fa group

Clone the playbook:

```
git clone https://github.com/perfsonar/ansible-playbook-perfsonar.git
cd ansible-playbook-perfsonar
```

Clone this inventory in the playbook dir:

```
git clone https://github.com/UMNET-perfSONAR/ansible-inventory-perfsonar-AWS-China.git
```

Get the required roles (ignore errors so we can run this multiple times):

```
ansible-galaxy install -r requirements.yml --ignore-errors
```

Use Ansible ping to verify connectivity to targets:

```
ansible all \
  --ask-become-pass \
  -i ansible-inventory-perfsonar-AWS-China/inventory \
  -m ping
```

Run the perfsonar provisioning playbook:

```
ansible-playbook \
  --ask-become-pass \
  -i ansible-inventory-perfsonar-AWS-China/inventory \
  perfsonar.yml
```

**Management Commands:**
