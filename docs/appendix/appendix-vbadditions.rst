.. _appendix-vbadditions:

プラグインを使用した VB Guest Additions のインストール
====================================================================================================
``vagrant up`` コマンドで仮想マシンを起動したとき、 VB Guest Addtions がインストール済みか確認されます。
インストールされていないと次のメッセージが表示されます。

.. code-block:: none

   ==> default: Checking for guest additions in VM...
       default: No guest additions were detected on the base box for this VM! Guest
       default: additions are required for forwarded ports, shared folders, host only
       default: networking, and more. If SSH fails on this machine, please install
       default: the guest additions and repackage the box to continue.
       default:
       default: This is not an error message; everything may continue to work properly,
       default: in which case you may ignore this message.

Vagrant で作成した仮想マシンに VB Guest Additions をインストールするには次のコマンドを実行します。

| :command:`vagrant plugin install vagrant-vbguest`
| :command:`vagrant vbguest`

以下の順番に実行します。

| VB Guest Additions がインストールされていない状態で仮想マシンを起動
| 　↓
| VB Guest Additions をインストール
| 　↓
| 仮想マシンを停止
| 　↓
| 仮想マシンを起動
| 　↓
| 仮想マシンを停止

実行ログです。仮想マシンの 2 回目の起動時に次のメッセージが表示され、 VB Guest Addtions がインストール済みであることが
わかります。

.. code-block:: none

   [default] GuestAdditions 6.1.2 running --- OK.
   ==> default: Checking for guest additions in VM...

.. code-block:: none
   :emphasize-lines: 27-34,522-523

   PS C:\vagrant\my_centos> vagrant up
   Bringing machine 'default' up with 'virtualbox' provider...
   ==> default: Importing base box 'centos/7'...
   ==> default: Matching MAC address for NAT networking...
   ==> default: Checking if box 'centos/7' version '1905.1' is up to date...
   ==> default: Setting the name of the VM: node1
   ==> default: Clearing any previously set network interfaces...
   ==> default: Preparing network interfaces based on configuration...
       default: Adapter 1: nat
       default: Adapter 2: bridged
   ==> default: Forwarding ports...
       default: 22 (guest) => 2222 (host) (adapter 1)
   ==> default: Running 'pre-boot' VM customizations...
   ==> default: Booting VM...
   ==> default: Waiting for machine to boot. This may take a few minutes...
       default: SSH address: 127.0.0.1:2222
       default: SSH username: vagrant
       default: SSH auth method: private key
       default:
       default: Vagrant insecure key detected. Vagrant will automatically replace
       default: this with a newly generated keypair for better security.
       default:
       default: Inserting generated public key within guest...
       default: Removing insecure key from the guest if it's present...
       default: Key inserted! Disconnecting and reconnecting using new SSH key...
   ==> default: Machine booted and ready!
   ==> default: Checking for guest additions in VM...
       default: No guest additions were detected on the base box for this VM! Guest
       default: additions are required for forwarded ports, shared folders, host only
       default: networking, and more. If SSH fails on this machine, please install
       default: the guest additions and repackage the box to continue.
       default:
       default: This is not an error message; everything may continue to work properly,
       default: in which case you may ignore this message.
   ==> default: Setting hostname...
   ==> default: Configuring and enabling network interfaces...
   ==> default: Rsyncing folder: /cygdrive/c/vagrant/my_centos/ => /vagrant
   PS C:\vagrant\my_centos> vagrant plugin install vagrant-vbguest
   Installing the 'vagrant-vbguest' plugin. This can take a few minutes...
   Fetching: micromachine-3.0.0.gem (100%)
   Fetching: vagrant-vbguest-0.23.0.gem (100%)
   Installed the plugin 'vagrant-vbguest (0.23.0)'!
   PS C:\vagrant\my_centos> vagrant vbguest
   [default] No Virtualbox Guest Additions installation found.
   Loaded plugins: fastestmirror
   Loading mirror speeds from cached hostfile
    * base: ftp.riken.jp
    * extras: ftp.riken.jp
    * updates: ftp.riken.jp
   Resolving Dependencies
   --> Running transaction check
   ---> Package centos-release.x86_64 0:7-6.1810.2.el7.centos will be updated
   ---> Package centos-release.x86_64 0:7-7.1908.0.el7.centos will be an update
   --> Finished Dependency Resolution
   
   Dependencies Resolved
   
   ================================================================================
    Package              Arch         Version                     Repository  Size
   ================================================================================
   Updating:
    centos-release       x86_64       7-7.1908.0.el7.centos       base        26 k
   
   Transaction Summary
   ================================================================================
   Upgrade  1 Package
   
   Total download size: 26 k
   Downloading packages:
   No Presto metadata available for base
   Public key for centos-release-7-7.1908.0.el7.centos.x86_64.rpm is not installed
   warning: /var/cache/yum/x86_64/7/base/packages/centos-release-7-7.1908.0.el7.centos.x86_64.rpm: Header V3 RSA/SHA256 Signature, key ID f4a80eb5: NOKEY
   Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
   Importing GPG key 0xF4A80EB5:
    Userid     : "CentOS-7 Key (CentOS 7 Official Signing Key) <security@centos.org>"
    Fingerprint: 6341 ab27 53d7 8a78 a7c2 7bb1 24c6 a8a7 f4a8 0eb5
    Package    : centos-release-7-6.1810.2.el7.centos.x86_64 (@anaconda)
    From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
   Running transaction check
   Running transaction test
   Transaction test succeeded
   Running transaction
     Updating   : centos-release-7-7.1908.0.el7.centos.x86_64                  1/2
     Cleanup    : centos-release-7-6.1810.2.el7.centos.x86_64                  2/2
     Verifying  : centos-release-7-7.1908.0.el7.centos.x86_64                  1/2
     Verifying  : centos-release-7-6.1810.2.el7.centos.x86_64                  2/2
   
   Updated:
     centos-release.x86_64 0:7-7.1908.0.el7.centos
   
   Complete!
   Loaded plugins: fastestmirror
   Loading mirror speeds from cached hostfile
    * base: ftp.riken.jp
    * extras: ftp.riken.jp
    * updates: ftp.riken.jp
   Resolving Dependencies
   --> Running transaction check
   ---> Package kernel-devel.x86_64 0:3.10.0-957.12.2.el7 will be installed
   --> Processing Dependency: perl for package: kernel-devel-3.10.0-957.12.2.el7.x86_64
   --> Running transaction check
   ---> Package perl.x86_64 4:5.16.3-294.el7_6 will be installed
   --> Processing Dependency: perl-libs = 4:5.16.3-294.el7_6 for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(Socket) >= 1.3 for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(Scalar::Util) >= 1.10 for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl-macros for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl-libs for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(threads::shared) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(threads) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(constant) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(Time::Local) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(Time::HiRes) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(Storable) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(Socket) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(Scalar::Util) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(Pod::Simple::XHTML) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(Pod::Simple::Search) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(Getopt::Long) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(Filter::Util::Call) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(File::Temp) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(File::Spec::Unix) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(File::Spec::Functions) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(File::Spec) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(File::Path) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(Exporter) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(Cwd) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: perl(Carp) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Processing Dependency: libperl.so()(64bit) for package: 4:perl-5.16.3-294.el7_6.x86_64
   --> Running transaction check
   ---> Package perl-Carp.noarch 0:1.26-244.el7 will be installed
   ---> Package perl-Exporter.noarch 0:5.68-3.el7 will be installed
   ---> Package perl-File-Path.noarch 0:2.09-2.el7 will be installed
   ---> Package perl-File-Temp.noarch 0:0.23.01-3.el7 will be installed
   ---> Package perl-Filter.x86_64 0:1.49-3.el7 will be installed
   ---> Package perl-Getopt-Long.noarch 0:2.40-3.el7 will be installed
   --> Processing Dependency: perl(Pod::Usage) >= 1.14 for package: perl-Getopt-Long-2.40-3.el7.noarch
   --> Processing Dependency: perl(Text::ParseWords) for package: perl-Getopt-Long-2.40-3.el7.noarch
   ---> Package perl-PathTools.x86_64 0:3.40-5.el7 will be installed
   ---> Package perl-Pod-Simple.noarch 1:3.28-4.el7 will be installed
   --> Processing Dependency: perl(Pod::Escapes) >= 1.04 for package: 1:perl-Pod-Simple-3.28-4.el7.noarch
   --> Processing Dependency: perl(Encode) for package: 1:perl-Pod-Simple-3.28-4.el7.noarch
   ---> Package perl-Scalar-List-Utils.x86_64 0:1.27-248.el7 will be installed
   ---> Package perl-Socket.x86_64 0:2.010-4.el7 will be installed
   ---> Package perl-Storable.x86_64 0:2.45-3.el7 will be installed
   ---> Package perl-Time-HiRes.x86_64 4:1.9725-3.el7 will be installed
   ---> Package perl-Time-Local.noarch 0:1.2300-2.el7 will be installed
   ---> Package perl-constant.noarch 0:1.27-2.el7 will be installed
   ---> Package perl-libs.x86_64 4:5.16.3-294.el7_6 will be installed
   ---> Package perl-macros.x86_64 4:5.16.3-294.el7_6 will be installed
   ---> Package perl-threads.x86_64 0:1.87-4.el7 will be installed
   ---> Package perl-threads-shared.x86_64 0:1.43-6.el7 will be installed
   --> Running transaction check
   ---> Package perl-Encode.x86_64 0:2.51-7.el7 will be installed
   ---> Package perl-Pod-Escapes.noarch 1:1.04-294.el7_6 will be installed
   ---> Package perl-Pod-Usage.noarch 0:1.63-3.el7 will be installed
   --> Processing Dependency: perl(Pod::Text) >= 3.15 for package: perl-Pod-Usage-1.63-3.el7.noarch
   --> Processing Dependency: perl-Pod-Perldoc for package: perl-Pod-Usage-1.63-3.el7.noarch
   ---> Package perl-Text-ParseWords.noarch 0:3.29-4.el7 will be installed
   --> Running transaction check
   ---> Package perl-Pod-Perldoc.noarch 0:3.20-4.el7 will be installed
   --> Processing Dependency: perl(parent) for package: perl-Pod-Perldoc-3.20-4.el7.noarch
   --> Processing Dependency: perl(HTTP::Tiny) for package: perl-Pod-Perldoc-3.20-4.el7.noarch
   ---> Package perl-podlators.noarch 0:2.5.1-3.el7 will be installed
   --> Running transaction check
   ---> Package perl-HTTP-Tiny.noarch 0:0.033-3.el7 will be installed
   ---> Package perl-parent.noarch 1:0.225-244.el7 will be installed
   --> Finished Dependency Resolution
   
   Dependencies Resolved
   
   ================================================================================
    Package                 Arch    Version               Repository          Size
   ================================================================================
   Installing:
    kernel-devel            x86_64  3.10.0-957.12.2.el7   C7.6.1810-updates   17 M
   Installing for dependencies:
    perl                    x86_64  4:5.16.3-294.el7_6    C7.6.1810-updates  8.0 M
    perl-Carp               noarch  1.26-244.el7          C7.0.1406-base      19 k
    perl-Encode             x86_64  2.51-7.el7            C7.0.1406-base     1.5 M
    perl-Exporter           noarch  5.68-3.el7            C7.0.1406-base      28 k
    perl-File-Path          noarch  2.09-2.el7            C7.0.1406-base      26 k
    perl-File-Temp          noarch  0.23.01-3.el7         C7.0.1406-base      56 k
    perl-Filter             x86_64  1.49-3.el7            C7.0.1406-base      76 k
    perl-Getopt-Long        noarch  2.40-3.el7            C7.5.1804-base      56 k
    perl-HTTP-Tiny          noarch  0.033-3.el7           C7.0.1406-base      38 k
    perl-PathTools          x86_64  3.40-5.el7            C7.0.1406-base      82 k
    perl-Pod-Escapes        noarch  1:1.04-294.el7_6      C7.6.1810-updates   51 k
    perl-Pod-Perldoc        noarch  3.20-4.el7            C7.0.1406-base      87 k
    perl-Pod-Simple         noarch  1:3.28-4.el7          C7.0.1406-base     216 k
    perl-Pod-Usage          noarch  1.63-3.el7            C7.0.1406-base      27 k
    perl-Scalar-List-Utils  x86_64  1.27-248.el7          C7.0.1406-base      36 k
    perl-Socket             x86_64  2.010-4.el7           C7.3.1611-base      49 k
    perl-Storable           x86_64  2.45-3.el7            C7.0.1406-base      77 k
    perl-Text-ParseWords    noarch  3.29-4.el7            C7.0.1406-base      14 k
    perl-Time-HiRes         x86_64  4:1.9725-3.el7        C7.0.1406-base      45 k
    perl-Time-Local         noarch  1.2300-2.el7          C7.0.1406-base      24 k
    perl-constant           noarch  1.27-2.el7            C7.0.1406-base      19 k
    perl-libs               x86_64  4:5.16.3-294.el7_6    C7.6.1810-updates  688 k
    perl-macros             x86_64  4:5.16.3-294.el7_6    C7.6.1810-updates   44 k
    perl-parent             noarch  1:0.225-244.el7       C7.0.1406-base      12 k
    perl-podlators          noarch  2.5.1-3.el7           C7.0.1406-base     112 k
    perl-threads            x86_64  1.87-4.el7            C7.0.1406-base      49 k
    perl-threads-shared     x86_64  1.43-6.el7            C7.0.1406-base      39 k
   
   Transaction Summary
   ================================================================================
   Install  1 Package (+27 Dependent packages)
   
   Total download size: 28 M
   Installed size: 74 M
   Downloading packages:
   --------------------------------------------------------------------------------
   Total                                              1.6 MB/s |  28 MB  00:18
   Running transaction check
   Running transaction test
   Transaction test succeeded
   Running transaction
     Installing : 1:perl-parent-0.225-244.el7.noarch                          1/28
     Installing : perl-HTTP-Tiny-0.033-3.el7.noarch                           2/28
     Installing : perl-podlators-2.5.1-3.el7.noarch                           3/28
     Installing : perl-Pod-Perldoc-3.20-4.el7.noarch                          4/28
     Installing : 1:perl-Pod-Escapes-1.04-294.el7_6.noarch                    5/28
     Installing : perl-Text-ParseWords-3.29-4.el7.noarch                      6/28
     Installing : perl-Encode-2.51-7.el7.x86_64                               7/28
     Installing : perl-Pod-Usage-1.63-3.el7.noarch                            8/28
     Installing : 4:perl-libs-5.16.3-294.el7_6.x86_64                         9/28
     Installing : 4:perl-macros-5.16.3-294.el7_6.x86_64                      10/28
     Installing : perl-Storable-2.45-3.el7.x86_64                            11/28
     Installing : perl-Exporter-5.68-3.el7.noarch                            12/28
     Installing : perl-constant-1.27-2.el7.noarch                            13/28
     Installing : perl-Time-Local-1.2300-2.el7.noarch                        14/28
     Installing : perl-Carp-1.26-244.el7.noarch                              15/28
     Installing : 4:perl-Time-HiRes-1.9725-3.el7.x86_64                      16/28
     Installing : perl-PathTools-3.40-5.el7.x86_64                           17/28
     Installing : perl-Scalar-List-Utils-1.27-248.el7.x86_64                 18/28
     Installing : perl-File-Temp-0.23.01-3.el7.noarch                        19/28
     Installing : perl-File-Path-2.09-2.el7.noarch                           20/28
     Installing : perl-threads-shared-1.43-6.el7.x86_64                      21/28
     Installing : perl-threads-1.87-4.el7.x86_64                             22/28
     Installing : perl-Filter-1.49-3.el7.x86_64                              23/28
     Installing : perl-Socket-2.010-4.el7.x86_64                             24/28
     Installing : 1:perl-Pod-Simple-3.28-4.el7.noarch                        25/28
     Installing : perl-Getopt-Long-2.40-3.el7.noarch                         26/28
     Installing : 4:perl-5.16.3-294.el7_6.x86_64                             27/28
     Installing : kernel-devel-3.10.0-957.12.2.el7.x86_64                    28/28
     Verifying  : perl-HTTP-Tiny-0.033-3.el7.noarch                           1/28
     Verifying  : perl-threads-shared-1.43-6.el7.x86_64                       2/28
     Verifying  : perl-Storable-2.45-3.el7.x86_64                             3/28
     Verifying  : 1:perl-Pod-Escapes-1.04-294.el7_6.noarch                    4/28
     Verifying  : perl-Exporter-5.68-3.el7.noarch                             5/28
     Verifying  : perl-constant-1.27-2.el7.noarch                             6/28
     Verifying  : perl-PathTools-3.40-5.el7.x86_64                            7/28
     Verifying  : 1:perl-parent-0.225-244.el7.noarch                          8/28
     Verifying  : 4:perl-libs-5.16.3-294.el7_6.x86_64                         9/28
     Verifying  : perl-File-Temp-0.23.01-3.el7.noarch                        10/28
     Verifying  : 1:perl-Pod-Simple-3.28-4.el7.noarch                        11/28
     Verifying  : perl-Time-Local-1.2300-2.el7.noarch                        12/28
     Verifying  : 4:perl-macros-5.16.3-294.el7_6.x86_64                      13/28
     Verifying  : 4:perl-5.16.3-294.el7_6.x86_64                             14/28
     Verifying  : perl-Carp-1.26-244.el7.noarch                              15/28
     Verifying  : 4:perl-Time-HiRes-1.9725-3.el7.x86_64                      16/28
     Verifying  : perl-Scalar-List-Utils-1.27-248.el7.x86_64                 17/28
     Verifying  : perl-Pod-Usage-1.63-3.el7.noarch                           18/28
     Verifying  : kernel-devel-3.10.0-957.12.2.el7.x86_64                    19/28
     Verifying  : perl-Encode-2.51-7.el7.x86_64                              20/28
     Verifying  : perl-Pod-Perldoc-3.20-4.el7.noarch                         21/28
     Verifying  : perl-podlators-2.5.1-3.el7.noarch                          22/28
     Verifying  : perl-File-Path-2.09-2.el7.noarch                           23/28
     Verifying  : perl-threads-1.87-4.el7.x86_64                             24/28
     Verifying  : perl-Filter-1.49-3.el7.x86_64                              25/28
     Verifying  : perl-Getopt-Long-2.40-3.el7.noarch                         26/28
     Verifying  : perl-Text-ParseWords-3.29-4.el7.noarch                     27/28
     Verifying  : perl-Socket-2.010-4.el7.x86_64                             28/28
   
   Installed:
     kernel-devel.x86_64 0:3.10.0-957.12.2.el7
   
   Dependency Installed:
     perl.x86_64 4:5.16.3-294.el7_6
     perl-Carp.noarch 0:1.26-244.el7
     perl-Encode.x86_64 0:2.51-7.el7
     perl-Exporter.noarch 0:5.68-3.el7
     perl-File-Path.noarch 0:2.09-2.el7
     perl-File-Temp.noarch 0:0.23.01-3.el7
     perl-Filter.x86_64 0:1.49-3.el7
     perl-Getopt-Long.noarch 0:2.40-3.el7
     perl-HTTP-Tiny.noarch 0:0.033-3.el7
     perl-PathTools.x86_64 0:3.40-5.el7
     perl-Pod-Escapes.noarch 1:1.04-294.el7_6
     perl-Pod-Perldoc.noarch 0:3.20-4.el7
     perl-Pod-Simple.noarch 1:3.28-4.el7
     perl-Pod-Usage.noarch 0:1.63-3.el7
     perl-Scalar-List-Utils.x86_64 0:1.27-248.el7
     perl-Socket.x86_64 0:2.010-4.el7
     perl-Storable.x86_64 0:2.45-3.el7
     perl-Text-ParseWords.noarch 0:3.29-4.el7
     perl-Time-HiRes.x86_64 4:1.9725-3.el7
     perl-Time-Local.noarch 0:1.2300-2.el7
     perl-constant.noarch 0:1.27-2.el7
     perl-libs.x86_64 4:5.16.3-294.el7_6
     perl-macros.x86_64 4:5.16.3-294.el7_6
     perl-parent.noarch 1:0.225-244.el7
     perl-podlators.noarch 0:2.5.1-3.el7
     perl-threads.x86_64 0:1.87-4.el7
     perl-threads-shared.x86_64 0:1.43-6.el7
   
   Complete!
   Loaded plugins: fastestmirror
   Loading mirror speeds from cached hostfile
    * base: ftp.riken.jp
    * extras: ftp.riken.jp
    * updates: ftp.riken.jp
   Package 4:perl-5.16.3-294.el7_6.x86_64 already installed and latest version
   Package bzip2-1.0.6-13.el7.x86_64 already installed and latest version
   Resolving Dependencies
   --> Running transaction check
   ---> Package binutils.x86_64 0:2.27-34.base.el7 will be updated
   ---> Package binutils.x86_64 0:2.27-41.base.el7_7.2 will be an update
   ---> Package elfutils-libelf-devel.x86_64 0:0.176-2.el7 will be installed
   --> Processing Dependency: elfutils-libelf(x86-64) = 0.176-2.el7 for package: elfutils-libelf-devel-0.176-2.el7.x86_64
   --> Processing Dependency: pkgconfig(zlib) for package: elfutils-libelf-devel-0.176-2.el7.x86_64
   ---> Package gcc.x86_64 0:4.8.5-39.el7 will be installed
   --> Processing Dependency: libgomp = 4.8.5-39.el7 for package: gcc-4.8.5-39.el7.x86_64
   --> Processing Dependency: cpp = 4.8.5-39.el7 for package: gcc-4.8.5-39.el7.x86_64
   --> Processing Dependency: libgcc >= 4.8.5-39.el7 for package: gcc-4.8.5-39.el7.x86_64
   --> Processing Dependency: glibc-devel >= 2.2.90-12 for package: gcc-4.8.5-39.el7.x86_64
   --> Processing Dependency: libmpfr.so.4()(64bit) for package: gcc-4.8.5-39.el7.x86_64
   --> Processing Dependency: libmpc.so.3()(64bit) for package: gcc-4.8.5-39.el7.x86_64
   ---> Package make.x86_64 1:3.82-23.el7 will be updated
   ---> Package make.x86_64 1:3.82-24.el7 will be an update
   --> Running transaction check
   ---> Package cpp.x86_64 0:4.8.5-39.el7 will be installed
   ---> Package elfutils-libelf.x86_64 0:0.172-2.el7 will be updated
   --> Processing Dependency: elfutils-libelf(x86-64) = 0.172-2.el7 for package: elfutils-libs-0.172-2.el7.x86_64
   ---> Package elfutils-libelf.x86_64 0:0.176-2.el7 will be an update
   ---> Package glibc-devel.x86_64 0:2.17-292.el7 will be installed
   --> Processing Dependency: glibc-headers = 2.17-292.el7 for package: glibc-devel-2.17-292.el7.x86_64
   --> Processing Dependency: glibc = 2.17-292.el7 for package: glibc-devel-2.17-292.el7.x86_64
   --> Processing Dependency: glibc-headers for package: glibc-devel-2.17-292.el7.x86_64
   ---> Package libgcc.x86_64 0:4.8.5-36.el7_6.2 will be updated
   ---> Package libgcc.x86_64 0:4.8.5-39.el7 will be an update
   ---> Package libgomp.x86_64 0:4.8.5-36.el7_6.2 will be updated
   ---> Package libgomp.x86_64 0:4.8.5-39.el7 will be an update
   ---> Package libmpc.x86_64 0:1.0.1-3.el7 will be installed
   ---> Package mpfr.x86_64 0:3.1.1-4.el7 will be installed
   ---> Package zlib-devel.x86_64 0:1.2.7-18.el7 will be installed
   --> Running transaction check
   ---> Package elfutils-libs.x86_64 0:0.172-2.el7 will be updated
   ---> Package elfutils-libs.x86_64 0:0.176-2.el7 will be an update
   ---> Package glibc.x86_64 0:2.17-260.el7_6.5 will be updated
   --> Processing Dependency: glibc = 2.17-260.el7_6.5 for package: glibc-common-2.17-260.el7_6.5.x86_64
   ---> Package glibc.x86_64 0:2.17-292.el7 will be an update
   ---> Package glibc-headers.x86_64 0:2.17-292.el7 will be installed
   --> Processing Dependency: kernel-headers >= 2.2.1 for package: glibc-headers-2.17-292.el7.x86_64
   --> Processing Dependency: kernel-headers for package: glibc-headers-2.17-292.el7.x86_64
   --> Running transaction check
   ---> Package glibc-common.x86_64 0:2.17-260.el7_6.5 will be updated
   ---> Package glibc-common.x86_64 0:2.17-292.el7 will be an update
   ---> Package kernel-headers.x86_64 0:3.10.0-1062.12.1.el7 will be installed
   --> Finished Dependency Resolution
   
   Dependencies Resolved
   
   ================================================================================
    Package                  Arch      Version                    Repository  Size
   ================================================================================
   Installing:
    elfutils-libelf-devel    x86_64    0.176-2.el7                base        39 k
    gcc                      x86_64    4.8.5-39.el7               base        16 M
   Updating:
    binutils                 x86_64    2.27-41.base.el7_7.2       updates    5.9 M
    make                     x86_64    1:3.82-24.el7              base       421 k
   Installing for dependencies:
    cpp                      x86_64    4.8.5-39.el7               base       5.9 M
    glibc-devel              x86_64    2.17-292.el7               base       1.1 M
    glibc-headers            x86_64    2.17-292.el7               base       687 k
    kernel-headers           x86_64    3.10.0-1062.12.1.el7       updates    8.7 M
    libmpc                   x86_64    1.0.1-3.el7                base        51 k
    mpfr                     x86_64    3.1.1-4.el7                base       203 k
    zlib-devel               x86_64    1.2.7-18.el7               base        50 k
   Updating for dependencies:
    elfutils-libelf          x86_64    0.176-2.el7                base       194 k
    elfutils-libs            x86_64    0.176-2.el7                base       291 k
    glibc                    x86_64    2.17-292.el7               base       3.6 M
    glibc-common             x86_64    2.17-292.el7               base        11 M
    libgcc                   x86_64    4.8.5-39.el7               base       102 k
    libgomp                  x86_64    4.8.5-39.el7               base       158 k
   
   Transaction Summary
   ================================================================================
   Install  2 Packages (+7 Dependent packages)
   Upgrade  2 Packages (+6 Dependent packages)
   
   Total download size: 55 M
   Downloading packages:
   No Presto metadata available for base
   No Presto metadata available for updates
   --------------------------------------------------------------------------------
   Total                                               11 MB/s |  55 MB  00:04
   Running transaction check
   Running transaction test
   Transaction test succeeded
   Running transaction
     Updating   : libgcc-4.8.5-39.el7.x86_64                                  1/25
     Updating   : glibc-2.17-292.el7.x86_64                                   2/25
   warning: /etc/nsswitch.conf created as /etc/nsswitch.conf.rpmnew
     Updating   : glibc-common-2.17-292.el7.x86_64                            3/25
     Installing : mpfr-3.1.1-4.el7.x86_64                                     4/25
     Installing : libmpc-1.0.1-3.el7.x86_64                                   5/25
     Updating   : elfutils-libelf-0.176-2.el7.x86_64                          6/25
     Installing : cpp-4.8.5-39.el7.x86_64                                     7/25
     Updating   : binutils-2.27-41.base.el7_7.2.x86_64                        8/25
     Updating   : libgomp-4.8.5-39.el7.x86_64                                 9/25
     Installing : kernel-headers-3.10.0-1062.12.1.el7.x86_64                 10/25
     Installing : glibc-headers-2.17-292.el7.x86_64                          11/25
     Installing : glibc-devel-2.17-292.el7.x86_64                            12/25
     Installing : zlib-devel-1.2.7-18.el7.x86_64                             13/25
     Installing : elfutils-libelf-devel-0.176-2.el7.x86_64                   14/25
     Installing : gcc-4.8.5-39.el7.x86_64                                    15/25
     Updating   : elfutils-libs-0.176-2.el7.x86_64                           16/25
     Updating   : 1:make-3.82-24.el7.x86_64                                  17/25
     Cleanup    : elfutils-libs-0.172-2.el7.x86_64                           18/25
     Cleanup    : elfutils-libelf-0.172-2.el7.x86_64                         19/25
     Cleanup    : libgomp-4.8.5-36.el7_6.2.x86_64                            20/25
     Cleanup    : 1:make-3.82-23.el7.x86_64                                  21/25
     Cleanup    : binutils-2.27-34.base.el7.x86_64                           22/25
     Cleanup    : glibc-common-2.17-260.el7_6.5.x86_64                       23/25
     Cleanup    : glibc-2.17-260.el7_6.5.x86_64                              24/25
     Cleanup    : libgcc-4.8.5-36.el7_6.2.x86_64                             25/25
     Verifying  : binutils-2.27-41.base.el7_7.2.x86_64                        1/25
     Verifying  : mpfr-3.1.1-4.el7.x86_64                                     2/25
     Verifying  : gcc-4.8.5-39.el7.x86_64                                     3/25
     Verifying  : zlib-devel-1.2.7-18.el7.x86_64                              4/25
     Verifying  : 1:make-3.82-24.el7.x86_64                                   5/25
     Verifying  : libgomp-4.8.5-39.el7.x86_64                                 6/25
     Verifying  : glibc-common-2.17-292.el7.x86_64                            7/25
     Verifying  : libgcc-4.8.5-39.el7.x86_64                                  8/25
     Verifying  : cpp-4.8.5-39.el7.x86_64                                     9/25
     Verifying  : elfutils-libelf-devel-0.176-2.el7.x86_64                   10/25
     Verifying  : libmpc-1.0.1-3.el7.x86_64                                  11/25
     Verifying  : glibc-2.17-292.el7.x86_64                                  12/25
     Verifying  : kernel-headers-3.10.0-1062.12.1.el7.x86_64                 13/25
     Verifying  : glibc-devel-2.17-292.el7.x86_64                            14/25
     Verifying  : elfutils-libs-0.176-2.el7.x86_64                           15/25
     Verifying  : elfutils-libelf-0.176-2.el7.x86_64                         16/25
     Verifying  : glibc-headers-2.17-292.el7.x86_64                          17/25
     Verifying  : binutils-2.27-34.base.el7.x86_64                           18/25
     Verifying  : libgcc-4.8.5-36.el7_6.2.x86_64                             19/25
     Verifying  : libgomp-4.8.5-36.el7_6.2.x86_64                            20/25
     Verifying  : glibc-common-2.17-260.el7_6.5.x86_64                       21/25
     Verifying  : glibc-2.17-260.el7_6.5.x86_64                              22/25
     Verifying  : elfutils-libelf-0.172-2.el7.x86_64                         23/25
     Verifying  : 1:make-3.82-23.el7.x86_64                                  24/25
     Verifying  : elfutils-libs-0.172-2.el7.x86_64                           25/25
   
   Installed:
     elfutils-libelf-devel.x86_64 0:0.176-2.el7      gcc.x86_64 0:4.8.5-39.el7
   
   Dependency Installed:
     cpp.x86_64 0:4.8.5-39.el7
     glibc-devel.x86_64 0:2.17-292.el7
     glibc-headers.x86_64 0:2.17-292.el7
     kernel-headers.x86_64 0:3.10.0-1062.12.1.el7
     libmpc.x86_64 0:1.0.1-3.el7
     mpfr.x86_64 0:3.1.1-4.el7
     zlib-devel.x86_64 0:1.2.7-18.el7
   
   Updated:
     binutils.x86_64 0:2.27-41.base.el7_7.2        make.x86_64 1:3.82-24.el7
   
   Dependency Updated:
     elfutils-libelf.x86_64 0:0.176-2.el7    elfutils-libs.x86_64 0:0.176-2.el7
     glibc.x86_64 0:2.17-292.el7             glibc-common.x86_64 0:2.17-292.el7
     libgcc.x86_64 0:4.8.5-39.el7            libgomp.x86_64 0:4.8.5-39.el7
   
   Complete!
   Copy iso file C:\Program Files\Oracle\VirtualBox\VBoxGuestAdditions.iso into the box /tmp/VBoxGuestAdditions.iso
   Mounting Virtualbox Guest Additions ISO to: /mnt
   mount: /dev/loop0 is write-protected, mounting read-only
   Installing Virtualbox Guest Additions 6.1.2 - guest version is unknown
   Verifying archive integrity... All good.
   Uncompressing VirtualBox 6.1.2 Guest Additions for Linux........
   VirtualBox Guest Additions installer
   Copying additional installer modules ...
   Installing additional modules ...
   VirtualBox Guest Additions: Starting.
   VirtualBox Guest Additions: Building the VirtualBox Guest Additions kernel
   modules.  This may take a while.
   VirtualBox Guest Additions: To build modules for other installed kernels, run
   VirtualBox Guest Additions:   /sbin/rcvboxadd quicksetup <version>
   VirtualBox Guest Additions: or
   VirtualBox Guest Additions:   /sbin/rcvboxadd quicksetup all
   VirtualBox Guest Additions: Building the modules for kernel
   3.10.0-957.12.2.el7.x86_64.
   Redirecting to /bin/systemctl start vboxadd.service
   Redirecting to /bin/systemctl start vboxadd-service.service
   Unmounting Virtualbox Guest Additions ISO from: /mnt
   PS C:\vagrant\my_centos>
   PS C:\vagrant\my_centos> vagrant halt
   ==> default: Attempting graceful shutdown of VM...
   PS C:\vagrant\my_centos>
   PS C:\vagrant\my_centos> vagrant up
   Bringing machine 'default' up with 'virtualbox' provider...
   ==> default: Checking if box 'centos/7' version '1905.1' is up to date...
   ==> default: Clearing any previously set forwarded ports...
   ==> default: Clearing any previously set network interfaces...
   ==> default: Preparing network interfaces based on configuration...
       default: Adapter 1: nat
       default: Adapter 2: bridged
   ==> default: Forwarding ports...
       default: 22 (guest) => 2222 (host) (adapter 1)
   ==> default: Running 'pre-boot' VM customizations...
   ==> default: Booting VM...
   ==> default: Waiting for machine to boot. This may take a few minutes...
       default: SSH address: 127.0.0.1:2222
       default: SSH username: vagrant
       default: SSH auth method: private key
       default: Warning: Connection aborted. Retrying...
       default: Warning: Connection reset. Retrying...
       default: Warning: Remote connection disconnect. Retrying...
   ==> default: Machine booted and ready!
   [default] GuestAdditions 6.1.2 running --- OK.
   ==> default: Checking for guest additions in VM...
   ==> default: Setting hostname...
   ==> default: Configuring and enabling network interfaces...
   ==> default: Rsyncing folder: /cygdrive/c/vagrant/my_centos/ => /vagrant
   ==> default: Machine already provisioned. Run `vagrant provision` or use the `--provision`
   ==> default: flag to force provisioning. Provisioners marked to run always will still run.
   PS C:\vagrant\my_centos>
   PS C:\vagrant\my_centos> vagrant halt
   ==> default: Attempting graceful shutdown of VM...
   PS C:\vagrant\my_centos> 
