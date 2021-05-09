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

# Set work directory
#WORKDIR /home/${MY_USER_NAME}


#ENTRYPOINT ["/bin/bash"]


