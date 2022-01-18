.. _Tf2Main:

tf2 튜너리얼(tf2 Tutorials)
=============

다수의 tf2 튜터리얼은 C++과 Python 모두 가능하다.
튜터리얼은 C++이나 Python 중에 하나를 가지고 따라할 수 있다.
C++과 Python 모두를 배우고자 한다면 일단 C++로 하고 Pyhthon으로도 따라해 보자.
Many of the tf2 tutorials are available for both C++ and Python.
The tutorials are streamlined to complete either the C++ track or the Python track.
If you want to learn both C++ and Python, you should go through the tutorials once for C++ and once for Python.

.. contents:: Contents
   :depth: 2
   :local:

.. toctree::
   :hidden:

   Introduction-To-Tf2
   Writing-A-Tf2-Static-Broadcaster-Py
   Writing-A-Tf2-Static-Broadcaster-Cpp
   Writing-A-Tf2-Broadcaster-Py
   Writing-A-Tf2-Broadcaster-Cpp
   Writing-A-Tf2-Listener-Py
   Writing-A-Tf2-Listener-Cpp
   Adding-A-Frame-Py
   Adding-A-Frame-Cpp
   Learning-About-Tf2-And-Time-Py
   Learning-About-Tf2-And-Time-Cpp
   Time-Travel-With-Tf2-Py
   Time-Travel-With-Tf2-Cpp
   Debugging-Tf2-Problems
   Quaternion-Fundamentals
   Using-Stamped-Datatypes-With-Tf2-Ros-MessageFilter

Workspace 설정(Workspace setup)
---------------

튜터리얼을 완료하기 위해서 workspace를 아직 생성하지 않았다면 :doc:`follow this tutorial <../Workspace/Creating-A-Workspace>` 를 따라하자.
If you have not yet created a workspace in which to complete the tutorials, :doc:`follow this tutorial <../Workspace/Creating-A-Workspace>`.

tf2 익히기(Learning tf2)
------------

#. :doc:`Introduction to tf2 <./Introduction-To-Tf2>`.

   이 튜터리얼은 tf2가 무엇을 하는지 개념을 알려준다.
   turtlesim을 사용하여 멀티로봇 예제에서 tf2의 강력함을 확인할 수 있다.
   ``tf2_echo``, ``view_frames``,  ``rviz``를 사용한다.
   This tutorial will give you a good idea of what tf2 can do for you.
   It shows off some of the tf2 power in a multi-robot example using turtlesim.
   This also introduces using ``tf2_echo``, ``view_frames``, and ``rviz``.

#. tf2 static broadcaster 작성하기(Writing a tf2 static broadcaster) :doc:`(Python) <./Writing-A-Tf2-Static-Broadcaster-Py>` :doc:`(C++) <./Writing-A-Tf2-Static-Broadcaster-Cpp>`.

   이 튜터리얼은 static coordinate frames을 tf2로 broadcast하는 방법을 가르쳐준다.
   This tutorial teaches you how to broadcast static coordinate frames to tf2.

#. tf2 broadcaster 작성하기(Writing a tf2 broadcaster) :doc:`(Python) <./Writing-A-Tf2-Broadcaster-Py>` :doc:`(C++) <Writing-A-Tf2-Broadcaster-Cpp>`.

   이 튜터리얼은 robot의 상태를 tf2로 broadcst하는 방법을 가르쳐준다.
   This tutorial teaches you how to broadcast the state of a robot to tf2.

#. tf2 listener 작성하기(Writing a tf2 listener) :doc:`(Python) <./Writing-A-Tf2-Listener-Py>` :doc:`(C++) <./Writing-A-Tf2-Listener-Cpp>`.

   이 튜터리얼은 tf2를 사용하여 frame transformations에 접근하는 방법을 가르쳐준다.
   This tutorial teaches you how to use tf2 to get access to frame transformations.

#. frame 추가하기(Adding a frame) :doc:`(Python) <./Adding-A-Frame-Py>` :doc:`(C++) <Adding-A-Frame-Cpp>`.

   이 튜터리얼은 추가 fixed frame을 tf2에 추가하는 방법을 가르쳐준다.
   This tutorial teaches you how to add an extra fixed frame to tf2.

#. tf2와 time에 대해 익히기(Learning about tf2 and time) :doc:`(Python) <Learning-About-Tf2-And-Time-Py>` :doc:`(C++) <Learning-About-Tf2-And-Time-Cpp>`.

   이 튜터리얼은 ``lookup_transform`` 함수에서 timeout을 사용하여 transform이 tf2 tree에서 유효할때까지 기다리기 위해서 사용하는 방법을 가르쳐준다.
   This tutorial teaches you to use the timeout in ``lookup_transform`` function to
   wait for a transform to be available on the tf2 tree.

#. tf2와 time travel(Time travel with tf2) :doc:`(Python) <./Time-Travel-With-Tf2-Py>` :doc:`(C++) <./Time-Travel-With-Tf2-Cpp>`.

   이 튜터리얼은 tf2의 고급 time travel 특징에 대해서 가르쳐준다.
   This tutorial teaches you about advanced time travel features of tf2.

tf2 디버깅(Debugging tf2)
-------------

#. :doc:`Quaternion fundamentals <./Quaternion-Fundamentals>`.

   This tutorial teaches you basics of quaternion usage in ROS 2.

#. :doc:`Debugging tf2 problems <./Debugging-Tf2-Problems>`.

   This tutorial teaches you about a systematic approach for debugging tf2 related problems.

Using sensor messages with tf2
------------------------------

#. :doc:`Using stamped datatypes with tf2_ros::MessageFilter <./Using-Stamped-Datatypes-With-Tf2-Ros-MessageFilter>`.

   This tutorial teaches you how to use ``tf2_ros::MessageFilter`` to process stamped datatypes.
