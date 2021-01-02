 Webserver Setup
======================

Die derzeit verwendeten Webserver werden benötigt um static content auszuliefern oder um Dienste per Reverse Proxy einzubinden.
Dafür ist keine krasse Magie notwendig sondern das kann relativ einfach mit nginx, etwas Lets Encrypt und ansible erledigt werden.

 Allgemeines Setup
-------------------

Das allgemeine Setup zum absichern, aufhübschen und bedienen von Linux Servern ist in [docs/README.md](docs/README.md) näher beschrieben.

 Webserver related Setup
-------------------------
```yml
- name: deploy web config
  hosts: web
  roles:
    - { role: webhost2, tags: [web,webhost]}
    - { role: acmetool_fix, tags: [web,acmetool]}
    - { role: acmetool2, tags: [web,acmetool]}
    - { role: nginx2, tags: [web,nginx]}
    - { role: goaccess, tags: [web,goaccess]}
```

Hier abgebildet ist ein teil des Webserver Playbook. Die aktuelle Version gibt es in [site.yml](site.yml) in diesem Repo.

:x

