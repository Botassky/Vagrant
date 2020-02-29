.. _vagrant-top:

Windows 10 で Vagrant を使う
====================================================================================================

.. _vagrant-about:

Vagrant とは
----------------------------------------------------------------------------------------------------
- Oracle VritualBox や VMware Workstation などの仮想環境と組み合わせて使用し、仮想環境上に自動でサーバーを構築するツール
- サーバー構築後に Ansible などの構成管理ツールやシェルスクリプトと連携し、アプリケーションなどのインストールや設定まで自動化が可能
- Windows 、 macOS 、 Linux 用が提供されている

.. _vagrant-enviroment:

検証環境
----------------------------------------------------------------------------------------------------
- Microsoft Windows 10 Pro Version 1909 (64-bit)
- HashiCorp Vagrant 2.2.7 (Windows - 64-bit)
- Orace VritualBox 6.1.2 (Windows hosts)

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   ./environment/environment
   ./words/words
   ./command/command
   ./help/help
   ./walkthrough/walkthrough
   ./vms/vms
   ./vagrantfile/vagrantfile
   ./provisioning/provisioning
   ./package/package
   ./multi/multi
   ./appendix/appendix
   ./changelog/changelog
