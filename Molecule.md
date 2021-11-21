# Molecule

Steps I am using to molecule all the things!!  This will include info for both the docker based tests and vagrant based tests.

## Installing Molecule along with the drivers for docker and vagrant

```
sudo pip3 install molecule
sudo pip3 install molecule-docker
sudo pip3 install molecule-vagrant

```

## Verify successful installation with the following

```
pip3 list | grep molecule

Expected Sample Output:  ( versions may differ )
molecule                     3.5.2
molecule-docker              1.1.0
molecule-vagrant             0.6.3

```
## New Role - Initialize using Molecule ( docker driver )

`molecule init role -d docker <rolename>`

## Add molecule testing to existing role

**NOTE:** Command needs to be run *INSIDE* role directory

If you don't include a scenario name, molecule will use default as the scenario

`molecule init scenario -d docker <scenario name>`
 
Example:

```
cd /dvl/ansible/roles/OSUpdate
molecule init sceario -d docker

```

## What each file is used for

* molecule.yml - sets up the docker/vagrant image to prepare for testing
* converge.yml - this is the playbook that actually calls the role being tested
* verify.yml - this is where the tests would go
* requirements.yml - Put any roles you need to download as pre-reqs into this file. Same format that ansible-galaxy uses
* collections.yml - Put any collections you need in this file.  Same format as requirements.yml that ansible-galaxy uses


## How to execute molecule

* test the default scenario

    `molecule test`

* test a scenario called vagrant

    `molecule test -s <scenario name>`

* test all scenarios

    `molecule test --all`

## Notes

* Scenarios can be used to specify different drivers to use, OR it can be used for additional testing methods