# Data-Bias
Analysis of Google's Prospective API and what biases it carries

# Getting Started
To get started create a Google Cloud account and request access to Perspective API: https://cloud.google.com/
To replicate data go to Google's Perspective API documentation: https://developers.perspectiveapi.com/s/?language=en_US
Follow the instructions to get an API key and insert into jupyter notebook! 
- Make sure not to share your API key with anyone else.

# Hypothesis
From what I learned about the way the model works and how the toxicty scores are assigned, my hypothesis is that profanity is needlessly labeled as toxic. In my opinion works like "fuck" and "shit" can be used positively depending on context, but I believe the model cannot read the context and disproportionately labels comments with profanity toxic.

# Tests
To test my hypothesis I will create a CSV of 60 comments of which I will label as toxic or not myself. Then I will use my threshold to have the model apply a "yes" or "no" label to the comments then test for false positives, false negatives, true positives, and true negatives. Each comment will be less than 15 words to prevent a long vs short bias, and comments will use gender neutral terms as well to avoid a gender bias.

# Low Sample Size
I am using a limit of 60 comments because my quota is 60 requests per minute, this limits my ability to create a larger sample size and reduce the possibility of it being an exception instead of a part of the rule.

# Reflection
This project has taught me how to use Google's Perspective API and understanding how to access different parts of a response. It also gave me the opportunity to learn how to read a complex API's documentation and form a hypothesis on attempting to understand a LLM model. It also allowed me to create a threshold using samples of a labeled corpus that I later used to determine toxicity of another test corpus. I found that it does tend to be biased towards profanity because of the way that it is trained to also target profanity as described in its documentation. However, my test questions were formed by me and were more vulgar/disrespectful than I intended for testing. My tests also faced bias from my definition of toxicity which was different from what the model was trained. 

### What biases do you think might exist in the model based on intuitions or public documentation about how the model was created?
I think it has a lack of contextual understanding to allow for a good concept of toxicity, it does pretty well for absolute toxicity but not conditionally. 

### What were your results?
My results were that it accurately guessed "yes" for most of my test comments but did not do well in accurately guessed "no".

### What theories do you have about why your results are what they are?
1. I believe the model has a bias against any and all profanity, which increases the score pass the threshold to label it toxic.
2. It is possible the model does not fully understand insults
3. The training data label something "no" as in not toxic for an insult because the human understood sarcasm but the machine does not