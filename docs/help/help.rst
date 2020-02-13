.. _help:

ヘルプ
====================================================================================================
ヘルプの表示方法
 
| :command:`vagrant <COMMAND> -h`
| :command:`vagrant <COMMAND> <SUBCOMMAND> -h`

.. code-block:: none

   PS C:\Users\user> vagrant -h
   Usage: vagrant [options] <command> [<args>]
   
       -v, --version                    Print the version and exit.
       -h, --help                       Print this help.
   
   Common commands:
        box             manages boxes: installation, removal, etc.
        cloud           manages everything related to Vagrant Cloud
        destroy         stops and deletes all traces of the vagrant machine
        global-status   outputs status Vagrant environments for this user
        halt            stops the vagrant machine
        help            shows the help for a subcommand
        init            initializes a new Vagrant environment by creating a Vagrantfile
        login
        package         packages a running vagrant environment into a box
        plugin          manages plugins: install, uninstall, update, etc.
        port            displays information about guest port mappings
        powershell      connects to machine via powershell remoting
        provision       provisions the vagrant machine
        push            deploys code in this environment to a configured destination
        rdp             connects to machine via RDP
        reload          restarts vagrant machine, loads new Vagrantfile configuration
        resume          resume a suspended vagrant machine
        snapshot        manages snapshots: saving, restoring, etc.
        ssh             connects to machine via SSH
        ssh-config      outputs OpenSSH valid configuration to connect to the machine
        status          outputs status of the vagrant machine
        suspend         suspends the machine
        up              starts and provisions the vagrant environment
        upload          upload to machine via communicator
        validate        validates the Vagrantfile
        version         prints current and latest Vagrant version
        winrm           executes commands on a machine via WinRM
        winrm-config    outputs WinRM configuration to connect to the machine
   
   For help on any individual command run `vagrant COMMAND -h`
   
   Additional subcommands are available, but are either more advanced
   or not commonly used. To see all subcommands, run the command
   `vagrant list-commands`.
   PS C:\Users\user> 

.. code-block:: none

   PS C:\Users\user> vagrant box -h
   Usage: vagrant box <subcommand> [<args>]
   
   Available subcommands:
        add
        list
        outdated
        prune
        remove
        repackage
        update
   
   For help on any individual subcommand run `vagrant box <subcommand> -h`
   PS C:\Users\user>  

.. code-block:: none

   PS C:\Users\user> vagrant box add -h
   Usage: vagrant box add [options] <name, url, or path>
   
   Options:
   
       -c, --clean                      Clean any temporary download files
       -f, --force                      Overwrite an existing box if it exists
           --insecure                   Do not validate SSL certificates
           --cacert FILE                CA certificate for SSL download
           --capath DIR                 CA certificate directory for SSL download
           --cert FILE                  A client SSL cert, if needed
           --location-trusted           Trust 'Location' header from HTTP redirects and use the same credentials for subsequent urls as for the initial one
           --provider PROVIDER          Provider the box should satisfy
           --box-version VERSION        Constrain version of the added box
   
   The box descriptor can be the name of a box on HashiCorp's Vagrant Cloud,
   or a URL, or a local .box file, or a local .json file containing
   the catalog metadata.
   
   The options below only apply if you're adding a box file directly,
   and not using a Vagrant server or a box structured like 'user/box':
   
           --checksum CHECKSUM          Checksum for the box
           --checksum-type TYPE         Checksum type (md5, sha1, sha256)
           --name BOX                   Name of the box
       -h, --help                       Print this help
   PS C:\Users\user>  
