FROM java:8


ARG JMETER_VERSION=5.3

RUN wget http://mirror.its.dal.ca/apache//jmeter/binaries/apache-jmeter-${JMETER_VERSION}.tgz
RUN tar -xvzf apache-jmeter-${JMETER_VERSION}.tgz
RUN rm apache-jmeter-${JMETER_VERSION}.tgz

RUN mv apache-jmeter-${JMETER_VERSION} /jmeter

ENV JMETER_HOME /jmeter

# Add Jmeter to the Path
ENV PATH $JMETER_HOME/bin:$PATH

ADD test/${JMETER_TEST} test/${JMETER_TEST}

ADD test/user.properties test/user.properties

ENTRYPOINT jmeter -n -t test/${JMETER_TEST} -p test/user.properties