# Math Solving LLM | Self-Consistency w/ Question Rephrasing Decoding

### PROJECT

Inspired by kaggle's million-dollar competition, **the project was aimed to improve upon the performance of open-source fientuned models to solve math problems through text-generation**, using intuitive reasoning and coding.

For this, I used efficient decoding strategies to improve the performance of open-source model ‘deepseek-math-7b-rl‘. Using `Self-Consistency` followed by `Question Rephrasing`, `iterative prompting using stopping criteria`, and `running python code generated by the LLM in terminal`, the model’s performance improved significantly.

Leaderboard rank for the competition was 303/1,831 (top 16%)

### IDEA

Decoding strategy used was `self-consistency` with `iterative prompting using special stopping criteria`. **The program prompts the model ‘deepseek-math-7b-rl‘ multiple times with different prompts**. 60% of the time the model is prompted to solve the problem using a python based coding approach, and 30% of the time it's prompted to sovle the problem through intuitive reasoning. **The model is stopped with special stopping criteria everytime it generates python code and then the python code is programmed to run on terminal**, which gives accurate output, as compared to the output that the model would generate. **This way the model is prompted iteratively until it reaches the last stopping criteria by producing the answer within `//boxed{}' brackets**.

**The second most imporatnt and unique idea I used was `Question Rephrasing` from the paper MetaMath**. The idea implemented in the paper was to rephrase original questions to create an augmented training set. **The goal was to view each question from multiple perspectives**.

In the attached notebook below, I used the same idea, except now it's used while decoding, rather than training. For each question, I rephrased the question multiple times (using an LLM) and then used self-consistency to get the final result. For instance, suppose I rephrased a question 'X' 3 times. Then I will have a total of 1 + 3 rephrased questions. 4 different angles of viewing the same question. First is the original question, and then remaining 3 are the rephrased versions of the original question. Now supposing that I will prompt the model 20 time (20 repetitions), I will iterate using each question from the total 4 questions 5 times. And then take the majority answer as the final answer.

Notebook: https://www.kaggle.com/code/ammar727/llm-self-consistency-w-question-rephrasing

### TESTING

Using this method, Self-Consistency with Question Rephrasing, I was able to score 15 on the final leaderboard. On the 10 questions (AIMO training set), the model performed slightly better with question rephrasing (2 questions answered correctly), than without question rephrasing (0 questions answered correctly).

This is obviously not enough data to conclude if this method can improve the model's performance. Due to time limitations, I was not able to implement RAG or vLLMs, I suppose I could have scored better if I were to implement them.

It will be great if someone can try and test this method. I'll try to run some tests too and continue this thread if I find something.
