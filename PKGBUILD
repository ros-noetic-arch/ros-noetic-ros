# Maintainer: Hermann von Kleist (stertingen yahoo com)
pkgdesc="ROS - ROS packaging system."
url='https://www.wiki.ros.org/ROS'
pkgbase='ros-noetic-ros'
pkgname=(
    'ros-noetic-mk'
    'ros-noetic-ros'
    'ros-noetic-rosbash'
    'ros-noetic-rosboost-cfg'
    'ros-noetic-rosbuild'
    'ros-noetic-rosclean'
    'ros-noetic-roscreate'
    'ros-noetic-roslang'
    'ros-noetic-roslib'
    'ros-noetic-rosmake'
    'ros-noetic-rosunit'
)
pkgver='1.15.2'
arch=('i686' 'x86_64' 'aarch64' 'armv7h' 'armv6h')
pkgrel=1
license=('BSD')

source=("${pkgbase}-${pkgver}.tar.gz"::"https://github.com/ros/ros/archive/${pkgver}.tar.gz")
sha256sums=('596bb5e04ece0ad0662d6d2ee9b4223aaa890770e83c7310ec71bf9c0c3c7b5e')

makedepends=(
	cmake
	ros-build-tools
	ros-noetic-catkin
)

build() {
    # Use ROS environment variables.
    source /usr/share/ros-build-tools/clear-ros-env.sh
    [ -f /opt/ros/noetic/setup.bash ] && source /opt/ros/noetic/setup.bash

    catkin_make_isolated \
        --directory ${srcdir} \
        --source ${srcdir}/ros-${pkgver} \
        --install-space /opt/ros/noetic \
        --cmake-args \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DPYTHON_EXECUTABLE=/usr/bin/python3 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
}

check() {
    catkin_make_isolated \
        --directory ${srcdir} \
        --source ${srcdir}/ros-${pkgver} \
        --install-space /opt/ros/noetic \
        --catkin-make-args run_tests
}

package_ros-noetic-mk() {
    pkgdesc="ROS - A collection of .mk include files for building ROS architectural elements."
    url='https://wiki.ros.org/mk'
    depends=(
        ros-noetic-rosbuild
    )
    cd "${srcdir}/build_isolated/mk"
    make DESTDIR="${pkgdir}/" install
}

package_ros-noetic-ros() {
    pkgdesc="ROS - ROS packaging system."
    url='https://www.wiki.ros.org/ROS'
    depends=(
        ros-noetic-catkin
        ros-noetic-mk
        ros-noetic-rosbash
        ros-noetic-rosboost-cfg
        ros-noetic-rosbuild
        ros-noetic-rosclean
        ros-noetic-roscreate
        ros-noetic-roslang
        ros-noetic-roslib
        ros-noetic-rosmake
        ros-noetic-rosunit
    )
    cd "${srcdir}/build_isolated/ros"
    make DESTDIR="${pkgdir}/" install
}

package_ros-noetic-rosbash() {
    pkgdesc="ROS - Assorted shell commands for using ros with bash."
    url='https://wiki.ros.org/rosbash'
    depends=(
        ros-noetic-catkin
    )
    cd "${srcdir}/build_isolated/rosbash"
    make DESTDIR="${pkgdir}/" install
}

package_ros-noetic-rosboost-cfg() {
    pkgdesc="ROS - Contains scripts used by the rosboost-cfg tool for determining cflags/lflags/etc."
    url='https://wiki.ros.org/rosboost_cfg'
    depends=(
    )
    cd "${srcdir}/build_isolated/rosboost_cfg"
    make DESTDIR="${pkgdir}/" install
}

package_ros-noetic-rosbuild() {
    pkgdesc="ROS - rosbuild contains scripts for managing the CMake-based build system for ROS."
    url='https://wiki.ros.org/rosbuild'
    depends=(
        ros-noetic-message-runtime
        ros-noetic-message-generation
        ros-noetic-catkin

    )
    cd "${srcdir}/build_isolated/rosbuild"
    make DESTDIR="${pkgdir}/" install
}

package_ros-noetic-rosclean() {
    pkgdesc="ROS - rosclean: cleanup filesystem resources (e.g."
    url='https://wiki.ros.org/rosclean'
    depends=(
        python-rospkg
    )
    cd "${srcdir}/build_isolated/rosclean"
    make DESTDIR="${pkgdir}/" install
}

package_ros-noetic-roscreate() {
    pkgdesc="ROS - roscreate contains a tool that assists in the creation of ROS filesystem resources."
    url='https://wiki.ros.org/roscreate'
    depends=(
        python-rospkg
    )
    cd "${srcdir}/build_isolated/roscreate"
    make DESTDIR="${pkgdir}/" install
}

package_ros-noetic-roslang() {
    pkgdesc="ROS - roslang is a common package that all ROS client libraries depend on."
    url='https://wiki.ros.org/roslang'
    depends=(
        ros-noetic-genmsg
        ros-noetic-catkin
    )
    cd "${srcdir}/build_isolated/roslang"
    make DESTDIR="${pkgdir}/" install
}

package_ros-noetic-roslib() {
    pkgdesc="ROS - Base dependencies and support libraries for ROS."
    url='https://wiki.ros.org/roslib'
    depends=(
        ros-noetic-ros-environment
        ros-noetic-rospack
        ros-noetic-catkin
        python-rospkg
    )
    cd "${srcdir}/build_isolated/roslib"
    make DESTDIR="${pkgdir}/" install
}

package_ros-noetic-rosmake() {
    pkgdesc="ROS - rosmake is a ros dependency aware build tool which can be used to build all dependencies in the correct order."
    url='https://wiki.ros.org/rosmake'
    depends=(
        ros-noetic-catkin
        python-rospkg
    )
    cd "${srcdir}/build_isolated/rosmake"
    make DESTDIR="${pkgdir}/" install
}

package_ros-noetic-rosunit() {
    pkgdesc="ROS - Unit-testing package for ROS."
    url='https://wiki.ros.org/rosunit'
    depends=(
        ros-noetic-roslib
        python-rospkg
    )
    cd "${srcdir}/build_isolated/rosunit"
    make DESTDIR="${pkgdir}/" install
}
