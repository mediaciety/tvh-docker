FROM phusion/baseimage:0.11

# Use baseimage-docker's init system.
CMD ["/sbin/my_init"]

RUN apt-get update && apt-get -y upgrade
RUN apt-get -y install build-essential subversion dialog libssl1.0-dev dvb-apps libdvb* usbutils wget libudev-dev


RUN wget https://sourceforge.net/projects/libusb/files/libusb-1.0/libusb-1.0.20/libusb-1.0.20.tar.bz2
RUN tar -xf libusb-1.0.20.tar.bz2
WORKDIR ./libusb-1.0.20

RUN ./configure
RUN make
RUN make install

WORKDIR ..
RUN svn checkout http://www.streamboard.tv/svn/oscam/trunk oscam-svn

WORKDIR ./oscam-svn
RUN make allyesconfig
RUN make USE_LIBUSB=1

EXPOSE 8888:8888