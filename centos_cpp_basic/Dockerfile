FROM centos:7.6.1810

# Make sure manpages will get downloaded
RUN sed -i '/tsflags=nodocs/d' /etc/yum.conf

# Configure apt and install packages
RUN yum -y makecache \
    && yum -y install man man-pages man-db \
    #
    # Install git v2
    && yum -y install https://packages.endpoint.com/rhel/7/os/x86_64/endpoint-repo-1.7-1.x86_64.rpm \
    && yum -y install git \
    #
    # Install C++ tools
    && yum -y install centos-release-scl \
    && yum -y install devtoolset-7-toolchain-7.1 \
    && yum -y install devtoolset-7-perftools-7.1 \
    && yum -y autoremove \
    && yum -y clean all \
    && printf "\nsource scl_source enable devtoolset-7\n\n" >> ~/.bashrc

# Fix expected paths for VSCode
    # launch.json -> miDebuggerPath
RUN ln -s /opt/rh/devtoolset-7/root/usr/bin/gdb /usr/bin/gdb \
    # c_cpp_properties.json -> compilerPath
    && ln -s /opt/rh/devtoolset-7/root/usr/bin/c++ /usr/bin/c++ \
    && ln -s /opt/rh/devtoolset-7/root/usr/bin/g++ /usr/bin/g++

# Set the default shell to bash instead of sh
ENV SHELL /bin/bash
