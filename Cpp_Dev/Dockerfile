# Base docker image
ARG UBUNTU_VERSION=20.04
FROM ubuntu:$UBUNTU_VERSION


# Define label with author information
LABEL author="Hadi Ghasemi Zadeh"


# Define timezone environment variable
ENV TZ=Europe/Lisbon
# Create a /etc/timezone file and set it with defined TimeZone(TZ)
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

	
	
# Install all cpp tools 
RUN apt-get update \
	&& apt-get install -y  --no-install-recommends \
	sudo \
	libssl-dev \
	ca-certificates \
	bzip2 \
	tini \
	nano \
	vim \
	git \
	wget \
	curl \
	perl \
	make \
	gcc \
	g++ \
	gdb \
	cmake \
	libaio-dev \
	manpages-dev \
	cppcheck \
	clang-tools \
	libgtest-dev \
	libbenchmark-dev 



## Install Google Test
#ENV GTEST_HOME=/opt/googletest
#RUN	mkdir -p ${GTEST_HOME} \
#	&& cd ${GTEST_HOME} \
#	&& git clone https://github.com/google/googletest.git . \
#	&& cmake . \
#	&& make
#	#&& rm -rf /tmp/*


## Install CMake from building its source file
#ARG CMAKE_VER=3.16.5
#RUN cd /tmp/ \
#	&& apt-get update \
#	&& apt-get install -y libssl-dev \
#	&& wget https://github.com/Kitware/CMake/releases/download/v${CMAKE_VER}/cmake-${CMAKE_VER}.tar.gz --no-check-certificate \
#	&& tar -zxf cmake-${CMAKE_VER}.tar.gz -C /opt/ \
#	&& cd /opt/cmake-${CMAKE_VER} \
#	&& ./bootstrap \
#	&& make \
#	&& make install \
#	&& apt-get clean \
#	&& rm -rf /tmp/*
#	
#ENV PATH=/opt/cmake-${CMAKE_VER}/bin:${PATH} 


ENV LD_LIBRARY_PATH=${GTEST_HOME}/lib:${LD_LIBRARY_PATH}


# Create a user and set his/her home directory, bash and make him/her sudoer
ARG MY_USER_NAME=hadi

RUN useradd -ms /bin/bash ${MY_USER_NAME}
RUN sudo usermod -a -G sudo ${MY_USER_NAME} 

# Set work directory
WORKDIR /home/${MY_USER_NAME}


## Copy project source code it copies the proj_dist_dir/ from current directory to WORKDIR/proj_dist_dir/
##COPY proj_dist_dir ./proj_dist_dir/
##RUN chown -R ${MY_USER_NAME}:${MY_USER_NAME} ./proj_dist_dir/


USER ${MY_USER_NAME}	 


ENTRYPOINT ["/bin/bash"]


