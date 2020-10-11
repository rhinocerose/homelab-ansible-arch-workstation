### enable multiple items
```
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

### install from pacman
```
- name: install dunst notification server
  pacman:
    name: dunst
    state: present
  register: task_result
  until: task_result is success
  retries: 10
  delay: 2
  ```
