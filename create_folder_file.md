
### 1)  Creating dir1 folder file with 755 permission
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


### 2)  Creating file.txt with permission 777 on node1 server

```
---
- hosts: node1
  become: true
  tasks:
    - name: Create directory for daily logs
      ansible.builtin.file:
        path: /home/file.txt
        state: touch
        mode: '0777'
```
