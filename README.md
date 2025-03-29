# Image Acquisition using Web Camera
## Aim:

To write a python program using OpenCV to capture the image from the web camera and do the following image manipulations.
i) Write the frame as JPG 
ii) Display the video 
iii) Display the video by resizing the window
iv) Rotate and display the video

## Software Used

Anaconda - Python 3.7

## Algorithm

### Step 1:
Import the cv2 and numpy package.

### Step 2:
Read the Video frame using the cv2.VideoCapture(0)

### Step 3:
Write the image using imwrite()

### Step 4:
Display the frame using the imshow().

### Step 5:
Divide the frame into halves and assign the smaller frame and Rotate the frame using the cv2.rotate().

## Program:
``` Python
### Developed By: Dharshni V M
### Register No: 212223240029

## i) Write the frame as JPG file

import cv2
cap = cv2.VideoCapture(0)
frame_number = 0
while frame_number<5:
    ret,frame = cap.read()
    cv2.imshow('frame',frame)
    cv2.imwrite(f"frame_{frame_number}.jpg",frame)
    frame_number+=1
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
cap.release()
cv2.destroyAllWindows

## ii) Display the video

import cv2
cap = cv2.VideoCapture(0)
while True:
    ret, frame = cap.read()
    cv2.imshow('Video', frame)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
cap.release()
cv2.destroyAllWindows()

## iii) Display the video by resizing the window

import numpy as np
import cv2
cap=cv2.VideoCapture(0)
while True:
    ret,frame=cap.read()
    width=int(cap.get(3))
    height=int(cap.get(4))
    image=np.zeros(frame.shape,np.uint8)
    smaller_frame=cv2.resize(frame,(0,0),fx=0.5,fy=0.5)
    image[:height//2, :width//2]=smaller_frame
    image[height//2:, :width//2]=smaller_frame
    image[:height//2, width//2:]=smaller_frame
    image[height//2:, width//2:]=smaller_frame
    cv2.imshow('PIC',smaller_frame)
    if cv2.waitKey(1)==ord('q'):
        break
cap.release()
cv2.destroyAllWindows()

## iv) Rotate and display the video

import cv2
import numpy as np
cap = cv2.VideoCapture(0)
while True:
    ret, frame = cap.read() 
    width = int(cap.get(3))
    height = int(cap.get(4))
    image = np.zeros(frame.shape, np.uint8) 
    smaller_frame = cv2.resize(frame, (0,0), fx = 0.5, fy=0.5)
    image[:height//2, :width//2] = cv2.rotate(smaller_frame,cv2.ROTATE_180)
    image[height//2:, :width//2] = smaller_frame 
    image[:height//2, width//2:] = smaller_frame
    image[height//2:, width//2:] = cv2.rotate(smaller_frame,cv2.ROTATE_180)
    cv2.imshow('Photo', image)
    if cv2.waitKey(1)==ord('q'):
        break
cap.release()
cv2.destroyAllWindows()

```
## Output

### i) Write the frame as JPG image

![frame_4](https://github.com/user-attachments/assets/bb7b8290-263e-47ee-a66f-d5979e6c9f9e)

### ii) Display the video

![video](https://github.com/user-attachments/assets/6bf0b9d1-adf4-4a4e-86b7-88ff992fec9d)

### iii) Display the video by resizing the window

![resized](https://github.com/user-attachments/assets/9cebcb5b-9513-470f-aaa6-08ced1e854bf)

### iv) Rotate and display the video

![rotate](https://github.com/user-attachments/assets/af52d15f-81d3-4344-bde1-b37e322eac7d)

## Result:
Thus the image is accessed from webcamera and displayed using openCV.
