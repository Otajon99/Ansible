
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

### 3) Partitioning /dev/sdb disk into 2 parts 6GB and 4GB

```
---
- name: Create partitions on a disk
  hosts: node1
  become: true
 
  tasks:
    - name: Create the first primary partition on /dev/sdb
      community.general.parted:
        device: /dev/sdb
        number: 1
        state: present
        part_start: 0%
        part_end: 6GiB   # your original size
 
    - name: Create the second primary partition on /dev/sdb
      community.general.parted:
        device: /dev/sdb
        number: 2
        state: present
        part_start: 6GiB   # start right after partition 1
        part_end: 10GiB    # or whatever size you want
```


### 4) Pinging server and printing Hello World message

```
---
- name: My first play
  hosts: node1
  tasks:
    - name: Ping my hosts
      ansible.builtin.ping:
    - name: Print message
      ansible.builtin.debug:
        msg: Hello world.

```

### 5) Copying file from local machine to server

```
---
- name: Copy file from local to remote clients
hosts: group1
tasks:
  - name: Copying file
    become: true
  - copy:
      src: /root/some.cfg
      dest: /root
      owner: root
      group: root
      mode: 0777
```
