FROM maven:3.9.9-eclipse-temurin-21-jammy as BUILD_IMAGE
RUN git clone https://github.com/hkhcoder/vprofile-project.git
RUN cd vprofile-project && git checkout containers && mvn install


FROM tomcat:10-jdk21
LABEL "Project"="Vprofile"
LABEL "Author"="Manash"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]

# this is a multistage docker file and we create multistage docker file to reduce the size of our image.
# in multi stage docker file we build the source code in different image and then copy the build to original image.

