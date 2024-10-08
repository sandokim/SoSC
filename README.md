# SoSC
CVPR2025

## Environment Setups
Conda environment:
```bash
conda env create --file environment.yml
conda activate SparseGS
```
We suggest using **CUDA 12** but CUDA 11 should work. You may need to change the cudatoolkit and pytorch version in the .yml file. 

-----------

Note that similar to MipNeRF360, we target images at resolutions in the 1-1.6K pixel range. 
For convenience, arbitrary-size inputs can be passed and will be automatically resized if their width exceeds 1600 pixels. 
We recommend to keep this behavior, but you may force training to use your higher-resolution images by setting -r 1.

## Mip-NeRF 360: Dataset Pt.1 (360_v2.zip) / Dataset Pt.2 (360_extra_scenes.zip)

The MipNeRF360 scenes are hosted by the paper authors [here](https://jonbarron.info/mipnerf360/). 

If you run the original gaussian_splatting/train.py, it will automatically generate an SfM point cloud for the target scene located at `sparse/0/points3D.ply`.

### Dataset Pt.1
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

### Dataset Pt.2
```
360_extra_scenes/
├── treehill/
│ ├── sparse/
│ │ └── 0/
│ │ ├── points3D.bin
│ │ ├── images.bin
│ │ └── cameras.bin
│ ├── images/
│ │ ├── _DSC9003.JPG
│ │ ├── _DSC9004.JPG
│ │ └── ...
│ ├── images_2/
│ ├── images_4/
│ ├── images_8/
│ └── poses_bounds.npy
├── flowers/
│ ├── sparse/
│ │ └── 0/
│ │ ├── points3D.bin
│ │ ├── images.bin
│ │ └── cameras.bin
│ ├── images/
│ │ ├── _DSC9040.JPG
│ │ ├── _DSC9041.JPG
│ │ └── ...
│ ├── images_2/
│ ├── images_4/
│ ├── images_8/
│ └── poses_bounds.npy
```

## Tanks & Temples and Deep Blending Dataset Structure 

You can find our SfM data sets for Tanks&Temples and Deep Blending [here](https://repo-sam.inria.fr/fungraph/3d-gaussian-splatting/datasets/input/tandt_db.zip). 

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

### Forward-facing scenes from the DTU dataset

All models are trained with 3 input images.

On the DTU dataset, the background of these scenes is a white table or a black background, which has few textures. As mentioned in RegNeRF we mask the background during inference to avoid background bias.


### For depth maps, the ground truth is the output of the Monodepth model.

--------------------------------------

## Datasets


<details>
  <summary><b>DTU</b></summary>

* Images: We use the DTU dataset, processed by PixelNeRF, where the images are processed and resized to 300 x 400.
Download the data [here](https://drive.google.com/drive/folders/1PsT3uKwqHHD2bEEHkIXB99AlIjtmrEiR?usp=sharing). 

* Mask Data: For evaluation, we report also masked metrics. For this, we use the object masks provided by DVR, IDR and RegNeRF. [RegNeRF](https://github.com/google-research/google-research/tree/master/regnerf) provides the full mask data (for the test splits), which you can download [here](https://drive.google.com/file/d/1Yt5T3LJ9DZDiHbtd9PDFNHqJAd7wt-_E/view?usp=sharing). 

* Ground-truth depth maps: For evaluation, we report the depth error. For this, we download the [depth maps](https://virutalbuy-public.oss-cn-hangzhou.aliyuncs.com/share/cascade-stereo/CasMVSNet/dtu_data/dtu_train_hr/Depths_raw.zip). They are extracted from [MVSNeRF](https://github.com/apchenstu/mvsnerf#:~:text=training%20data%20and-,Depth_raw,-from%20original%20MVSNet).  

</details>

```
DTU
  |-- images
    <model_id>
    |-- cameras_xxx.npz    # camera parameters
    |-- image
        |-- 000000.png        # target image for each view, 400x300
        |-- 000001.png
        ...

    |-- new_val.lst           # Used for val/test dataset split for gaussian splatting

    |-- mask
        |-- 000000.png        # target mask each view, 1600x1200  (For unmasked setting, set all pixels as 255)
        |-- 000001.png
        ...
    |-- depth
        |-- 000000.png     
        |-- 000001.png


```

<details>
  <summary><b>LLFF</b></summary>

The LLFF real-world data can be found in the [NeRF Google Drive](https://drive.google.com/drive/folders/128yBriW1IG_3NJ5Rp7APSTZsJqdJdfc1).
For convenience, you can download them with the following script: (under this repo)
```bash
gdown --id 16VnMcF1KJYxN9QId6TClMsZRahHNMW5g # download nerf_llff_data.zip
unzip nerf_llff_data.zip
rm -f nerf_llff_data.zip
mv nerf_llff_data data/llff
```

</details>

<details>
  <summary><b>Replica</b></summary>

You can download the replica dataset with the following script:
```bash
# you can also download the Replica.zip manually through
# link: https://caiyun.139.com/m/i?1A5Ch5C3abNiL password: v3fY (the zip is split into smaller zips because of the size limitation of caiyun)
wget https://cvg-data.inf.ethz.ch/nice-slam/data/Replica.zip
unzip Replica.zip
  ```
</details>

--------------------------------------

# Implementation Details

In practice, we optimize the zeroth-order SH for the first 1000 iterations, which equates to a simple diffuse color representation $c \in \mathbb{R}^3$, and we introduce 1 band every 1000 iterations untill all 4 bands of SH are represented.



# Supplement

**Number of Training views** Fig. K provides a study of how our model performs relative to base 3DGS as the number of training views is changed. We test 8, 10, 12, 14, 16, and 18 views. Across all metrics, PSNR, SSIM, and LPIPS, our model consistently outperforms Base 3DGS in all settings.

**Fig. K:** Ablation study on the number of views used to train models. Our models consistently outperform Base 3DGS on PSNR, SSIM, and LPIPS when we use as few as 8 or as many as 18 images for trianing.



### Paper Terminology

- resorts to
- The scale-invariant depth constraint is strong for real-world coarse depth maps from pre-trained depth models or consumer-level depth sensors due to wide-range depth distances in the wild. (scale-invariant --> maintain the line length in the world, no perspective transformation but affine transformation)
- a simple yet effective method that distills depth priors from pre-trained depth models [41] or inaccurate depth maps from consumer-level depth sensors
- Directly scaling the coarse depth maps to a NeRF [17, 65] leads to inconsistent geometry against the expected depth of the NeRF.
- Supervised single-image depth estimation methods can be categorized into regressing metric depth [5,6,16,26,30, 50] and relative depth [21,30,32,33]. Metric depth models are typically trained on singular datasets, are more prone to overfitting, and typically generalize poorly to unseen environments or across varying depth ranges. **Relative depth models tend to generalize better as they can be trained on more diverse datasets with relative depth annotations using scale-invariant losses.** Yet, their utility for downstream tasks requiring metric depth is limited, as relative depth models regress depth with unknown scale and shift.
- Depth estimation is commonly treated as a per-pixel regression task.
- Movie data comes with its own challenges and imperfections. The primary objective when producing stereoscopic film is providing a visually pleasing viewing experience while avoding discomfort for the viewer. This means that the disparity range for any given scene (also known as the depth budget) is limited and depends on both artistic and psychophysical considerations.
- `disparity range for any given scene = depth budget`
- For example, disparity ranges are often increased in the beginning and the end of a moive, in order to induce a very noticeable stereoscopic effect for a short time. Depth budgets in the middle may be lower to allow for more comfortable viewing.
- Depth budget = disparity range가 영화 중간에는 낮아서 보는데 편하고, 영화 초반과 후반에 극적인 효과를 주는 경우 disparity range를 키웁니다.
