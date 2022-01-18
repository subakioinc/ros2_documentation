.. _Turtlesim:

turtlesim 및 rqt 소개
Introducing turtlesim and rqt
=============================

**목표:** turtlesim 패키지 및 rqt 도구 설치하여 준비
**Goal:** Install and use the turtlesim package and rqt tools to prepare for upcoming tutorials.

**레벌:** 초급
**Tutorial level:** Beginner

**소요시간:** 15분
**Time:** 15 minutes

.. contents:: Contents
   :depth: 2
   :local:

배경(Background)
----------

Turtlesim은 ROS 2를 익히기 위한 가벼운 시뮬레이터
가장 기본 레벨에서 ROS 2가 무엇을 하는지 보여주어 실제 로봇 혹은 로봇 시뮬레이터와 무엇을 할 수 있을지 아이디어를 준다.  
Turtlesim is a lightweight simulator for learning ROS 2.
It illustrates what ROS 2 does at the most basic level, to give you an idea of what you will do with a real robot or robot simulation later on.

rqt는 ROS 2를 위한 GUI 도구이다.
rqt에서 되는 모든 것들은 커맨드 라인에서도 가능하며 ROS 2 엘리멘터를 사용자가 쉽게 처리할 수 있는 것을 제공한다. 
rqt is a GUI tool for ROS 2.
Everything done in rqt can be done on the command line, but it provides an easier, more user-friendly way to manipulate ROS 2 elements.

이 튜터리얼에서는 core ROS 2 컨셉인 node, topic, service를 다룬다.
이런 모든 컨셉은 이후 튜터리얼에서 상세히 다룬다. 여기에서는 단순하게 도구를 설정하고 경험해본다. 
This tutorial touches on core ROS 2 concepts, like the separation of nodes, topics, and services.
All of these concepts will be elaborated on in later tutorials; for now, you will simply set up the tools and get a feel for them.

사전준비(Prerequisites)
-------------

이전 튜터리얼 :doc:`../Configuring-ROS2-Environment` 에서 환경설정 방법을 알아봤다.
The previous tutorial, :doc:`../Configuring-ROS2-Environment`, will show you how to set up your environment.

Tasks
-----

1 turtlesim 설치하기(Install turtlesim)
^^^^^^^^^^^^^^^^^^^

항상 새 터미널을 실행해서 setup 파일을 source 명령을 준다. 이것에 대한 설명은  :doc:`previous tutorial <../Configuring-ROS2-Environment>` 참고.
As always, start by sourcing your setup files in a new terminal, as described in the :doc:`previous tutorial <../Configuring-ROS2-Environment>`.

ROS 2 배포판에 대한 turtlesim 패키지 설치:
Install the turtlesim package for your ROS 2 distro:

.. tabs::

   .. group-tab:: Linux

      .. code-block:: console

        sudo apt update

        sudo apt install ros-{DISTRO}-turtlesim

   .. group-tab:: macOS

      As long as the archive you installed ROS 2 from contains the ``ros_tutorials`` repository, you should already have turtlesim installed.

   .. group-tab:: Windows

      As long as the archive you installed ROS 2 from contains the ``ros_tutorials`` repository, you should already have turtlesim installed.

해당 패키지가 설치되었는지 확인:
Check that the package installed:

.. code-block:: console

  ros2 pkg executables turtlesim

위 명령을 수행함녀 turtlesim의 실행자의 목록을 반환:
The above command should return a list of turtlesim's executables:

.. code-block:: console

  turtlesim draw_square
  turtlesim mimic
  turtlesim turtle_teleop_key
  turtlesim turtlesim_node

2 turtlesim 시작하기(Start turtlesim)
^^^^^^^^^^^^^^^^^

turtlesim을 시작시키기 위해서 터미널에서 다음 명령을 입력한다:
To start turtlesim, enter the following command in your terminal:

.. code-block:: console

  ros2 run turtlesim turtlesim_node

시뮬레이터 윈도우가 나타나며 중앙에 임의의 turtle이 나타남.
The simulator window should appear, with a random turtle in the center.

.. image:: turtlesim.png

명령 아래에 node로부터 받은 메시지가 나타난다.:
In the terminal under the command, you will see messages from the node:

.. code-block:: console

  [INFO] [turtlesim]: Starting turtlesim with node name /turtlesim

  [INFO] [turtlesim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]

여기서 기본 turtle의 이름이 ``turtle1``이고 기본 좌표에 생성된다.
Here you can see your default turtle’s name is ``turtle1``, and the default coordinates where it spawns.

3 turtlesim 사용하기(Use turtlesim)
^^^^^^^^^^^^^^^

새로운 터미널을 열고 ROS 2를 다시 source하기
Open a new terminal and source ROS 2 again.

이제 첫번째 node에 있는 turtle을 제어하기 위해서 새로운 node를 실행:
Now you will run a new node to control the turtle in the first node:

.. code-block:: console

  ros2 run turtlesim turtle_teleop_key

At this point you should have three windows open: a terminal running ``turtlesim_node``, a terminal running ``turtle_teleop_key`` and the turtlesim window.
Arrange these windows so that you can see the turtlesim window, but also have the terminal running ``turtle_teleop_key`` active so that you can control the turtle in turtlesim.

Use the arrow keys on your keyboard to control the turtle.
It will move around the screen, using its attached "pen" to draw the path it followed so far.

.. note::

  Pressing an arrow key will only cause the turtle to move a short distance and then stop.
  This is because, realistically, you wouldn’t want a robot to continue carrying on an instruction if, for example, the operator lost the connection to the robot.

You can see the nodes and their associated services, topics, and actions using the ``list`` command:

.. code-block:: console

  ros2 node list
  ros2 topic list
  ros2 service list
  ros2 action list

You will learn more about these concepts in the coming tutorials.
Since the goal of this tutorial is only to get a general overview of turtlesim, we will use rqt (a graphical user interface for ROS 2) to look at services a little closer.

4 Install rqt
^^^^^^^^^^^^^

Open a new terminal to install ``rqt`` and its plugins:

.. tabs::

  .. group-tab:: Linux (apt 2.0/Ubuntu 20.04 and newer)

    .. code-block:: console

      sudo apt update

      sudo apt install ~nros-{DISTRO}-rqt*

  .. group-tab:: Linux (apt 1.x/Ubuntu 18.04 and older)

    .. code-block:: console

      sudo apt update

      sudo apt install ros-{DISTRO}-rqt*

  .. group-tab:: macOS

    The standard archive for installing ROS 2 on macOS contains ``rqt`` and its plugins, so you should already have ``rqt`` installed.

  .. group-tab:: Windows

    The standard archive for installing ROS 2 on Windows contains ``rqt`` and its plugins, so you should already have ``rqt`` installed.

To run rqt:

.. code-block:: console

  rqt

5 Use rqt
^^^^^^^^^

After running rqt the first time, the window will be blank.
No worries; just select **Plugins** > **Services** > **Service Caller** from the menu bar at the top.

.. note::

  It may take some time for rqt to locate all the plugins itself.
  If you click on **Plugins**, but don’t see **Services** or any other options, you should close rqt, enter the command ``rqt --force-discover`` in your terminal.

.. image:: rqt.png

Use the refresh button to the left of the **Service** dropdown list to ensure all the services of your turtlesim node are available.

Click on the **Service** dropdown list to see turtlesim's services, and select the ``/spawn`` service.

5.1 Try the spawn service
~~~~~~~~~~~~~~~~~~~~~~~~~

Let’s use rqt to call the ``/spawn`` service.
You can guess from its name that ``/spawn`` will create another turtle in the turtlesim window.

Give the new turtle a unique name, like ``turtle2`` by double-clicking between the empty single quotes in the **Expression** column.
You can see that this expression corresponds to the **name** value, and is of type **string**.

Enter new coordinates for the turtle to spawn at, like ``x = 1.0`` and ``y = 1.0``.

.. image:: spawn.png

.. note::

  If you try to spawn a new turtle with the same name as an existing turtle, like your default ``turtle1``, you will get an error message in the terminal running ``turtlesim_node``:

  .. code-block:: console

    [ERROR] [turtlesim]: A turtle named [turtle1] already exists

To spawn turtle2, you have to call the service by clicking the **Call** button on the upper right side of the rqt window.

You will see a new turtle (again with a random design) spawn at the coordinates you input for **x** and **y**.

If you refresh the service list in rqt, you will also see that now there are services related to the new turtle, ``/turtle2/…``, in addition to ``/turtle1/…``.

5.2 set_pen service 해보기(Try the set_pen service)
~~~~~~~~~~~~~~~~~~~~~~~~~~~

이제 ``/set_pen`` service를 사용해서 turtle1에게 고유 pen을 보여하기:
Now let's give turtle1 a unique pen using the ``/set_pen`` service:

.. image:: set_pen.png

**r**, **g**, **b**에 대한 값은 0에서 255까지 값으로 pen turtle1의 색상을 설정하고 turtle1의 폭은 **width**로 설정. 
The values for **r**, **g** and **b**, between 0 and 255, will set the color of the pen turtle1 draws with, and **width** sets the thickness of the line.

빨간선으로 turtle1을 그리기 위해서  **r**의 값을 255로 설정하고 **width**는 5로 설정.
값을 업데이트한 후에 service 호출해야만 한다.
To have turtle1 draw with a distinct red line, change the value of **r** to 255, and the value of **width** to 5.
Don't forget to call the service after updating the values.

``turtle_teleop_node``가 실행되고 있는 터미널로 돌아가서 화살표 키를 누르면 turtle1의 펜이 변경되는 것을 볼 수 있음.
If you return to the terminal where ``turtle_teleop_node`` is running and press the arrow keys, you will see turtle1’s pen has changed.

.. image:: new_pen.png

turtle2를 움직일 수 있는 방법이 없다는 것을 알게됨.
turtle1의 ``cmd_vel`` topic을 turtle2에 리매핑하면 된다. 
You've probably noticed that there's no way to move turtle2.
You can accomplish this by remapping turtle1's ``cmd_vel`` topic onto turtle2.

6 리매핑(Remapping)
^^^^^^^^^^^

새로운 터미널에서 ROS 2를 source하고 실행:
In a new terminal, source ROS 2, and run:

.. code-block:: console

  ros2 run turtlesim turtle_teleop_key --ros-args --remap turtle1/cmd_vel:=turtle2/cmd_vel


터미널이 활성화되면 이제 turtle2 를 움직일 수 있다. ``turtle_teleop_key``가 실행되는 다른 터미널에서 turtle1이 활성화된다. 
Now you can move turtle2 when this terminal is active, and turtle1 when the other terminal running the ``turtle_teleop_key`` is active.

.. image:: remap.png

7 turtlesim 닫기(Close turtlesim)
^^^^^^^^^^^^^^^^^

시뮬레이션을 멈추기 위해서 ``turtlesim_node`` 터미널에서 ``Ctrl + C``를 입력하고 teleop 터미널에서 ``q``를 누른다.
To stop the simulation, you can enter ``Ctrl + C`` in the ``turtlesim_node`` terminal, and ``q`` in the teleop terminal.

요약(Summary)
-------

turtlesim와 rqt를 사용하여 ROS 2의 핷미 개념을 익히는 가장 좋은 방법.
Using turtlesim and rqt is a great way to learn the core concepts of ROS 2.

다음 단계(Next steps)
----------

turtlesim과 rqt를 실행하여 어떻게 동작하는지를 알아봄. 다음 튜터리얼에서 ROS 2 핵심 개념을 좀더 깊이 알아보자. 
Now that you have turtlesim and rqt up and running, and an idea of how they work, let's dive in to the first core ROS 2 concept with the next tutorial, :doc:`../Understanding-ROS2-Nodes`.

관련 컨텐츠(Related content)
---------------

turtlesim 패키지는 `ros_tutorials repo <https://github.com/ros/ros_tutorials/tree/galactic-devel/turtlesim>`_ 참조.
설치한 ROS 2 배포판과 관련된 turtlesim의 버전을 보려면 branch를 조정하여 확인.
The turtlesim package can be found in the `ros_tutorials repo <https://github.com/ros/ros_tutorials/tree/galactic-devel/turtlesim>`_.
Make sure to adjust the branch to view the version of turtlesim corresponding to your installed ROS 2 distro.

`This community contributed video <https://youtu.be/xwT7XWflMdc>`_ demonstrates many of the items covered in this tutorial.
