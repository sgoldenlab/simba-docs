======================
IBANGS ML Social Behavior Workshop Tutorial
======================

This is a step by step tutorial to start using SimBA to create behavioral classifiers for the IBANGS ML Social Behavior Workshop. For more information
about the menus and options and their use cases, see the
`SimBA Scenario tutorials <https://github.com/sgoldenlab/simba#scenario-tutorials>`_

Logistics prior to workshop start
=================================
Prior to the workshop please familiar yourself with the folder structure provided. 

.. note::

    If you are in this workshop, the files are in **C:\Golden**. There is a shortcut to the folder structure located on the desktop named **SimBA-IBANG**, double click on it to get access to **C:\\Golden**.
    
    .. image:: /images/folderstruct.JPG

- ``Classifier`` : This folder contains pre-trained classifiers from the Golden Lab (*Attack.sav*, *Defensive.sav*) and the classifier settings used for training (*model_settings.csv*).

- ``raw_videos`` : This folder contains preprocessed videos that will be used in **Part 1**

- ``Videos`` : This folder contains the videos that will be used in **Part 2** to train a classifier.

- ``Tracking_data`` : This folder contains the tracking data of the videos that are generated using DeepLabCut.

- ``targets_inserted``: This folder contains our hand annotated csvs for training a classifier in **Part 2**


Please click `here <https://osf.io/dg385/>`_ to download our sample data to follow through this tutorial. 
    

Starting simba
===============
We will be using miniconda in this workshop tutorial and the environment has been set up to use.

    1. Open up command prompt, type in ``conda activate simbaenv`` and press ``"Enter"``.

    2. Type ``simba`` and press ``"Enter"``.


Part 1: Video Preprocessing with SimBA
=======================================
This step will preprocess the videos for SimBA to analyze. There are multiple ways you can do this:
    - `Built-in Tools in SimBA <./tutorial_tools.html>`_
    - `Batch videos processing <./batch_videos.html>`_

In this workshop we are going to use batch videos pipeline.

Step 1: Folder Selection
***************************


    .. image:: /images/processvideo.PNG

1. In the main SimBA window click on ``Process Videos`` --> ``Batch pre-process videos``. The window shown below will display.

    .. image:: /images/batchprocessvideo1.PNG

2. Under **Folder Selection** heading and next to ``Video directory``, click on ``Browse Folder`` and navigate to **C:/Golden/raw_videos** and click on ``Select Folder``.

    .. image:: /images/ibangselectfolder.PNG

3. Next to ``Output Directory``, click on ``Browse Folder`` and create a folder **C:/Golden/output** that should store the processed videos and click on ``Select Folder``.

4. Click to ``Confirm`` the two selected directories.

.. warning::

    - Please make sure there are no spaces in your folder names or video names, use underscores if needed.

    - If you select the same video directory as the output directory, your video will be **overwritten**. Best practice is to select a different output directory.



Step 2: Select parameters
*****************************

1. Once you select ``Confirm``, a table listing the videos in the ``Video directory`` folder will auto-generate and display. This sequence of videos will now be processed with the parameters you selected, starting with the cropping function.

    .. image:: /images/ibangbatchp2.PNG

2. To crop your videos, click on the ``Crop`` button. A frame from the video will pop up. Left click on the frame and drag the rectangular bounding box to mark the region of the video you wish to keep. Once the rectangle is marked, double tap "Enter" on your keyboard. *(The relevant crop button will turn red once you have selected to crop a video)*

    .. image:: /images/cropvideoroi.gif

3. Please refer to the image below as input parameters:

    .. image:: /images/ibangvideotable.PNG

    - To trim a specific video, check the ``Shorten`` box and enter the **Start Time** and  **End Time** in the **HH:MM:SS** format. In our case, try to trim all the videos to 10 seconds by entering 0 for ``Start Time``  and 10 for ``End time`` .

    - To downsample a specific video, check the ``Downsample`` box and enter the **Width** and **Height** in pixels as shown in the image.

    - To change a specific video to grayscale, check the ``Grayscale`` box.

    - To superimpose the specific frame numbers onto the frames of the video, check on the ``Add Frame #`` box. For an example output video with frame numbers overlaid, click `here <https://youtu.be/TMQmNr8Ssyg>`_

    - We are not going to do this as it is computationally expensive but to apply CLAHE, check on the ``CLAHE`` box. For more information on CLAHE, click `here <https://docs.opencv.org/master/d5/daf/tutorial_py_histogram_equalization.html>`_

4. In the first row of the table, there are ``Select All`` checkboxes. Use these checkboxes to apply a manipulation to all of the videos in the folder.

.. note::
    We know that the `Select All` checkbox might be slightly off position in the table. We will work on fixing it soon.

Step 3: Execute
********************

1. Once all the parameters are set, click on ``Execute``.

2. The final output videos will be saved in the ``Output Directory`` that you selected in *Step 1*.

    .. image:: /images/ibangvid.PNG

3. A subfolder in the ``Output Directory`` called **tmp** will contain the step-by-step processed videos.

4. The **process_archive** folder contains a **.txt** file that lists the processes that were run.

5. The **Output Directory** will contain all the final processed videos.


Part 2: Create Project
======================
Now that we have the videos in the optimal format, we can start using SimBA. In this part, we are going to create an "Attack" classifier.

Step 1: Generate Project Config
********************************

In this step you create your main project folder which will contain all of the required sub-directories.

1. In the main SimBA window, click on ``File`` and and ``Create a new project``. The following windows will pop up.

    .. image:: /images/createproject.PNG

2. Navigate to the ``[ Generate project config ]`` tab. Under **General Settings**, click on the ``Browse Folder`` on ``Project Path`` and select **C:/Golden** and click ``Select Folder``

3. ``Project Name`` is the name of your project, in this case type in **ibangs_attack**

    .. note::
            *Keep in mind that the project name cannot contain spaces. Instead use underscore "_"*

4. Under `SML Settings`, put in the number of predictive classifiers that you wish to create. In this case, put **1**.

5. Click ``Add Classifier`` and it creates a row as shown in the following image. In each entry box, fill in the name of the behavior that you want to classify. In this case type **Attack**. 

    .. image:: /images/classifier1.PNG


6. ``Type of Tracking`` allows the user to choose (same color) multi-animal tracking or the classic tracking, and we are going to select ``classic tracking``.

7. ``Animal Settings`` is the number of animals and body parts that that the pose estimation tracking data contains.
The default for **SimBA** is 2 animals and 16 body parts ( ``2 animals, 16bp``). There are a few other - ** yet not validated** - options, accessible in the dropdown menu.
Here, we are going to select ``2 animals, 14bp``.

8. Your windows should look like the image as shown below.

    .. image:: /images/ibangcreateproject.PNG

8. Click on ``Generate Project Config`` to generate your project. The project folder will be located in **C:/Golden/ibangs_attack**.

Step 2: Import videos into project folder for training
*******************************************

In this step, there are options to import either one or multiple videos. The imported videos are used for visualizing
predictions and standardizing distances across videos by calculating metric distances from pixel distances. We are going to import **multiple** videos.

    .. image:: /images/Import_videos.PNG

Import multiple videos
#########################

1. Navigate to the ``[ Import videos into project folder ]`` tab.

2. Under the ``Import multiple videos`` heading, click on ``Browse Folder`` to select a folder that contains all the videos that you wish to import into your project. In our case, we go to **C:/Golden/Videos**

3. Enter the file type of your videos, ``mp4`` in the ``Video type`` entry box.

4. Click on ``Import multiple videos``.

5. The videos will be imported into **C:/Golden/ibangs_attack/project_folder/videos**


Step 3: Import Tracking Data
*****************************

In this step, you will import your pose-estimation tracking data. We support tracking from most common pose estimation platforms and these can be imported from:  `click here <./third_party_annot.html>`_
In this workshop, we are going to use DeepLabCut's tracking data and they will be in **.csv** format.

For more information about using DeepLabCut to generate tracking data:

    - `DeepLabCut Github page <https://github.com/DeepLabCut/DeepLabCut>`_
    - `DeepLabCut Preprint <https://arxiv.org/abs/1804.03142>`_
    - `DeepLabCut Community on Gitter <https://gitter.im/DeepLabCut/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge>`_

    .. image:: /images/importcsv.PNG

Import tracking data (.csv)
###########################

1. Navigate to the ``[ Import tracking data ]`` tab. Under the ``Import tracking data`` click on the ``File type`` drop down menu.

2. From the drop down menu, .csv files = ``CSV (DLC/DeepPoseKit)``.

3. To import multiple files, choose the folder that contains the files by clicking ``Browse Folder``. In our case, go to *C:/Golden/Tracking_data*, then click ``Import csv to project folder``.

4. The csvs will be located in **C:/Golden/ibangs_attack/project_folder/csv/input_csv**


Part 3: Load project
=====================
To use SimBA, you will load the project you have created.

Step 1: Load Project Config
****************************

In this step you will load the *project_config.ini* file that was created. It is located in **C:/Golden/ibangs_attack/project_folder**

    .. Note::
        A project_config.ini should always be loaded before any other process.

1. In the main SimBA window, click on ``File`` and ``Load project``. The following windows will pop up.


    .. image:: /images/loadprojectini.PNG


2. Click on ``Browse File``. Then, go to **C:/Golden/ibangs_attack/project_folder**  and click on *project_config.ini* file. Once this step is completed, it should look like the following, and you should no longer see the text **No file selected**.


    .. image:: /images/ibangloadproject.PNG


    In this image, you can see the **C:/Golden** is my selected working directory, **ibangs_attack** is my project name, and the last two sections of the folder path is always going to be **project_folder/project_config.ini**.

3. Click on ``Load Project``.

4. The following window will pop out.

    .. image:: /images/ibangloadproject2.PNG


Step 2: Set video parameters
*****************************
Meta data such as FPS and resolution are automatically pulled for your videos. 

In order to standardize your arena size, you will specify a known distance in your videos. SimBA then calculates the pixels per millimeter for each video.

You will be using a tool that requires the known distance between two points (e.g., the cage width or the cage height) in order to calculate **pixels per millimeter**.
The real life distance between the two points is called ``Distance in mm``.

    .. image:: /images/setvidparameter.PNG

1. Under **Set video parameters(distances,resolution,etc.)**, the entry box named ``Distance in mm`` is the known distance
between two points in the videos in millimeters. If the known distance is the same in all the videos in the project,
then enter the value *(e.g,: 245)* and click on ``Auto populate Distance in mm in tables``.
and it will auto-populate the table in the next step (see below). If you leave the `Distance in mm` entry box empty,
the known distance will default to zero and you will fill in the value for each video individually.

2. In this case, we are going to leave ``Known distance (mm)`` empty and click on ``Set Video Parameters``. The following will pop up.

    .. image:: /images/ibangppm.PNG

3. We have imported 3 videos and their names are listed on the ``Video`` column. In our case, the ``Distance in mm`` for the videos are the following:

    - **Box4-20200705T1421-1425**  = ``190``
    - **RI_02_8788**               = ``190``
    - **CSDS04712701**             = ``127``

4.Enter the values in the entry boxes sand click on ``Update distance_in_mm`` and this will update the whole table.

5. Next, to get the ``Pixels/mm`` for the first video, click on ``Video1`` and the following window will pop up.
The window that pops up displays the first frame of ``Video1``.


    .. image:: /images/getcoord1.PNG

6. Now, double **left** click to select two points that defines the known distance in real life.

    .. image:: /images/getcoord2.PNG


7. If you misplaced one or both of the dots, you can double click on either of the dots to place them somewhere else in
the image. Once you are done, hit ``Esc``.


    .. image:: /images/getcoord.gif


8. If every step is done correctly, the ``Pixels/mm`` column in the table should populate with the number of pixels
that represent one millimeter,

    .. image:: /images/ibangvidtab2.JPG


9. Repeat the steps for every video in the table, and once it is done, click on ``Save Data``.
This will generate a csv file named **video_info.csv** in ``/project_folder/log`` folder that contains a table with your video meta data.

Step 3: Outlier Correction
***************************

Outlier correction is used to correct gross tracking inaccuracies by detecting outliers based on movements and locations
of body parts in relation to the animal body length. For more details, please click `here <https://github.com/sgoldenlab/simba/blob/master/misc/Outlier_settings.pdf>`_

    .. image:: /images/outliercorrection.PNG

1. Under ``Outlier correction`` click on ``Settings``, and the following window will pop up. The image shows the settings we used in our lab.

    .. image:: /images/ibangoutlier.PNG

2. Make sure your settings matches the image. Enter ``1.5`` for ``Location criterion`` and ``0.7`` for ``Movement criterion``

3. For ``Median or Mean`` select ``mean``, and hit ``Confirm``.

4. Click ``Run outlier correction``.

5. This step will correct the outliers and store the new csvs in **C:/Golden/ibangs_attack/project_folder/csv/outlier_corrected_movement_location**. If you are confident with your tracking data you can skip outlier correction by clicking ``Skip outlier correction (CAUTION)``, but we do not recommend it. 

Step 4: Extract Features
************************

Based on the coordinates of body parts in each frame - and the frame rate and the pixels per millimeter values - the feature extraction step calculates a large set of features per frame (~500) used for behavioral classification.
Features are values such as metric distances between body parts, angles, areas, movement, paths, and their deviations and rank in individual frames and across rolling windows.
This set of features will depend on the body-parts tracked during pose-estimation (which is defined when creating the project).

Click `here <https://github.com/sgoldenlab/simba/blob/master/misc/Feature_description.csv>`_ for an example list of features when tracking 2 mice and 16 body parts.

Click `here <https://github.com/sgoldenlab/simba/blob/master/misc/features_user_defined_pose_config.csv>`_ for example list of features for user defined pose config.

Click `here <https://github.com/sgoldenlab/simba/blob/master/docs/extractFeatures.md>`_ for user-defined feature extraction script.

1. Click on ``Extract Features``.

Step 5: Label Behavior
************************

This step is used to label the behaviors in each frames of a video. This data will be concatenated with the features and used for creating behavioral classifiers. 

There are two options, one is to start a **new video annotation** and one is to **continue on where you last left off**.
Both are essentially the same, except the latter will start with the frame where you last saved.
For example, one day, you started a new video by clicking ``Select video (create new video annotation)``
and you feel tired and sick of annotating the videos. You can now click ``Generate/Save`` button to save your work for your coworker to continue.
Your coworker can continue by clicking ` Select folder with frames(continue existing video annotation)`
and select the the video folder that you have annotated half way and take it from there!


1. Click on ``Select video``. In your project folder navigate to the ``/project_folder/videos/`` folder,
and you should select the videos that you wish to annotate.


    .. image:: /images/labelbe.PNG


2. Please click `here <./b_annotation.html>`_ to learn how to use the behavior annotation interface.

3. Once finished, click on ``Generate/Save`` and it will generate a new *.csv* file in **/csv/targets_inserted** folder.

Step 6: Train Machine Model
****************************

This step is used for training new machine models for behavioral classifications. 

.. note::
    If you import existing models, you can skip this step and go straight to **Step 8** to run machine models on new video data.

Train single model
###################
For more details on the training parameters please click `here <https://github.com/sgoldenlab/simba/blob/master/docs/tutorial.md#step-7-train-machine-model>`_

1. Click on ``Settings`` and the following window will pop up.

    .. image:: /images/machinemodelsettings.PNG


.. note::
    If you have a .csv file containing hyper-parameter meta data, you can import this file by clicking on ``Browse File``
    and then click on ``Load``. This will autofill all the hyper-parameter entry boxes and model evaluation settings.

2. Under ``Load Metadata``, click on ``Browse File`` and navigate to *C:\Golden\Classifier* and select the *model_settings.csv* and click ``Load``. It will fill up the information as shown as the image below.

    .. image:: /images/ibangtrainsettings.PNG

6. Click on the ``Save settings into global environment`` button to save your settings into the *project_config.ini* file and use the settings to train a single model.

7. Alternatively, click on the ``Save settings for specific model`` button to save the settings for one model. To generate multiple models - for either multiple different behaviors and/or using multiple different hyper-parameters - re-define the Machine model settings and click on ``Save settings for specific model`` again. Each time the ``Save settings for specific model`` is clicked, a new config file is generated in the */project_folder/configs* folder. In the next step (see below), a model for each config file will be created if pressing the **Train multiple models, one for each saved settings** button.

8. Now, we will replace the csvs in the **C:/Golden/ibangs_attack/project_folder/csv/targets_inserted** with the Golden Lab annotated csvs in **C:/Golden/targets_inserted**.

9. Then click on ``Train single model from global environment``.


Step 7: Model Validation before running machine model on new data
##########################################################

The user can validate each model *( saved in .sav format)* file. In this validation step the user specifies the path to
a previously created model in .sav file format, and a .csv file containing the features extracted from a video. This process
will (i) run the classifications on the video, and (ii) create a video with the predictions overlaid together with a gantt plot showing predicted behavioral bouts.
Click `here <https://youtu.be/UOLSj7DGKRo>`_ for an example validation video.

1. Click ``Browse File`` and select the *project_config.ini* file and click ``Load Project``.

2. Under **[Run machine model]** tab --> **validate Model on Single Video**, select a features file (Box4-20200705T1421-1425.csv). It is located in ``project_folder/csv/features_extracted``.

    .. image:: /images/validatemodel_graph1.PNG

3. Under ``Select model file``, click on ``Browse File`` to select the  *Attack.sav file* from **C:/Golden/Classifier**.

4. Click on  ``Run Model``.

5. Once, it is completed, it should print *"Predictions generated."*, now you can click on ``Generate plot``. A graph window and a frame window will pop up.

    - ``Graph window``: model prediction probability versus frame numbers will be plotted. The graph is interactive - click on the graph and the frame window will display the selected frames.

    - ``Frame window``: Frames of the chosen video with controls.

    .. image:: /images/validategraph1.PNG

7. As you click on points on the graph, the selected frame will pop up in the adjacent window. There will be a red line to show the points that you have clicked.

    .. image:: /images/validategraph2.PNG

8. Once it jumps to the desired frame, you can navigate through the frames to determine if the behavior is present. This step is to find the optimal threshold to validate your model.

    .. image:: /images/validategraph.gif

9. Once the threshold is determined, enter the threshold into the ``Discrimination threshold`` entry box and the desire minimum behavior bouth length into the ``Minimum behavior bout lenght(ms)`` entrybox. Note: we recommend using a minimum duration of 0ms and following this with Kleinberg Smoothing as described further down. 

    - ``Discrimination threshold``: The level of probability required to define that the frame belongs to the target class. Accepts a float value between 0.0-1.0. For example, if set to 0.50, then all frames with a probability of containing the behavior of 0.5 or above will be classified as containing the behavior. For more information on classification threshold, click `here <https://www.scikit-yb.org/en/latest/api/classifier/threshold.html>`_

    - ``Minimum behavior bout length (ms)``: The minimum length of a classified behavioral bout. **Example**: The random forest makes the following attack predictions for 9 consecutive frames in a 50 fps video: 1,1,1,1,0,1,1,1,1. This would mean, if we don't have a minimum bout length, that the animals fought for 80ms (4 frames), took a break for 20ms (1 frame), then fought again for another 80ms (4 frames). You may want to classify this as a single 180ms attack bout rather than two separate 80ms attack bouts. With this setting you can do this. If the minimum behavior bout length is set to 20, any interruption in the behavior that is 20ms or shorter will be removed and the behavioral sequence above will be re-classified as: 1,1,1,1,1,1,1,1,1 - and instead classified as a single 180ms attack bout.

10. Click ``Validate`` to validate your model. **Note that this step will take a long time as it will generate a lot of frames.**

Step 8: Run Machine Model
******************************

This step runs behavioral classifiers on new data. 

    .. image:: /images/runrfmodel.PNG

1.  Under the **Run Machine Model** heading, click on ``Model Selection``. The following window with the classifier names defined in the *project_config.ini* file will pop up.

    .. image:: /images/ibangattk.PNG


2. Click on ``Browse File`` and select the *Attack.sav* file from *C:/Golden/Classifier*.

3. Once all the models have been chosen, click on ``Set Model`` to save the paths.

4. Fill in the ``Discrimination threshold``.

    - ``Discrimination threshold``: The level of probability required to define that the frame belongs to the target class that you found in step 7.

5. Fill in the ``Minimum behavior bout length``.

    - ``Minimum behavior bout length (ms)``:  Your desired minimum bout length.

6. Click on ``Set model(s)`` and then click on ``Run RF Model`` to run the machine model on the new data.

Step 9: Analyze Machine Results
********************************

Access this menu through the ``Load project`` menu and the ``Run machine model`` tab. This step performs summary analyses and presents descriptive statistics in .csv file format. There are three forms of summary analyses: ``Analyze``, ``Analyze distance/velocity``, and ``Analyze severity``.

    .. image:: /images/ibangmachineresult.JPG

    - ``Analyze machine prediction``: This button generates descriptive statistics for each predictive classifier in the project, including the total time, the number of frames, total number of ‘bouts’, mean and median bout interval, time to first occurrence, and mean and median interval between each bout. A date-time stamped output csv file with the data is saved in the ``/project_folder/log`` folder.

    - ``Analyze distance/velocity``: This button generates descriptive statistics for mean and median movements and distances between animals. The date-time stamped output csv file with the data is saved in the ``/project_folder/log`` folder.


Step 10: Sklearn Visualization
*******************************

These steps generate visualizations of features and machine learning classification results. This includes images and videos of the animals with prediction overlays, gantt plots, line plots, paths plots and data plots. In this step the different frames can also be merged into video mp4 format. 

    .. image:: /images/visualization_11_20.PNG

1. Under the **Sklearn visualization** heading, check on the box and click on ``Visualize classification results``.

   - ``Generate video``: This generates a video of the classification result

   - ``Generate frame``: This generates frames(images) of the classification result

    .. note::
        Generating frames is required if you want to merge frames into videos in the future.

This step grabs the frames of the videos in the project, and draws circles at the location of the tracked body parts, the convex hull of the animal, and prints the behavioral predictions on top of the frame. For an example, click `here <https://www.youtube.com/watch?v=7AVUWz71rG4&t=519s>`_

Step 11: Visualizations
************************

The user can also create a range of plots: **gantt plot**, **Data plot**, **Path plot**, **Distance plot**, and **Heatmap**.

    .. image:: /images/visualizations.PNG

Gantt plot
##########

Gantt plot generates gantt plots that display the length and frequencies of behavioral bouts for all the videos in the project.

    .. image:: /images/gantt_plot.gif

1. Under the **Gantt plot** heading, click on ``Generate Gantt plot`` and gantt plot frames will be generated in the ``project_folder/frames/output/gantt_plots`` folder.

Data plot
##########

Generates 'live' data plot frames for all of the videos in the project that display current distances and velocities. 

    .. image:: /images/dataplot.gif

1. Under the **Data plot** heading, click on ``Generate Data plot`` and data plot frames will be generated in the ``project_folder/frames/output/live_data_table`` folder.

Path plot
##########

Generates path plots displaying the current location of the animal trajectories, and location and severity of attack behavior, for all of the videos in the project.

    .. image:: /images/pathplot.gif

1. Under the **Path plot** heading, fill in the following user defined values.

    - ``Max Lines``: Integer specifying the max number of lines depicting the path of the animals. For example, if 100, the most recent 100 movements of animal 1 and animal 2 will be plotted as lines.

    - ``Severity Scale``: Integer specifying the scale on which to classify 'severity'. For example, if set to 10, all frames containing attack behavior will be classified from 1 to 10 (see above).

    - ``Bodyparts``: String to specify the bodyparts  tracked in the path plot. For example, if Nose_1 and Centroid_2, the nose of animal 1 and the centroid of animal 2 will be represented in the path plot.

    - ``plot_severity``: Tick this box to include color-coded circles on the path plot that signify the location and severity of attack interactions.

2. Click on ``Generate Path plot``, and path plot frames will be generated in the ``project_folder/frames/output/path_plots`` folder.

Distance plot
##########

Generates distance line plots between two body parts for all of the videos in the project.

    .. image:: /images/distance_plot.gif

1. Fill in the ``Body part 1`` and ``Body part 2``

    - ``Body part 1``: String that specifies the the bodypart of animal 1. Eg., Nose_1

    - ``Body part 2``: String that specifies the the bodypart of animal 1. Eg., Nose_2

2. Click on ``Generate Distance plot``, and the distance plot frames will be generated in the ``project_folder/frames/output/line_plot`` folder.

Heatmap
########

Generates heatmap of behavior that happened in the video.

To generate heatmaps, SimBA needs several user-defined variables:

    - ``Bin size(mm)`` : Pose-estimation coupled with supervised machine learning in SimBA gives information on the location of an event at the single pixel resolution, which is too-high of a resolution to be useful in heatmap generation. In this entry box, insert an integer value (e.g., 100) that dictates, in pixels, how big a location is. For example, if the user inserts *100*, and the video is filmed using 1000x1000 pixels, then SimBA will generate a heatmap based on 10x10 locations (each being 100x100 pixels large).

    - ``max`` (integer, or auto): How many color increments on the heatmap that should be generated. For example, if the user inputs *11*, then a 11-point scale will be created (as in the gifs above). If the user inserts auto in this entry box, then SimBA will calculate the ideal number of increments automatically for each video.

    - ``Color Palette`` : Which color pallette to use to plot the heatmap. See the gifs above for different output examples.

    - ``Target``: Which target behavior to plot in the heatmap. As the number of behavioral target events increment in a specific location, the color representing that region changes.

    - ``Bodypart``: To determine the location of the event in the video, SimBA uses a single body-part coordinate. Specify which body-part to use here.

    - ``Save last image only``: Users can either choose to generate a "heatmap video" for every video in your project. These videos contain one frame for every frame in your video. Alternative, users may want to generate a **single image** representing the final heatmap and all of the events in each video - with one png for every video in your project. If you'd like to generate single images, tick this box. If you do not tick this box, then videos will be generated (which is significantly more time-consuming).

2. Click ``Generate heatmap`` to generate heatmap of the target behavior. For more information on heatmaps based on behavioral events in SimBA - check the `tutorial for scenario 2 - visualizing machine predictions <https://github.com/sgoldenlab/simba/blob/master/docs/Scenario2.md#part-5--visualizing-machine-predictions>`_

Step 12: Merge Frames
*********************

Merge all the generated plots from the previous step into a single frame and generate a **video** as an **output**.

    .. image:: /images/mergeframes_new.PNG

    .. image:: /images/mergeplot.gif

.. note::
    All the frames must be generated in the previous step for this to work. This step combines all the frames(images) that are generated and merge them together and make a video.**

1. Check on the plot that you wish to merge together and output as a single video.

2. Under **Merge Frames**, click ``Merge Frames`` and frames with all the generated plots will be combined and saved in the ``project_folder/frames/output/merged`` folder in a video format.


Other cool stuff
=================

    - `SHAP <./shap.html>`_
    - `Kleinberg smoothing <./kleinberg.html>`_
    - `FSTTC <./fsttc.html>`_
    - `ROI <./roi_tutorial.html>`_
