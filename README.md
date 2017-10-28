# ComputeFeatures
This repository contains the feature extraction code in our image search service.

## Requirements ##
This code is written in C++ and requires the following libraries:
- Caffe (already included)
- CUDA
- Anaconda
- OpenCV3
- boost
- zeromq

## Compile ##
- Compile the Caffe in the folder ./Features/CNN/external. Please configure the correct paths for libraries in the file ./Features/CNN/external/caffe/Makefile.config. More details can be found on [Caffe](http://caffe.berkeleyvision.org/) Website.
- Compile the feature extraction code. The Makefile is stored in: ./Features/CNN/ver2.

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


