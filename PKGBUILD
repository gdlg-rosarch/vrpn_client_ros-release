# Script generated with Bloom
pkgdesc="ROS - ROS client nodes for the <a href="https://github.com/vrpn/vrpn/wiki">VRPN</a> library, compatible with VICON, OptiTrack, and other <a href="https://github.com/vrpn/vrpn/wiki/Supported-hardware-devices">hardware interfaces</a>."


pkgname='ros-kinetic-vrpn-client-ros'
pkgver='0.2.2_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
'ros-kinetic-geometry-msgs'
'ros-kinetic-roscpp'
'ros-kinetic-roslaunch'
'ros-kinetic-roslint'
'ros-kinetic-tf2-ros'
'ros-kinetic-vrpn'
)

depends=('ros-kinetic-geometry-msgs'
'ros-kinetic-roscpp'
'ros-kinetic-tf2-ros'
'ros-kinetic-vrpn'
)

conflicts=()
replaces=()

_dir=vrpn_client_ros
source=()
md5sums=()

prepare() {
    cp -R $startdir/vrpn_client_ros $srcdir/vrpn_client_ros
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

