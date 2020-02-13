.. _appendix-vbmanual:

VB Guest Additions の手動インストール
====================================================================================================
| 何らかの理由で :ref:`appendix-vbadditions` が行えないときは仮想マシンに ``vagrant ssh`` コマンドで接続し、次のコマンドを実行します。
| ※ VirtualBox 6.1.2 用です。

.. code-block:: none

   sudo yum -y update
   sudo yum -y install wget
   sudo yum -y groupinstall 'Development tools'
   wget http://download.virtualbox.org/virtualbox/6.1.2/VBoxGuestAdditions_6.1.2.iso
   sudo mkdir /media/iso
   sudo shutdown -r now
   sudo yum -y install kernel-devel
   sudo mount -o loop,ro VBoxGuestAdditions_6.1.2.iso /media/iso
   sudo sh /media/iso/VBoxLinuxAdditions.run

.. important::

   VB Guest Additions は VirtulBox のバージョンごとに用意されています。下記の URL でお使いの VirutualBox のバージョンにあった VB Guest Additions をご使用ください。
   
   `http://download.virtualbox.org/virtualbox/ <http://download.virtualbox.org/virtualbox/>`_
