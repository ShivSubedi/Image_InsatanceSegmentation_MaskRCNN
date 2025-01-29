# Image_InstanceSegmentation_MaskRCNN

Understanding Mask R-CNN

Mask R-CNN is an extension of Faster R-CNN that introduces a branch for pixel-wise object segmentation. It enhances previous methods by incorporating:

- Bounding Box Detection: Identifies objects in an image.
- Instance Segmentation: Predicts pixel-wise masks for each object.
- Feature Pyramid Networks (FPN): Improves multi-scale feature detection.
- ROI Align: Eliminates misalignment issues in object detection.
The original paper:
He, K., Gkioxari, G., Dollár, P., & Girshick, R. (2017). "Mask R-CNN."


Repository Features

This project is an adapted version of alsombra/Mask_RCNN-TF2 with key enhancements:

- Upgraded to TensorFlow 2.x for modern compatibility.
- Pretrained COCO weights for transfer learning.
- Custom dataset support for instance segmentation.
- ROI Align implementation for precise mask extraction.
- Multi-GPU training support.
- Background removal & visualization tools.


Project Workflow

Step 1: Downloading the Repository
- Clone the repository to your local machine or Google Colab environment.

Step 2: Installing Required Dependencies
- Navigate to the repository folder (Mask_RCNN-TF2) and install all required libraries.
- Some dependencies require compatibility adjustments for TensorFlow 2.x.

 
Step 3: Importing the Required Libraries
  - 3(A): Installing Older Versions of NumPy
    I had to downgrade and install the numpy version (1.23.5) that:
      - supports 'np.bool' alias
      - is compatible to the Tensoflow version (2.15.0) to be installed below.
      - is compatible with Python version 3.11 I am currently using
  - 3(B): Installing Older Versions of TensorFlow
    - TensorFlow 2.16+ introduced changes that break compatibility with older .h5 weights. TensorFlow 2.15.0 still supports by_name=True for .h5 models without issues.
   
Step 4: Importing Files from the MRCNN Folder
- Import the necessary files from the MRCNN directory, which includes model architecture, utility, and visualisation functions.

Step 5: Importing the (coco) Dataset
  - 5(A): Creating the Logs and Accessing the Images Folder
    - Create a logs/ directory to store model checkpoints and training logs.
    - Access the images/ folder to load sample images for segmentation.
   
Step 6: Updating Compatibility with TensorFlow v2
- Since the original implementation was designed for TensorFlow 1.x, certain modifications are necessary. Make sure to import TensorFlow 1.x configuration and session classes while using the 2.x-compatible interface.

Step 7: Loading the Pre-trained Neural Network
  - 7(A): Specifying the Path and Data Format
    - Define the file path where the COCO pre-trained weights are stored.
  - 7(B): Downloading the Pre-trained Model and Weights
    - The model uses pre-trained COCO weights to perform instance segmentation on images.
    - These weights allow the model to detect multiple object classes.
  - 7(C): Specifying GPU Resources
    - Configure the GPU settings to optimize memory usage.
    - Ensure that TensorFlow allocates only necessary resources instead of consuming all available memory.
  - 7(D): Instantiating the Mask R-CNN Model for Inference
    - Create an instance of the MaskRCNN class in inference mode.
    - Set up the configuration parameters needed for testing.
  - 7(E): Loading the Weights into the Network
    - Load the pre-trained weights into the Mask R-CNN model.
    - Ensure that the weight format is compatible with the TensorFlow version being used.
   
Step 8: Detecting Objects
  - 8(A): Creating a List of Objects from the COCO Dataset
    - The COCO dataset provides labels for multiple object categories.
    - The repository uses this dataset for inference on sample images.
  - 8(B): Visualizing the Image
    - Display the input image before performing segmentation.
  - 8(C): Getting Results from the Network
    - Run the Mask R-CNN model on the input image.
    - Retrieve the bounding boxes, segmentation masks, class labels, and confidence scores.

Step 9: Removing the Background
  - 9(A): Counting Object and Background Masks
    - Determine how many objects are detected in the image.
    - Identify the pixels belonging to each object versus the background.
  - 9(B): Segmenting Objects from the Background
    - Use the predicted masks to separate objects from the background.
    - Create binary masks to extract objects.
  - 9(C): Visualizing Segmentation for a Specific Object
    - Display segmentation results for a selected object.
    - The extracted object appears with a transparent or modified background.
 -  9(D): Visualizing Segmentation for All Objects in a Loop
    - Iterate through all detected objects and visualize them one by one.
    - Provide side-by-side comparisons of segmented objects.
