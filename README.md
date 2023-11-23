# ansible

### Manual run:
```
ansible-playbook --inventory-file ./hosts --ask-vault-pass site.yaml
```

### Check whithout apply:
```
ansible-playbook site.yaml --check --diff --ask-vault-pass --limit server.domain.com
```

### New host setup:
##### ping new host
```
ansible -i 'server.domain.com,' -m ping server.domain.com
```
##### if you need, you can get "facts" (all info about host)
```
ansible -i 'server.domain.com,' -m setup server.domain.com
```
##### setup
```
ansible-playbook -i 'server.domain.com,' ./site.yaml --ask-vault-pass
```

### Debug
##### debug vars
```
ansible -i 'server.domain.com,' -m debug -a "var=hostvars" server.domain.com
```
