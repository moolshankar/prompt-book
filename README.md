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



