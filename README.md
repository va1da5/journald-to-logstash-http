# Journald to Logstash HTTP Using FluentBit

The repository contains Ansible playbooks that facilitate the configuration of servers to transmit their logs from JournalD to a remote aggregator via HTTP. It includes example configurations for [RSyslog](https://www.rsyslog.com/doc/v8-stable/) and [Fluent-Bit](https://docs.fluentbit.io/manual).

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

## Configure Forwarders

```bash
ansible-playbook ansible/main.yml

# test connection
curl -v -X POST http://192.168.123.50:8080/json \
      -H 'Content-Type: application/json' \
      -d '{"hello":"world","number":42, "bool": true}'
```

## References

- [geerlingguy/ansible-role-logstash](https://github.com/geerlingguy/ansible-role-logstash/tree/master)
- [Fluent Bit v2.1 Documentation](https://docs.fluentbit.io/manual/)
- [orachide/ansible-role-fluentbit](https://github.com/orachide/ansible-role-fluentbit)
- [RSyslog Documentation](https://www.rsyslog.com/doc/v8-stable/)
- [Troubleshooting problems related to SELinux](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/using_selinux/troubleshooting-problems-related-to-selinux_using-selinux)
