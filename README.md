# config_drift_l2_interfaces

Role to preserve configuration applied to interfaces using on box templating `source template`, by collecting the configuration converting it to structured data as source of truth, followed by negation of the source templates per interface and re-applying the configuration back to the device using resource modules.
Helps migrating on box l2 & interface configuration from on box templates based configuration.

## Execution steps

- Fetching `derived-config` configuration.
- Feed it to the parsed state of ios.interfaces and ios.l2_interfaces resource module.
- Store the source of truth generated in corresponding yaml files.

- Identify the interfaces using templates using with `running-config`.
- Generate a template based configuration for the interfaces using templates.
- Negate the templates per interface using the config generated.

- Apply back the configuration with ios.interfaces and ios.l2_interfaces resource module.

## Example Playbook

play.yml

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
