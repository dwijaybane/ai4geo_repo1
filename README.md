# ai4geo_repo1


## DATASET
The ground reference data were collected by the PlantVillage team, and Radiant Earth Foundation curated the training dataset after inspecting and selecting more than 4,000 fields from the original ground reference data. The dataset has been split into training and test sets (3,286 in the train and 1,402 in the test).

The dataset is cataloged in four tiles. These tiles are smaller than the original Sentinel-2 tile that has been clipped and chipped to the geographical area that labels have been collected.

Each tile has:
- a) 13 multi-band observations throughout the growing season. Each observation includes 12 bands from Sentinel-2 L2A product, and a cloud probability layer. The twelve bands are [B01, B02, B03, B04, B05, B06, B07, B08, B8A, B09, B11, B12]. The cloud probability layer is a product of the Sentinel-2 atmospheric correction algorithm (Sen2Cor) and provides an estimated cloud probability (0-100%) per pixel. All of the bands are mapped to a common 10 m spatial resolution grid.;
- b) A raster layer indicating the crop ID for the fields in the training set;
- c) A raster layer indicating field IDs for the fields (both training and test sets). Fields with a crop ID of 0 are the test fields.

[Challenge Page](https://zindi.africa/competitions/iclr-workshop-challenge-2-radiant-earth-computer-vision-for-crop-recognition/data)
[CMR NASA KENYA CROP DATASET](https://cmr.earthdata.nasa.gov/search/concepts/C2781412688-MLHUB.html#)
[AWS S3 Bucket](https://registry.opendata.aws/radiant-mlhub/)

- Accessing and Downloading the Dataset (Make sure you have AWS CLI installed beforehand)
```
aws s3 ls --no-sign-request s3://radiant-mlhub/kenya-crop-challenge/data/
aws s3 cp --no-sign-request s3://radiant-mlhub/kenya-crop-challenge/data/ ./data/ --recursive
# Or you can download each tile separately
aws s3 cp --no-sign-request s3://radiant-mlhub/kenya-crop-challenge/data/2/ ./data/2/ --recursive
```

## ENV
- Create a conda environment and install the dependencies
```
conda create -n ai4geo python=3.9 -c conda-forge
conda activate ai4geo
conda install ipython jupyter -c conda-forge
conda install rasterio numpy matplotlib scipy scikit-image scikit-learn libgdal=3.6.3 -c conda-forge
conda install pandas geopandas fiona -c conda-forge
pip install torch==1.13.1+cu117 torchvision==0.14.1+cu117 torchaudio==0.13.1 --extra-index-url https://download.pytorch.org/whl/cu117

```
