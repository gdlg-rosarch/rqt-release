# Script generated with Bloom
pkgdesc="ROS - rqt_gui provides the main to start an instance of the ROS integrated graphical user interface provided by qt_gui."
url='http://ros.org/wiki/rqt_gui'

pkgname='ros-lunar-rqt-gui'
pkgver='0.5.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-lunar-catkin'
'ros-lunar-qt-gui>=0.3.0'
)

depends=('ros-lunar-catkin'
'ros-lunar-qt-gui>=0.3.0'
)

conflicts=()
replaces=()

_dir=rqt_gui
source=()
md5sums=()

prepare() {
    cp -R $startdir/rqt_gui $srcdir/rqt_gui
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
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

