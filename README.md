# Fashion-AI-Stylist-Buy-Me-That-Look




    Have you ever looked at an Instagram model, or a model in a fashion e-commerce web-page, and thought “Wish I could get a list of fashion items similar to the ones worn by the model!”.

    This is what I address in this project, where I  developed a computer vision based application to address the challenging problem of recommending similar fashion products. The idea of this project has been taken from the myntras's research paper .

    My goal is to suggest similar clothing accessories to the one worn by the model in the input image.

![uc](https://github.com/Ankush-kadu/Fashion-AI-Stylist-Buy-Me-That-Look/assets/107274024/f8c4f2fc-a32b-4a90-822f-4bb0e0d25a2b)

Checking for Full-Shot Images

Pose estimation is the task of using an ML model to estimate the pose of a person from an image or a video by estimating the spatial locations of key body joints

![uc](https://github.com/Ankush-kadu/Fashion-AI-Stylist-Buy-Me-That-Look/assets/107274024/c54fc892-702d-4484-a85f-80951fa93e7d)




    There is a large variety of pre-trained models available for pose-estimation. Some of the most prominent methods are : PoseNet, OpenPose, MoveNet etc.

    In this project, I am going to use an open-source pre-trained pose estimation model by Google called MediaPipe.

    MediaPipe Pose is a ML solution for high-fidelity body pose tracking, inferring 33 landmarks on the whole body from RGB video frames. MediaPipe is relatively faster than all the other models and also has great accuracy.

![pose_tracking_full_body_landmarks](https://github.com/Ankush-kadu/Fashion-AI-Stylist-Buy-Me-That-Look/assets/107274024/c7d2cb08-504a-471e-ade7-40b2ecd2824d)




use Pose-Estimation to check for full-shot images


For the input image to be a full-shot image of a person, we will need to make sure that :

    The landmarks 1, 4, 29 and 30 should exist inside the frame of the image.(NOTE : MediaPipe extrapolates the parts of human body which are not present inside the image frame)

    To make sure that the model in the input image is standing erect, the distance between the pair of landmarks 1 and 29 and 4 and 30 should be greater than a threshold.



You can refer to the landmark map given below :
![uc](https://github.com/Ankush-kadu/Fashion-AI-Stylist-Buy-Me-That-Look/assets/107274024/fde2bb96-c6ab-4018-8f70-dd58e6486b9f)



# Data Collection


For my purpose, I am creating my own dataset using web scraping. i am scrapping data from an online shopping website called Myntra.

I am collecting data from the given categories :

    Topwear
    Bottomwear
    Footwear
    Eyewear
    Handbag

For each item, I am scraping these attributes apart from the image :

    Link
    Title
    Name
    Price
    Category
    Sex

I am using Selenium for web scraping in this project. Selenium is an open source umbrella project for a range of tools and libraries aimed at supporting browser automation.

# Custom Object Detection
![uc](https://github.com/Ankush-kadu/Fashion-AI-Stylist-Buy-Me-That-Look/assets/107274024/ce538199-debf-4519-b69c-03a51857af39)
![uc](https://github.com/Ankush-kadu/Fashion-AI-Stylist-Buy-Me-That-Look/assets/107274024/90ecf38e-3a18-430e-b211-dbc6ef1618a5)


there are various state-of-the-art object detection algorithms. But low latency is one of our bussiness constraints. Thus i am using the YOLO algorithm. The YOLO algorithm has great inference speeds. It is used for object detection in real-time videos also.

#  Feature Extraction and Similarity Search

i am using a pre-trained ResNet-50 model for our purpose.

![uc](https://github.com/Ankush-kadu/Fashion-AI-Stylist-Buy-Me-That-Look/assets/107274024/e61fb160-4702-481e-8230-154f1fce6e6f)

# find similar images

For this project, i am using the KNN algorithm to find similar images. Simply put, I will train a nearest-neighbor model to find the nearest neighbors based on Euclidean distance.



![uc](https://github.com/Ankush-kadu/Fashion-AI-Stylist-Buy-Me-That-Look/assets/107274024/5d0839ce-fe7e-47a3-bdbd-2a6f28c90e70)

