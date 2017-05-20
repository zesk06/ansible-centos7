# ansible

Demonstrate how to use ansible to configure a developer workstation

The playbook has to be runned on a target host indicated in the ``inventory``
file.

Unless you want to install on a bare computer, I suggest that you install on a
vagrant test machine.

## vagrant test machine

To test the playbook, you can spawn a vagrant computer.

```bash
cd vagrant
vagrant up
```

We now assume that the vagrant computer is launched on the 2222 port on
localhost

You must now copy your current computer public ssh key to the vagrant machine.

```bash
vagrant ssh
# once in the machine, append your public key to the authorized keys
vi .ssh/authorized_keys
```

## inventory

Edit the ``inventory`` file, and fill the target host.

```ini
[developer-computer]
localhost:2222
```

## install

The main playbook is nammed ``machine.ym``, launch it using:

```bash
ansible-playbook -K playbooks/machine.yml -i inventory
```

Once terminated, a developer nammed zesk has been created.
Zsh and oh-my-zsh has been installed and configured.