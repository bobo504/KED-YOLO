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
Performance comparison of integrating different attention modules
Model    | Precision(%)    | Recall(%)  | mAP50(%)  | Parameters
-------- | -----           | -----      | -----     | -----
YOLOv5n  | 87.7    | 84.1	| 89.2        | 1,764,577        
+SE      | 88.6    | 84.4 | 89.6 (+0.4) | 1,775,329(+10,752) 			
+CA      | 87.5    | 84.2 | 89.6 (+0.4) | 1,776,297(+11,720)
+ELA     | 89.7    | 83.0 | 90.0 (+0.8) | 1,783,393(+18,816) 			
