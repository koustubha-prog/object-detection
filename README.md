This Project designs an online image retrieval system. Image preprocessing is performed by target detection and image segmentation, which solves the problem of acquiring key information in complex background. The integrated ResNet and HNSW methods are proposed to extract image features and perform nearest neighbor search. The results of target detection and image tags are The combination of inverted indexes enables further refined merchandise search. At the same time, this paper also proposes a retrieval system based on image classifier based on convolutional neural network, which further optimizes the accuracy and speed of retrieval through commodity pre-classification.
The system is based on Python+Mxnet+Flask. The front end interacts with the background through the web interface, providing a variety of image search methods that meet the needs of modern e-commerce websites. The background includes offline and online processing. Offline processing completes feature extraction, classification, and tag indexing of all products. Online processing completes functions from image preprocessing to feature extraction and nearest neighbor search. For the real-time nature of the system, multiple concurrent high-availability processing is performed in the background using the Redis cache. The system uses the Amazon e-commerce data set for testing, which enables a more accurate search than the general e-commerce search system under the condition of real-time performance.

demo
FrontEnd Visualization
Front End uses javascript to make mesh results visualize according to the given point cloud and parameters given.

Feature Extraction and KNN search
According to ResNet and extracting image features: download the image and name the image as its ASIN ID through the address in the source file provided by the Amazon dataset, configure the CUDA environment on the Linux system and perform GPU-based Mxnet installation, loading Pre-train the ResNet model, convert each picture into the required input format. After the information is completed, perform batch feature extraction, and put 1 million pictures into the pre-trained ResNet one by one to establish an ASIN-to-feature mapping.
The nearest neighbor search of this system mainly uses an improved NSW (Navigable Small World) algorithm.

Object dectection module
For some products with more complicated patterns such as clothing, bags, shoes, etc., you can consider using a more sophisticated image search method, that is, adding some pre-processing before feature extraction. As mentioned in the above, the system integrates target detection. And image segmentation two image preprocessing algorithms to improve accuracy.
In terms of target detection, the system uses the pre-trained Faster R-CNN structure of the COCO training set to target the target and the classification label of the target, while in the image segmentation, the FCN is used to segment the most critical elements in the image.

Sample

Use Faster RCNN to detect person

Object Detection & Inverted Index Based Searching
In many cases, there are two products with similar patterns and similar shapes, but they are not the same type of goods in nature. In this case, only the feature extraction may be misjudged, so the system also uses another search method. - Image search based on target detection and inverted index.

In actual use, the system automatically recognizes the images uploaded by the user and performs preliminary target recognition, searching and matching in the documents created by the image set.

