# Base docker image
ARG UBUNTU_VERSION=20.04
FROM ubuntu:$UBUNTU_VERSION


# Define label with author information
LABEL author="Hadi Ghasemi Zadeh"


# Create the user and his/her home directory and bash
ARG MY_USER_NAME=hadi
RUN useradd -ms /bin/bash ${MY_USER_NAME}



# Define timezone environment variable
ENV TZ=Europe/Lisbon
# Create a /etc/timezone file and set it with defined TimeZone(TZ)
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

	
# Install all tools 
RUN apt-get update \
	&& apt-get install -y  --no-install-recommends \
	wget \
	vim \
	ca-certificates \
	gzip \
	zip \
	git \
	g++ \
	make \
	cmake


ENV GTEST_HOME=/opt/googletest

RUN	mkdir -p ${GTEST_HOME} \
	&& cd ${GTEST_HOME} \
	&& git clone https://github.com/google/googletest.git . \
	&& cmake . \
	&& make
	#&& rm -rf /tmp/*

ENV LD_LIBRARY_PATH=${GTEST_HOME}/lib:${LD_LIBRARY_PATH}

RUN apt-get update \
	&& apt-get install -y --no-install-recommends \
	&& cd /root \
	&& wget https://github.com/hadighasemizadeh/Containers/blob/master/GTest/cpp_example.tar.gz --no-check-certificate 

RUN unzip cpp_example.tar.gz


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

