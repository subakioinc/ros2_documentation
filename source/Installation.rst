.. _InstallationGuide:
.. _GalacticInstall:

Installation
============

Options for installing ROS 2 {DISTRO_TITLE_FULL}:

.. toctree::
   :hidden:
   :glob:

   Installation/Ubuntu-Development-Setup
   Installation/Ubuntu-Install-Binary
   Installation/Ubuntu-Install-Debians
   Installation/macOS-Development-Setup
   Installation/Windows-Development-Setup
   Installation/Windows-Install-Binary
   Installation/RHEL-Development-Setup
   Installation/RHEL-Install-Binary
   Installation/RHEL-Install-RPMs
   Installation/Fedora-Development-Setup
   Installation/Latest-Development-Setup
   Installation/Maintaining-a-Source-Checkout
   Installation/Testing
   Installation/DDS-Implementations

바이너리 패키지
---------------

플랫폼별 현재 제공하는 ROS 2 바이너리 패키지 :

* Ubuntu Linux - Focal Fossa (20.04)

  * :doc:`Debian packages <Installation/Ubuntu-Install-Debians>`
  * :doc:`"fat" archive <Installation/Ubuntu-Install-Binary>`

* RHEL 8

  * :doc:`RPM packages <Installation/RHEL-Install-RPMs>`
  * :doc:`"fat" archive <Installation/RHEL-Install-Binary>`

* :doc:`Windows <Installation/Windows-Install-Binary>`

As defined in `REP 2000 <https://www.ros.org/reps/rep-2000.html>`_


.. _building-from-source:

소스에서 빌드하기(Building from source)
--------------------

플랫폼별 소스에서 ROS 2 빌드 지원 :
We support building ROS 2 from source on the following platforms:


* :doc:`Ubuntu Linux <Installation/Ubuntu-Development-Setup>`
* :doc:`macOS <Installation/macOS-Development-Setup>`
* :doc:`RHEL <Installation/RHEL-Development-Setup>`
* :doc:`Windows <Installation/Windows-Development-Setup>`


설치 선택(Which install should you choose?)
--------------------------------

바이너리 패키지 혹은 소스로부터 설치.
ROS 2 사용 계획에 따라 선택
Installing from binary packages or from source will both result in a fully-functional and usable ROS 2 install.
Differences between the options depend on what you plan to do with ROS 2.

**바이너리 패키지** : 일반적인 사용. 이미 빌드된 것을 설치. ROS 2를 시작하는 사람이나 바로 시작할 사람에게 적합
**Binary packages** are for general use and provide an already-built install of ROS 2.
This is great for people who want to dive in and start using ROS 2 as-is, right away.

Linux 사용자의 경우 바이너리 패키지를 설치하는데 2가지 옵션 :
Linux users have two options for installing binary packages:

- Debian packages
- "fat" archive

Debian 패키지로 설치하는 방식을 추천. 편리한 이유는 필요한 의존성을 자동으로 설치해 준다. 정규 시스템 업데이트와 함께 업데이트됨.
Installing from Debian packages is the recommended method.
It's more convenient because it installs its necessary dependencies automatically.
It also updates alongside regular system updates.

하지만 root 권한이 필요하므로 만약 root 권한이 없다면 "fat" archive가 차선책이다.
However, you need root access in order to install Debian packages.
If you don't have root access, the "fat" archive is the next best choice.

macOS and Windows users who choose to install from binary packages only have the "fat" archive option
(Debian packages are exclusive to Ubuntu/Debian).

**소스에서 빌드하기** : 개발자용. 바이너리가 지원되지 않는 플랫폼인 경우. ROS 2 최신 버전 설치 가능.
**Building from source** is meant for developers looking to alter or explicitly omit parts of ROS 2's base.
It is also recommended for platforms that don't support binaries.
Building from source also gives you the option to install the absolute latest version of ROS 2.

ROS 2 core에 컨트리뷰션 할려면?
Contributing to ROS 2 core?
^^^^^^^^^^^^^^^^^^^^^^^^^^^
If you plan to contribute directly to ROS 2 core packages, you can install the :doc:`latest development from source <Installation/Latest-Development-Setup>` which shares installation instructions with the :ref:`Rolling distribution <rolling_distribution>`.
