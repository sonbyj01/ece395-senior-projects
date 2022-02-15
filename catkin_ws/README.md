## properly build catkin workspace
```
cd catkin_ws
rosdep install --from-paths src --ignore-src -r -y
catkin_make -DCMAKE_BUILD_TYPE=Release
```

## test video subscriber using video file
1. start roscore
```
roscore
```
2. start publishing video file
```
roslaunch video_stream_opencv video_file.launch
```
3. start subscribing to video file
```
rosrun yolor_ros listener-zed.py
```