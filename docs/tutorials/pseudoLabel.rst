=========================================
'Pseudo-labelling' behaviors in SimBA
=========================================

Annotating frames can be the most time-consuming aspect of supervised machine learning, and computational tools are developed at pace to address this time-sink. For example, pose-estimation tools such as `DeepLabCut <https://github.com/DeepLabCut/DeepLabCut>`_ and `SLEAP <https://sleap.ai/>`_, promote workflows that significantly decrease the required body-part labelling time; DeepLabCut asks users to `extract/refine/merge body-part outlier <https://github.com/DeepLabCut/DeepLabCut/blob/master/docs/UseOverviewGuide.md#optional-active-learning----network-refinement---extract-outlier-frames-from-a-video>`_, and SLEAP asks users to take a computer-assisted labelling approach and run `non-optimized models and correct their prediction results until they are perfected <https://sleap.ai/tutorials/initial-training.html>`_. `JAABA (Janelia Automatic Animal Behavior Annotator) <http://jaaba.sourceforge.net/>`_, another excellent and  popular tool for machine classification of animal behavior, is also based on a workflow composed of `iterative re-training of classifiers based on machine-generated predictions <http://jaaba.sourceforge.net/Training.html#Predictions>`_.

These workflows are built upon feeding computer-generated predictions, initially with human oversight, back into the model as training examples and thus improving its predictions through more data, all while spending significantly less time annotating images. This is approach is **not** restricted to animal tracking / pose-estimation, but can also use for improving the performance of behavior classifiers in SimBA.

.. note::
    If you want to label behaviors, including the use of pseudo-labelling methods in SimBA, you **must** extract the frames for the videos you wish to label. The frame extraction ensures that the frame number, the behavioral label, and the displayed frame during the annotation-work are all align. For more information on how to extract frames in SimBA, see the `Scenario 1 Part 2 - Import more tracking data into project <https://github.com/sgoldenlab/simba/blob/master/docs/tutorial.md#step-2-optional--import-more-dlc-tracking-data-or-videos>`_, or the generic `Tools menu tutorials <https://github.com/sgoldenlab/simba/blob/master/docs/Tutorial_tools.md#extract-frames>`_.

Step 1: Generating initial machine predictions in SimBA
========================================================

Before using the 'pseudo-labelling' tool in SimBA, we need to generate some machine learning classification predictions for videos that has not been used to train the model. Detailed information on how to generate such machine classifications can be found in the `Scenario 1 - building classifiers from scratch <https://github.com/sgoldenlab/simba/blob/master/docs/Scenario1.md>`_ tutorial. More documentation on how to generate machine predictions can also be found in the `generic SimBA documentation <https://github.com/sgoldenlab/simba/blob/master/docs/tutorial.md>`_. We recommend reading the of these tutorials up to and including `Step 8 - Run Machine Model <https://github.com/sgoldenlab/simba/blob/master/docs/tutorial.md#step-8-run-machine-model>`_.

When you've successfully generated your machine predictions, you will have CSV files containing your machine classifications, with one CSV file for each video in your project, in your ``project_folder/csv/machine_results`` directory. We will now use the ``Pseudo-labelling`` tool in SimBA to look at these machine classifications and correct them when necessary.

Step 2: Using Pseudo-labelling in SimBA
=========================================

After `loading your project in SimBA <https://github.com/sgoldenlab/simba/blob/master/docs/tutorial.md#step-1-load-project-config>`_, navigate to the ``Label behavior`` tab and uou should see the following menu:

    .. image:: /images/Pseudo_1.PNG

1. In the sub-menu titled ``Pseudo Labelling``, there is a entry-box called ``Frame folder``. Click on ``Browse`` and select to the folder containing the frames for the video you wish to correct the machine predictions for.

2. Beneath the ``Frame folder`` entry-box, there is a sub-menu titled ``Threshold``. Within this sub-menu there are entry-boxes, with one entry-box for each classifier in the project. in each of these entry-boxes, insert a value between ``0.00`` and ``1.00``. These numbers  represents the classification threshold for each classifier. If you are unfamiliar with ``classification thresholds``, then you can read more about them in the tutorial for `Scenario 1 - Step 8 <https://github.com/sgoldenlab/simba/blob/master/docs/tutorial.md#step-8-run-machine-model>`_, or `Scenario 2 - Part3 <https://github.com/sgoldenlab/simba/blob/master/docs/Scenario2.md#part-3-run-the-classifier-on-new-data>`_. In brief, the ``classification threshold`` represents how sure the computer has to be before it classifies a frame as containing the behavior. A ``classification threshold`` value of 0.80, for example, would mean that the computer has to be 80% sure that the frame contains the behavior to classify it as containing the behaviour. When the ``classification threshold(s)`` have all been entered, click the ``Correct label`` button.

3. After clicking the ``Correct label`` button, a window will pop open that looks similar to this:

    .. image:: /images/Visualize_05.PNG

This interface is near-identical to the labelling interface described in the `SimBA behavioral annotator GUI tutorial <https://github.com/sgoldenlab/simba/blob/master/docs/labelling_aggression_tutorial.md>`_ and users should head over to `this tutoral <https://github.com/sgoldenlab/simba/blob/master/docs/labelling_aggression_tutorial.md>`_ for detailed instructions on how to use this interface to label behaviors.

This interface, however, contains one key difference: the ``Check Behavior`` menu has been pre-filled with the models classification results according to the threshold the user set in ``Threshold`` menu described in above:

    .. image:: /images/Visualize_06.PNG

Now navigate the frames and the machine model predictions, by using the arrow keys, and view the video by clicking the ``Open video`` button. Proceed to add any ticks in tick-boxes that may be missing ticks in the ``Check behavior`` menu, or remove ticks that are incorrectly present. Again, please see the `SimBA behavioral annotator GUI tutorial <https://github.com/sgoldenlab/simba/blob/master/docs/labelling_aggression_tutorial.md>`_ for more information on how to use this annotator interface. Once you have finished correcting the machine-generated predictions, click on ``Save csv``. A new CSV, named after the video, with the user-corrected labels, is then saved in the ``project_folder/csv/targets_inserted`` folder and can be used, together with other annotated CSV files, to generate new machine classification models for the behaviors of interest.

.. note::
    If the representations of the machine predictions (e.g., the tick-boxes) are too sensitive (e.g., too many boxes are ticked when they shouldn't be ticked) or too weak (e.g., too many boxes are un-ticked when they should be ticked), consider closing the labelling interface window, and revise the thresholds in the ``Pseudo Labelling - thresholds`` sub-menu. If too many boxes are ticked for a specific behavior classifier, then decrease the threshold for this classifier. If too few boxes are ticked, then increase the threshold for the specific classifier. When you have titrated the thresholds, re-start the labelling interface by clicking the ``Correct labels`` button.

If you want to correct further videos with machine-generated predictions, then close the labelling interface, and navigate back to the sub-menu titled ``Pseudo Labelling`` and the ``Frame folder`` entry-box and browse and select a new folder containing frames from a different video.

.. note::
    What happens during this process, is that SimBA grabs the CSV file associated with the name of the frame folder from the ``project_folder/csv/machine_results`` directory when the user clicks the ``Correct labels`` button. Moreover, when the user clicks the ``Save csv`` button, a new CSV file is generated in the ``project_folder/csv/targets_inserted`` folder, and this new file is identical to the file in the  ``project_folder/csv/machine_results`` folder, except that the relevant prediction columns have been amended to reflect the users-introduced changes indicated through the ``Check behavior`` tick-box menu.

Congrats! You have now successfully generated more machine model training data using ``Pseudo-labelling`` in SimBA.

For details tutorial on how to generate machine classifiers based on the pseudo-labelled data, and all other CSV data files in your ``project_folder/csv/targets_inserted`` directory,  see the `Train Machine Model <https://github.com/sgoldenlab/simba/blob/master/docs/tutorial.md#step-7-train-machine-model>`_ tutorial.



