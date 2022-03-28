# config_drift_l2_interfaces

Helps migrating on box l2 & interface configuration from on box templates based configuration.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
  tasks:
  - name: Run the demo role build SOT
    ansible.builtin.include_role: &ref_role
      name: config_drift_l2_interfaces
    vars:
      action: build source of truth

  - name: Negate existing source templates
    ansible.builtin.include_role: *ref_role
    vars:
      action: negate existing templates

  - name: Negate existing source templates
    ansible.builtin.include_role: *ref_role
    vars:
      action: apply back configuration
```
