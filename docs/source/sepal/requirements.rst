Module Requirements
===================

Initial Setup
^^^^^^^^^^^^^
SEPAL is closely linked to Google Earth Engine (GEE), a Google-powered Earth-observation cloud-computing platform, as it integrates many of its functionalities. Consequently,to run SEPAL-SDG 15.4.2 :sub:`beta` you will need to have **connected SEPAL and GEE accounts**.

Before getting started with SEPAL-SDG 15.4.2 :sub:`beta` you need:

- To **Create a SEPAL account** , please follow the `registration steps described here <https://docs.sepal.io/en/latest/setup/register.html#sign-up-to-sepal>`_ and then familiarize yourself with the tool by exploring its interface.
- To **Create a Google Earth Engine (GEE) account** , please follow these `steps <https://docs.sepal.io/en/latest/setup/gee.html#create-a-gee-account>`_ and don't forget to `initialize the home folder <https://docs.sepal.io/en/latest/setup/gee.html#initialize-the-home-folder>`_.
- To **Connect your SEPAL and GEE accounts**, follow the `instructions described here <https://docs.sepal.io/en/latest/setup/gee.html#connection-between-gee-and-sepal>`_


Data Requirements
^^^^^^^^^^^^^^^^^
SDG Indicator 15.4.2 requires several spatial data inputs to be computed namely :

- **A Mountain Area Map** 
  
For the purposes of standardization and international comparability of indicators values, SDG Indicator 15.4.2 adheres to the UNEP-WCMC mountain definition (UNEP-WCMC, 2002). The UNEP-WCMC method defines total global mountain area as the sum of seven classes (commonly known as ‘Kapos mountain classes’), based on elevation, slope and local elevation ranges parameters. This mountain area is subdivided into bioclimatic belts (Nival, Alpine, Montane, and Remaining Mountain Area) based on average temperatures as defined by Körner et al. (2011). A global mountain area map based on these definitions and methodologies has been developed by FAO and is used by default by SEPAL-SDG 15.4.2 :sub:`beta` as part of the computations. 

- **A National Administrative Boundary for the country of interest** 
  
SEPAL-SDG 15.4.2 :sub:`beta` has been conceived to facilitate the computation of SDG Indicator 15.4.2 at country level. To facilitate this , SEPAL-SDG 15.4.2 :sub:`beta` uses a default global data source for national boundaries - the FAO GAUL Global Administrative Unit Layers 2015 data set. However, the tool also allows national agencies to use their own national country boundary layer if available. 

- **A collection of Land Cover Maps for the country of interest** 
  
Land cover maps represent spatially the physical coverage of the Earth's surface into different types (classes) e.g. forests, grasslands, croplands, lakes, wetlands. This data serves different functions for SDG Indicator 15.4.2: 
  
**In Sub-Indicator 15.4.2a**, land cover is used to categorize land into green and non-green cover areas. 
  
**In Sub-Indicator 15.4.2b**, land cover is used to identify areas where changes in the type of land cover may indicate a decline or loss of biodiversity, mountain ecosystem functions or services that are considered desirable in a local or national context. 
 
The collection of land cover maps to compute this indicator should be available from the year **2000**. SEPAL SDG 15.4.2 :sub:`beta` facilitates national authorities to use relevant national or regional land cover datasets. 
Similar to the national administrative boundary dataset, SEPAL-SDG 15.4.2 :sub:`beta` provides access to default land cover datasets, selected by FAO to compute the indicator when national datasets are not available see the :ref:`Data Sources section <DataSources>`
  
.. Note:: 
   Country-defined datasets must be made available as GEE assets as an `image collection <https://developers.google.com/earth-engine/guides/ic_creating>`_ for SEPAL-SDG 15.4.2       :sub:`beta` to access it. This will be demonstrated in the next section of the tutorial. 
 


Uploading files into Google Earth Engine
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Once you have created accounts in both SEPAL and GEE and linked them accordingly,you will now learn how to upload files into GEE.
GEE accepts a number of data formats namely: shapefiles, raster images,and CSV tables. This section will demonstrate the uploading of the different data types into the platform.

1. To upload files,go to the **Assets** tab in the top left panel in the **Earth Engine Code Editor** page. Clicking on it will open the **Asset Manager** as shown below:

.. image:: ../_static/sepal/uploading_data.PNG
   :align: center
   :width: 800
   :alt: GEE_Interface

2. Clicking on the  **New** button will list the acceptable options, including **Raster** (Geotiffs or TFRecords), **Vector** (Shapefiles) and **Data tables** (CSV files), which will be described in the following subsections.

2.1.Uploading Vector Files
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. Note::
   In SEPAL-SDG 15.4.2 :sub:`beta` custom country boundaries need to be uploaded in vector format.


1. To do so, choose the **Shapefiles** option in the drop-down list. A pop-up window will appear prompting you to navigate to the location of your data.
2. Select the file you want to upload from your computer.You can either upload the vector data as a compressed file :code:`.zip` or :code:`.shp` .Remember that a :code:`.shp` file alone is not sufficient and must be accompanied with all the other files describing the vector data i.e. :code:`.shx`, :code:`.dbf` and :code:`.prj`.

.. imag ../_static/sepal/uploading_vector.PNG
   :align: center
   :width: 400
   :alt: Vector_File

Any file errors will be highlighted by the uploader, as in the example below:

.. imag ../_static/sepal/vector_error_warning.PNG
   :align: center
   :width: 400
   :alt: Vector_Error

3. Once all files are loaded correctly, the upload progress is displayed in the task manager. Typically this process takes a couple of minutes depending on the size of the dataset. The progress of the upload is displayed in the task manager as shown below:

.. image../_static/sepal/uploading_progress.PNG
   :align: center
   :width: 400
   :alt: vector_uploading_process

4. Once completed,the uploaded assets will be listed in the Assets List under the Assets tab. If not displayed, click on the **Refresh** button.

.. image../_static/sepal/vector_asset_list.PNG
   :align: center
   :width: 300
   :alt: Assets_listed

5. Clicking on the asset will open an asset details window :The asset is ready for use. You can now visualize, share or delete it accordingly 

.. image../_static/sepal/asset_details_gee.PNG
   :align: center
   :width: 800
   :alt: asset_popup


Uploading Raster Files
~~~~~~~~~~~~~~~~~~~~~~~

When computing SDG 15.4.2, land cover maps are uploaded as raster files and  made available as `image collections <https://developers.google.com/earth-engine/guides/ic_creating>`_ to be usable in SEPAL-SDG 15.4.2 :sub:`beta` . 

1. To upload the rasters, select **New > Image Upload**.

2. In the pop-up window, select the file you want to upload from your computer (compatible formats include :code:`.tiff`, :code:`.tif`, :code:`.json`, :code:`.tfrecord` or :code:`.tfrecord.gz`; By default, the asset will be named after the basename.However,the name of your asset can be changed in the next text field.

.. Note:: 
   Please ensure that the name includes the reference year of the land cover map e.g Nepal_2000 for Nepal's landcover map for 2000.

.. image:: ../_static/sepal/uploading_rasters.PNG
   :align: center
   :width: 400
   :alt: Geotiff_upload

3. Repeat step 2 for each of the land cover maps.


Creating an Image Collection
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

An Image Collection is a stack or sequence of images.Once all the land cover maps have been successfuly uploaded,we now need to create an image collection for the images to be usable in computation as explained earlier.
To create an Image Collection;

1. Click on the **Assets Tab** and then New > **Image collection.**

.. image:: ../_static/sepal/image_collection.png
   :align: center
   :width: 300
   :alt: Image-collection

2. This will open the image collection constructor that will first prompt you to name your image collection as shown below:

.. image:: ../_static/sepal/naming_image_collection.png
   :align: center
   :width: 400
   :alt: Naming Image-collection

3. Once the image collection is created, you can load it by pasting an Earth Engine asset ID into the Image Collection constructor (Ensure the **Edit** button is on) or by simply dragging the individual assets to the image collection in the assets list as shown below:

.. image:: ../_static/sepal/naming_image_collection.png
   :align: center
   :width: 700
   :alt: Creating Image-collection

4. Repeat this for each asset. Clicking on the Image Collection(in the asset list) should now show all the images that are contained in that collection and should now be ready to be used in your analysis or visualization.
 
.. image:: ../_static/sepal/image_collection_result.png
   :align: center
   :width: 700
   :alt: Image-collection-result


Uploading  Table files
~~~~~~~~~~~~~~~~~~~~~~
Tabular data can be uploaded into Google Earth Engine as comma-separated values (CSV) or Javascript Object Notation(JSON) files :code:`.csv`, or :code:`.json`). To upload a tabular files do the following:

1. Select New > **csv file upload**. 
2. In the pop-up window that appears, select the file you want to upload from your computer 

.. image:: ../_static/sepal/uploading_csv.PNG
   :align: center
   :width: 400
   :alt: Geotiff_upload


.. tip::
   Now that all your files are uploaded in GEE, you can now access and use your assets in SEPAL. As you have already established a connection between your GEE and SEPAL accounts, all your assets are synced and available for you in SEPAL. You will be able to select them from the dropdown or copy/paste them directly from GEE when prompted in SEPAL-SDG 15.4.2 :sub:`beta`


.. _Vector_File_Manager:

Uploading vector files into SEPAL via the Vector File Manager.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Apart from Google Earth Engine,you can directly upload your tabular datasets ( vector or CSV tables) into the SEPAL environment through the Vector File Manager.Read more on the `Vector File Manager here <https://docs.sepal.io/en/latest/modules/dwn/vector_manager.html>`_.

1. Navigate to the **Apps** tab (located on the left of the SEPAL interface) and find the **Vector File Manager** by either navigating through the app list or using the search bar.
2. Clicking on the app opens the vector file manager as shown below:
   
.. image:: ../_static/sepal/uploading_csv.PNG
   :align: center
   :width: 800
   :alt: Vector File Manager Interface

3. Clicking on the drop down arrow allows you to select the table type.(Accepted formats are shapefiles :code:`.shp` and table file :code:`.csv`)
4. Choose the shapefile option and click on the :code:`📎` icon to navigate to your files and choose all appropriate files and click :guilabel:`Import`.

.. image:: ../_static/sepal/uploading_csv.PNG
   :align: center
   :width: 1000
   :alt:   Uploading Vector Files.

5. The vector file manager notifies you when the importation is complete and shows its location as follows:
   
.. image:: ../_static/sepal/importation_complete.PNG
   :align: center
   :width: 1000
   :alt: Vector File Upload Notification

6. To locate the file you just uploaded into SEPAL, Click on the Module_Results > AOI in the Home page:
   
.. image:: ../_static/sepal/vector_location.PNG
   :align: center
   :width: 450
   :alt: Vector File Location


The vector files you just uploaded are now within the SEPAL environment and can be used when required.


.. seealso:: The methods are explained above should suffice for our case. However,since SEPAL’s built-in tools for uploading and downloading are limited, large amounts of data should be uploaded or downloaded using an FTP solution.More on this can be found `here <https://docs.sepal.io/en/latest/setup/filezilla.html#>`_.

