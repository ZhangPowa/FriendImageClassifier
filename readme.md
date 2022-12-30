# Friend Image Classifier

## Table of Contents
* [Summary](#Summary)
* [Methodology](#methodology)
* [Conclusion](#conclusion)


## Summary
I have created an end-to-end classification project that allows people to upload photos of four of my friends and I and classify them. An example of the implemenation can be found here:
https://youtu.be/gCPxlcQnmnU .

If you want to try on your own you can by going to the website http://ec2-34-212-34-6.us-west-2.compute.amazonaws.com/. YOU MUST HAVE chrome://flags/#block-insecure-private-network-requests
disabled due to the new CORS policy on chrome. Unfortunately this is a must to get the full classification table. If you do not use chrome you must disable this on the other browsers as well.

By using different classification methods such as svm, logistic regression and random forests, my model was able to achieve an 84% accuracy rate. 

## Methodology 
In the world of statistics one of the main problems many data scientists and machine learning engineers might take on is classification. For this project I decided I wanted to classify myself and four of my friends.This way
it would be fun to see new images being uploaded and having the model classify us correctly. The classification pool was made up of 4 20-21 year old asian males and one 26 year old asian female.

For classification, there are many different statistical based methods that you can use to classify different elements into groups or classes. In this case we wanted to use support vector machines, 
logistic regression, and random forests. With quantitative-based things, it is very easy to use these different classification methods. However, with image classification, the main issue is how do we extract
features from images in order to use these tools. 

This was the first step of our model creation: pre-processing and feature extraction. In order to extract features that could be used for classification first I created an algorithm to focus on an individuals
face. A face needed to have two clear eyes and a mouth, and utilizing haarcascades software, I was able to filter out photos that did not have clear faces in the photo. Also for my training dataset, I acquired photos
of just a singular person in the photo. If there are multiple people present, this image classifier has a hard time determing which to classify. Once we filtered to just the face, we used wavelet transformations to extract
meaningful features from the faces. 

After extracting all the features we simply split our data into testing and training datasets, ran svm, logistic regression, and random forests until we found a suitable accuracy rate. This did not come
about until we had around 50 images of each person. Once the model was finished we then moved onto creating a flask server and html webpage so others could try uploading their own photos.
This part of the project was heavily cs based and relied on html, css and js code. 

Lastly once the website was working locally, the next step was to connect it to an aws instance so that anyone could use it around the globe. This part of the project was the most challenging
as I had never dealt with deployment before. Using nginx and aws ec2 I was able to deploy the web page. However there were some major bugs that needed fixing. The main issue is that many browsers 
do not accept POST requests from local servers (which use http). I tried to fix this error, but found the only successful method was to disable the flag in chrome in order to receive the POST request. Thus
if others were to use the site, they would be able to upload pictures and see the webpage, but would require disabling of the same flag in order to get the POST request. 


## Conclusion
Overall, this project helped me learn both software engineer skills and statistical data science skills. I was able to obtain a high accuracy rate on my classification groups. Before using the girl as a classification object,
I had used 5 other asian male friends and myself. However no matter how many images I used to increase the sample size, the classification tools I used were too simple to classify 6 similar looking asian males. 
Thus I reduce the population to 5 groups and included a girl, which despite being asian as well, has very different features from males that makes classification easier. While my deployment
strategy was not fully efficient, it taught me the struggles of actual deployment for others to use. This project served as a very good introduction to the world of data science and machine learning and
I hope to learn even more. 
