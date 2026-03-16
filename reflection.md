# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

  When I first ran the game using Streamlit, the interface loaded correctly and allowed me to enter guesses, but the gameplay behavior felt incorrect. After a few attempts, I noticed that the hints did not match my guesses. For example, when my guess was higher than the secret number, the game sometimes told me to go higher instead of lower. Another bug was that the difficulty ranges were inconsistent: the Hard difficulty had a smaller range than the Normal difficulty, which made the game easier instead of harder. I also noticed that the secret number sometimes behaved inconsistently because the code converted it into a string during some attempts, which caused incorrect comparisons.

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).


During this project I used ChatGPT to help analyze the code and understand where the logic errors were coming from. One correct suggestion from AI was identifying that the hint logic inside the check_guess() function was reversed. The AI recommended changing the hint messages so that when the guess is greater than the secret number it tells the player to go lower, and I verified this by running the game again and confirming the hints matched the guesses. One misleading suggestion I encountered earlier was when AI suggested modifying unrelated parts of the scoring logic even though the main issue was the hint logic. I verified this by running the game and realizing the hints were still incorrect until I fixed the comparison logic itself.
---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?


To determine whether a bug was fixed, I repeatedly ran the Streamlit application and tested different guesses while watching the "Developer Debug Info" panel. This allowed me to see the secret number and check whether the hints matched the correct direction. For example, I tested cases where my guess was greater than the secret number to confirm that the game now returned "Too High" and suggested guessing lower. I also used pytest to run the automated tests for the logic functions and confirmed that they passed after I corrected the logic in logic_utils.py. AI helped me understand how the tests were verifying the behavior of functions like check_guess().
---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?


Streamlit reruns the entire script every time a user interacts with the interface, such as clicking a button or entering input. Because of this behavior, variables defined normally inside the script will reset each time the app reruns. To keep important values like the secret number or score persistent, Streamlit uses something called session_state. I would explain it to a friend as a way to store variables that survive across reruns so the app can remember things like the player's progress.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.


One habit I want to reuse in future projects is testing small pieces of logic step by step instead of assuming the code works. Observing the game's behavior and checking the debug information helped me find the real cause of the bugs more quickly. Next time I work with AI on a coding task, I would verify each suggestion carefully instead of applying all changes at once. This project showed me that AI-generated code can be helpful for debugging and explanations, but it can also introduce mistakes, so developers still need to carefully review and test the code.