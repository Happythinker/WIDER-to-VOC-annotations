# WIDER FACE PASCAL VOC ANNOTATIONS

This repository contains the [WIDER FACE](http://mmlab.ie.cuhk.edu.hk/projects/WIDERFace/) annotations converted to the [Pascal VOC](http://host.robots.ox.ac.uk/pascal/VOC/) XML format.

```
usage: convert.py [-h] -ap ANNOTATIONS_PATH -td TARGET_DIR -id IMAGES_DIR
                  [-vl] [-oc {0,1,2} [{0,1,2} ...]]
                  [-bl {0,1,2} [{0,1,2} ...]]

optional arguments:
  -h, --help            show this help message and exit
  -ap ANNOTATIONS_PATH  the annotations file path. ie: "-ap
                        ./wider_face_split/wider_face_train_bbx_gt.txt".
  -td TARGET_DIR        the target directory where XML files will be saved.
                        ie: "-td ./WIDER_train_annotations"
  -id IMAGES_DIR        the images directory. ie:"-id ./WIDER_train/images"
  -vl                   Only include valid boxes from WIDERFACE annotation
  -oc {0,1,2} [{0,1,2} ...]
                        Filter boxes by "occlusion" flag: no occlusion->0,
                        partial occlusion->1, heavy occlusion->2; ie: "-oc 0
                        1"
  -bl {0,1,2} [{0,1,2} ...]
                        Filter boxes by "blur" flag: clear->0, normal blur->1,
                        heavy blur->2; ie: "-bl 0 1"
```

Convert wider annotation text files using the following commands:

```
$ python convert.py -ap ./wider_face_split/wider_face_train_bbx_gt.txt -td ./WIDER_train_annotations/ -id ./WIDER_train/images/
$ python convert.py -ap ./wider_face_split/wider_face_val_bbx_gt.txt -td ./WIDER_val_annotations/ -id ./WIDER_val/images/
```

Note: the convert.py is modified from [here](https://github.com/akofman/wider-face-pascal-voc-annotations) to
1) Discard invalid bounding boxes (e.g. "0--Parade/0_Parade_Parade_0_452.jpg" x1 y1 w h: 0 0 0 0)
2) Add toprettyxml for xml readability
