
# What is a Texform?

| Input | Texform | 
| --- | --- |
| <img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Side1_big_animal_0.56_hoofed-gemsbok1.png" width="440"> | <img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Gifs/Animated_Texform.gif" width="440"> | 

Texforms are images that preserve the coarse shape and
texture information of objects using a modified texture synthesis algorithm of [Freeman & Simoncelli, 2011](https://www.nature.com/articles/nn.2889). 

Long et al., conducted behavioral experiments to select texfroms that are unrecoganizable at the basic level. 
at  the  basic level ([Long, Yu & Konkle, 2018](https://www.pnas.org/content/115/38/E9015)), thus enabling one to test whether any visual processes depend on explicit recognition or can rely on more primitive mid-level features.  

However, to generate these images, the current implementation and computational complexity of the model requires
 approximately   4-24  hours  per  object --  a significant hurdle for experiments that require large number of stimuli. 
 
This repository has code to generate texforms in minutes.  This algorithm is implementationally equivalent to Long et al., 2018 (in terms of the first and second order image statistics that are preserved), but is both faster and can generate higher resolution images. 


## Download and Install depending packages [Linux/MAC]

This code depends on the following modules: 

[Freeman and Simoncelli Metamer model](https://github.com/freeman-lab/metamers)

[Steerable Pyramid Toolbox](https://github.com/LabForComputationalVision/matlabPyrTools)

On a linux/MAC system, you can install these directly by running the following script: 

```
bash dowload_dependencies.sh
```

## Run code demo to generate a sample Texform:

```
fast_texform.m 
```

# Texform Variations

The algorithm used to generate texforms has a number of parameters that yeild texform variations that may be of theoretical interest (e.g. by preserving more or less of the spatial information, which generally renders the stimuli more or less recognizable).

These involve:
1- simiulating how far out in the periphery is the object placed (i.e. vary point of fixation)
2- changing the rate of growth of the receptive field (i.e. log polar pooling windows)
Note these variations have similar consequnces, and are depicted below. 


## Varying the point of Fixation

| Center Fixation | Side Fixation | Out of Image Fixation |  
| --- | --- | --- |
| <img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Gifs/Animation_Texform_Center.gif" width="256"> | <img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Gifs/Animation_Texform_Side.gif" width="256"> | <img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Gifs/Animated_Texform_Further.gif" width="256"> |
| <img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Gifs/Doodles_Texform1.png" width="256"> | <img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Gifs/Doodles_Texform2.png" width="256"> | <img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Gifs/Doodles_Texform3.png" width="256"> |


## Varying the rate of Growth of Receptive Field Size (scaling factor)
| Low Scaling Factor (s=0.3) | Medium Scaling Factor (s=0.5) | High Scaling Factor (s=0.7) |  
| --- | --- | --- |
| <img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Gifs/Scale_030.gif" width="256"> | <img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Gifs/Scale_050.gif" width="256"> | <img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Gifs/Scale_070.gif" width="256"> |
| <img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Gifs/Doodle_s030.png" width="256"> | <img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Gifs/Doodle_s050.png" width="256"> | <img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Gifs/Doodle_s070.png" width="256"> |

# How is the Fast-texform method different from Long et al., 2018?

In the original method, stimuli were placed in at small size in a gray image, and the whole image was synthesized assuming a central point of fixation.  This method places the original image fully in the display, and synthesizes based on a point of fixation that is off the image. By doing so, the resulting texform is not only higher resolution, but the algorithm is also faster because there's many fewer pooling regions overall. However, computationally, it is the exact same algorithm.  The original and current methods are depicted below. 

<img src="https://github.com/ArturoDeza/Fast-Texforms/blob/master/Gifs/TexForms_Comparison_Fast.png" width="800">

Here is the code for the previous [Texform generation model](https://github.com/brialorelle/TexformGen) as used in [Long, Yu & Konkle, 2018](https://www.pnas.org/content/115/38/E9015). A more detailed explanation of what is a Texform can also be accessed [here](https://www.brialong.com/all-about-texforms).


# Citation

```
@inproceedings{
deza2019accelerated,
title={Accelerated Texforms: Alternative Methods for Generating Unrecognizable Object Images with Preserved Mid-Level Features},
author={Arturo Deza and Yi-Chia Chen and Bria Long and Talia Konkle},
booktitle={Cognitive Computational Neuroscience (CCN) 2019},
year={2019},
}
```
