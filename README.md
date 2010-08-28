Chef-Solo Capistrano Bootstrap 
============
by Mike Smullin <mike@smullindesign.com>

**Utilize Capistrano to automatically bootstrap any remote server for Chef-Solo via SSH using a single command.**

Installation
------------

  - Git clone the blank Opscode Chef Cookbook Repository to your local machine

    `git clone http://github.com/opscode/chef-repo`

  - Reset the git history

    `rm -rf .git && git init .`

  - Make a special directory for containing all your dna.json files

    `mkdir ./dna/ && touch ./dna/example-node.json`

  - Git clone or wget the Capfile into your cookbook repo root dir

    `wget`

  - Write your cookbook recipes and roles

Usage
------------

  - Execute the Capistrano Chef Bootstrap task

    `cap chef:bootstrap <role> <remote_host>`

  - Enjoy!


Example
------------

    cap chef:bootstrap observer 149.60.10.25

There are other commands you can find by `cap -vT` but remember to include the last
two args as <role> and <remote_host> for all of them, or they won't work. These are separated
out in case one fails so you can resume from where it left off.

Also, during development, it is handy to use:

     reset && cap chef:install_cookbook_repo chef:install_dna chef:solo <role> <remote_host>

Which will push out your latest cookbook plus the dna.json and execute chef-solo on it.

Future goals
------------

Is it possible that with the power of Ruby Expect, either Capistrano or Chef could be made better
so that only one or the other is ultimately necessary?

Credits
------------

Opscode Chef is originally by Opscode, Inc. see http://www.opscode.com/chef/

Capistrano is originally by Jamis Buck <jamis@37signals.com> see http://www.capify.org/