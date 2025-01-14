# Docker Apache NiFi - [![](https://badge.imagelayers.io/mkobit/nifi:latest.svg)](https://imagelayers.io/?images=mkobit/nifi:latest 'Get your own badge on imagelayers.io')

This is an unofficial [Apache NiFi](https://nifi.apache.org/) Docker image

## Base image

Apache NiFi requires a Java runtime. Starting with the *0.4.0* release, I am producing multiple images that each use a different base Java images.

Both the *0.3.0* and *0.2.1* versions use [java/8](https://hub.docker.com/_/java/) as their base image.

## Latest release and image

The latest version of NiFi is the *0.4.0* release (December 11th 2015). The release notes can be found [here](https://cwiki.apache.org/confluence/display/NIFI/Release+Notes#ReleaseNotes-Version0.4.0).

The *latest* image is the same as the *0.4.0-openjdk-8* image.

## Docker Hub

This image is available on Docker Hub at [mkobit/nifi](https://hub.docker.com/r/mkobit/nifi/).

### Testing out NiFi

To run this image and play around with NiFi:

1. Pull `latest` image

    ```console
    docker pull mkobit/nifi
    ```

2. Run image and expose default ports to host.

    ```console
    # --rm : remove container on exit
    # -i : interactive
    # -t : allocate TTY
    # -p : publish each container port to host port. format: ip:hostPort:containerPort | ip::containerPort | hostPort:containerPort | containerPort
    docker run -it --rm -p 8080-8081:8080-8081 mkobit/nifi
    ```

3. Go to default local NiFi endpoint in browser - [http://localhost:8080/nifi/](http://localhost:8080/nifi/)

### Extending

This can easily be used as a base image to create NiFi applications. One way would be to build a [NAR](https://nifi.apache.org/developer-guide.html) with extensions built upon the framework and including it in your own image. I recommend reading the [Developer's Guide](https://nifi.apache.org/developer-guide.html) if you want to head down this route.

### Volumes

These are the default locations as specified by the Apache NiFi properties. You can find more information about each of these repositories on the [System Administration Guide](https://nifi.apache.org/docs/nifi-docs/html/administration-guide.html)

- `$NIFI_HOME/database_repository` - user access and flow controller history
- `$NIFI_HOME/flowfile_repository` - FlowFile attributes and current state in the system
- `$NIFI_HOME/content_repository` - content for all the FlowFiles in the system
- `$NIFI_HOME/provenance_repository` - information related to Data Provenance

## Official Apache NiFi Documentation and Guides

* [Overview](https://nifi.apache.org/docs.html)
* [User Guide](https://nifi.apache.org/docs/nifi-docs/html/user-guide.html)
* [Expression Language](https://nifi.apache.org/docs/nifi-docs/html/expression-language-guide.html)
* [Development Quickstart](https://nifi.apache.org/quickstart.html)
* [Developer's Guide](https://nifi.apache.org/developer-guide.html)
* [System Administrator](https://nifi.apache.org/docs/nifi-docs/html/administration-guide.html)

## ListenHTTP Processor

The standard library has a built-in processor for an HTTP endpoint listener. That processor is named [`ListenHTTP`](https://nifi.apache.org/docs/nifi-docs/components/org.apache.nifi.processors.standard.ListenHTTP/index.html). You should set the **Listening Port** to 8081 if you follow the instructions above to run this image.

## Usage

This image can either be used as a base image for building on top of NiFi or just to experiment with the tool.

## Issues

If you have any problems, comments, or questions with this image, feel free to reach out at [mkobit/docker-nifi](https://github.com/mkobit/docker-nifi). If you have Apache NiFi specific questions or concerns you can reach out on one of the [community mailing lists](https://nifi.apache.org/mailing_lists.html).

## Contributing to this repository

Contributing changes to this repository is extremely welcome. If it is a larger change, it is usually best to discuss your plans first. Please see the [Github issues](https://github.com/mkobit/docker-nifi/issues) to see if a similar issue already exists.

## Contributing to NiFi

The Apache NiFi source code can be found on Github at [apache/nifi](https://github.com/apache/nifi). You can browse issues related to the project on the [Apache NiFi Jira](https://issues.apache.org/jira/browse/NIFI/).
