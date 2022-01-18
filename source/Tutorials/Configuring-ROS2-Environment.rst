.. _ConfigROS2:

ROS 2 환경 설정
Configuring your ROS 2 environment
==================================

**목표:** 이 튜토리얼은 ROS 2 환경을 준비하는 방법을 보여준다.
**Goal:** This tutorial will show you how to prepare your ROS 2 environment.

**레벨:** 초급자
**Tutorial level:** Beginner

**소요시간:** 5분
**Time:** 5 minutes

.. contents:: Contents
   :depth: 2
   :local:

배경(Background)
----------

ROS 2는 shell 환경을 사용해서 workspaces를 결합하는 개념.
"workspaces"는 ROS 2로 개발하는 시스템에 해당 위치를 가리키는 ROS 용어.
core ROS 2 workspace를 underlay라고 부른다.
이하 로컬 workspaces를 overlays라고 부른다.
ROS 2로 개발할때, 일반적으로 동시에 여러 workspace들이 활성화된다.
ROS 2 relies on the notion of combining workspaces using the shell environment.
"Workspace" is a ROS term for the location on your system where you're developing with ROS 2.
The core ROS 2 workspace is called the underlay.
Subsequent local workspaces are called overlays.
When developing with ROS 2, you will typically have several workspaces active concurrently.

workspace들을 결합하면 ROS 2의 다른 버전에 대응 혹은 다른 패키지들의 집합을 좀더 쉽게 개발.
동일한 컴퓨터에 여러 ROS 2 배포 버전을 설치하여 버전 사이에 스위칭이 가능.
Combining workspaces makes developing against different versions of ROS 2, or against different sets of packages, easier.
It also allows the installation of several ROS 2 distributions (or “distros”, e.g. Dashing and Eloquent) on the same computer and switching between them.

매번 새로운 shell을 열때 setup 파일을 source 명령을 통하거나 shell startup 스크립트에서 한 번만 source 명령을 추가해 줄 수도 있다.
setup 파일을 source 명령을 사용하지 않으면 ROS 2 명령에 접근할 수 없고 ROS 2 패키지를 찾거나 사용할 수 없다.
다시 말하자면 ROS 2를 사용할 수 없다. 
This is accomplished by sourcing setup files every time you open a new shell, or by adding the source command to your shell startup script once.
Without sourcing the setup files, you won’t be able to access ROS 2 commands, or find or use ROS 2 packages.
In other words, you won’t be able to use ROS 2.

사전준비(Prerequisites)
-------------

이 튜토리얼을 시작하기 전에 ROS 2를 설치.
Before starting these tutorials, install ROS 2 by following the instructions on the ROS 2 :doc:`../Installation` page.

이 튜토리얼에 사용한 명령은 리눅스 바이너리 패키지 설치가 되어 있다고 가정하고 사용.
만약 소스 빌드로 설치한 경우라면 setup 파일의 위치가 약간 다를 수 있음.
소스 빌드로 설치한 경우 ``sudo apt install ros-<distro>-<package>`` 명령을 사용할 수 없음.
The commands used in this tutorial assume you followed the binary packages installation guide for your operating system (Debian packages for Linux).
You can still follow along if you built from source, but the path to your setup files will likely be different.
You also won't be able to use the ``sudo apt install ros-<distro>-<package>`` command (used frequently in the beginner level tutorials) if you install from source.

리눅스를 사용하는데 shell 환경에 익숙하지 않다면 아래 튜토리얼을 참고하자.
If you are using Linux or macOS, but are not already familiar with the shell, `this tutorial <http://www.ee.surrey.ac.uk/Teaching/Unix/>`__ will help.

Tasks
-----

1 setup 파일을 source하기 (Source the setup files)
^^^^^^^^^^^^^^^^^^^^^^^^

매번 새로운 shell을 열때마다 다음 명령을 수행하여 ROS 2명령에 접근할 수 있다. 다음과 같이:
You will need to run this command on every new shell you open to have access to the ROS 2 commands, like so:

.. tabs::

   .. group-tab:: Linux

      .. code-block:: console

        source /opt/ros/{DISTRO}/setup.bash

   .. group-tab:: macOS

      .. code-block:: console

        . ~/ros2_install/ros2-osx/setup.bash

   .. group-tab:: Windows

      .. code-block:: console

        call C:\dev\ros2\local_setup.bat

.. note::
    The exact command depends on where you installed ROS 2.
    If you're having problems, ensure the file path leads to your installation.

2 Add sourcing to your shell startup script
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you don’t want to have to source the setup file every time you open a new shell (skipping task 1), then you can add the command to your shell startup script:

.. tabs::

   .. group-tab:: Linux

      .. code-block:: console

        echo "source /opt/ros/{DISTRO}/setup.bash" >> ~/.bashrc

     To undo this, locate your system’s shell startup script and remove the appended source command.

   .. group-tab:: macOS

      .. code-block:: console

        echo "source ~/ros2_install/ros2-osx/setup.bash" >> ~/.bash_profile

      To undo this, locate your system’s shell startup script and remove the appended source command.

   .. group-tab:: Windows

      Only for PowerShell users, create a folder in 'My Documents' called 'WindowsPowerShell'.
      Within 'WindowsPowerShell', create file 'Microsoft.PowerShell_profile.ps1'.
      Inside the file, paste:

      .. code-block:: console

        C:\dev\ros2_{DISTRO}\local_setup.ps1

      PowerShell will request permission to run this script everytime a new shell is opened.
      To avoid that issue you can run:

      .. code-block:: console

        Unblock-File C:\dev\ros2_{DISTRO}\local_setup.ps1

      To undo this, remove the new 'Microsoft.PowerShell_profile.ps1' file.

3 Check environment variables
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Sourcing ROS 2 setup files will set several environment variables necessary for operating ROS 2.
If you ever have problems finding or using your ROS 2 packages, make sure that your environment is properly setup using the following command:

.. tabs::

   .. group-tab:: Linux

      .. code-block:: console

        printenv | grep -i ROS

   .. group-tab:: macOS

      .. code-block:: console

        printenv | grep -i ROS

   .. group-tab:: Windows

      .. code-block:: console

        set | findstr -i ROS

Check that variables like ``ROS_DISTRO`` and ``ROS_VERSION`` are set.

::

  ROS_VERSION=2
  ROS_PYTHON_VERSION=3
  ROS_DISTRO={DISTRO}

If the environment variables are not set correctly, return to the ROS 2 package installation section of the installation guide you followed.
If you need more specific help (because environment setup files can come from different places), you can `get answers <https://answers.ros.org>`__ from the community.

3.1 The ``ROS_DOMAIN_ID`` variable
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

See the `domain ID <../Concepts/About-Domain-ID>` article for details on ROS domain IDs.

Once you have determined a unique integer for your group of ROS 2 agents, you can set the environment variable with the following command:

.. tabs::

   .. group-tab:: Linux

      .. code-block:: console

        export ROS_DOMAIN_ID=<your_domain_id>

      To maintain this setting between shell sessions, you can add the command to your shell startup script:

      .. code-block:: console

        echo "export ROS_DOMAIN_ID=<your_domain_id>" >> ~/.bashrc

   .. group-tab:: macOS

      .. code-block:: console

        export ROS_DOMAIN_ID=<your_domain_id>

      To maintain this setting between shell sessions, you can add the command to your shell startup script:

      .. code-block:: console

        echo "export ROS_DOMAIN_ID=<your_domain_id>" >> ~/.bash_profile

   .. group-tab:: Windows

      .. code-block:: console

        set ROS_DOMAIN_ID=<your_domain_id>

      If you want to make this permanant between shell sessions, also run:

      .. code-block:: console

        setx ROS_DOMAIN_ID <your_domain_id>


Summary
-------

The ROS 2 development environment needs to be correctly configured before use.
This can be done in two ways: either sourcing the setup files in every new shell you open, or adding the source command to your startup script.

If you ever face any problems locating or using packages with ROS 2, the first thing you should do is check your environment variables and ensure they are set to the version and distro you intended.

Next steps
----------

Now that you have a working ROS 2 installation and you know how to source its setup files, you can start learning the ins and outs of ROS 2 with the :doc:`turtlesim tool <./Turtlesim/Introducing-Turtlesim>`.
