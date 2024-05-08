Role Name: snow_create_task
=========

This role will create a given TASK in servicenow

Role Variables
-------------

|fact|value|Notes|
| ---- | ---- |  --- |
|snow_instance| "servicedev"                       | ervice , sandbox service now instance
|task_description| long description of what needs to be done |
|task_short_name |short description of task
|task_assignment_group |"Engineering" | you must get the group right if you dont group it sussed out from task_assignment_user
|task_work_notes|"notes you want to add" |
|task_assignment_user |"The Dude" | Person to assign the ticket to leave blank if going to the group<b><p>Comment out if you want the group
|task_priority|4|1=high 2=something 3=medium 4=low
|task_cmdb_ci |server the ci to tie this too
|task_ci_class | Server, Buisness Application, Cluster, Database |
|  Uname| service_account_name                                 | passed by our vault file
|  Upass| service_account_password                             | passed by our vault file


Notes
------------
* if group is not right it will fail but if you leave it off it will use the task_assignment_user for the group


Example Playbook
----------------
```yml
---

- name: include role snow_create_task
  include_role:
    name: create_close_task  # if using automation hub
    public: yes
  vars:
    snow_instance: "servicedev"                          # uncomment this for test and commment out above
    task_description: "EOC - Deploy Nintex Forms eocnumber" # long description
    task_short_name: "EOC - Deploy Nintex Forms"            # short description
    task_assignment_group: "Engineering"                    # assignment group if empty then gotten from user below
    task_assignment_user: "Holly Troy"                      # assignment user
    task_cmdb_ci: "Virtualization"                          # ci aka SERVER
    task_ci_class: "Business Application"                   # can be Server just take a look at snow drop down
    task_work_notes: "Hey were good now"
    task_priority: "4" #1 = high 3 moderate 4 low

```

Author Information
------------------

Hailaeos Troy
hailaeos.troy@denvergov.org