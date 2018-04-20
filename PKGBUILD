# Script generated with Bloom
pkgdesc="ROS - Catkin macros to allow using pure python packages in usual catkin workspaces with normal python workflow."
url='http://github.com/asmodehn/catkin_pip'

pkgname='ros-lunar-catkin-pip'
pkgver='0.2.3_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('git>=1.9.1'
'python2-pip>=1.5.4'
'python2>=2.7.5'
'ros-lunar-catkin'
)

depends=('python2-pip>=1.5.4'
'python2>=2.7.5'
)

conflicts=()
replaces=()

_dir=catkin_pip
source=()
md5sums=()

prepare() {
    cp -R $startdir/catkin_pip $srcdir/catkin_pip
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

