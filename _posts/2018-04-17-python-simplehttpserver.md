---
layout: post
title: Using Python HTTP server to serve your directory content
categories: others
---

Python standard library includes a simple HTTP server module that can be quickly used to have a HTTP server running on your machine. It can be very handy in somecases, for example you need to serve the files in one of your folder so you can download it via HTTP.

To serve the content of a folder, just change the current working directory to that folder and run the command:

Python 2:

    python -m SimpleHTTPServer 8000

Python 3:

    python -m http.server 8000

The files in your folder is now available at http://localhost:8000/ .

Do note that this is not recommended for production because it only implements basic security checks.

