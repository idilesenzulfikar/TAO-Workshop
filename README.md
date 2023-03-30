# TAO-Workshop
We are excited to announce two Multi-Object Tracking (MOT) competitions: the _Long-Tail Challenge_ and the _Open-World Challenge_ at the 2nd TAO-Workshop in **CVPR2023**. With these challenges, we aim to advance multi-object tracking and segmentation research in the challenging few-shot and open-world conditions.

We base our challenge on [TAO (Tracking Any Object) dataset](https://taodataset.org/) and [BURST (Benchmark for Unifying Object Recognition, Segmentation, and Tracking)](https://github.com/Ali2500/BURST-benchmark) video segmentation labels. We provide **2,914 videos** with **pixel-precise** labels for **16,089 unique object tracks** (600,000 per-frame masks) spanning **482 object classes**!

### Updates

* **28-03-2023:** The challenge repo is launced.

### Annotations
Dowload the dataset and pixel-wise annotations:
- Image sequences: Available from the [MOTChallenge website](https://motchallenge.net/tao_download.php).
- Annotations: Available from [RWTH omnomnom](https://omnomnom.vision.rwth-aachen.de/data/BURST/annotations.zip)

The annotations are organized in the following directory structure:
```
- train:
  - all_classes.json
- val:
  - all_classes.json
  - common_classes.json
  - uncommon_classes.json
- test:
  - all_classes.json
  - common_classes.json
  - uncommon_classes.json
- info:
  - categories.json
  - class_split.json
```

**NOTE:** The annotations in this dataset are not exhaustive, i.e., not every object belonging to the dataset class set is annotated. We do, however, provide two fields per video that convey (1) which classes are present but not exhaustively annotated and (2) which classes are definitely not present in the video. This follows the format of the LVIS dataset.

For each split, ```all_classes.json``` is the primary file containing all mask annotations. The others are a sub-set of those: ```common_classes.json``` and ```uncommon_classes.json``` only contain object tracks belonging to the corresponding class split (see ```class_split.json```). 

**NOTE:** In contrast to other datasets, we have decided to make the test set annotations public. Remember though: with great power comes great responsibility. Please use the test set fairly when reporting scores for your methods. **We will ask top-performers to provide repositories for our internal revision for us to verify that no training/tunning was performed on the test set or, in the case of the TAO Open-World challenge, on the held-out classes**.

### Evaluation

Please refer to the instructions in the [BURST repository](https://github.com/Ali2500/BURST-benchmark#evaluation):

Assuming that you have the repo clonsed, and your are in a single JSON file in the same format as the ground-truth (see annotation format), you can run the eval script as follows
```
bash burstapi/eval/run.sh --pred /path/to/your/predictions.json --gt /path/to/directory/with/gt_annotations --task {class_guided,open_world}
```
- Please use ```--task class_guided``` for Long-Tail task, and ```--task open_world``` for the Open-World task.
- For this to work, you need to clone the TrackEval repo and set the environment variable ```TRACKEVAL_DIR``` to its path.
- ***Frame-rate:*** The val and test sets are evaluated at 1FPS. 
- ***Important***: We ask all participants to report (i.e., store in the output format) *results **only** for the labeled frames.*


## Cite

```
@article{luiten2020IJCV,
  title={HOTA: A Higher Order Metric for Evaluating Multi-Object Tracking},
  author={Luiten, Jonathon and Osep, Aljosa and Dendorfer, Patrick and Torr, Philip and Geiger, Andreas and Leal-Taix{\'e}, Laura and Leibe, Bastian},
  journal={International Journal of Computer Vision},
  pages={1--31},
  year={2020},
  publisher={Springer}
}
```

```
@inproceedings{liu2022opening,
  title={Opening up Open-World Tracking},
  author={Liu, Yang and Zulfikar, Idil Esen and Luiten, Jonathon and Dave, Achal and Ramanan, Deva and Leibe, Bastian and O{\v{s}}ep, Aljo{\v{s}}a and Leal-Taix{\'e}, Laura},
  journal={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
  year={2022}
}
```

```
@inproceedings{athar2023burst,
  title={BURST: A Benchmark for Unifying Object Recognition, Segmentation and Tracking in Video},
  author={Athar, Ali and Luiten, Jonathon and Voigtlaender, Paul and Khurana, Tarasha and Dave, Achal and Leibe, Bastian and Ramanan, Deva},
  booktitle={WACV},
  year={2023}
}
```
