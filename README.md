[![Build Status](https://travis-ci.org/TOOCS/diffsofancy.svg?branch=master)](https://travis-ci.org/TOOCS/diffsofancy) [![Ansible Role](https://img.shields.io/ansible/role/36100.svg)](https://galaxy.ansible.com/FlorianKempenich/toocs_diffsofancy)


# TOOCS / Ansible Role: `FlorianKempenich.toocs_diffsofancy`
> #### /!\ This role has been renamed - Old name: `diff-so-fancy` /!\

Install `diff-so-fancy` and set-up `git`

> ### TOOCS?
> TOOCS - The Opinionated One-Click Setups are a set of tools / ansible roles designed to setup a system in one click. They are a simple, reliable, way to setup a given tool. You can use them as is, or, inspecting their code, as a tutorial to follow step by step.
> 
> They are, as their name suggests, opinionated: while they guarantee to setup the given tool in one click, they do **not** guarantee consistency in _how_ they achieve it, new releases might introduce breaking changes.  
> Read the code and make sure you understand what's happening!

## Requirements
`NodeJs` and `npm` is required.
Also the path to the `node` executable needs to be set, see **Role Variables**

## Role Variables
**Set the `node_path` variable to the path of the `node` executable**

Before running this role set the `node_path` fact before running this role, or pass it as a variable
If `node` is already accessible with the default `PATH` environment variable, you can set `node_path` to an empty string.

If `node` was installed with `nvm`, check out this cool project of mine that will the the `node_path` fact for you: [FlorianKempenich.toocs_nodejs](https://galaxy.ansible.com/FlorianKempenich/toocs_nodejs)  
See below for examples.


## Example Playbook
Basic installation:
```
- hosts: sandbox
  tasks:
    - include_role:
        name: FlorianKempenich.toocs_diffsofancy
      vars:
        node_path: "{{ ansible_env.HOME }}/.nvm/versions/node/v6.11.4/bin"
```

If `node` is accessible with the default `PATH` variable, an empty `node_path` will do:
```
- hosts: sandbox
  tasks:
    - include_role:
        name: FlorianKempenich.toocs_diffsofancy
      vars:
        node_path: "" <--- Setting the variable is still required !!
```

Setting the path on a `nvm` installation with [FlorianKempenich.toocs_nodejs](https://galaxy.ansible.com/FlorianKempenich/toocs_nodejs):
```
- hosts: sandbox
  tasks:
    - include_role:
        name: FlorianKempenich.toocs_nodejs
        tasks_from: set-node-path-fact.yml
                      ^
                      ^--- This sets the `node_path` fact.
                           No more need to pass it as variable.

    - include_role:
        name: FlorianKempenich.toocs_diffsofancy
```

## License
MIT

## Author Information
Find out more about my work: [Florian Kempenich](https://floriankempenich.com)
