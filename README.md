# BNB Dip Defaults

Shared dip configuration defaults for Brand New Box team members.

## Background

BNB uses dip to consistently act inside our docker containers. A lot of those commands are the same across all projects. This project maintains a set of shared dip commands that we can all use.

## How to use

Install [dip](https://github.com/bibendi/dip).

Clone this repository onto your machine. Location does not matter.

Create a symbolic link to this projects `dip.yml` file in your home directory (or some other high level directory that contains all of your BNB projects).

```
cd ~
ln -s /path/to/bnb-dip-defaults/dip.yml ~/dip.yml
```

Now, when you are in any sub-directory, dip will search up and find this shared `dip.yml` file.

## Update

You can get the latest and greatest BNB Dip Defaults by pulling the latest from GitHub.

