# Journald to Logstash HTTP Using FluentBit

## Requirements

- [Qemu](https://www.qemu.org/)
- [Libvirt](https://libvirt.org/)
- [Vagrant](https://www.vagrantup.com/)
- [Vagrant-libvirt plugin](https://vagrant-libvirt.github.io/vagrant-libvirt/configuration.html)
- [Ansible](https://docs.ansible.com/)

## Initial Steps

```bash
# start servers
export LIBVIRT_DEFAULT_URI=qemu:///system
export VAGRANT_DEFAULT_PROVIDER=libvirt
vagrant box update
vagrant up

vagrant status
ssh
# install required Ansbile roles
ansible-galaxy install -r requirements.yml
```

```bash
# test logstash service
curl -X POST http://192.168.123.20:8080/json  -H 'Content-Type: application/json' -d '{"name":"test","number":42}'
```

## References

- [geerlingguy/ansible-role-logstash](https://github.com/geerlingguy/ansible-role-logstash/tree/master)
- [Fluent Bit v2.1 Documentation](https://docs.fluentbit.io/manual/)
- [orachide/ansible-role-fluentbit](https://github.com/orachide/ansible-role-fluentbit)
