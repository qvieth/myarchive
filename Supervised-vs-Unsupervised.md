# Supervised vs Unsupervised
- Introduction to the two main classes of algorithms in Machine Learning — Supervised Learning & Unsupervised Learning
- As humans, we have many different ways we learn things
    - The way you learned calculus, for example, is probably not the same way you learned to stack blocks
    - The way you learned the alphabet is probably wildly different from the way you learned how to tell if objects are approaching you or going away from you
    - The latter you might not even realize you learned at all!
- Similarly, when we think about making programs that can learn, we have to think about these programs learning in different ways
    - Two main ways that we can approach machine learning are __Supervised Learning__ and __Unsupervised Learning__
    - Both are useful for different situations or kinds of data available
## Supervised Learning
- Let’s imagine you’re first learning about different genres in music
    - Your music teacher plays you an indie rock song and says “This is an indie rock song”
    - Then, they play you a K-pop song and tell you “This is a K-pop song”
    - Then, they play you a techno track and say “This is techno”
    - You go through many examples of these genres.
- The next time you’re listening to the radio, and you hear techno, you may think “This is similar to the 5 techno tracks I heard in class today
    - This must be techno!”
- Even though the teacher didn’t tell you about this techno track
    - she gave you enough examples of songs that were techno
    - so you could recognize more examples of it
- When we explicitly tell a program what we expect the output to be
    - and let it learn the rules that produce expected outputs from given inputs
    - we are performing supervised learning

![Supervised Learning GIF](https://content.codecademy.com/programs/data-science-path/supervised-learning.gif)

- A common example of this is __image classification__
    - Often, we want to build systems that will be able to describe a picture
    - To do this, we normally show a program thousands of examples of pictures, with labels that describe them
    - During this process, the program adjusts its internal parameters
    - Then, when we show it a new example of a photo with an unknown description, it should be able to produce a reasonable description of the photo
- When you complete a Captcha and identify the images that have cars
    - you’re labeling images!
    - A supervised machine learning algorithm can now use those pictures that you’ve tagged to make it’s car-image predictor more accurate

## Unsupervised Learning
- Let’s say you are an alien who has been observing the meals people eat
- You’ve embedded yourself into the body of an employee at a typical tech startup, and you see people eating breakfasts, lunches, and snacks
- Over the course of a couple weeks, you surmise that for breakfast people mostly eat foods like:
    - Cereals
    - Bagels
    - Granola bars
- Lunch is usually a combination of:
    - Some sort of vegetable
    - Some sort of protein
    - Some sort of grain
- Snacks are usually a piece of fruit or a handful of nuts
- No one explicitly told you what kinds of foods go with each meal, but you learned from natural observation and put the patterns together
- In unsupervised learning, we don’t tell the program anything about what we expect the output to be
- The program itself analyzes the data it encounters and tries to pick out patterns and group the data in meaningful ways

![Unsupervised Learning](https://content.codecademy.com/programs/data-science-path/unsupervised-learning.gif)

- An example of this includes __clustering__ to create segments in a business’s user population
- In this case, an unsupervised learning algorithm would probably create groups
    - (or clusters) based on parameters that a human may not even consider

## Summary
- We have gone over the difference between supervised and unsupervised learning:
    - Supervised Learning: data is labeled and the program learns to predict the output from the input data
    - Unsupervised Learning: data is unlabeled and the program learns to recognize the inherent structure in the input data
