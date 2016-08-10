Freeze Frame Program -- Nathan Majumder, Summer Wu, Fanhao Yang

Two options for freeze frame:
1. use -processVid option to simply freeze the image within the picture
	frame at a certain frame number. For all subsequent frames it will
	the frame will hold the frozen image
2. use -multipleFreezes option for more freedom to freeze and unfreeze
	multiple times. The code currently supports 3 freezes (the final
	freeze remains through the end of the video), and the code will
	require very slight modifications (in imgpro.cpp) for a different
	number

Both options take a single argument which is the number of frames in the input
video, but you MUST change a couple variables within the code depending on the
video. For -processVid, go to the "start_tracking" variable in the -processVid
code in imgpro.cpp (line 228 as of now) and change it from 0 to whatever frame
number you would like to freee at. For -multipleFreezes, go to the corresponding
section in imgpro.cpp (starting around line 259) and modify the startX and endX
variables, which are pretty self-explanatory. As stated above, right now it will
freeze 3 times and unfreeze 2 times, but to change this you must look at the code
below these variables in the loop through all the frames and add 'else if's for
your extra (or remove for less) freezes, copying the format used already.

examply command lines for each option are:

$ ./imgpro ../input ../output -processVid 200
$ ./imgpro ../input ../output -multipleFreezes 200

if you have 200 frames specified in the input directory and want the results to
be written to the output directory. Fully qualified path names are also fine.
Note, in practice you will probably want subdirectories in input/ and output/
because you may not specify an input directory that contains anything other than
the frames you want to process.

Ignore excess code and options for imgpro, the skeleton was taken from some
previous work. We are interested in these two 'else if's (for processVid and
multipleFreezes) in imgpro and the functions they call in R2Image.cpp and the
subsequent declarations in R2Image.h.

