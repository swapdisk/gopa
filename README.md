# Gopa

Gopa (Good Old Preupgrade Assistant) is a fork of the [Preupgrade Assistant](https://github.com/upgrades-migrations/preupgrade-assistant) (PA) framework originally developed for [Red Hat Upgrade Tool](https://github.com/upgrades-migrations/redhat-upgrade-tool) (RUT) in-place upgrades to Red Hat Enterprise Linux 7 (RHEL7). Gopa is actually more of a reincarnation than a fork as the original PA and RUT source repos are now archived with a "Disclaimer: It was fun. R.I.P. :-)" note attached.

PA and RUT are replaced with [Leapp](https://leapp.readthedocs.io/en/latest/) for doing in-place upgrades to RHEL8 and later, so why do we need Gopa now? The answer lies in one of the PA framework's best features: its support for dropping in custom modules. Many RHEL users developed custom modules for their RHEL6 to RHEL7 in-place upgrade projects. With Gopa, they can reuse that work as they move on to RHEL8 and RHEL9. Some RHEL users also developed custom reporting that would aggregate the PA results to tools like ELK or Splunk. Gopa can be used to wrap the results from a Leapp preupgrade so those reporting integrations still work as is.

## Overview

The framework is designed to run PA modules, which analyze the system for possible in-place upgrade limitations. It is based on a modular system, with each module performing a separate test, checking for package removals, incompatible obsolete packages, changes in libraries, users, groups, services, or incompatibilities of command-line options or configuration files. It is able to execute post-upgrade scripts to finalize complex tasks after the system upgrade. It then produces a report, which assists you in performing the upgrade itself by outlining potential problem areas and by offering suggestions about mitigating any possible incompatibilities. 

The original Preupgrade Assistant was designed as a prerequisite for completing a successful in-place RHEL upgrade. For upgrades to RHEL7, RUT automatically invoked the pre- and post-upgrade scripts staged by the modules. For upgrades to RHEL8 and later which use Leapp in lieu of RUT, these scripts will be run from [these](https://github.com/swapdisk/gopa-playbooks) Ansible playbooks.

## Building a Gopa package

- Create the primary packaging source by entering: `python2 setup.py sdist --formats=gztar`. Note: The other packaging sources are in the `packaging/sources/` folder.
- Build an RPM package by using a specfile in the `packaging/` folder:
  ```
  rpmbuild -bs packaging/gopa.spec \
    --define "__python /usr/bin/python2" \
    --define "_sourcedir dist"
   ```

## Executing the Gopa preupgrade

- Install the _gopa_ package.
- Gopa requires modules. Either create your own modules by following the tutorial described below, or find modules for Red Hat Enterprise Linux in our Gopa modules repos.
- Run the `preupg` command with root privileges.

## Running unit tests

- Enter the `python setup.py test` command. TODO: does this really work?

## Learning how to write modules

To learn how to write modules for Gopa, see the tutorial located in the `doc/module_writing_tutorial` file.

## Contributing

See our guidelines on [how to contribute to this project](https://github.com/swapdisk/gopa/wiki/Contribute).

## Todo

Right, this isn't much more than just an idea yet. Time to get to work!

## Contact

Open [a new issue](https://github.com/swapdisk/gopa/issues/new) to ask your question or share an idea for improvement.

Bob Mader [bmader@redhat.com](mailto:bmader@redhat.com) 
