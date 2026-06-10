 SSH Public key Store
----------------------

This is designed to work with the [ssh_auth](https://github.com/chaos-bodensee/role-ssh_authorized_keys.git) role.

A example usage to add l3d as admin and raoul only as unprivviledged user:
```yaml
---
admins:
  - l3d

users:
  l3d:
    - l3d@pinkie.l3d.yt
    - l3d@mobile.l3d.yt
    - l3d@backup.l3d.yt
    - l3d@derpy.l3d.yt
    - l3d@backup-rsa.l3d.yt
    - l3d@business.wingcon.com
  raoul:
    - raoul@ccczh

accounts:
  - l3d
  - raoul
```
