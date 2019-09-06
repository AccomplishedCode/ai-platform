# Image Captioning using CNN and LSTM

For generating captions for images, I used the Microsoft Common Objects in Context (MS-COCO) dataset.The whole workflow is defined in the python notebook. Here are the steps I took to achieve this task:

- First, process images from the dataset (MS-COCO) to obtain an encoding of the images with a pretrained CNN , which is already good at classifying images. 
- The CNN will take a fixed-size image as the input and output the class the image belongs to (for example, cat, dog, bus, and tree).
- Using this CNN, obtain compressed encoded vectors describing the images.
- Then process the captions of the images to learn the word embeddings of the words found in captions.
- Finally, having obtained both the image and word encodings, feed them into an LSTM and train it on the images and their   respective captions. 
- Then generate a caption for a set of unseen images (that is, the validation set).

# Dataset

The MS-COCO dataset is available here: http://cocodataset.org/#download . Download the files '2014 Val images' (~6GB) and '2014 Train/Val annotations' (~250 MB). After cloning the repo, you need to create a specific folder structure and place downloaded files correctly, so that the algorithm can retrieve necessary files.
* Folder Creation
 * Create a folder `image_caption_data` inside the img-len folder (i.e. `img-len/image_caption_data`)
 * Create a folder `train_valid` within `image_caption_data` folder
 * Create two folders `images` and `annotations` folders within the `train_valid` folder
* Training and Validation set (`val2014.zip`, `annotations_trainval2014.zip`): 2014 Validation set (approximately 41,000 data points (6GB))
 * Download the zip file (`val2014.zip`) and extract the contents to `image_caption_data/train/images` folder
 * Download the zip file (`annotations_trainval2014.zip`) and extract the contents to `image_caption_data/train/annotations` folder
 
 # Pretrained CNN weights
 
 I used the VGG16 CNN model weights for this task. The weights are a .npz file & can be downloaded here: http://www.cs.toronto.edu/~frossard/post/vgg16/
 
Move the weights file to the img-gen folder. 

That's it, you're set to run the notebook! The notebook itself has detailed comments on each step. Please feel free to let me know what you think!
