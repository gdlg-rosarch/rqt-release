# Script generated with Bloom
pkgdesc="ROS - rqt is a Qt-based framework for GUI development for ROS. It consists of three parts/metapackages<br/> <ul> <li>rqt (you're here)</li> <li><a href="http://ros.org/wiki/rqt_common_plugins">rqt_common_plugins</a> - ROS backend tools suite that can be used on/off of robot runtime.</li> <li><a href="http://ros.org/wiki/rqt_robot_plugins">rqt_robot_plugins</a> - Tools for interacting with robots during their runtime.</li> </ul> rqt metapackage provides a widget <a href="http://ros.org/wiki/rqt_gui">rqt_gui</a> that enables multiple `rqt` widgets to be docked in a single window."
url='http://ros.org/wiki/rqt'

pkgname='ros-kinetic-rqt'
pkgver='0.5.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
)

depends=('ros-kinetic-rqt-gui-cpp>=0.3.0'
'ros-kinetic-rqt-gui-py>=0.3.0'
'ros-kinetic-rqt-gui>=0.3.0'
)

conflicts=()
replaces=()

_dir=rqt
source=()
md5sums=()

prepare() {
    cp -R $startdir/rqt $srcdir/rqt
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

