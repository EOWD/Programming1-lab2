# Scrabble Game in C# - Guided Lab

![Game Time GIF](https://media.giphy.com/media/1C8bHHJturSx2/giphy.gif?cid=ecf05e47nb9p5xzvk3d7kglo60qvqfachsbwe4hhg8v9fxog&ep=v1_gifs_search&rid=giphy.gif&ct=g)

Welcome to the **Scrabble Showdown**! 🎉 Get ready to dive into the wild world of C#, where we’ll build a Scrabble-like game, and you’ll get to decide the victor between two brave players. Will you code the next Scrabble champion or... tie? 🤔

Let’s grab our virtual coding mugs, and may the best wordsmith win! 💻☕ (Bonus points for style. Just kidding, maybe.)

---

## Step 1: Set Up Your Coding Arena

### What to do:
1. **Grab your gear**:
   - **Visual Studio Code**: Your trusty code editor. Download it [here](https://code.visualstudio.com/). 🛠️
   - **.NET SDK**: Without this, you’ll be coding in the dark! Download it [here](https://dotnet.microsoft.com/download). 🌟

2. Time to throw some commands into your terminal like a coding wizard:
   ```bash
   dotnet new console -n ScrabbleGame
   cd ScrabbleGame
   ```

3. Use this mystical command to open your newly created magic portal (aka project) in **Visual Studio Code**:
   ```bash
   code .
   ```

Now your coding arena is ready for battle... or, you know, for learning and fun.

---

## Step 2: Summon the Scores Array (Our Trusty Sidekick)

### What to do:
Let’s set up a **score array** for each letter in the alphabet, Scrabble-style. It’s like creating a scoreboard... without the scoreboard. 🏆

**Hint**: 
- Use `int[] arrayName = { values };` to create an array. You got this!
- Imagine each letter like a contestant. "A" gets 1 point for being awesome, "Z" gets 10 points because, well, it's rare! 💯

1. In `Program.cs`, create an array to store these mighty scores.

Try creating the array before peeking at the answer. (No cheating... unless you must!)

<details>
  <summary>Click here if your code-sorcery fails you</summary>

```csharp
static int[] scores = {
    1, 3, 3, 2, 1, 4, 2, 4, 1, 8, 5, 1, 3, 1, 1, 3, 10, 1, 1, 1, 1, 4, 4, 8, 4, 10
};
```

### Fun Fact:
- The letter "Z" is like the rare Pokémon of letters—worth 10 points! 💥
</details>

---

## Step 3: Let’s Get Looping (The Fun Kind, Not the Infinite Kind)

### What to do:
Now we need a method that checks each letter of a word and gives them a score. Like a Scrabble referee—but cooler. 😎

**Hint**:
- Declare a method using `static` (because it’s always there for you) and a `for` loop (because you're in control).
- Convert the word to uppercase so even "cAt" looks like "CAT". You know, to be fair. 😺

1. Write a method called `ComputeScore` that takes a word and returns the score. It's like counting points in a very sophisticated word-battle.

2. Use a **for** loop to check each letter and add up the score like a true Scrabble master.

Give it a whirl before you check the answer... go on, take a risk! 😜

<details>
  <summary>Click here if you're looping out of control...</summary>

```csharp
static int ComputeScore(string word)
{
    int score = 0;
    word = word.ToUpper();  // Let's make everything capitalized, no bias here!

    for (int i = 0; i < word.Length; i++)  // Let’s go through every letter
    {
        char letter = word[i];
        if (char.IsLetter(letter))
        {
            score += scores[letter - 'A'];  // Add the letter's score from the array
        }
    }
    return score;  // Victory or defeat lies in the numbers...
}
```

### Pro Tip:
- Keep track of those scores, like counting snacks—don’t let any letters slip away unnoticed! 🍕
</details>

---

## Step 4: Ask Your Brave Players for Words

### What to do:
Now it's time to get our **two players** to input their words. Will Player 1 bring out "WIZARD" while Player 2 battles with "ZEBRA"? 🦓 Let’s find out!

**Hint**:
- Use `Console.WriteLine()` to ask for input (because we need to be polite).
- Store each word in a **string** variable. It’s a bit like keeping a secret until it’s time to reveal the scores! 🤫

1. Use `Console.WriteLine` to prompt each player for their word.
2. Use `Console.ReadLine` to collect their words.

Give it a shot, and then check below if the words won’t appear like magic. ✨

<details>
  <summary>Stuck? Here's how to collect those words like a pro</summary>

```csharp
Console.Write("Player 1, enter your word: ");
string player1Word = Console.ReadLine();  // Whatever they say, we’ll take note!

Console.Write("Player 2, enter your word: ");
string player2Word = Console.ReadLine();  // Player 2 is ready for battle!
```

### Fun Fact:
- Player 1 vs Player 2. This is what legends are made of! 🏅
</details>

---

## Step 5: The Moment of Truth—Calculate Scores and Determine the Winner

### What to do:
Let’s do some math! (Don’t panic, it’s the fun kind.) We’re about to find out who wins this epic word clash.

**Hint**:
- Use **if...else** to compare scores and print the winner.
- You’re the game judge now. No pressure... 😏

1. Use the `ComputeScore` method to get the scores for each player’s word.
2. Use some **if...else** magic to print who wins or if it’s a tie. Let the code decide!

Got your winner in mind? Now let’s see if the code agrees.

<details>
  <summary>Click if you need a little push toward glory</summary>

```csharp
int player1Score = ComputeScore(player1Word);
int player2Score = ComputeScore(player2Word);

if (player1Score > player2Score)
{
    Console.WriteLine("Player 1 is victorious! 🏆");
}
else if (player2Score > player1Score)
{
    Console.WriteLine("Player 2 takes the crown! 👑");
}
else
{
    Console.WriteLine("It's a tie! How anticlimactic... 😅");
}
```

### Fun Fact:
- If it’s a tie, you might have just witnessed the rarest of Scrabble moments...! 🤷‍♂️
</details>

---

## Step 6: Time to Run Your Masterpiece!

### What to do:
It’s time to put all your hard work to the test and run your game. Let’s find out who will reign supreme!

1. Open your terminal and run:
   ```bash
   dotnet run
   ```

2. Sit back, relax, and see who emerges victorious. Is it Player 1, Player 2, or... is it you, the coder?! 💻

---

## Bonus Challenge: Level Up Your Game

Now that your game is working, what’s next? Let’s add some extra flair!
- **Input Validation**: Make sure players enter real words—no gibberish here! 🧐
- **Bonus Points**: Why not add special points for longer words or specific letters? Double the fun! 🎉

---

### Explanation of the Structure:
- **Interactive learning**: Follow each step, and reveal solutions only when necessary—kind of like leveling up in a video game.
- **Fun and humor**: Code with a smile, because learning doesn’t have to be boring!

---

### Publishing the Glory:
Once you’re done, push your code to GitHub and show the world (or, at least, your friends):
```bash
git add .
git commit -m "Victory is mine!"
git push origin main
```

---

And there you have it! You’ve not only coded a game but also created a fun battle between two players. Ready to take over the coding world? Of course, you are! 😎💻
