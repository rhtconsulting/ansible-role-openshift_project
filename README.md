# oc_tools

Ansible role for creating or deleting an OpenShift project.

## Role Variables

| parameter      | required | default | choices        | comments 
| -------------- |:--------:|:-------:| -------------- |:-------- 
| `state`        | yes      | exists  | exists, absent | Whether to ensure the OpenShift projects exists or is absent.
| `project`      | yes      |         |                | Name of the OpenShift project
                                   
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

* oc_tools
