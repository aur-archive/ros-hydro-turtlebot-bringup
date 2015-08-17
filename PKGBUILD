# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - turtlebot_bringup provides roslaunch scripts for starting the TurtleBot base functionality."
url='http://ros.org/wiki/turtlebot_bringup'

pkgname='ros-hydro-turtlebot-bringup'
pkgver='2.2.5'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-hydro-catkin)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]})

ros_depends=(ros-hydro-zeroconf-avahi
  ros-hydro-depthimage-to-laserscan
  ros-hydro-diagnostic-aggregator
  ros-hydro-rocon-app-manager
  ros-hydro-openni-launch
  ros-hydro-kobuki-safety-controller
  ros-hydro-robot-state-publisher
  ros-hydro-kobuki-node
  ros-hydro-create-node
  ros-hydro-robot-pose-ekf
  ros-hydro-turtlebot-description
  ros-hydro-yocs-cmd-vel-mux
  ros-hydro-kobuki-bumper2pc
  ros-hydro-linux-hardware)
depends=(${ros_depends[@]})

_tag=release/hydro/turtlebot_bringup/${pkgver}-${_pkgver_patch}
_dir=turtlebot_bringup
source=("${_dir}"::"git+https://github.com/turtlebot-release/turtlebot-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
