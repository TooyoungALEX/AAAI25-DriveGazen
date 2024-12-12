# Instructions 
Our DriveGaze dataset provides both intensity frames and accumulated event frames. The event accumulation period is 16.7 ms, corresponding to the event-based camera's ASP frame rate, i.e., 60 FPS. 

## The file structure is shown as follows:
```
DriveGaze/
|-- event
|   |-- angry
|   |   |-- 1_001_woman_24_Master_manchu_angry_92_take000
|   |   |   |-- 00000.jpg
|   |   |   |-- 00001.jpg
|   |   |   |-- ...
|   |   |   |-- ...
|   |   |   |-- ...
|   |   |-- 2_001_woman_24_Master_manchu_angry_129_take001
|   |   |-- ...
|   |   |-- ...
|   |   `-- ...
|   |-- brake
|   |-- distracted
|   |-- excited
|   |-- focus
|   |-- mistake
|   `-- tired
`--  frame
    |-- angry
    |-- brake
    |-- distracted
    |-- excited
    |-- focus
    |-- mistake
    `-- tired
```

## Sequence Name Format
For each sequence, there are two folders: one is under the frame folder, containing the intensity frames; the other is under the event folder, providing the corresponding accumulated event frames. The two folders have the same name, with the following format:
```
[sequence#]_[ID]_[sex]_[age]_[degree]_[race]_[driveStatus]_[length]_[take#]
```
>[sequence#]: the sequence number
[ID]: volunteer ID
[sex]: volunteer's sex, man or woman
[age]: volunteer's age
[degree]: volunteer's highest educational degree
[race]: volunteer's race
[driveStatus]: the ground truth label of the sequence
[length]: the length of the sequence in the number of frames
[take#]: the sequence is the [take#]th sequence of the volunteer with [ID]


For example:
``` 
1_001_woman_24_Master_manchu_angry_92_take000 
```

>[sequence#=1]: the first sequence
[ID=001]: volunteer ID is 001
[sex=woman]: a **female** volunteer
[age=24]: volunteer's age is 24 years old
[degree=Master]: volunteer's highest educational degree is a master degree
[race=manchu]: volunteer's race is manchu
[driveStatus=angry]: the ground truth label of the sequence is **angry**
[length=92]: total number of frames in the sequence is 92
[take#]: It is the first sequence of the volunteer 001.

## Dataset Training/testing split
The training/testing split is provided in the driveStatus.json
One example is shown as follows:
```
"1011_029_man_21_Undergraduate_han_tired_168_take000": {
      "subset": "training",
      "annotations": {
        "label": "tired",
        "segment": [
          0,
          168
        ]
      }
    },
```
>[subset: training]: indicates the seqeuce belongs to __training set__
>[label: tired]: indicates ground truth label of the sequence is __tired__
>[segment: [0,168] ]: indicates the **start** and **end** frame index of the sequence


