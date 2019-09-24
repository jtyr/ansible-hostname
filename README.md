hostname
========

Ansible role which helps to set custom hostname as a class call.

Please report any issues or send PR.


Example
-------

```yaml
---

# Example of the basic usage
- hosts: myhost
  roles:
    - hostname

# Example of how to ser a custom hostname
- hosts: myhost
  roles:
    - role: hostname
      hostname_string: myhostname
```

You can also put some logic into the variable. For example use the invenotry
hostname when the host is a VM run by VirtualBox:

```yaml
---

- hosts: myhost
  roles:
    - role: hostname
      hostname_string: "{{ inventory_hostname if ansible_facts.virtualization_role == 'guest' and ansible_facts.virtualization_type == 'virtualbox' else ansible_facts.hostname }}"
```


Role variables
--------------

List of variables used by the role:

```yaml
# Description and default value of the variable
hostname_string: "{{ inventory_hostname }}"
```


License
-------

MIT


Author
------

Jiri Tyr
