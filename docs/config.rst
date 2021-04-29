=====================
Configuration Options
=====================

.. toctree::
   :maxdepth: 2
   :caption: Contents:


Simulation setup options
########################

The section that's relevant for the simulation setup should look something like this:

.. code-block:: yaml

   binning_options:
      block_size: 10 # Number of trajectories to be processed in blocks
      center_freq: 1 # How frequently do we add new Voronoi centers?
      max_centers: 300 # Maximum number of Voronoi centers to be added
      traj_per_bin: 100 # Number of trajectories per Voronoi center
   path_options: # this entire section should be automatically set by the tool
      WESTPA_path: /home/USER/westpa
      bng_path: /home/USER/apps/anaconda3/lib/python3.7/site-packages/bionetgen/bng-linux
      bngl_file: /home/USER/webng/testing/test.bngl
      sim_name: /home/USER/webng/testing/test # you can adjust sim folder here
   propagator_options:
      pcoords: # These should match observables in your model
      - Atot
      - Btot
      propagator_type: libRoadRunner # this is the suggested propagator
   sampling_options:
      dimensions: 2 # Dimensionality of the WESTPA progress coordinates
      max_iter: 10 # Maximum number of WE iterations
      pcoord_length: 10 # Number of data points per WE iteration
      tau: 100 # Resampling frequency

you can change various aspects of the simulation setup in this file.

Analysis options
################

When you first create a setup configuration file like :code:`mysim.yaml`, you will see
an analysis section like this

.. code-block:: yaml
    :linenos:

   analyses:
      enabled: false
      average:
         dimensions: null # you can limit the tool to the first N dimensions
         enabled: false # this needs to be set to true to run the analysis 
         first-iter: null # first iteration to start the averaging
         last-iter: null # first iteration to end the averaging
         mapper-iter: null # the iteration to pull the voronoi bin mapper from, last iteration by default
         normalize: false # normalizes the distributions
         output: average.png # output file name 
         plot-energy: false # plots -ln of probabilies
         plot-opts: # various plotting options like font sizes and line width
            name-font-size: 12
            voronoi-col: 0.75
            voronoi-lw: 1
         plot-voronoi: false # true if you want to plot voronoi centers
         smoothing: 0.5 # the amount of smoothing to apply
         work-path: /home/USER/webng/testing/test/analysis # the folder to run the analysis under
      evolution:
         avg_window: null # number of iterations to average for each point in the plot
         dimensions: null # you can limit the tool to the first N dimensions
         enabled: false # this needs to be set to true to run the analysis
         normalize: false # normalizes the distributions
         output: evolution.png # output file name 
         plot-energy: false # plots -ln of probabilies
         plot-opts: # various plotting options like font sizes and line width
            name-font-size: 12
         work-path: /home/USER/webng/testing/test/analysis # the folder to run the analysis under


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`