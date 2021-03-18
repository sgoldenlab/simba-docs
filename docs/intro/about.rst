What is SimBA?
================

Several excellent computational frameworks exist that enable high-throughput and consistent tracking of freely moving unmarked animals. Here we introduce and distribute a plug-and play pipeline that enabled users to use these pose-estimation approaches in combination with behavioral annotation and generation of supervised machine-learning behavioral predictive classifiers. We have developed this pipeline for the analysis of complex social behaviors, but have included the flexibility for users to generate predictive classifiers across other behavioral modalities with minimal effort and no specialized computational background.

SimBA does not require computer science and programing experience, and SimBA is optimized for wide-ranging video acquisition parameters and quality. SimBA is written for Microsoft Windows. We may be able to provide support and advice for specific use instances, especially if it benefits multiple users and advances the scope of SimBA. Feel free to post issues and bugs here or contact us directly and we'll work on squashing them as they appear. We hope that users will contribute to the community!

- The SimBA pipeline requires no programing knowledge

- Specialized commercial or custom-made equipment is not required

- Extensive annotations are not required

- The pipeline is flexible and can be used to create and validate classifiers for different behaviors and environments

- Currently included behavioral classifiers have been validated in mice and rats

- SimBA is written for Windows

SimBA provides several validated classifer libraries using videos filmed from above at 90° angle with pose-estimation data from 8 body parts per animal; please see our OSF repository for access to all files. SimBA now accepts any user-defined pose-estimation annotation schemes with the inclusion of the Flexible Annotation Module in v1.1. SimBA now supports maDLC and SLEAP for similar looking animals with the release of maDLC/SLEAP module in v1.2.

Installation note: SimBA can be installed either with TensorFlow compatability (for generating DeepLabCut, DeepPoseKit and SLEAP pose-estimation models), or without TensorFlow (for stand-alone use with classifiers and other functions). Please choose the appropriate branch for your needs, using pip install. More details are found in the Installation Documentation.

Listserv for release information: If you would like to receive notification for new releases of SimBA, please fill out this form and you will be added to the listserv.

