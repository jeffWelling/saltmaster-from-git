## Pillars from Git

I found this difficult, but in hindsight there were a lot of things I wish I'd tried differently at the start to progress a bit faster. If you're having trouble configuring salt to pull from pillars, maybe this can be helpful for you too.

#fileserver_backend:
#  - gitfs
#
#gitfs_provider: pygit2
#gitfs_base: master
#gitfs_root: salt
#gitfs_pubkey: /root/.ssh/id_rsa.pub
#gitfs_privkey: /root/.ssh/id_rsa
#
#gitfs_remotes:
#  - git@github.com:jeffWelling/saltmaster-from-git.git

pillar_roots:
  master: 
    - pillar/
file_roots:
  master:
    - salt/

ext_pillar:
  - git:
    - main git@github.com:jeffWelling/saltmaster-from-git.git:
      - env: '__env__'

log_level: 'debug'

state_top: top2.sls

state_top_saltenv: "master"

pillar_raise_on_missing: True
git_pillar_provider: pygit2
git_pillar_pubkey: /root/.ssh/id_rsa.pub
git_pillar_privkey: /root/.ssh/id_rsa
