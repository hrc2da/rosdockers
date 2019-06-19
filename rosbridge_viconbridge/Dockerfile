FROM osrf/ros:indigo-desktop-full
SHELL ["/bin/bash", "-c"]
RUN apt-get update && apt-get install -y ros-indigo-rosbridge-suite && \
    apt-get install -y build-essential && apt-get install -y ros-indigo-tf
RUN mkdir ~/catkin_ws && mkdir ~/catkin_ws/src && cd ~/catkin_ws/src && \
    git clone https://github.com/ethz-asl/vicon_bridge && \
    rosdep install -r --from-paths vicon_bridge/
RUN . /opt/ros/indigo/setup.bash && cd ~/catkin_ws &&  catkin_make 
EXPOSE 9090

CMD ["/bin/bash","-c",". ~/catkin_ws/devel/setup.bash && (roscore & (sleep 3 && (roslaunch rosbridge_server rosbridge_websocket.launch & roslaunch vicon_bridge vicon.launch)))"]  


