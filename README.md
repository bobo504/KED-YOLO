# KED-YOLO
A real-time lightweight transmission line insulator defect detection algorithm
# Usage
1. Download this repository
2. Create a virtual environment python >= 3.8
3. Install Pytorch
4. pip install -r requrements.txt
# Code Description
1. dataset configrue file: "data/insulator.yaml"
2. model configrue files: "models/yolov5n-insulator/*.yaml"
3. attention module files: "models/ELA.py, SE.py, CoordAttention.py". They are registered in "yolo.py"
4. DCNv2, Bottleneck_DCN, and C3_DCN are defined in "models/common.py" and registered in "yolo.py"
# Dataset
The dataset is available at:
# Results
1. Results of K-means Clustering
The scales of the nine prior anchor boxes obtained after clustering were as follows:
[
 [119 40], [161 285], [ 60 49],
 [105 89], [195 158], [497 296],
 [46 98], [84 154], [156 511]
]

3. Performance comparison of integrating different attention modules

Model    | Precision(%)    | Recall(%)  | mAP50(%)  | Parameters
-------- | -----           | -----      | -----     | -----
YOLOv5n  | 87.7    | 84.1	| 89.2        | 1,764,577        
+SE      | 88.6    | 84.4 | 89.6 (+0.4) | 1,775,329(+10,752) 			
+CA      | 87.5    | 84.2 | 89.6 (+0.4) | 1,776,297(+11,720)
+ELA     | 89.7    | 83.0 | 90.0 (+0.8) | 1,783,393(+18,816)

3. Performance comparison of YOLOv5n, YOLOv5n-ELA, and KED-YOLO models

Model    | Precision(%)    | Recall(%)  | mAP50(%)  | Parameters
-------- | -----           | -----      | -----     | -----
YOLOv5n   | 87.7    | 84.1	| 89.2        | 1,764,577        
+ELA      | 89.7    | 83.0 | 90.0 (+0.8) | 1,783,393(+18,816) 			
+ELA+DCNv2 (KED-YOLO)      | 90.0(+2.3)    | 89.8(+5.7) | 90.8(+1.6) | 1,825,398 (+60,821)
