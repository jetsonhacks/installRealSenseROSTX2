# installRealSenseROSTX2
Install the Intel RealSense ROS package on the NVIDIA® Jetson TX2
The installLibRealSenseROS script install librealsense and realsense as ROS packages. These scripts have been tested with a RealSense R200 camera.

This is the third step of a three step process.

The first step requires a kernel modification. librealsense requires a modified kernel which modularizes uvcvideo and adds the RealSense video modes to the uvcvideo driver.

The easiest way to accomplish this is to use the 'installLibrealsenseTX2' repository on the Github JetsonHacks account (https://github.com/jetsonhacks/installLibrealsenseTX2). There are scripts which download the kernel source, apply the necessary patches, make the kernel, and then copy the kernel images to the boot directory. There are also scripts to build the librealsense library itself, which is useful for testing purposes.

The second step is to install ROS on the Jetson TX2. There are convenience scripts to help do this on the Github JetsonHacks account in the installROSTX2 repository (https://github.com/jetsonhacks/installROSTX2). Note that the repository installs ros-base, if other configurations such as ros-desktop are desired, the scripts should be modified accordingly.

This step, the third step, is to install librealsense and realsense as ROS packages. The script installRealSenseROS.sh in this directory will install librealsense and realsense and dependencies in a Catkin Workspace. Note that the previous librealsense installation, though valid, then becomes superflous.

To install:

$ ./installRealSenseROS.sh \<catkin_ws_name\>

The script 'setupTX2.sh' simply turns off the USB autosuspend setting on the Jetson TX2 so that the camera is always available. 

This installs RealSense ROS version 1.8. There is an issue in the version that is available in the ROS repository (1.7.2) which does not allow one of the auto-exposure modes to work correctly. This be bad for most use cases.
