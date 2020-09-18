# Ansible Presentation

* CM == Configuration Management

#### Building a CM Platform for IT Ops

* Vagrent
    - System and Software requirements added to a Vagrantfile, this is used to build on systems like AWS, Docker, etc...

* Ansible Controlled VMware Template
    - Define VM params in VMware Template, control with ansible

#### Ansible - Approach & Considerations

* Mutable vs Immutable 
    - Ansible by itself works against infrastructure in a mutable way
    - Other CM tools manage and build infrastructure in a immutable way, Once they are deployed they are not adjusted ( Containers, Images ) 

* Procedural vs Declarative
    - Missed the slide

* Pre-Work: Configuration Identification 
    - Categorize and audit systems by functions
    - Define desired systems states and requirements 
    - Identify commonalities between functionally despite system type
    - Find a common denominator between systems to save time when config
    - Even if something is working before, how can we make it better

* Ansible Structure & Development
    - Ansible has a number of different levels of grouping, this is modular
    - Differentiate code between new app/service stand-up, and system life cycle maintenance
    - DON'T REINVENT THE WHEEL, there is a rich library of modules and plugins to help
    - Develop security conscious code as a _standard_ 

* Data Import & Reference
    - Ansible Facts provide powerful system reference data
    - json, yaml, maybe XML
    - includes things like: OS, FS details, IP, MAC, OS params
    - EX: updated pkgs on Debian:
```yaml
 tasks:
     block:
        name: Update Packages on Debian
        apt:
            update_cache: true
            upgrade: yes
        register: result
        name: Print results
        debug: 
            var=result.stdout_lines
    when: ansible_facts['distribution'] == 'Debian'
```


