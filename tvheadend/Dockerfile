FROM phusion/baseimage:0.11

# Use baseimage-docker's init system.
CMD ["/sbin/my_init"]



RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 379CE192D401AB61 

RUN echo "deb https://dl.bintray.com/tvheadend/deb bionic stable-4.2" | tee /etc/apt/sources.list.d/tvheadend.list


RUN apt-get update && apt-get -y upgrade 
RUN apt-get -y install wget tvheadend udev linux-firmware avahi-daemon libavahi-client3
RUN wget -O /etc/init.d/tvheadend https://raw.githubusercontent.com/tvheadend/tvheadend/master/debian/tvheadend.init
RUN chmod 755 /etc/init.d/tvheadend
RUN update-rc.d tvheadend defaults

EXPOSE 9981 9982 554

WORKDIR /home/hts/
#ADD ./config /home/hts/.hts/tvheadend

COPY ./entrypoint.sh /


#ENTRYPOINT ["/entrypoint.sh"]
