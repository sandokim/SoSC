# SoSC
CVPR2025

Note that similar to MipNeRF360, we target images at resolutions in the 1-1.6K pixel range. 
For convenience, arbitrary-size inputs can be passed and will be automatically resized if their width exceeds 1600 pixels. 
We recommend to keep this behavior, but you may force training to use your higher-resolution images by setting -r 1.

The MipNeRF360 scenes are hosted by the paper authors [here](https://jonbarron.info/mipnerf360/). 

### Mip-NeRF 360: Dataset Pt.1 (360_v2.zip) / Dataset Pt.2 (360_extra_scenes.zip)

```
360_v2/
├── stump/
│   ├── sparse/
│   │   └── 0/
│   │       ├── points3D.bin
│   │       ├── images.bin
│   │       └── cameras.bin
│   ├── images/
│   ├── images_2/
│   ├── images_4/
│   ├── images_8/
│   └── poses_bounds.npy
├── room/
│   ├── sparse/
│   │   └── 0/
│   │       ├── points3D.bin
│   │       ├── images.bin
│   │       └── cameras.bin
│   ├── images/
│   ├── images_2/
│   ├── images_4/
│   ├── images_8/
│   └── poses_bounds.npy
├── kitchen/
│   ├── sparse/
│   │   └── 0/
│   │       ├── points3D.bin
│   │       ├── images.bin
│   │       └── cameras.bin
│   ├── images/
│   ├── images_2/
│   ├── images_4/
│   ├── images_8/
│   └── poses_bounds.npy
├── garden/
│   ├── sparse/
│   │   └── 0/
│   │       ├── points3D.bin
│   │       ├── images.bin
│   │       └── cameras.bin
│   ├── images/
│   ├── images_2/
│   ├── images_4/
│   ├── images_8/
│   └── poses_bounds.npy
├── counter/
│   ├── sparse/
│   │   └── 0/
│   │       ├── points3D.bin
│   │       ├── images.bin
│   │       └── cameras.bin
│   ├── images/
│   ├── images_2/
│   ├── images_4/
│   ├── images_8/
│   └── poses_bounds.npy
├── bonsai/
│   ├── sparse/
│   │   └── 0/
│   │       ├── points3D.bin
│   │       ├── images.bin
│   │       └── cameras.bin
│   ├── images/
│   ├── images_2/
│   ├── images_4/
│   ├── images_8/
│   └── poses_bounds.npy
├── bicycle/
│   ├── sparse/
│   │   └── 0/
│   │       ├── points3D.bin
│   │       ├── images.bin
│   │       └── cameras.bin
│   ├── images/
│   ├── images_2/
│   ├── images_4/
│   ├── images_8/
│   └── poses_bounds.npy
├── treehill.txt
└── flowers.txt
```



You can find our SfM data sets for Tanks&Temples and Deep Blending [here](https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/datasets/input/tandt_db.zip). 
### Tanks & Temples and Deep Blending Dataset Structure 
```
tandt_db/
├── db/
│ ├── drjohnson/
│ │ ├── images/
│ │ │ ├── IMG_6292.jpg
│ │ │ ├── IMG_6293.jpg
│ │ │ └── ...
│ │ └── sparse/
│ │ └── 0/
│ │ ├── cameras.bin
│ │ ├── images.bin
│ │ ├── points3D.bin
│ │ └── project.ini
│ └── playroom/
│ ├── images/
│ │ ├── DSC05572.jpg
│ │ ├── DSC05573.jpg
│ │ └── ...
│ └── sparse/
│ └── 0/
│ ├── cameras.bin
│ ├── images.bin
│ ├── points3D.bin
│ └── project.ini
└── tandt/
├── train/
│ ├── images/
│ │ ├── 00001.jpg
│ │ ├── 00002.jpg
│ │ └── ...
│ └── sparse/
│ └── 0/
│ ├── cameras.bin
│ ├── images.bin
│ ├── points3D.bin
│ └── project.ini
└── truck/
├── images/
│ ├── 000001.jpg
│ │ ├── 000002.jpg
│ └── ...
└── sparse/
└── 0/
├── cameras.bin
├── images.bin
├── points3D.bin
└── project.ini
```

If you do not provide an output model directory (-m), trained models are written to folders with randomized unique names inside the output directory. 
At this point, the trained models may be viewed with the real-time viewer (see further below).

