============================================
How to use tools to process videos in SimBA
============================================

We have developed video and image processing tools and incorporated them into the overall SimBA pipeline. However, many of the tools are useful on their own or in "one-off" situations. To make these easily accessible, the tools have been incorporated into their own space within the GUI, and are described below.


Shorten Videos
==============

This is a tool used to trim video lengths. The tool contains two different methods:

**Method 1** and **Method 2**.

    .. image:: /images/shortenvideos.PNG

Method 1
********

Use Method 1 to trim both the beginning and the end of the video.

Let's say we have a 2 minute long video and we want to get rid of the first 10 seconds, and the last 5 seconds.
We would start our video on at ``00:00:10``, and end the video at ``00:01:55``.

1. First, click on ``Browse File`` to select the video to trim.

2. Enter the start time in the ``Start at:`` entry box, in this case it will be *00:00:10*

3. Enter the end time in ``End at:`` entry box, in this case it will be *00:01:55*. The settings should look like the image below.

    .. image:: /images/shortenvideos1.PNG

4. Click ``Cut Video`` to trim the video and a new shorter video will be generated. The new shorter video will have a name of *Name of original video* + *_shorten* and will be located in the same folder as the original video.

    .. image:: /images/shortenvideos2.PNG


Method 2
********

Method 2 cuts of the beginning of the video. 

Let's say we have a 2 minute long video and we want to get rid of the first 20 seconds from the start of the video.

1. Enter the amount of time that needs to be trimmed from the start of the video in ``Seconds:``, in this case it will be *20*

    .. image:: /images/shortenvideos3.PNG

2. Click ``Cut Video`` to trim video and a new shorten video will be generated, the new video will have a name of *Name of original video* + *_shorten* and will be located in the same folder as the original video.

Clip video into multiple videos
===============================

This tool can help users to cut the videos into multiple clips/section.

1. Click on the ``Clip video into multiple videos`` from the ``Tools`` section.

    .. image:: /images/clipmulti1.png

2. Select the video that you want to split/clip by clicking ``Browse File``

    .. image:: /images/clipmulti2.png

3. Put in the number of output clips/sections that you want in ``# of clips``, and click ``Confirm``. Please note that if you put in the wrong number the first time, you can re-enter the number and click ``Confirm`` to change the table.

    .. image:: /images/clipmulti3.png

4. Then enter the ``Start Time`` and ``Stop Time`` in the following format ``HH:MM:SS``. For example, for a minute and 20 seconds it will be ``00:01:20``.

5. Once the table has been filled, click ``Clip video`` and the video will be output on the same folder path/ directory of your original video.

Crop Video
==========

This is a tool to crop videos.

    .. image:: /images/cropvideo.PNG

1. First, click on ``Browse File`` to select a video to crop.

2. Click on ``Crop Video`` and the following window ``Select ROI`` will pop up.

    .. image:: /images/cropvideo2.PNG

3. Use your mouse to *Left Click* on the video and drag the rectangle bounding box to contain the area of the video you wish to keep. *You can always left click and drag on the video to recrop your video*

    .. image:: /images/cropvideo3.PNG

4. Hit ``Enter`` **twice** and SimBA will crop the video. The new video will have a name of *Name of original video* + *_cropped* and will be located in the same folder as the original video.

    .. image:: /images/cropvideo4.PNG

Fixed Crop Videos
=================

This tool allows the user to crop once and apply the same dimension to the rest of the videos in the folder.

    .. image:: /images/fixcropvid.PNG

1. Under ``Video directory``, select the input video folder by clicking ``Browse Folder``.

2. Then, select an output folder.

3. Click on ``Confirm`` and an image will pop up, use your mouse to *Left Click* on the video and drag the rectangle bounding box to contain the area of the video you wish to keep. *You can always left click and drag on the video to recrop your video*

4. Hit ``Enter`` **twice** and SimBA will crop all the videos in the folder with the same coordinate. The new videos will have a name of *Name of original video* + *_cropped* and will be located in the output folder.

Multi-crop videos
=================

This is a tool to used to multi-crop videos. For example, if you recorded four different environments with a single camera, you can use this tool to split single recordings into 4 different videos. This tool operates on all videos in a folder that is defined by the user. The user is required to draw the number of defined rectangles on **each** of the videos in the specified folder.  

1. First, click on Multi-crop and the following menu will pop-open:

    .. image:: /images/Multi_crop_1.JPG

2. Next to *Video Folder*, click on ``Browse Folder`` and select a folder containing the videos you which to multi-crop.

3. Next to *Output folder*, click on ``Browse Folder`` and select a folder that should house the cropped output videos.

4. Next to *Video type*, type the file format of your input videos (e.g., mp4, avi etc).

5. Next to *# of crop*, type in the number of cropped videos you which to generate from each single input video (e.g., 4). Click on **Crop** to proceed. When you click on **Crop**, the first frame of the first video in the specified folder will be displayed, and the name of the video and rectangle number is printed overlaid:

    .. image:: /images/Multi_crop_example.gif

6. Left click the mouse and drag from the top left corner to the bottom right corner of the first video you wish to generate. When finished with the first video, press ``Enter``. Repeat this step for the next videos you wish to generate from Video 1. Once Video1 is complete, repeat these steps for all the videos in the user-specified *Video Folder*.

7. The cropped output videos will be located in the user-defined *Output folder* as defined in Step 3. 


Downsample video
================

This is a tool to downsample a video into smaller size and reduce the resolution of the video.

    .. image:: /images/downsamplevid.PNG

The downsample video tool has two options: **Customize Resolution** and **Default Resolution**.

Customize Resolution
*********************

Use this tool to downsample video into any height and width.

1. First, click on ``Browse File`` to select a video to downsample.

2. Then, enter any values in the ``Height`` and ``Width`` entry boxes.

    .. image:: /images/downsamplevid2.PNG

3. Click on ``Downsample to custom resolution`` to downsample the video. The new video will have a name of *Name of original video* + *_downsampled* and will be located in the same folder as the original video.

    .. image:: /images/downsamplevid3.PNG

Default resolution
******************

This tool allows the user to downsample a video quickly.

1. First, click on ``Browse File`` to select a video to downsample.

2. Tick on one of the resolution options.

3. Click on ``Downsample to default resolution`` and the video will downsample into the selected resolution. The video will be located in the same folder as the original video.


Get Coordinates (calibrate distance)
=====================================
This tool is to get the length (millimeter) per pixel of a video.

    .. image:: /images/getcoordtool.PNG

Let's say we want to find out the metric length per pixel of a video of a mouse in a cage, and we know the width of cage is 130 millimeters (it's a tight one).

1. First, click on ``Browse File`` to select a video.

2. Enter *130* in the ``Known length in real life(mm)`` entry box.

3. Click on ``Get Distance``, and the following window will pop up.

    .. image:: /images/getcoordtool2.PNG

.. note::
    When the frame is displayed, it may not be shown at the correct aspect ratio. To fix this, drag the window corner to the correct aspect ratio.

4. Use your mouse to double *Left click* at the left side of the cage and double *Left click* again on the right side of the cage. These are the known distance of 130 mm.

    .. image:: /images/getcoordtool3.PNG

.. tip::
    You can double click any point again to change the location of the point.

    .. image:: /images/getcoord.gif

5. Once two points are selected, hit ``Esc`` button. The millimeter per pixel value is printed in the main SimBA interface.

    .. image:: /images/getcoordtool4.PNG

Change formats
==============

This menu includes **Change image formats** and **Change video formats**

Change image formats
********************

This tool allows the user to select a folder containing multiple images and convert the formats.

    .. image:: /images/changeimageformat.PNG

1. Click on ``Browse Folder`` to select a folder that contains multiple images.

2. Choose the original format of the images in the selected folder.

3. Choose the desired output image format.

4. Click on ``Convert image file format``.

Change video format
********************

This tool allows the user to convert the file format of a single or multiple videos.  

    .. image:: /images/changevideoformat.PNG

Convert multiple videos
-----------------------

1. Click on ``Browse Folder`` to select the directory that contains the videos that you want to convert.

2. Enter the original file format (eg: mp4, flv, avi etc.) in the ``Input format`` entry box. **Note: do not put dots ('.') in the file format name (eg: mp4 or flv, etc)**.

3. Enter the desired output format in the ``Output format`` entry box .

4. Click on ``Convert multiple videos``.

Convert single video
--------------------

1. Click on ``Browse File`` to select a video to convert.

2. Choose one of the following ``Convert .avi to .mp4`` or ``Convert mp4 into Powerpoint supported format``

3. Click on ``Convert video format``.


`CLAHE enhance video <https://docs.opencv.org/3.4/d5/daf/tutorial_py_histogram_equalization.html>`_
====================================================================================================

1. Click on ``Browse File`` and select a video file.

2. Click ``Apply CLAHE``. The new video will have a name of *CLAHE_* *Name of original video*. The new file will be in a **.avi** format will be located in the same folder as the original video.

Superimpose frame numbers on video
===================================

This tool creates a video with the frame numbers printed on top of the video. 

1. Click on ``Superimpose frame numbers on video`` and a new window will pop up.

2. Select a video and click on ``Open``.

3. The new version of the video will be created with the name *Name of original video* + *_frame_no* and will be located in the same folder as the original video.

Convert to grayscale
====================

1. Click on ``Convert to grayscale`` and a new window will pop up.

2. Select video and click ``Open``.

3. The new greyscale version of the video will be created and have the name *Name of original video* + *_grayscale*. The new video will be located in the same folder as the original video.


Merge images to video
=====================

1. Click on ``Browse Folder`` to select a folder containing multiple frames.

2. Enter the input image format of the frames. Eg: if the image name is *Image001.PNG*, enter *PNG* in the ``Image format`` entry box.

3. Enter the desire output video format. Eg: if the video should be in *.mp4* file format, enter *mp4* in the ``Video format`` entry box.

4. Enter the desire frames per second in the ``fps`` entry box.

5. Enter the desired `bitrate <https://help.encoding.com/knowledge-base/article/understanding-bitrates-in-video-files/>`_ for the video in the ``Bitrate`` entry box.

6. Click on ``Merge Images`` to create the video.

Generate gifs
=============

1. Click on ``Browse File`` and select a video to convert to a GIF.

2. Enter the starting time of the GIF from the video in the ``Start times(s)`` entry box.

3. Enter the duration of the GIF in the ``Duration(s)`` entry box.

4. Enter the size of the GIF in the ``Width`` entry box. The output GIF will be scale automatically.

5. Click on ``Generate gif`` to create the gif.

Extract Frames
==============

The Extract frames menu has two options: **Extract defined frames**, **Extract frames**, and **Extract frames from seq files**.

Extract defined Frames
**********************

This tool allows users to extract frames from a video by inputting specific start- and end-frame numbers. This is useful if you want to extract a subset of frames from a larger video, without first needing to generate a new video of the desired length.

1. Click ``Browse File`` to select a video.

2. Enter the starting frame number in the ``Start Frame`` entry box.

3. Enter the ending frame number in the ``End Frame`` entry box.

4. Click on ``Extract Frames`` to extract the frames from the ``Start Frame`` to the ``End Frame``.

5. A folder with the video name will be generated and the all the extracted frames will be located in the folder. The frames will be in *.png* file format. 

Extract frames
**************

Use this tool to extract every frame from a single video or multiple videos.

Single video
------------

1. Click on ``Browse File`` to select a video file.

2. Click on ``Extract Frames(Single video)`` to extract every frame from the video.

3. A folder with the video name will be generated and the all the extracted frames will be located in the folder. The frames will be in *.png* file format. 

Multiple videos
---------------

1. Click on ``Browse Folder`` to select the folder with videos.

2. Click on ``Extract Frames(Multiple videos)`` to extract every frame from the video.

3. Folders with the video name will be generated and the all the extracted frames will be located in the folders. The frames will be in *.png* file format. 

Extract frames from seq files
*****************************

Use this tool to extract all the frames from a video in **seq** file format.

1. Click on ``Browse File`` to select a video.

2. Click on ``Extract All Frames`` to extract all the frames from the video.

3. A folder with the video name will be generated and the all the extracted frames will be located in the folder. The frames will be in *.png* file format.

Convert . seq files to .mp4 files
*********************************

Use this tool to convert .seq files to .mp4 files.

1. Click on ``Tools``, then ``Change formats``, and click on ``Change .seq to .mp4``.

2. A window will pop up and you can then navigate and select the video folder that contains the mp4's. 

3. The conversion progress can be followed through the progress bar printed in the terminal window. 

