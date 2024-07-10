# LLM Self-Consistency w/ Question Rephrasing

### PROJECT

This project was created while participating in a million-dollar kaggle competition. The program created is an LLM that takes in intermediate-level high school math problems as prompts and solves them step-by-step through reasoning and coding, to find final answers.

All efforts were targeted towards efficient decoding strategies that are discussed below. Leaderboard rank was 303/1,831 (in top 16%).

### IDEA

I took the idea of Question Rephrasing from the paper MetaMath. The idea implemented in the paper was to rephrase original questions to create an augmented training set. The goal was to view each question from multiple perspectives.

In the attached notebook below, I used the same idea, except now it's used while decoding, rather than training. For each question, I rephrased the question multiple times (using an LLM) and then used self-consistency to get the final result. For instance, suppose I rephrased a question 'X' 3 times. Then I will have a total of 1 + 3 rephrased questions. 4 different angles of viewing the same question. First is the original question, and then remaining 3 are the rephrased versions of the original question. Now supposing that I will prompt the model 20 time (20 repetitions), I will iterate using each question from the total 4 questions 5 times. And then take the majority answer as the final answer.

Notebook: https://www.kaggle.com/code/ammar727/llm-self-consistency-w-question-rephrasing

### TESTING

Using this method, Self-Consistency with Question Rephrasing, I was able to score 15 on the final leaderboard. On the 10 questions (AIMO training set), the model performed slightly better with question rephrasing (2 questions answered correctly), than without question rephrasing (0 questions answered correctly).

This is obviously not enough data to conclude if this method can improve the model's performance. Due to time limitations, I was not able to implement RAG or vLLMs, I suppose I could have scored better if I were to implement them.

It will be great if someone can try and test this method. I'll try to run some tests too and continue this thread if I find something.
