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

