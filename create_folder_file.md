
### Creating dir1 file with 755 permission
```
---
- hosts: all
  become: true
  tasks:
    - name: Create directory for daily logs
      ansible.builtin.file:
        path: /home/dir1
        state: directory
        mode: '0755'

```
