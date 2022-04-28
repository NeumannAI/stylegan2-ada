# Prepare Dataset for GAN ADA Model StyleGan2 

This Markdown decoumnt contains instructions for preparing our custom data to be train on Nvidia StyleGan2 with adaptive discriminator augmentation (ADA) - Official TensorFlow implementation.  

### Before you begin

This guide requires you to clone the [Nvidia StyleGAN2](https://github.com/NVlabs/stylegan2-ada) repository.

### Steps:

- Remove the label files from the dataset folder if its exisit. 
- Resize the dataset images to fit to the model. 
- Store the data as multi-resolution TFRecords.


#### 1- Remove the label files from the dataset folder if its exisit. 

Run bellow code, :

``` 
import os
directory = "/home/watad/Downloads/data/data2" # change the dataset path to your local dataset path 
files_in_directory = os.listdir(directory)
filtered_files = [file for file in files_in_directory if file.endswith(".xml")]
for file in filtered_files:
	path_to_file = os.path.join(directory, file)
	os.remove(path_to_file) 
```

#### 2- Resize the dataset images to fit to the model. 

The images must be square-shaped and they must all have the same power-of-two dimensions, run the bellow code:
``` 
import PIL
import os
from PIL import Image
# change the dataset path to your local dataset path
f = r'/home/watad/Downloads/data/dataTest'  
for file in os.listdir(f):
    f_img = f+"/"+file
    img = Image.open(f_img)
    img = img.resize((1024,1024))
    img.save(f_img)
```
#### 3- Store the data as multi-resolution TFRecords.
To convert the images to multi-resolution TFRecords, run in the terminal:
> Note: make sure you are on the project directory

``` 
python dataset_tool.py create_from_images [PATH TO SAVE THE NEW DATASET] [YOUR CURRENT DATASET PATH]
python dataset_tool.py display [YOUR NEW DATASET PATH]
```




