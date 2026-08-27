---
name: explain-this-code
description: Use when the user provides existing code and asks what it does, how it works, for a walkthrough, or to identify assumptions or problems. Do not use for writing new code.
---

## Instructions 

When explaining code: 

Start by explaining what the code is for and what problem it is trying to solve. 

Then explain how the code works in a logical order, using simple language suitable for someone new to the project. 

Explain important functions, variables, libraries or components only where they help the reader understand the code. 

Identify any assumptions the code makes that are not clearly written down. 

If any part of the code is unclear, incomplete or appears to be wrong, say this clearly rather than guessing what the author intended. 

Avoid unnecessary technical jargon. If a technical term is needed, explain it briefly. 

 

 

## Output format 

Always use exactly these five headings, in this order. Do not replace them with different headings or combine sections:
##  1. What the code is for  

Briefly explain the overall purpose of the code and what problem it is solving. 

 

##  2. How it works 

Explain the code in a logical order, focusing on the main flow rather than describing every line unnecessarily. 

 

##  3. Important parts 

Explain any important functions, variables, libraries or components that are needed to understand the code. 

 

##  4. Assumptions 

List any assumptions the code appears to make that are not explicitly stated. 

 

##  5. Anything unclear or potentially wrong 

Clearly point out anything that is confusing, incomplete, inconsistent or appears to be incorrect. If nothing stands out, say so. 

 

##  Rules and missing information 
 
- Never guess what unclear code is supposed to do. 
- Never invent missing functions, variables, files or dependencies. 
- Never describe something as correct if the code does not provide enough information to know. 
- If important context is missing, explain what information is needed before giving a confident explanation. 
- If the code depends on another file, function or library that has not been provided, state this clearly. 
- If only part of the code can be explained confidently, explain that part and identify what remains uncertain. 
- Do not speculate about what missing values, functions, variables or data structures probably mean. Only explain what is directly supported by the code provided.
- Do not suggest possible implementations or fixes for missing code unless the user explicitly asks for suggestions.
- When describing unknown values or return types, do not infer their meaning from variable or function names alone. State only what the code directly shows.
 
 
##  Example of good output 
 
###  Example input  
 
The user asks: 
 
"Can you explain what this code does?" 
  
```javascript 
function calculateTotal(price, quantity) { 
  return price * quantity; 
} 
```
 
### Good output 
 
#### 1. What the code is for 
This function calculates the total cost by multiplying the price of one item by the quantity. 
 
#### 2. How it works 
The function takes two values, `price` and `quantity`, multiplies them together and returns the result. 
  
#### 3. Important parts 
- `calculateTotal` is the name of the function.  
- `price` represents the price of one item.  
- `quantity` represents how many items there are.  
- `return` gives the calculated result back. 
 
#### 4. Assumptions 
The code assumes that `price` and `quantity` are valid numbers.  
 
#### 5. Anything unclear or potentially wrong 
The function does not check whether the inputs are actually numbers, so unexpected input could cause an incorrect result. 
 
 
 
##  Example of bad output 
 
##  Bad output  
 
"This code just multiplies two numbers together. It is correct and should work fine." 
 
##  Why this is bad  
- It does not explain what the code is for before explaining how it works. 
- It is too vague for someone new to the project. 
- It does not explain the important parts of the function. 
- It does not identify the assumption that both inputs should be numbers. 
- It incorrectly says the code is definitely correct without considering missing validation or other context. 
