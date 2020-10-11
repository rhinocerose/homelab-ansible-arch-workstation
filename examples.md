## enable multiple items
```ansible
- name: install termite terminal emulator
  pacman:
    name: "{{ item }}"
    state: present
  register: task_result
  until: task_result is success
  retries: 10
  delay: 2
  with_items:
    - termite
    - termite-terminfo
```
