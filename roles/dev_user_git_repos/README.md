dev_user_git_repos
=========

Setup repos described in {{ project_repos }} to {{ src_home}}


Requirements
------------
git

Role Variables
--------------
`src_home` is the base dir to install repos to, defaults to ~/src

Dependencies
------------


Example Playbook
----------------
``` yaml

---
- name: Setup alikins git repos
  hosts: localhost
  vars:
    dev_user: "adrian"
    home: "{{ ansible_env.HOME }}"
    src_home: "{{ home }}/src/"
    bin_home: "{{ home }}/bin/"
    project_git_repos:
      - name: Checkout ansible project
        git: git@github.com:ansible/ansible
        path: ansible

      - name: Checkout ansible galaxy project
        git: git@github.com:ansible/galaxy
        path: galaxy

        #- name: Checkout ansible/mazer project
        #   git: git@github.com:ansible/mazer
        #  path: ansible-mazer

      - name: Checkout ansible-bug-repro project
        git: git@github.com:alikins/ansible-bug-repro.git
        path: ansible-bug-repro

  roles:
      - {role: alikins.dev_user_git_repos,
         project_repos: "{{ project_git_repos }}"
         tags: ['dev_user_git_repos']}
```

License
-------

MIT

