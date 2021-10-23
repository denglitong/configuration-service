FROM openjdk:8-jdk-alpine
RUN apk update && apk upgrade && apk add netcat-openbsd && apk add wget \
    && apk add bind-tools
RUN mkdir -p /usr/local/configuration-service
RUN echo $JAVA_HOME
RUN wget --no-check-certificate --no-cookies \
    --header "Cookie: oraclelicense=accept-securebackup-cookie" \
    "http://download.oracle.com/otn-pub/java/jce/8/jce_policy-8.zip"
RUN unzip jce_policy-8.zip && \
    rm jce_policy-8.zip && \
    cp UnlimitedJCEPolicyJDK8/*.jar /usr/lib/jvm/java-1.8-openjdk/jre/lib/security/
ADD @project.build.finalName@.jar /usr/local/configuration-service/
ADD run.sh run.sh
RUN chmod +x run.sh
CMD ./run.sh
