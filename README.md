# CS412-Project

# CS412 Fall 2023-2024 Term Project (Individual)

## Contents
  1. Description
  2. Approach
  3. Preprocessing
  4. Prompt Matching
  5. Feature Extraction
  6. Training the Model
  7. Evaluating the Model



## 1. Description
Hello ML enthusiasts,

Let's chanllenge ourselves and work on a real-life problem. Our task is predicting the score of an assignment using how a student interacted with the ChatGPT system. 

In the first assignment, you kindly provided your ChatGPT chat history and seperately your assignment were graded by our TAs. We are interested in predicting scores by extracting information from ChatGPT. 

Since this is a real-world challenge and we don't know whether a significant level of accouracy is even possible, we will evaluate your projects considering the creativity and the different approaches you use for this assignment. 



In the dataset you will find two files:

- dataset.zip : Compressed file for different ChatGPT chats as HTML files. Unique code in each file name represents the ID of the instance. 

- scores.csv : This file has multiple rows corresponds to different file. First column is the ID that you can use to match HTML files and second column is the HW scores that you are going to predict.

- Assignment.ipynb : IPython notebook for the assignment.



Couple of hints:

- Dataset may have malformed files. You still need to predict scores for them (think about data imputation and prior distributions)

- Students may only ask some questions to ChatGPT. Predicting score require matching prompts with questions. (vector space models, text clustering etc.) 

- Scores range between (0,100) that means you need be careful about the total score.



There will be plenty more assumptions or smart analysis you can conduct. Ali provided a video tutorial and starter code for this assignment. Please make sure to apply any necessary changes and improvements.

All Q&A about the project will be done on SUCourse. This exchange will help everyone to benefit from the information shared by everyone. 

To deliver the project, we need one public Github repository for each team. Your repository must contain a README file with all the necessary descriptions and report the findings and approaches used to work on this task. Please also refer to the slides that we share about the project.


## 2. Approach

In this project, there are 3 main steps:
  1. Preprocessing the prompts obtained from the files and the questions in the homework.
  2. Matching the prompts with the relevant questions.
  3. By obtaining features from the question-prompt pairs and the scores from the homework, training a model to predict scores for the next homeworks.

I used **cosine similarity measure** between the questions and the prompts to see the correspondence levels of each prompt-question pairs. For each prompt, the most similar question is assigned to the prompt. Then, I extracted some features:

  1. **Number of prompts in a file**: This was already given in the examle colab file.
  2. **Question coverage**: After matching prompts with the questions in the homework, I acquired a set of numbers between 1-8 (numbers of the questions in the HW). The set consisted of the questions that are matched by the prompts for each file. Question coverage score is the ratio of the number of elements in this set and the total number of questions.
  3.**Point converage**: Since we already know the distribution of points, it might be useful to consider it and include it in our training set. It is similar to the feature above, however, point coverage is the ratio of the points of the questions that are covered by the prompts to 100.
  4. **Length of the prompts**: The training set in hand had variance in the length of the number and thus the length of the prompts. 
 
PS: I worked individually in this project.
