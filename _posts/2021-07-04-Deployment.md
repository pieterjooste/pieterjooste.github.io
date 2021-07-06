#Deployment

It took a week to build my model based on the bear classifier in Fastai chapter 2.  A baby mood classifier which can distinguish between a happy or a sad baby.

The goal would be to build a model that can distinguish between a healthy and an ill baby, but it is easier to find photos of happy and sad babies. Let’s take baby steps.

Photos of babies were collected with Google Search. Downloaded 45 photos of babies less than 2 years with a 50:50 distribution between happy and sad. I made sure that babies of all races were represented. Copied the photos to have a total of 90 photos.

A model was built using the Bear classifier from Fastai. Resnet101 with a learning rate of 0.01 and 15 epochs delivered an accuracy of 89%. There is not much difference in results between Resnet34, 50 or 101. Decreased batch size from default 64 to 16 on dataloader. I think more photos will be needed to improve accuracy and to be more consistent with metrics.

The deployment was the more challenging part of this assignment.

MyBinder

Excellent support from Vikrant Behal on the Fastai forum provided guidance.

The first challenge: uploading files larger than 25MB on github.

Install Homebrew in order to install git. Note that the git command line and the zsh command line on a MacBook Air is the same thing. On Windows OS it is not. Introduction to the Terminal.

It took 3 days to figure out how to upload the project.pkl file of 85MB to the git lfs (large file storage) repository. Then it was found that MyBinder/voila and Fastai 2.4 were not compatible.

Back to the forums:

Heroku: This time excellent guidance from Joe Dockrill on forums.  Create Procfile on github and got requirements up to date. Deployment unsuccessful. Slug size (>500MB) especially with fastai 2.4 seems to be the problem.

Render was the next option but monthly fee a deterrent. Impressed by builder @anurag’s support on fastai forum.

Seeme.ai founded by Jan van de Poel was the final attempt and at last a successful outcome! Again excellent guidance on forum and fastai course material.

It was a big “Yes” when my model appeared on my mobile phone. [app.seeme.ai](url)

Next is the MNIST database.

Just met Geoffrey Hinton on YouTube. Wow, this guy is impressive, and his criticism of convolutional neural networks is worth noting.
