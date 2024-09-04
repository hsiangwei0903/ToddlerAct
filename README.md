# Baseline for ToddlerAct

<!-- TODO:  add ToddlerAct Paper Link-->
<div id="wrapper" align="center">
<figure>
  <img src="demo_output.gif" width="520px">&emsp;
</figure>
</div>

## Introduction
In paper [ToddlerAct: A Toddler Action Recognition Dataset for Gross Motor Development Assessment](), we propose a dataset, named TodderAct, for toddler action recognition, along with baseline performance output by our image-based [CLIP](https://arxiv.org/pdf/2103.00020)+MLP model and state-of-the-art [PoseConv3D](https://arxiv.org/abs/2104.13586) model.

In this project, we use our fine-tuned PoseConv3D ([weight](https://drive.google.com/drive/folders/1wc_VYEkxowexPDemOaJMFp_xYfhBjGDv)) to conduct skeleton-based action recognition on our ToddlerAct dataset. The model is pre-trained on the [K400](https://arxiv.org/pdf/1705.06950v1) dataset and then fine-tuned on ToddlerAct dataset for 10 epochs.

## Models
- Detector: [Fast-RCNN](https://arxiv.org/abs/1506.01497) ([COCO](https://cocodataset.org/#home) pre-trained)

- Human Pose Estimation Model: [HRNet](https://arxiv.org/abs/1908.07919) (COCO pre-trained)

- Action Recognition Model: PoseC3d Slowonly R50 (K400 pre-trained + ToddlerAct data fine-tuned)

## Installation
- Please follow instructions below to clone project repository:
    ```bash
    git clone https://github.com/hsiangwei0903/pyskl.git
    cd pyskl
    # This command runs well with conda 22.9.0, if you are running an early conda version and got some errors, try to update your conda first
    conda env create -f pyskl.yaml
    conda activate pyskl
    pip install -e .
    ```

## Model Preparation
- We provided the fine-tuned PoseC3D [here](https://drive.google.com/drive/folders/1wc_VYEkxowexPDemOaJMFp_xYfhBjGDv), please download the checkpoint to conduct inference.
- The human detection model and human pose estimation model should be downloaded automatically when running the demo.

## Demo on custom dataset
- Use this command to conduct demo on your custom video (specify video path and recognizer model checkpoint path and other relavent parameters as needed):
    ```bash
    python demo/demo_skeleton_frame.py {video_path} {output.mp4} --checkpoint {checkpoint_path} --det-score-thr {we use 0.4}
    ```
- Use this command to conduct demo with smoothing on your custom video:
    ```bash
    python demo/demo_skeleton_frame_smooth.py {video_path} {output.mp4} --checkpoint {checkpoint path} --det-score-thr {we use 0.4} –-vote_length {default is 10}
    ```

## Citation

If you use ToddlerAct dataset in your research or wish to refer to the baseline results published in the paper, please use the following BibTeX entry and the BibTex entry corresponding to the specific algorithm you used.

```BibTeX
@inproceedings{

}
```

## Contact
For any questions, feel free to contact: hwhuang@uw.edu
