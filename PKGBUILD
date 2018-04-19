# Script generated with Bloom
pkgdesc="ROS - rqt_gui_cpp enables GUI plugins to use the C++ client library for ROS."
url='http://ros.org/wiki/rqt_gui_cpp'

pkgname='ros-kinetic-rqt-gui-cpp'
pkgver='0.5.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('qt5-base'
'ros-kinetic-catkin'
'ros-kinetic-nodelet'
'ros-kinetic-qt-gui-cpp>=0.3.0'
'ros-kinetic-qt-gui>=0.3.0'
'ros-kinetic-roscpp'
)

depends=('ros-kinetic-nodelet'
'ros-kinetic-qt-gui-cpp>=0.3.0'
'ros-kinetic-qt-gui>=0.3.0'
'ros-kinetic-roscpp'
)

conflicts=()
replaces=()

_dir=rqt_gui_cpp
source=()
md5sums=()

prepare() {
    cp -R $startdir/rqt_gui_cpp $srcdir/rqt_gui_cpp
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
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

