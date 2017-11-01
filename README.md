# ComputeFeatures
This repository contains the feature extraction code in our Memex image search service. It includes the ability to
    
    1. Extract features of images from a specic layer from a pre-trained neural network.
    2. Store all the features in a format that is usable by the image serach service.

In our image search service, we use the code to extract the features of database images and store all the features on the disk. Later, [ScalableLSH](https://github.com/Minione/ScalableLSH) will deploy the image search service based on the database image features.

## Requirements ##
This code is written in C++ and requires the following libraries:
- Caffe (already included)
- CUDA
- Anaconda
- OpenCV3
- boost
- zeromq

## Compile ##
### A. Compile Caffe ###
We frist compile the Caffe included in the folder ./Features/CNN/external. Please configure the correct paths for libraries in the file ./Features/CNN/external/caffe/Makefile.config. More details can be found on [Caffe](http://caffe.berkeleyvision.org/) Website.
### B. Compile the feature extraction code ###
Then we compile the feature extraction code. The Makefile is: ./Features/CNN/ver2/Makefile. Since some libraries are not installed in the default path in our environment, we include the library paths in the example Makefile explicitly. You will need to manually modify the Makefile with correct library paths in your own environment to successfully compile the code.

## Usage ##
```
./computeFeatures.bin \
    -i <imgsdir> "Input directory of images" \
    -q <imgslst> "List of images relative to input directory" \
    -n <network-path> "Path to corresponding caffemodel" \
    -m <model-path> "Path to corresponding caffemodel" \
    -l <layer> "CNN layer to extract features from" \
    -o <outdir> "Output directory" \
    -y <normalize> "Enable feature L2 normalization. 0: disable. 1: enable" \
    -t <output-type> "Output format [txt/lmdb/hdf5]" \
    -p <pool> "Pool the features from different regions. empty: no pooling. avg: avg pooling" \
    -f <foregorund> "Extract the features of the foreground (1) or background (0)"
```


