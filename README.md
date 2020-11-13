# SatIOpsT: Satellite Image Oparations Toolbox
This package helps you to run various oparations on satellite images.Currently Under development.

### 1. Installation Process:
You need anaconda or miniconda to run this package. First install anaconda or miniconda in your PC, From anaconda navigator or anaconda terminal run:

    conda install gdal rasterio geopandas pandas numpy
    # After finish this installation install this package.
    pip install SatIOpsT

### 2. Usage:
**Read and Write image:**

    from satiopst import imgReadWrite
    img,meta=imgReadWrite.imgRead(r"C:\Users\subha\Documents\MechineLearning\s2\S2.tif","r")
    imgReadWrite.imgWrite(img,r"C:\Users\subha\Documents\MechineLearning\s2\S21.tif",meta)
    
**Image to Pandas dataframe and pandas dataframe to image conversion:**

    from satiopst.imageFrame import imagetoframe, frametoimage
    iframe= imagetoframe(img)
    img2=frametoimage(iframe, meta)
    
**Extract Pixel values according to class using polygon shapefile:**

    from satiopst.extracttraindata import extractbypolygon as ext
    traind=ext(r"C:\Users\subha\Documents\MechineLearning\s2\S2forClassification.tif",
           r"C:\Users\subha\Documents\MechineLearning\s2\trysinglemarged.shp","r","ClassID")
           
** Crop, mask and Layer Stack of satellite images:**

    from satiopst.utils import icrop, imask, layerStack
    crop=icrop(r"C:\Users\subha\Documents\MechineLearning\s2\S2forClassification.tif",
               r"C:\Users\subha\Documents\MechineLearning\s2\trysinglemarged.shp")
    
    mask=imask(r"C:\Users\subha\Documents\MechineLearning\s2\S2forClassification.tif",
               r"C:\Users\subha\Documents\MechineLearning\s2\trysinglemarged.shp",nodata=0)
    
    imglist=[r"C:\Users\subha\Documents\MechineLearning\L2A_T45QXE_A015074_20200125T044114\IMG_DATA\R20m\b1.jp2",
             r"C:\Users\subha\Documents\MechineLearning\L2A_T45QXE_A015074_20200125T044114\IMG_DATA\R20m\b2.jp2",
             r"C:\Users\subha\Documents\MechineLearning\L2A_T45QXE_A015074_20200125T044114\IMG_DATA\R20m\b3.jp2"]
    stacki,meta=layerStack(imglist)
    
### Contact:
https://github.com/SubhadipDatta/SatIOpsT