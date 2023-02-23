MINOR PROJECT 1 (LICENSE PLATE DETECTION IN JAVA)
A project where the license plate number is extracted from image of a vehicle using Object detection and Character recognition techniques.

Introduction 🚀
This aim of this project “Forensic Analysis: License plate detection Criminal Investigation” is to make the detection and further prevention of crimes easier. This can be achieved by detecting the car License Plate Number which could narrow down the search radius. For this, we have created a model, which performs various operations on input that helps to extract license plates numbers. Finally, the result of the first phase, that is getting the license plate number which is then tested against the criminal database to find relevant matches.

Target Beneficiary 👮
It has a lot of applications mainly for the following departments :-

Law Enforcements
Police
Traffic Police
Anti-Terrorist Forces
RAW
CBI
NIA
Government Organizations
Private Security Firms
Approach 💥
The approach for the project is as follows: -

image

image

Read the image and perform the necessary transformations on it as part of pre-processing. This includes Downsampling and Grayscale conversion.
Apply feature extraction on the image to isolate our candidate i.e., license plates. This includes, Edge detection, Adaptive Thresholding and making a bounding box.
Finally, recoganize the characters of the license plate using Optical Character Recognition. We will store this data in the database.
Dataset 💾
Our primary dataset consisted of pictures clicked on our own. The dataset can be downloaded from here https://upesstd-my.sharepoint.com/:f:/g/personal/500083764_stu_upes_ac_in/EjcmlM172GhAu2vN725ciZgBSnKlqREY4Md4HazGxTJ-Yg?e=Wxlvp5
The second dataset is made with assumption. It is database of fake criminals. It has their information as well as the information of the vehicle.
Software Used 💻
Programming Language -> Java
IDE -> Eclipse
Libraries -> OpenCV, Marvin, Swing, Tesseract
Methadology 📜
Input Phase
1.1 Input the image from the dataset

Pre-Processing Phase
2.1 After we input the image we downsample it.

WHY DOWNSCALE THE IMAGE?
Since the input image is of high resolution, it poses a high computational cost for detecting license plate in an image. 
To address this issue we downscale the input image. 
However downscaling may cause loss of information and lead to a decrease in performance of detection. 
For this reason a lot of earlier developed methods skip this step. 
A common problem statement that arises is "how to balance detection accuracy and runtime efficiency"?  
We have proposed a method that can substantially reduce the image size without a major decrease in performance.
Since we know that the width of license plate is more than height and characters on license are printed in horizontal direction. 
Therefore we define different scaling factors for vertical and horizontal direction to downscale input image.
We can also compress more data in horizontal direction because the width of license plate is greater. 
Also it makes the resulting image compact which helps later in featuer extraction since there is lesser noise.
Finally, we use INTER_AREA interpolation method that is built into opencv for image downsampling.
# We used INTER_AREA because it works best when we need to shrink an image. 
INTER_AREA is Bilinear Interpolation with coefficients 1 and 0.
7

Fig 1: This is the original input image.




downgrade

Fig 2: This is the downscaled image.




Presentation1

Fig 3(a): The image shows the result of edge detection with downsampling applied to it.

Fig 3(b): The image shows the result of edge detection without applying downsampling to it.

NOTE: THIS IMAGE IS JUST FOR DEMONSTRATION




2.2 Convert the image into grayscale using the inbuilt opencv method. (RGB2GRAY)

gray

Fig 4: The image shows the result after applying cvtColor function and converting RGB image to Grayscale image.




Feature Extraction Phase
3.1 Edge Detection

3.1.1 Blurring -> Blurring is a simple and frequently used image processing operation in order to reduce noise.

image

Fig 5: The image shows the result after applying the blur function to the grayscale image.

From the figure it may seem that blurring didn't really create any difference in the image.
Blurring Function smoothens out some of the hard edges that would have become noise when performing edge detection.
Presentation2

Fig 6: This image shows that there is some advantage by applying blur to the grayscale image.

NOTE: THIS IMAGE IS JUST FOR DEMONSTRATION




3.1.2 Canny Algorithm -> The function finds edges in the input image and marks them in the output map edges using the Canny algorithm.

edge

Fig 7: This image shows the result after applying the Canny Function. This gives us an output with only the hard edges.




3.2 Adaptive Thresholding -> Applies an adaptive threshold to an array. Threshold value is calculated for smaller regions.

threshold

Fig 8: This image shows the result after applying Adaptive Thresholding to the Edge Detected Image.




3.3 Bounding Box -> We are using the Marvin Framework to create a box around the license plate. This is simply to isolate our candidate.

image

Fig 9: This image shows the result after applying the findTextRegions function of the Marvin Framework.

As you can see in the figure that the Marvin Framework provides a strong and robust method
to detect any characters or text regions in your image. This function has created a 
bounding box around all the texts and characters it sees in the image.
Plate Recognition
4.1 Optical Character Recognition -> We are using the Tesseract or Tess4J library to perform optical character recognition. This library had to be trained for recognizing Indian License Plate Numbers. For training the Tess4J you need to use the JTessBox Editor and the Indian License Plates Fonts Dataset. You can send me an email for more information regarding this (suyashthakur7@gmail.com)

image

Fig 10: This image shows the result after applying the doOCR function of the Tess4J Framework.

Output
5.1 Final Outputs -> We finally pass the extracted text to a method that searches the criminal database and returns all the information if the license plate matches any record in the criminal database.

image

Fig 11: This image shows if the person is involved in crime or not. If output of OCR matched, then person is involved, otherwise they are not.

image

Fig 12: This image shows details of the person whose record was matched in the criminal database.

