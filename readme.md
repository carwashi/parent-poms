# parent-poms
This repo contains our maven parent poms.

## parent-pom
A maven parent pom to use for all Main Street Hub projects.  This parent pom
is unique in that it stores build artifacts in Amazon S3 using the aws-maven
extension instead of to a traditional maven repo like Sonatype or Artifactory.

## ecs-parent-pom
This pom adds the ability to easily build a Docker image from the primary
artifact of a maven build.  This pom encapsulates all of the info necessary to
build as well as publish the Docker image into Main Street Hub's private Docker
registry (hosted in ECR).

**Note:** it is assumed that the primary artifact of the maven build is a single
fat jar that contains all of it's dependencies as well as a manifest specifying
a main class.

## dropwizard-parent-pom
This pom adds the ability to easily build a Dropwizard application as a Docker
image.  The image is automatically configured to expose ports 8080 and 8081 to
the container host so that the web and admin ports can both be used.  In
addition, the arguments to the application command are set to
`server classpath://config.yaml`.  If necessary this can be overridden in a
child pom.
