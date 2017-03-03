# openshift_project

Ansible role for creating or deleting an OpenShift project.

## Role Variables

| parameter      | required | default | choices        | comments 
| -------------- |:--------:|:-------:| -------------- |:-------- 
| `state`        | yes      | exists  | exists, absent | Whether to ensure the OpenShift projects exists or is absent.
| `project`      | yes      |         |                | Name of the OpenShift project
                                   
## Assumptions

Assumptions made by this Ansible role.

### Fact/Variable: `oc_tools`

This Ansible role assumes that the `oc_tools` fact has been set on the host that is running the role. Though this variable could be set as a role variable the recomendation is to use the [oc_tools](https://github.com/rhtconsulting/ansible-role-oc_tools) to both install the `oc` tools as well as log into OpenShift.

## Example Playbook

### Create an OpenShift Project

```
- name: Create an OpenShift Test Project
  hosts: localhost
  roles:
    - role: oc_tools
      state: login

    - role: openshift_project
      project: test
      state: exists

    - role: oc_tools
      state: logout
```

### Delete an OpenShift Project

```
- name: Delete an OpenShift Test Project
  hosts: localhost
  roles:
    - role: oc_tools
      state: login

    - role: openshift_project
      project: test
      state: absent

    - role: oc_tools
      state: logout
```

## Related Roles

* [oc_tools](https://github.com/rhtconsulting/ansible-role-oc_tools)
