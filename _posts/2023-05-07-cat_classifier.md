# AI Classifier 

I recently finished doing a fast.ai classifier for big cats! 
It was a very interesting task to see how all the parts of fast.ai interact. 
I was quite surprised at how little code and time was required to make it run effectively.
It was also very accurate model despite some interesting pieces of data. Here are some of the results!

## Batch of Cats
![](/images/cats_batch.png "batch example")

Here, we see a batch of cats. Batches are groups of images in the training set of a neural network. Basically, it shows an example of some of the images as well as their corresponding pre-allocated labels. These images were sourced from Duck Duck Go.

## Cat Classifier Losses
![](/images/cats_losses.png "losses")

This shows some of the losses of this model. As you can see, there are a few outlier images that shouldn't be part of the group.

## Cat Classifier Confusion Matrix
![](/images/cats_confusion.png "confusion matrix")

This shows the confusion matrix when trained and tested on around 200 images per cat. The model is relatively successful, only confusing a few of the less obvious cats. I'm sure many humans would struggle to classify them correctly.
