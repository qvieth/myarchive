# Deep Learning Math
- Review
- ![slack off of dl](http://content.codecademy.com/courses/deeplearning-with-tensorflow/deep-learning-math/review_comic.png)
- This overview completes the necessary mathematical intuition you need to move forward and begin coding your own learning models!
- To recap all the things we have learned (so many things!!!):
    - Scalars, vectors, matrices, and tensors
        - A scalar is a singular quantity like a number
        - A vector is an array of numbers (scalar values)
        - A matrix is a grid of information with rows and columns
        - A tensor is a multidimensional array and is a generalized version of a vector and matrix
    - Matrix Algebra
        - In scalar multiplication, every entry of the matrix is multiplied by a scalar value
        - In matrix addition, corresponding matrix entries are added together
        - In matrix multiplication, the dot product between the corresponding rows of the first matrix and columns of the second matrix is calculated
        - A matrix transpose turns the rows of a matrix into columns
    - In forward propagation, data is sent through a neural network to get initial outputs and error values
        - Weights are the learning parameters of a deep learning model that determine the strength of the connection between two nodes
        - A bias node shifts the activation function either left or right to create the best fit for the given data in a deep learning model
        - Activation Functions are used in each layer of a neural network and determine whether neurons should be “fired” or not based on output from a weighted sum
        - Loss functions are used to calculate the error between the predicted values and actual values of our training set in a learning model
    - In backpropagation, the gradient of the loss function is calculated with respect to the weight parameters within a neural network
        - Gradient descent updates our weight parameters by iteratively minimizing our loss function to increase our model’s accuracy
        - Stochastic gradient descent is a variant of gradient descent, where instead of using all data points to update parameters, a random data point is selected
        - Adam optimization is a variant of SGD that allows for adaptive learning rates
        - Mini-batch gradient descent is a variant of GD that uses random batches of data to update parameters instead of a random datapoint
- This has been a ton of material, so do not fret if you are confused or still wrapping your head around some of the concepts
- Many of this will be reviewed as you begin coding models
- Get excited to see how these concepts are powered with TensorFlow!
<!-- vim-markdown-toc GFM -->

* [Scalars, Vectors, and Matrices](#scalars-vectors-and-matrices)
* [Tensors](#tensors)
* [Matrix Algebra](#matrix-algebra)
* [Neural Networks Concept Overview](#neural-networks-concept-overview)
* [The Math Behind the Journey!](#the-math-behind-the-journey)
* [Loss Functions](#loss-functions)
* [Backpropagation](#backpropagation)
* [Gradient Descent](#gradient-descent)
* [Stochastic Gradient Descent](#stochastic-gradient-descent)
* [More Variants of Gradient Descent](#more-variants-of-gradient-descent)

<!-- vim-markdown-toc -->
- Before we dive into creating our deep learning models, let’s take a step back and unbox the mechanisms of these models
- In this lesson, we will investigate the foundations that run through the inner workings of neural networks
- Hopefully, after reading about the steps our data takes on its deep learning journey
    - you will have a clearer picture of the overall process and feel ready to get your hands on some code!

- We are not going to assume that you have a deep understanding of linear algebra, and you will not need a high-level math background to follow along

- Let’s take a look at the cartoon in the learning environment
- Deep learning is commonly viewed as a jumbled mess of linear algebra which this cartoon pokes fun at

![xkcd](https://xkcd.com/1838/)
 
- In this lesson, we hope to clarify the fundamental concepts that make deep learning possible
    - so you can build your own learning models with more precision than “pour the data into this big pile of linear algebra.”
- Source: [xkcd](https://xkcd.com/1838/)

## Scalars, Vectors, and Matrices
- To start
    - let us go over a couple of topics that will be integral to understanding the mathematical operations that are present in deep learning
    - including __how data is represented__:

1. Scalars: A scalar is a single quantity that you can think of as a number
    - In machine learning models, we can use scalar quantities to manipulate data, and we often modify them to improve our model’s accuracy
    - We can also represent data as scalar values depending on what dataset we are working with
    - Code example:
```python
x = 5
```
2. Vectors: Vectors are arrays of numbers
    - In Python, we often denote vectors as NumPy arrays
    - Each value in the array can be identified by its index (location within the array)
    - Code example:
```python
x = np.array([1,2,3])
```
3. Matrices: Matrices are grids of information with rows and columns
    - We can index a matrix just like an array; however
    - when indexing on a matrix, we need two arguments: one for the row and one for the column
    - Code example:
```python
x = np.array([[1,2,3],[4,5,6],[7,8,9]])
```

## Tensors
- Scalars, vectors, and matrices are foundational objects in linear algebra
- Understanding the different ways they interact with each other
    - and can be manipulated through matrix algebra is integral before diving into deep learning
- This is because the __data structure__ we use in __deep learning__ is called a __tensor__
    - which is a generalized form of a vector and matrix: a __multidimensional array__

- A __tensor__ allows for more flexibility with the type of data you are using and how you can manipulate that data
- https://www.tensorflow.org/guide/tensor

## Matrix Algebra
- The following gifs walkthrough matrix __multiplication, addition__, and __transpose__
- You can perform element-wise operations on tensors using matrix algebra as well, which you can read more about here : https://en.wikipedia.org/wiki/Matrix_(mathematics)#Addition,_scalar_multiplication,_and_transposition

1. __Matrix Addition__: Matrix addition being performed between two 2x2 matrices
    - Each element in the same position is added together
    - For example, if we add the numbers in the top left corner of each matrix being added 
        - 3 in the first matrix
        - and 4 in the second matrix 
        - we get a result of 7 in the top left corner of our new 2x2 matrix

![matrix addition](https://content.codecademy.com/courses/deeplearning-with-tensorflow/deep-learning-math/Matrix_B.gif)

2. __Scalar Multiplication__: Scalar multiplication being performed in a gif that shows a scalar value being multiplied by each element in a 2x2 matrix
    - For example, the number in the top left of our 2x2 matrix is 4
    - When it is multiplied by our scalar value, 2, we end up with the number 8 in our resulting 2x2 matrix

![scalar multiplication](https://content.codecademy.com/courses/deeplearning-with-tensorflow/deep-learning-math/Matrix_A.gif)

3. __Matrix Multiplication__:
    - This is the most complicated, so spend time understanding how it is done in the applet in the Learning Environment
    - Feel free to pause the animation if you would like to spend more time making sense of each slide!
    - https://content.codecademy.com/courses/deeplearning-with-tensorflow/deep-learning-math/matrix_interactive/index.html

4. __Transpose__:
    - A gif that shows each row of a matrix being converted into columns
    - For example, the first row in our original 3x2 matrix is (6, 4, 24)
    - When we perform the transpose, the first column of our resulting 2x3 matrix is (6, 4, 24)

![transpose](https://content.codecademy.com/courses/deeplearning-with-tensorflow/deep-learning-math/Matrix_C.gif)

- This is all of the matrix algebra we need to proceed with the rest of our deep learning investigation!
    - These concepts are the fundamental building blocks of why deep learning models are so powerful
- When we are training our models, we are performing operations on tensors
- This data is analyzed, manipulated, and shaped by the __matrix algebra__ we have quickly gone over

- Below are some optional practice questions for you to try out Matrix algebra on your own!

## Neural Networks Concept Overview
- Let’s take a look at the journey our inputs take inside of a neural network!
- By an __input__, we mean a data point from our dataset
    - Our input can have many different features, so in our input layer, each node represents a different input feature
    - For example, if we were working with a dataset of different types of food
        - some of our features might be size, shape, nutrition, etc.
        - where the value for each of these features would be held in an input node

- Besides an input layer, our neural network has two other different types of layers:
    - __Hidden layers__ are layers that come between the input layer and the output layer
        - They introduce complexity into our neural network and help with the learning process
        - You can have as many hidden layers as you want in a neural network (including zero of them)
    - The __output layer__ is the final layer in our neural network
        - It produces the final result, so every neural network must have only one output layer

- Each layer in a neural network contains __nodes__
    - Nodes between each layer are connected by __weights__
    - These are the learning __parameters__ of our neural network
    - determining the strength of the connection between each linked node

- The weighted sum between nodes and weights is calculated between each layer
    - For example, from our input layer, we take the weighted sum of the inputs and our weights with the following equation:
```
weighted_sum=(inputs⋅weight_transpose)+bias
```
- We then apply an activation function to it
```
Activation(weighted_sum)
```
- The two formulas we have gone over take all the inputs through one layer of a neural network
    - Aside from the __activation function__, all of the transformations we have done so far are linear
    - __Activation functions__ introduce nonlinearity in our learning model, creating more complexity during the learning process

- This is what makes activation functions important
- A neural network with many __hidden layers__ but no __activation functions__ would just be a series of successive layers
    - that would be __no more effective or accurate than simple linear regression__

- An __activation function__ decides what is fired to the next neuron based on its calculation for the weighted sums
    - Various types of activation functions can be applied at each layer
    - The most popular one for hidden layers is __ReLU__
        - A ReLU function has a y value of 0 for all negative numbers and a linear slope of 1 for all numbers over 0
        - The formula is f(x) = max(0, x)

![A ReLU function graph](https://content.codecademy.com/courses/deeplearning-with-tensorflow/deep-learning-math/ReLU.svg)



- Others commonly used, often for the output layer, are __sigmoid__ and __softmax__
- You will learn more about these functions as you use them later in this course

- A sigmoid function graph:
    - A sigmoid function has an logistic growth shape
    - the graph shown is between the values of -10 and 10
- The formula for a sigmoid function is f(x) = 1/(1+e^(-x))

![sigmoid](https://content.codecademy.com/courses/deeplearning-with-tensorflow/deep-learning-math/Sigmoid.svg)

- In this diagram, we see a basic neural network with no hidden layers
    - Use your mouse to hover over each section of the image to get a feel for how each step of the neural network works
    - Each part of the diagram contains a description to indicate its role in a neural network

https://content.codecademy.com/courses/deeplearning-with-tensorflow/deep-learning-math/applet_1.html

## The Math Behind the Journey!
- Let’s bring all of these concepts together and see how they function in a neural network with one hidden layer
- As you scroll over each section
    - you will see the inputs/weights/calculations associated with it
    - and see how inputs get from the starting point and make their way to the end!

- The process we have been going through is known as forward propagation
    - Inputs are moved forward from the input layer through the hidden layer(s) until they reach the output layer

- Instructions
- https://content.codecademy.com/courses/deeplearning-with-tensorflow/deep-learning-math/applet_2_new.html
- In this applet, you can scroll over each part of the neural network and observe the mathematics behind the diagram
- When you scroll over the input section, you should see how the input is represented as a vector
    - Scrolling over the weights, we see how each set of weights (blue and yellow) is represented as a vector
    - When brought together, they make up the weights_matrix and weights_matrix_transpose
- When scrolling through the hidden nodes sections, you will notice that there are two parts
    - In the first step, we take the weighted sum of our data using the weights_matrix_transpose
    - From this, we end up with a vector and apply our ReLU activation function to it
- This takes us to our teal weights
    - These are represented as a vector
    - The weights_teal_transpose turns our row vector into a column vector
    - Then we take another weighted sum in our output layer, this time between our hidden_nodes and our weights_teal_transpose
    - Following this, we have a sigmoid activation function, which gives us our output
- We now understand the adventure our data takes on one journey through our neural network

## Loss Functions
- We have seen how we get to an output! Now, what do we do with it? When a value is outputted, we calculate its __error__ using a loss function
    - Our predicted values are compared with the actual values within the training data
    - There are two commonly used loss calculation formulas:
        - __Mean squared error__, which is most likely familiar to you if you have come across linear regression
            - This gif below shows how mean squared error is calculated for a line of best fit in linear regression
            - A visual that shows the squared distance of each point from a line of best fit
            - ![loss](https://content.codecademy.com/courses/deeplearning-with-tensorflow/deep-learning-math/Loss.gif)
            - The formula for this is (predicted value - actual value)^2
        - __Cross-entropy loss__, which is used for classification learning models rather than regression

- You will learn more about this as you use loss functions in your deep learning models

- instruction : 
- The interactive visualization in the browser lets you try to find the line of best fit for a random set of data points:
    - The slider on the left controls the m (slope)
    - The slider on the right controls the b (intercept)
    - You can see the total squared error on the right side of the visualization. To get the line of best fit, we want this loss to be as small as possible.
- To check if you got the best line, check the “Plot Best-Fit” box
- Randomize a new set of points and try to fit a new line by entering the number of points you want (try 8!) in the textbox and pressing Randomize Points
- Play around with the interactive applet, and notice what method you use to minimize loss:
    - Do you first get the slope to where it produces lowest loss, and then move the intercept to where it produces lowest loss?
    - Do you create a rough idea in your mind where the line should be first, and then enter the parameters to match that image?
- https://content.codecademy.com/programs/data-science-path/line-fitter/line-fitter.html

## Backpropagation
- This all seems fine and dandy so far
- However, what if our output values are inaccurate?
- Do we cry?
- Try harder next time?
- Well, we can do that, but the good news is that there is more to our deep learning models

- This is where backpropagation and gradient descent come into play
    - Forward propagation deals with feeding the input values through hidden layers to the final output layer
    - Backpropagation refers to the computation of gradients with an algorithm known as gradient descent
    - This algorithm continuously updates and refines the weights between neurons to minimize our loss function

- By gradient, we mean the rate of change with respect to the parameters of our loss function
    - From this, backpropagation determines how much each weight is contributing to the error in our loss function
    - and gradient descent will update our weight values accordingly to decrease this error

- This is a conceptual overview of backpropagation
- If you would like to engage with the gritty mathematics of it, you can do so [here](https://en.wikipedia.org/wiki/Backpropagation)
- However, for this course, we will not need this level of detailed understanding

- Instructions
- https://content.codecademy.com/courses/deeplearning-with-tensorflow/deep-learning-math/interactives/index.html
    - Let’s take a look at what happens with backpropagation and gradient descent on a neural network directly
    - In the applet in the learning environment, watch as weights are updated and error is decreased after each iteration
    - Without backpropagation, neural networks would be much less accurate


## Gradient Descent
- We have the overall process of backpropagation down! Now, let’s zoom in on what is happening during gradient descent
- If we think about the concept graphically, we want to look for the minimum point of our loss function because this will yield us the highest accuracy
- If we start at a random point on our loss function, gradient descent will take “steps” in the “downhill direction” towards the negative gradient
- The size of the “step” taken is dependent on our learning rate
- Choosing the optimal learning rate is important because it affects both the efficiency and accuracy of our results

- The formula used with learning rate to update our weight parameters is the following:
```
parameter_new=parameter_old+learning_rate⋅gradient(loss_function(parameter_old))
```
- The learning rate we choose affects how large the “steps” our pointer takes when trying to optimize our error function
- Initial intuition might indicate that you should choose a large learning rate
    - however, as shown above, this can lead you to overshoot the value we are looking for and cause a divergent search

- Now you might think that you should choose an incredibly small learning rate
    - however, if it is too small
    - it could cause your model to be unbearably inefficient
        - or get stuck in a local minimum and never find the optimum value
- It is a tricky game of finding the correct combination of efficiency and accuracy

- Instructions
- Take a look at the graphs, which depict show some common issues you may run into when selecting a learning rate
    - If you select a learning rate that is too small, it will take a very long time to find the minimum value
    - However, if you choose a learning rate that is too large, it might overshoot the minimum value and end up with a divergent algorithm

- Choosing an ideal learning rate means it should find the ideal loss value efficiently and accurately
- ![gradient descent](https://content.codecademy.com/courses/deeplearning-with-tensorflow/deep-learning-math/Gradient_descent.gif)

## Stochastic Gradient Descent
- This leads us to the final point about gradient descent
- In deep learning models, we are often dealing with extremely large datasets
- Because of this, performing backpropagation and gradient descent calculations on all of our data may be inefficient
    - and computationally exhaustive no matter what learning rate we choose

- To solve this problem, a variation of gradient descent known as Stochastic Gradient Descent (SGD) was developed
    - Let’s say we have 100,000 data points and 5 parameters
    - If we did 1000 iterations (also known as epochs in Deep Learning) we would end up with 100000⋅5⋅1000 = 500,000,000 computations
    - We do not want our computer to do that many computations on top of the rest of the learning model; it will take forever

- This is where __SGD__ comes to play
    - Instead of performing gradient descent on our entire dataset, we pick out a random data point to use at each iteration
    - This cuts back on computation time immensely while still yielding accurate results

- Instructions
- The diagram below shows the performance differences between SGD and GD
    - You may notice that the SGD graph is a bit more sporadic
    - There is a reason for this, and we will address it in the next exercisex
- The main point is that both will reach the ideal parameters, and SGD will be easier and more efficient for your computer processor
- Because of this, SGD is almost universally used in favor of normal GD
- However, as well will see next, there are even more variants of gradient descent
- ![sgd](https://content.codecademy.com/courses/deeplearning-with-tensorflow/deep-learning-math/GD-Diagram.svg)

## More Variants of Gradient Descent
- Just when you thought SDG solved all our problems, even more options come into the picture!

- There are also other variants of gradient descent such as Adam optimization algorithm and mini-batch gradient descent
    - Adam is an adaptive learning algorithm that finds individual learning rates for each parameter
    - Mini-batch gradient descent is similar to SGD except instead of iterating on one data point at a time, we iterate on small batches of fixed size

- Adam optimizer’s ability to have an adaptive learning rate has made it an ideal variant of gradient descent and is commonly used in deep learning models
- Mini-batch gradient descent was developed as an ideal trade-off between GD and SGD
- Since mini-batch does not depend on just one training sample
    - it has a much smoother curve and is less affected by outliers
    - and [noisy data](https://en.wikipedia.org/wiki/Noisy_data) making it a more optimal algorithm for gradient descent than SGD
- These are just some quick notes! You can read more about Adam [here](https://arxiv.org/abs/1412.6980) and more about mini-batch [here](https://arxiv.org/pdf/1609.04747.pdf)
- Experts in deep learning are constantly coming up with ways to improve these algorithms to make them more efficient and accurate
    - so the ability to adapt and build upon what you learn as you dive into this domain will be key!

- Instructions
    - This is a diagram you will become accustomed to in future lessons
    - It shows us our loss function performance over many epochs (iterations) of our deep learning model with different types of gradient descent
    - These graphs are extremely useful when creating learning models because they offer us a detailed view of their performance
    - ![](https://content.codecademy.com/courses/deeplearning-with-tensorflow/deep-learning-math/Variants-of-Gradient%20Descent.png) 
