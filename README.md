# AAAI2025-DriveGazen

# DriveGazen: Event-Based Driving Status Recognition using Conventional Camera
Xiaoyin Yang
[[paper]( [https://do1511](https://arxiv.org/abs/2412.11753#))] [[dataset](https://www.kaggle.com/datasets/tooyoungalex/drivegaze/)]

<img width="100%" src="https://github.com/TooyoungALEX/AAAI25-DriveGazen/blob/main/image/dvs.png"></a>
We introduce a novel wearable prototype for driver status recognition, which can effectively estimate the driver's status under challenging lighting conditions. We investigated recognition based on input from conventional cameras. Conventional cameras have high resolution, captured frames can robustly encode spatial information. However, parsing temporal cues is challenging. We introduce DriveGazen, a learning-based novel solution for extracting informative temporal cues for status recognition. DriveGazen introduces several novel design components: a method for generating DVS event frames from video frames，a spatial feature extractor based on multi-scale self-attention,a CNN-SNN-based temporal feature extractor and guide attention mechanism. Leveraging spatial awareness and the pulse mechanism of SNN to effectively provide discriminative features for classification. Spatial attention is injected into temporal feature extraction during both training and inference stages. Our extensive experimental results demonstrate that DriveGazen can effectively estimate driver status at any stage. To the best of our knowledge, DriveGazen is the first attempt to utilize conventional camera-generated events and guided attention SNN for driving status recognition tasks.

## Abstract
We introduce a wearable driving status recognition device and our open-source dataset, along with a new real-time method robust to changes in lighting conditions for identifying driving status from eye observations of drivers. The core of our method is generating event frames from conventional intensity frames, and the other is a newly designed Attention Driving State Network (ADSN). Compared to event cameras, conventional cameras offer complete information and lower hardware costs, enabling captured frames to encode rich spatial information. However, these textures lack temporal information, posing challenges in effectively identifying driving status. DriveGazen addresses this issue from three perspectives. First, we utilize video frames to generate realistic synthetic dynamic vision sensor (DVS) events.Second, we adopt a spiking neural network to decode pertinent temporal information. Lastly, ADSN extracts crucial spatial cues from corresponding intensity frames and conveys spatial attention to convolutional spiking layers during both training and inference through a novel guide attention module to guide the feature learning and feature enhancement of the event frame. We specifically collected the Driving Status (DriveGaze) dataset to demonstrate the effectiveness of our approach. Additionally, we validate the superiority of the DriveGazen on the Single-eye Event-based Emotion (SEE) dataset. To the best of our knowledge, our method is the first to utilize guide attention spiking neural networks and eye-based event frames generated from conventional cameras for driving status recognition.

## Dataset DriveGaze

To the best of our knowledge, there currently does not exist a dataset for driving state recognition based on eye events captured by conventional cameras. To address the lack of training data for event-based driving state recognition, we collected a new event-based driving state dataset (DriveGaze). DriveGaze consists of driving state eye data from 47 volunteers of different ages, genders, and races, captured using the DG3 eye tracker's conventional camera and converted into event frames. The DG3 camera is positioned in front of both eyes, with a resolution of 384*288 and a frame rate of 60FPS. Unlike the previously mentioned datasets, our wearable device avoids screen occlusion, resulting in clearer features. Based on conventional cameras, the hardware cost is low, and the application scope is wide.

DriveGaze contains original video frames of 7 driving states . The average length of videos ranges from 30 to 464 frames, with an average of 149.2 frames and a standard deviation of 62.4 frames, reflecting differences in the duration of driving states among different subjects. In total, DriveGaze includes 1645 sequences / 245365 frames of original events, with a total duration of 68.1 minutes , divided into 1316 for training and 329 for testing. For more details about the dataset, such as the collection method and environment, category definition, data distribution, etc., please refer to the supplementary materials.
<img width="100%" src="https://github.com/TooyoungALEX/AAAI25-DriveGazen/blob/main/image/Drivedataset.png"></a>

Dataset can be found [here](https://www.kaggle.com/datasets/tooyoungalex/drivegaze/).

## Method(DriveGazen)
<img width="100%" src="https://github.com/TooyoungALEX/AAAI25-DriveGazen/blob/main/image/DriveGazenPipeline.png"></a>


## Requirements

* Python == 3.9
 
* Pytorch == '2.2.1'

* CUDA == 11.8

* torchvision==0.17.1

## Training

* Step 1: download DriveGaze dataset.
<!-- * Step 2: Specifying the command line -->
* Step 2: run main.py
```bash
CUDA_VISIBLE_DEVICES=4  python main.py --root_path /video-driveStatus-classfication/dataset-60  --event_video_path event_30 --frame_video_path frame  --annotation_path driveStatus.json --result_path  sometest/test_163   --dataset driveStatus --n_classes 7 --batch_size 32 --n_threads 16 --checkpoint 100 --inference --no_val --tensorboard --weight_decay 1e-3 --n_epochs 180 --sample_size 90 --no_hflip --sample_duration 4  --inference_batch_size 120 --inference_stride 0  --sample_t_stride 4  --inference_sample_duration 4 --thresh 0.3 --lens 0.5 --decay 0.2 --beta 0 --learning_rate 0.015 --lr_scheduler singlestep
```
<!-- 

## Documents
* More [Usages](moco-doc/usage.md)
* Detailed [HTTP APIs](moco-doc/apis.md) or [Socket APIs](moco-doc/socket-apis.md)
* Detailed [REST API](moco-doc/rest-apis.md)
* Detailed [Websocket API](moco-doc/websocket-apis.md)
* [Global Settings](moco-doc/global-settings.md) for multiple configuration files.
* [Command Line Usages](moco-doc/cmd.md)
* [Extend Moco](moco-doc/extending.md) if current API does not meet your requirement. -->

