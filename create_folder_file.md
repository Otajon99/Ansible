---
- hosts: all
  become: true
  tasks:
    - name: Create directory for daily logs
      ansible.builtin.file:
        path: /var/logs/app/daily_logs
        state: directory
        mode: '0755'
