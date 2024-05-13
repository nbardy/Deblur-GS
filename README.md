# Gaussian Splats for Real World Video

This adapts gaussian splats to be used on amateur(sparse, shaky, blurry) iphone data.


This adds:
- camera pose learning
- time variable
- deblur(https://github.com/Chaphlagical/Deblur-GS)
- importance sampling[Learns the frame and patches with the most intersting features across time and spacetime]

This started as a fork from:

Deblur-GS: 3D Gaussian Splatting from Camera Motion Blurred Images
Official  implementation of paper "Deblur-GS: 3D Gaussian Splatting from Camera Motion Blurred Images", I3D 2024

## Installation

```shell
SET DISTUTILS_USE_SDK=1 # Windows only
conda env create --file environment.yml
conda activate deblur_gs
```

## Running

### Training

```shell
python train.py -s <path to dataset> --eval # Train with train/test split
```

Additional Command Line Arguments for `train.py`

* `blur_sample_num`: number of key frames for trajectory time sampling
* `deblur`: switch the deblur mode
* `mode`: models of camera motion trajectory (i.e. Linear, Spline, Bezier)
* `bezier_order`: order of the Bézier curve when use Bézier curve for trajectory modeling

### Evaluation

```shell
python train.py -s <path to dataset> --eval # Train with train/test split
python render.py -m <path to trained model> # Generate renderings
python metrics.py -m <path to trained model> # Compute error metrics on renderings
```

Additional Command Line Arguments for `render.py`

* `optim_pose`: optimize the camera pose to align with the dataset

### Render Video

```shell
python render_video.py -m <path to trained model>
```

## BibTex

```latex
@article{Chen_deblurgs2024,
   author       = {Wenbo, Chen and Ligang, Liu},
   title        = {Deblur-GS: 3D Gaussian Splatting from Camera Motion Blurred Images},
   journal      = {Proc. ACM Comput. Graph. Interact. Tech. (Proceedings of I3D 2024)},
   year         = {2024},
   volume       = {7},
   number       = {1},
   numpages     = {13},
   location     = {Philadelphia, PA, USA},
   url          = {http://doi.acm.org/10.1145/3651301},
   doi          = {10.1145/3651301},
   publisher    = {ACM Press},
   address      = {New York, NY, USA},
}
```
