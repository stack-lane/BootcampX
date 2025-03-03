# Day #002

## Git & GitHub

- Introduction to [Git](https://git-scm.com)
- Introduction to [GitHub](https://github.com)
- Introduction to [GitHub Desktop](https://desktop.github.com/download/)
- [How to write a git commit message?](https://cbea.ms/git-commit)
- [Industry-Standard Commit Conventions](https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13)

## ChatGPT

Basics about ChatGPT prompts --

- Tokens
- Context Length

> Quick hack around ChatGPT's context length: _Summarise everything we've discussed so far._

### How to prompt ChatGPT better?

> [Anatomy Of A Good Prompt](./Assets/Anatomy%20Of%20The%20Prompt.jpg)

1. Shot Promoting

- Zero Shot Prompting
  > _E.g. Write a YouTube script for my tech review channel._
- One Shot Prompting
  > _E.g. Using this [Example] as reference and write a YouTube script for my tech review channel._
- Few Shot Prompting
  > _E.g. Using these [Example 1], [Example 2], [Example 3] as reference, write a 5 minute YouTube script on the latest iPhone camera specifications for my tech review channel. Start with a 10 second hook and notate a photo for each main point._

2. Chain Of Thought Prompting

   > _E.g. What is the diameter of the sun? Let’s think step by step._

3. Tabulate Format Prompting
   > _E.g. What are the main factors of growing a YouTube channel? Can you tabulate the results?_
4. Ask Before Prompting
   > _E.g. You are an expert in the field of [Industry]. I’m going to ask you to complete some specific tasks, but before you answer, I want you to do the following: If you have any questions about my task or uncertainty about delivering the best answer possible, always ask bullet point questions for clarification before generating your answer. Is that understood?_

### Prompt Frameworks

#### 1. Role, Goal & Context (RGC) Prompting

- **Role** <br/>
  ChatGPT’s persona <br/>
  _E.g. You are an expert marketer_
- **Result** <br/>
  Desired output <br/>
  _E.g Create 5 emails ending with a call to action_
- **Goal** <br/>
  Purpose of the output <br/>
  _E.g The goal is to drive sales to my product_
- **Context** <br/>
  Who, what, where, why <br/>
  _E.g The emails are for my online audience of entrepreneurs_
- **Constraint** <br/>
  Limitations and guidelines <br/>
  _E.g The emails should be friendly and less than 200 words_

> _E.g. You are an expert *nutritionist*. Create a *7 day meal plan for my 5 foot 7, 40 year old, female client who exercises 3 times a week*. The goal is for her to *lose 1 kg of fat a week by being in a caloric deficit and eating the right amount of carbs, sugar, and protein*. She doesn’t *eat meat and wants to spend ₹200 per week on food*. The meal plan should *give the recipes, cooking directions, preparation times, and a specific meal for breakfast, lunch, and dinner*._

#### 2. I Want You To Act As Prompting

> _E.g. I want you to act as a *virtual doctor*. I will describe my symptoms and you will provide a diagnosis and treatment plan. You should only reply with your explanation, diagnosis, and treatment plan, and nothing else. My important details are, "I have been experiencing a headache and dizziness for the last few days, what could be the cause?”_
