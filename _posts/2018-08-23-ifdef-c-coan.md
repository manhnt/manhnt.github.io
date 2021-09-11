---
layout: post
title: Removing ifdef directives in C code with Coan
categories: programming_technique
---


## Installation

Home page of the project: http://coan2.sourceforge.net/index.php


Download latest version from https://sourceforge.net/projects/coan2/files/v6.0.1/


For Ubuntu, download DEB file and install by dpkg command:


    sudo dpkg -i coan_6.0.1-for-Ubuntu_14.04_amd64.deb


## Usage

Basic command:

    coan source -V -DVALID_MACRO original_source.c > output.c


Check the [man page](http://coan2.sourceforge.net/coan_man_1.html) for list of full options.


