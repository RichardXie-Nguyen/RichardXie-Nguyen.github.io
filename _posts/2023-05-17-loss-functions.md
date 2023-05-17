# Loss Functions

So I've been looking into loss functions and it is also very interesting. From what I understand, loss functions are used to produce a derivable output to the performance of a deep learning model. 

Let's break it down with a **Cross-Entropy Loss Function** example for classifying images. The model does its thing learning about which classifiers are attributed to which images. It assesses the weights and features and whatnot to predict what each image is.
After training, the probabilities are passed into the loss function:

$H(x)=-\sum\limits_{i}X_{i}\log(p(x_{i}))$

It looks complicated but hopefully I'll be able to explain what's happening. We want to compare the actual classifier to the predicted classifier and this formula allows that to happen.
But because classifiers are just words, we need to encode them somehow so that we can use them. A one-hot encoding scheme is used on the *known* images. Here's an example for a model for classifying cats:

![](/images/tiger.jpg "Tiger")

| Tiger | Lion |
|-|-|
| Is a tiger | Is not a tiger |

| Tiger | Lion |
|-|-|
| 1 | 0 |


In this case, the image that we are looking at is a tiger and not a lion. So, that now becomes the *vector* (or *matrix* or *binary* - whatever you want to call it), (1,0) with the '1' being in the position of the **Tiger** and the '0' corresponding to the **Lion**. In fact, if we had other classifiers for more animals, we'd see 0b100000...
Hopefully, that much is clear. We've directly looked up what this image is supposed to be and the 1,0 tells us that it is a tiger. Fantastic. The next step is comparing our prediction to this one-hot encoded value.

Now, after some manipulations, the prediction model spits out a **confidence** 'rating' of what it thinks the image is. Assuming the model is working well, it might say that it's 90% sure that the image is a tiger. That means the model thinks there is another 10% chance that it could also be a lion.
In fact, if we had more animals, it might be believe there is a 5% chance of it being a lion, 2% chance of it being a leopard, etc. The point is, the 'confidence ratings' must add up to 100%.

We actually have all the pieces to put this information into our loss function. To summarise, what we have is our vector (1,0) for the *actual* result of the image and a confidence vector (90%,10%) for the *predicted* result of the image.

In this case, $X_{i}$ is the i-th one-hot vector value and $p(x_{i})$ is the i-th confidence value of the sum. So the calculation in this example will look something like this:

$H(x)=-(1*\log_{2}(0.9)+0*\log_{2}(0.1))=0.15$

The resultant value is the cross-entropy loss. The model will adjust the weights according to this value to try get it as close to 0 as possible and the certainty of its predictions towards 100%.

So that's it for loss functions from my understanding. It might be oversimplified or with some incorrect details, but that's a basic summary of what I have learned.
