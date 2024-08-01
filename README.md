# SoSC
CVPR2025

Note that similar to MipNeRF360, we target images at resolutions in the 1-1.6K pixel range. 
For convenience, arbitrary-size inputs can be passed and will be automatically resized if their width exceeds 1600 pixels. 
We recommend to keep this behavior, but you may force training to use your higher-resolution images by setting -r 1.

The MipNeRF360 scenes are hosted by the paper authors [here](https://jonbarron.info/mipnerf360/). 
You can find our SfM data sets for Tanks&Temples and Deep Blending [here](https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/datasets/input/tandt_db.zip). 
If you do not provide an output model directory (-m), trained models are written to folders with randomized unique names inside the output directory. 
At this point, the trained models may be viewed with the real-time viewer (see further below).

