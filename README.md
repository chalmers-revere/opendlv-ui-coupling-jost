# opendlv-ui-coupling-jost
This project contains the code for display the JOST panel in the Rhino truck on a local webpage. 

## Table of Contents
* [Description](#description)
* [Dependencies](#dependencies)
* [Usage](#usage)
* [Building](#building)
* [License](#license)

## Description

This repository is a part of a bigger project transfering the JOST panels CAN signals into opendlv messages and then displaying these on an webinterface using javascript, simultaniously as the panel is active in the truck. Transfering the signals from CAN to opendlv is done in a microservice not available on github. 
The cpp folder contains files for opening a od4 session and listening to opendlv standard messages. This then sends the messages to the webinterface.
The js folder contains the code for actually running and displaying the webinterface. 


## Dependencies
No dependencies! You just need a modern JavaScript-engine to interpret `libcluon.js`.

* [libcluon](https://github.com/chrberger/libcluon) - [![License: GPLv3](https://img.shields.io/badge/license-GPL--3-blue.svg
)](https://www.gnu.org/licenses/gpl-3.0.txt)

## Building and Usage
After pulling this repository, to build this microservice, simply build it using Docker:

```
docker build -f Dockerfile.amd64 -t cluon-jost-display:v0.0.1 .
docker build -f Dockerfile.amd64 -t cluon-jost-display-js:v0.0.1 .
```

Then, you can run your microservice:

```
docker run --rm -ti --net=host cluon-jost-display:v0.0.1 cluon-jost-display --cid=111
docker run --rm -ti --net=host cluon-jost-display-js:v0.0.1 --cid=111
```
Now, you can see the display by pointing your web-browser to http://localhost:8082.

## License

* This project is released under the terms of the MIT License.
