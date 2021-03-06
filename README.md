# Bayeux Pusher

This is a commandline tool to send a message to a [Bayeux 1.0](http://svn.cometd.com/trunk/bayeux/bayeux.html) compliant server. It can be a great tool to help test Bayeux server implementation as well.

Features

* Verbose mode to print out the HTTP requests sent and HTTP responses received
* Can do HANDSHAKE/CONNECT before sending the message. And then do the DISCONNECT request afterward. In this mode, you can control the message ID you use.
* Can skip HANDSHAKE/CONNECT/DISCONNECT completely and directly send the message to the server
* Support passing in authentication information as "ext" field in the HANDSHAKE request
* Support passing in authentication information through extra HTTP headers

You can run the tool with "-h" to see the help message

# Requirements

* PHP 5.2
* Supports [PHP Curl functions](http://www.php.net/manual/en/book.curl.php)
* Supports [PHP JSON functions](http://www.php.net/manual/en/ref.json.php)

# Installations

1. Download the script onto your machine
2. Make sure the script is in a directory that is in the $PATH
3. Make sure the script is executable
4. Make sure the php is in /usr/bin/php
