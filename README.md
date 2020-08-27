playbook for perfSONAR deployment and config

**Quick Start**:

Here is the list of ports that perfSONAR requres:

https://docs.perfsonar.net/manage_security.html

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

Campus

```
pscheduler troubleshoot perfsonar-bin-arbl.umnet.umich.edu

pscheduler task clock \
  --source perfsonar-bin-arbl.umnet.umich.edu \
  --dest localhost

pscheduler task latency \
  --source perfsonar-bin-arbl.umnet.umich.edu \
  --dest localhost

pscheduler task latency \
  --dest perfsonar-bin-arbl.umnet.umich.edu \
  --source localhost

```

Singapore

```

pscheduler task latency \
  --source owamp-ps.singaren.net.sg \
  --dest localhost

pscheduler task latency \
  --dest owamp-ps.singaren.net.sg \
  --source localhost

pscheduler task latency \
  --source perf-sin.sinet.ad.jp \
  --dest localhost

pscheduler task latency \
  --dest perf-sin.sinet.ad.jp \
  --source localhost

```
