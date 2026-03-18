# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
  • The game looked like a simple guessing game with few features that obvsiouly had some bugs.
- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").
  • If the guess was lower than the secret, it would say "go higher" when it should have said "go lower" and vice versa if the guess was higher than the secret.
  • Whenever a game would finish, the new game button wouldn't work and would have to refresh the localhost for it to work again. 

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
  • Claude 
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
  • A correct suggestion Claude gave me was identifying that the attempts were being incremented before input validation meaning invalid guesses still used an attempt. It fixed it by testing with bad inputs and it no longer reduced the attempt count.
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).
  • Claude moved the placeholder with the debug info to the bottom even though I didn't ask for that. When I ran the game I was looking for it and it ended up on the bottom. I told it to fix it and it did.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
  •I would run the game after every edit Claude would do and see if it fixed the bug I told it to fix.
- Describe at least one test you ran (manual or using pytest) and what it showed you about your code.
  • I would purposefully use all the attempts to see if the bugs that were there were fixed. At first, some of the bugs would still be there like a new game not starting or when it said I had 1 attempt left when I really had 0. After Claude fixed all bugs, I played the game again in multiple ways until everything worked fine.
- Did AI help you design or understand any tests? How?
  • Not that I know of because I would test it myself.

---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
  • Streamlit would rerun the python script from top to bottom and it somehow generated a new secret on every rerun.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
  • Everytime a button is clicked, it causes the whole code to restart from the beginning. Any variable that was set isn't saved so the answer gets reset.
- What change did you make that finally gave the game a stable secret number?
  • Claude found that by wrapping the random.randint() function in "if 'secret' not in st.session_state:' would generate the secret once and reuses it every time after.

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
  • a strategy I would use again is to tell claude to read the folder line by line to make sure there are no more bugs and testing it multiple times. I would also continue to ask it questions on things I dont fully understand as im still learning and feel like I have a lot to learn.
- What is one thing you would do differently next time you work with AI on a coding task?
  • I would ask Claude to explain why whatever it is was fixed works so I know what's happening.
- In one or two sentences, describe how this project changed the way you think about AI generated code.
  • AI-generated code is definitely something that I never thought would work so well but it still produces some bugs that it may not catch. A human still needs to guide it ti a working project. It can be good to get the basics done but once things start getting more complex, thats when you need to pay attention to whatever it is it's doing.
