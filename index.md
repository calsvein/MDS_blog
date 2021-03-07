## Understanding Testing Reliability: False Positives and False Negatives

Imagine that you are waiting in the doctor's office. She walks in, and she has the results back from a test you’ve recently taken. After clearing her throat, she informs you that in her medical opinion - you have the  disease in question.

How should you process this information? How confident should you be in the diagnosis? What if the diagnosis is an error? To understand and contextualize your test results, you first need to understand the probabilistic concepts that define False Positives and False Negatives used in testing. This is useful for anyone getting medically screened, but it’s relevance is much broader. In fact, the role of False Positives and False Negatives is a component underpinning the testing of every scientific hypothesis.

### In the Context of Medical Screening

Sticking to our medical example, let’s start out by formalizing all of the possibilities. The patient has the disease or they do not. This is a binary outcome, since there are only one of two possibilities that can exist. Likewise, a test result can only come back positive or negative. 

Because we have to two variables (disease status and test result), and because each variable has a binary outcome, we have have four distinct possibilities:

- A patient has the disease and the test result is positive. The test and reality agree. We call this a True Positive.
     
- A patient does not have the disease, and the test comes back negative. The test and reality agree. We call this a True Negative.
     
- A patient has the disease, but the test comes back negative. The test and reality disagree. We call this a False Negative. 
     
- A patient does not have the disease, but the test comes back positive. The test and reality disagree. We call this a False Positive.     


We can think of these four possible outcomes by designing what is called a 2x2 Confusion Matrix:

Note the green and red coloring. While a patient would prefer not to be in the True Positive camp, we give this and the True Negative outcome the green (desirable) color because the testing diagnosis was correct. False Negatives and False Positives are labelled red because they are incorrect diagnoses.

Let’s illustrate the Confusion Matrix with perhaps a silly example of pregnancy testing. See if the labels for each picture make sense to you.


*Image attributed to @Mo Garoub, 2020-2021 MDS.*

Let’s populate our Confusion Matrix with some numbers. Let’s say that 100 people were tested for the same disease that our original patient was tested for, with the following results:

Of these 100 predictions, 86 are correct (green) , and 14 are erroneous (red). Of these prediction errors, 9 are False Negatives, and 5 are False Positives. Overall, this testing sample had 86% accuracy rate.

For our original patient, the critical question to be asked is how often their test result is wrong. That is, given they tested positive, is the test in fact a True Positive or a False Positive. This corresponds to the first column in our Confusion Matrix. We see that for 20 total positive test results, 5 of them were False Positives. Therefore, the **False Positive Rate** is 25%. This would suggest our original patient has a 25% chance of not having the disease, and 75% chance that they do. 

Conversely, the **False Negative Rate** is the proportion of total negative test results (71 + 9) that are False Negatives (9), corresponding to 11.3%. So if a patient was provided a negative test result, there would be a 11.3% chance that they have the disease, and a 88.7% chance that they do not. 

### The Trade Off

All tests are subject to incorrect predictions, but the real-life consequences of a False Positive versus a False Negative can be profoundly different.

Consider scenario 1. A disease is deadly unless treated early and the treatment carries minimal side-effects. The harm then of a False Positive diagnosis is minimal, while the harm of a False Negative is disastrous. This is the classical “better safe than sorry” testing situation. We would gladly prefer a prediction model that generated manyFalse Positives, as long as it minimized any False Negatives. 

But now consider scenario 2. A disease has a small chance of being deadly, but the procedure carries with it a moderate or even significantreduced quality of life for the patient. As well, there is no way to confirm if the disease exists other than to carry out the procedure. The harm then of a False Positive may now be worse than a False Negative, or at least certainly on even footing. This is the, “sometimes better to leave stones unturned” situation. We would tolerate a prediction model that generated a fair number of False Negatives to keep False Positives low. 

### Controlling the Tradeoff

At this point you may be wondering if scientists can explicitly control the design of their predictive models in ways that trade off fewer False Negatives at the expense of more False Positives (or vice versa). The answer is a mathematically beautiful, and eloquent yes! But you’ll have to read my next blog post to see how.

