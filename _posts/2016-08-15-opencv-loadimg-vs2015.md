---
layout: post
title: OpenCV C++: How to succesfully read image in Visual Studio 2015
categories: opencv
---

# OpenCV C++ - How to succesfully read image in Visual Studio 2015

Recently I started to work with OpenCV again after along time not touching it (about 2 years and a half). One problem that block me is
that my freaking super-simple code CAN NOT read an image successfully!

So I downloaded and build the (maybe) latest OpenCV from source on my Windows machine, targeting to work with Visual Studio (VS) 2015 in C++.
After alot of troubles and headache, finally I built and installed OpenCV succesfully and my "Hello World" project was compile succesfully
on VS 2015. (Thanks to [this awesome article](http://dogfeatherdesign.com/opencv-3-0-microsoft-visual-studio-2015-cmake-and-c/) ).

The code is simple: Just read an image in display in a window. Pretty typical for a "hello world" OpenCV project.

```c
#include "opencv2\highgui\highgui.hpp"
int main()
{
	Mat img = imread("mypic.jpg", CV_LOAD_IMAGE_UNCHANGED);
	if (img.empty())
	{
		cout << "Error: Image cannot be loaded!\n";
		return -1;
	}

	namedWindow("My Image", CV_WINDOW_AUTOSIZE);
	imshow("My Image", img);

	waitKey(0);

	destroyWindow("My Image");

  return 0;
}
```

Everything was going fine until I start to run the program from VS debug menu: the `img` is always empty! But when I double click on the
executable file, which has been built, it runs well!

It looks like when the program is run from inside VS, it cannot find the image in its current directory. And the solution is quite simple:
Because in VS, when you run the program in debug mode, the working directory is set to `$(ProjectDir)`, which is your project
directory, by default configuration. But the executable file is put in the build output directory, which can be referred as `$(OutDir)`.
So my solution is simply change the default working directory of the project in VS to `$(OutDir)`.

In VS, right click on the project. Select *Properties*, select *Debugging*. In debugging config, change the *Working Directory* to 
`$(OutDir).

Actually I'm not a guys who familiar with Visual Studio, have never use it in any work. So it took me days just to fix this simple problem.
This is like a quick note for my future self can have something to refer :)
