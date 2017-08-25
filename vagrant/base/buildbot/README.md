Buildbot
========

Vagrant instance for testing via Buildbot.

The current supported test suites are
  - quality
  - LMS unit tests
  - CMS unit tests
  - commonlib unit tests

Manually Restarting Master/Workers
----------------------------------

The Buildbot master and all of the workers are started during provisioning.  If
the VM is halted and restarted, the master and all of the workers must be
restarted manually.

To manually restart the master,

```
vagrant ssh
sudo su buildbot_master
cd /edx/app/buildbot_master
source venv/bin/activate
buildbot start master
```

To manually start a worker,

```
vagrant ssh
sudo su - buildbot_worker
cd /edx/app/buildbot_worker
source venv/bin/activate
buildbot-worker start <worker name>
```

X11 Forwarding
--------------
To enable X11 forwarding, run install XQuartz and run `export VAGRANT\_X11=1`
on your host machine.  Then run `vagrant reload` if you have already been
running vagrant. Note that X11 forwarding is not necessary for any of the
currently supported test suites.
