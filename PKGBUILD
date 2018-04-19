# Script generated with Bloom
pkgdesc="ROS - rqt_py_common provides common functionality for rqt plugins written in Python. Despite no plugin is provided, this package is part of the rqt_common_plugins repository to keep refactoring generic functionality from these common plugins into this package as easy as possible. Functionality included in this package should cover generic ROS concepts and should not introduce any special dependencies beside &quot;ros_base&quot;."
url='http://ros.org/wiki/rqt_py_common'

pkgname='ros-melodic-rqt-py-common'
pkgver='0.5.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-melodic-catkin'
'ros-melodic-genmsg'
'ros-melodic-std-msgs'
)

depends=('ros-melodic-actionlib'
'ros-melodic-genpy'
'ros-melodic-python-qt-binding>=0.2.19'
'ros-melodic-qt-gui'
'ros-melodic-rosbag'
'ros-melodic-roslib'
'ros-melodic-rospy'
'ros-melodic-rostopic'
)

conflicts=()
replaces=()

_dir=rqt_py_common
source=()
md5sums=()

prepare() {
    cp -R $startdir/rqt_py_common $srcdir/rqt_py_common
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

