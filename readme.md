## Mid360-3D雷达

### 1.驱动包：livox_ros_driver2

#### a)参数配置：./config/Mid360_config.json

host_net_info	里面的ip为192.168.1.50

雷达ip号lidar_configs：192.168.1.197(盒子上的编码后两位97)

#### b)启动文件：./launch_ROS1/msg_MID360.launch

启动后终端会看出已经与雷达连接



### 2.扫描3D图工具:FAST_LIO-main

#### a)配置文件：./config/Mid360.launch

雷达和里程计imu话题(可以直接用这两个)

blind:雷达扫描多少米之内的点忽略(如果是4,即2米内忽略)，定位和建图时针对比赛场地，建议改小一点

#### b)启动文件：./launch/Mid360.launch

​		 filter_size_surf    0.05    0.15    0.3

​         filter_size_map     0.15    0.2     0.3

​         cube_side_length    2000    2000    2000 排列组合

启动后雷达开始扫描建图，在rviz中可视，可以查看path类型话题的轨迹．



### 3.3D地图保存与调用

#### a)录制地图:./launch/cloud_recorder.launch

运行时只需要改变file_name的名字即可，会在data文件夹生成.pcd文件

需要注意的是储存的是点云地图，数据很大并且相同的点不会覆盖，所以扫描地图要快，否则内存不够存不下来．

### b)调用地图：./launch/my_map.launch

参数每次更改文件名即可(.pcd文件)

实质是调用.pcd文件，不在此处使用，在轨迹生成时调用即可

