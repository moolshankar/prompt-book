# prompt-book

## Types of prompts

### Text summarization
<pre>
Generate a brief summary for the following text
</pre>

### Information extraction
<pre>
Identify the dates and corresponding events in a list from the text above.
</pre>

### Question and answers
<pre>
Name top 10 countries in world by GDP?
</pre>

### Text classification
<pre>
Classify the following text into positive, negative, or neutral sentiment.

We can do much more with classification, for example, spam detection, topic classification, intent classification, and more.
</pre>

### Translation
<pre>
Translate the following source text from German to English.
</pre>

### Code generation
<pre>
Write a function that uses the bubble sort algorithm to sort a list of integers in ascending order.
</pre>

### Reasoning
<pre>
One of the most challenging tasks for an LLM is the requirement of reasoning. Reasoning is a fascinating area as it allows for complex applications to arise from LLMs. 
It's worth noting that to achieve satisfying results for reasoning tasks, we need to use advanced prompting techniques.

Prompt: "The sum of the odd numbers in this group is an even number: 15, 32, 5, 13, 82, 7, 1."
Output: "That statement is correct. The odd numbers in the group are 15, 5, 13, 7, and 1, and their sum is 41, which is an even number. The even numbers in the group are 32 and 82."

In this example, the model is unable to get to the correct answer. Let's try a different prompt for the same example.

Prompt: 
"
The sum of the odd numbers in this group is an even number: 15, 32, 5, 13, 82, 7, 1. 

Solve the problem by breaking it into the following steps:

Identify the odd numbers
Calculate their sum
Indicate whether the result is odd or even.
"

Output: 
"
The odd numbers in the group are 15, 5, 13, 7, and 1.
The sum of the odd numbers is 41.
41 is an odd number.
"
</pre>

## Template for common generation request
<pre>
  Role: "I want you to act as a ROLE_WITH_SPECIFIED_SKILLS"
  Goal: "Your goal is CRITERIA_FOR_OUTPUT"
  Reference: "You should take reference from ANY_REFERENCE_RESOURCE"
  Request: "Now generate ACTUAL_GENERATION_REQUEST"
</pre>

```
I want you to act as a ROLE_WITH_SPECIFIED_SKILLS. Your goal is CRITERIA_FOR_OUTPUT.
You should take reference from ANY_REFERENCE_RESOURCE.

Now generate ACTUAL_GENERATION_REQUEST.

```

## Techniques of Prompting

### Zero-shot Prompting

Zero-shot prompting is a prompting technique that involves generating text without any training on the specific task at hand.

Prompt (Classification):
<pre>
  Classify the following text as either a review of a Chinese restaurant or a review of an Italian restaurant.

  "I had the most amazing pasta at this restaurant. The sauce was perfectly seasoned and the noodles were cooked to perfection."
</pre>

Output:
<pre>
  The following text is a review of an Italian restaurant.
</pre>

Prompt (Information extraction):
<pre>
  Extract the keywords/key phrases from the following email:

  Dear John,
  
  Please note that the marketing team will be meeting tomorrow at noon to discuss the Q3 plans. We will be creating our to-dos and assigning priorities. You are responsible for taking the meeting notes, so please make sure to attend.
  
  Regards,
  
  Manager Ken
</pre>

Output:
<pre>
  Keywords/key phrases: John, marketing team, meeting, tomorrow, noon, Q3 plans, to-dos, assigning priorities, meeting notes, attend, Manager.
</pre>

### Few-shot Prompting

Few-shot prompting is a technique in which a model is trained to perform a specific task with limited or few training examples, also called shots, typically in the range of 1–10.

Prompt (With few examples first, that will help model develop a context):
<pre>
  This product is amazing! It exceeded my expectations. // positive
  I love this restaurant. The food is delicious and the service is excellent. // positive
  The customer support was terrible. They were unresponsive and rude. // negative
  
  I'm very disappointed with the quality of the food. //
</pre>

Output:
<pre>
  negative
</pre>

### Chain-of-Thought Prompting

Enables the model to demonstrate complex reasoning capabilities through intermediate reasoning steps.
CoT prompting guides the model to the correct answer through a chain of thoughts that mimics a step-by-step thought process.

CoT prompting is most commonly paired with few-shot prompting, as presenting examples is the best way for the model to learn how to break down and analyze the problem. However, it can also be used with zero-shot prompting

Prompt (Arithmetic reasoning):
<pre>
There are 3 managers working in the store. Each manager has a team of 4 workers. There are also 2 marketing agents and 1 sales representative. How many people are working in the store?
</pre>

Output:
<pre>
There are 15 people working in the clinic.
</pre>

Incorrect output. The actual answer should be 18.

Prompt (CoT with zero-shot prompting):
<pre>
There are 3 managers working in the store. Each manager has a team of 4 workers. There are also 2 marketing agents and 1 sales representative. How many people are working in the store?
Let's think step by step.
</pre>

Output:
<pre>
Sure, let's break it down step by step:

Managers: There are 3 managers working in the store.
Workers: Each manager has 4 workers in their team, so there are 3 managers * 4 workers = 12 workers in total.
Marketing agents: There are 2 marketing agents.
Sales representative: There is 1 sales representative.
Total: To calculate the total number of people working in the store, we add the number of managers, workers, marketing agents, and sales representatives: 3 managers + 12 workers + 2 marketing agents + 1 sales representative = 18 people.

Therefore, there are 18 people working in the store.
</pre>

Prompt (CoT with few-shot prompting):

Some problems can be more advanced, we can give the model a few example shots so that it can understand how to break down the problem.

<pre>
Q: There are 3 managers working in the store. Each manager has a team of 4 workers. There are also 2 marketing agents and 1 sales representative. How many people are working in the store?
A: The number of managers is 3. The number of workers is 3 * 4, which is 12. The number of marketing agents is 2. The number of sales representatives is 1. So the total number of people working in the clinic is 3 + 12 + 2 + 1, which is 18.

Q: In a veterinary clinic, there are 5 veterinarians working. Each veterinarian has 3 veterinary technicians assisting them. Additionally, there are 2 groomers and 1 office manager. How many people are working in the veterinary clinic?
A:
</pre>

Output:
<pre>
Sure, let's break it down step by step:

Managers: There are 3 managers working in the store.
Workers: Each manager has 4 workers in their team, so there are 3 managers * 4 workers = 12 workers in total.
Marketing agents: There are 2 marketing agents.
Sales representative: There is 1 sales representative.
Total: To calculate the total number of people working in the store, we add the number of managers, workers, marketing agents, and sales representatives: 3 managers + 12 workers + 2 marketing agents + 1 sales representative = 18 people.

Therefore, there are 18 people working in the store.
</pre>

This example shows that the model has adopted the same thinking style we mentioned in the prompt. Therefore, the answer is correct and structured in the same way as required.

Prompt (Common sense reasoning):

These may include problems related to human interactions with the environment, everyday knowledge, or cause-and-effect relationships

<pre>
Q: Lisa wanted to experience the vibrant nightlife of the city. Where might she go?
Options: (a) concert venue (b) remote mountain range (c) shopping mall (d) library (e) construction site

A: The answer to this question would be (a) concert venue. Concert venues often host live performances, including music concerts, which are popular nightlife attractions in cities. They offer a lively atmosphere and an opportunity to enjoy music and entertainment late into the night.


Q: Amy wanted to go where there were many birds. Where might she go?
Options: (a) zoo (b) forest (c) beach (d) library (e) shopping mall

A:
</pre>

Output:
<pre>
The answer must be a place where birds are commonly found. While birds can be found in various locations, the most likely option would be (b) forest, as forests are known to be habitats for a variety of bird species.
</pre>

Chain-of-thought prompting is a new technique and is still being researched widely.








