# calibration_camera_lidar
从autoware分离出来的相机雷达联合标定ros包
https://github.com/XidianLemon/calibration_camera_lidar

# install nlopt
git clone https://github.com/stevengj/nlopt.git
cd nlopt
mkdir build
cd build
cmake ..
make
sudo make install

######################################################
# start roscore
roscore	

# play rosbag
rosbag play bagname.bag /rslidar_points:=points_raw -l

# start calibtation tool
source devel/setup.bash
rosrun calibration_camera_lidar calibration_toolkit

#######################################################
# data collection 
1.LiDAR
./start.sh
2.image
./run2.sh

# undistort image
1.cd catkin_ws_undistort
  devel/lib/undistort/undistort

2.rosbag record usb_cam2/image_raw rslidar_points 

3.rosbag play bagname.bag -r 0.1


