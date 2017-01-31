RTSP-Server
===========
This module is designed to accept a number of sources to connect and
transmit audio and video streams.  
Clients can connect and send RTSP commands to receive RTP data.

This was designed to make rebroadcasting audio and video data over a
network simple.

## INSTALLATION
To install this module type the following:
```
   perl Makefile.PL
   make
   make test
   make install
```
To install debian jessie dependences:
```
Install enyevent
   sudo apt-get install libanyevent-perl
   sudo cpan AnyEvent::MPRPC::Client
   
Install moose
   sudo apt-get instal libmoose-perl
   sudo apt-get install libmoosex-getopt-perl
   
Install socket6
   sudo apt-get install libsocket6-perl

Clone from git
   git clone https://github.com/revmischa/rtsp-server

Then make, test and install
   perl Makefile.PL
   make
   make test
   make install

```

## RUNNING

Simply fire up the included rtsp-server.pl application and it will
listen for clients on port 554 (standard RTSP port), and source
streams on port 5545.

To begin sending video, you can use any client which supports the
ANNOUNCE and RECORD RTSP methods, such as [FFmpeg](https://www.ffmpeg.org/ffmpeg-protocols.html#rtsp):

`ffmpeg -re -i /input.avi -f rtsp -muxdelay 0.1 rtsp://12.34.56.78:5545/abc`

You should then be able to play that stream with any decent media
player. Just point it at rtsp://12.34.56.78/abc

If you don't want to run it as root, you may specify non-priviliged
ports with `--clientport/-c` and `--sourceport/-s`

## TODO:

Priv dropping, authentication, client encoder, stats, tests

## DEPENDENCIES

This module requires these other modules and libraries:

  Moose, AnyEvent::Socket, AnyEvent::Handle

## COPYRIGHT AND LICENCE

Copyright (C) 2014 by Mischa Spiegelmock

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself, either Perl version 5.10.0 or,
at your option, any later version of Perl 5 you may have available.


