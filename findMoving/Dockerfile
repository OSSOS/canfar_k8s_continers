FROM ubuntu
RUN apt-get update && apt-get -y install gcc  curl
RUN apt update -y && apt install -y xterm vim 
RUN apt update -y && apt install -y sssd-ad sssd-tools realmd adcli
# system settings and permissions
COPY src/nofiles.conf /etc/security/limits.d/
COPY src/iraf.sh /etc/profile.d/
COPY src/nsswitch.conf /etc/
## see https://bugzilla.redhat.com/show_bug.cgi?id=1773148
RUN touch /etc/sudo.conf && echo "Set disable_coredump false" > /etc/sudo.conf


RUN apt install -y python3.9
RUN apt install -y iraf
RUN apt install -y libx11-dev
RUN apt install -y libxpa-dev
RUN apt install -y xpa-tools
RUN apt install -y python3-pyds9
RUN apt install -y pip
RUN apt install -y  libgtk-3-dev libnotify-bin libsdl2-dev

RUN pip install -U \
    -f https://extras.wxpython.org/wxPython4/extras/linux/gtk3/ubuntu-20.04 \
    wxPython
RUN pip install pyraf
RUN pip install vos
RUN apt install -y git
RUN curl https://ds9.si.edu/download/ubuntu20/ds9.ubuntu20.8.2.1.tar.gz -o ds9.ubuntu20.8.2.1.tar.gz ; tar zxf ds9.ubuntu20.8.2.1.tar.gz  ; mv ds9 /usr/bin/ds9
RUN pip install stsci.tools==3.6.0
RUN apt install -y parallel
RUN apt install -y emacs
RUN pip install astropy ccdproc pyraf vos matplotlib scipy ephem pyds9 mp_ephem
RUN pip install ossos

ENV GITUSER=ijiraq
ENV REPO=findMoving
ENV BRANCH=master
ENV GIT_HOME=/tmp
ADD https://api.github.com/repos/$GITUSER/$REPO/git/refs/heads/$BRANCH version.json
RUN git clone -b $BRANCH https://github.com/$GITUSER/$REPO.git $GIT_HOME/$REPO
WORKDIR $GIT_HOME/$REPO/src
RUN pip install -r requirements.txt
RUN python3 setup.py install

CMD [ "bash" ]
