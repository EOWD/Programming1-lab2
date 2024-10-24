# Scrabble Game in C# - Step-by-Step Guide for Beginners

---
![Game Time GIF](https://media.giphy.com/media/0DYipdNqJ5n4GYATKL/giphy.gif?cid=ecf05e47g5m0w1g9bhemyff663qq9ymyslz5k2ca2plt1j8y&ep=v1_gifs_search&rid=giphy.gif&ct=g)
## Overview

We’re going to create a Scrabble-like game using the C# programming language. In this game, two players will type in words, and the program will calculate the scores for each word based on the Scrabble letter values.

Each letter in Scrabble has a specific point value. For example:

A is worth 1 point
B is worth 3 points
Z is worth 10 points
The program will:

Ask each player to type a word.
Calculate the score for each word by adding up the points for each letter.
Compare the scores to determine which player has the higher score.
Announce the winner, or declare a tie if both scores are equal.
By the end of this tutorial, you’ll have a basic understanding of how to:

Use arrays to store data (letter scores).
Write methods to perform tasks (calculate word scores).
Take input from users (the players).
Use conditionals (if-else statements) to decide the winner.
This is a great project for practicing basic programming concepts like loops, arrays, methods, and user input/output. Plus, it’s fun because you’re building a simple game that you can play with your friends!

---

## Step 1: Set Up Your Coding Environment

### What You Need:

1. **Visual Studio Code**: This is the program where you’ll write your code.
   - You can download it [here](https://code.visualstudio.com/).

2. **.NET SDK**: This is a tool that allows you to run and build C# programs.
   - You can download it [here](https://dotnet.microsoft.com/download).

### Steps:

1. **Install Visual Studio Code** by downloading and running the installer from the link above. Follow the instructions on the screen to finish the installation.

2. **Install the .NET SDK** by downloading it from the provided link and running the installer. Again, just follow the instructions.

3. After both tools are installed, **open Visual Studio Code**.

4. Now, you need to **open the terminal** inside Visual Studio Code:
   - Click on `Terminal` in the top menu.
   - Select `New Terminal` from the dropdown.

---

## Step 2: Create a New C# Project

We need to create a new C# project where we’ll write our Scrabble game code. A project is just a folder with some setup files that help us organize and run our code.

### Steps:

1. **In the terminal**, type this command and press **Enter**:

   ```bash
   dotnet new console -n ScrabbleGame
   ```

   - This creates a new folder called `ScrabbleGame` with some basic setup files.

2. Now, type this command to move into the new folder:

   ```bash
   cd ScrabbleGame
   ```

   - This tells your computer to switch to the `ScrabbleGame` folder.

3. Finally, type this command to **open the project** in Visual Studio Code:

   ```bash
   code .
   ```

   - This opens the current project folder in Visual Studio Code, so you can start writing code.

---

## Step 3: Create the `ScrabbleGame` Class

In C#, a **class** is like a container that holds your game’s code. Everything we write for the Scrabble game will go inside this class.

### What to Do:

1. In the Explorer panel (on the left side of the screen), find and click on `Program.cs` to open the file.

2. **Delete everything** in the file. We want to start from scratch.

3. Now, type this code:

<details>
  <summary>Click here to reveal the code for the class</summary>

```csharp
using System;

class ScrabbleGame
{
    // We will add code here soon.
}
```

</details>

**Explanation**:

- `using System;` is a line that allows us to use basic C# commands like `Console.WriteLine` to print messages to the screen.
- `class ScrabbleGame` defines a **class** called `ScrabbleGame`. All the code we write for the game will go inside this class (inside the curly braces `{ }`).

---

## Step 4: Store Letter Scores in an Array

In Scrabble, each letter has a point value. For example, 'A' is worth 1 point, 'B' is worth 3 points, and 'Z' is worth 10 points. We’ll store these values in something called an **array**.

An **array** is like a list that holds multiple values. In this case, the array will hold the scores for each letter from A to Z.

### What to Do:

1. Inside the `ScrabbleGame` class (between the curly braces `{ }`), add the following code:

<details>
  <summary>Click here to reveal the code for the letter scores</summary>

```csharp
private int[] letterScores = {
    1, 3, 3, 2, 1, 4, 2, 4, 1, 8,
    5, 1, 3, 1, 1, 3, 10, 1, 1, 1,
    1, 4, 4, 8, 4, 10
};
```

</details>

**Explanation**:

- `private int[] letterScores` creates an array called `letterScores` that holds integers (whole numbers).
- The numbers in the array represent the points for each letter:
   - The first number, `1`, is for 'A'.
   - The second number, `3`, is for 'B'.
   - The last number, `10`, is for 'Z'.

We now have an array that stores the points for all 26 letters of the alphabet.

---
![Game Time GIF](https://media.giphy.com/media/oVIMiFQKiFtm3vO8Bj/giphy.gif?cid=790b761145o3vjkf98yz8a2dq89cagmu0txbe98kz5rl3tdy&ep=v1_gifs_search&rid=giphy.gif&ct=g)

## Step 5: Write a Method to Compute the Score of a Word

Now, we’ll create a **method** that calculates the score of a word. A **method** is a block of code that performs a task. In this case, the method will go through each letter of a word, find its score in the `letterScores` array, and add up the total score.

### What to Do:

1. Inside the `ScrabbleGame` class, add the following method:

<details>
  <summary>Click here to reveal the code for the ComputeScore method</summary>

```csharp
public int ComputeScore(string word)
{
    int totalScore = 0;  // Start the score at 0
    word = word.ToUpper();  // Convert the word to uppercase

    // Loop through each letter in the word
    for (int i = 0; i < word.Length; i++)
    {
        char letter = word[i];  // Get the current letter

        // Check if the character is a letter
        if (char.IsLetter(letter))
        {
            // Find the index of the letter (A=0, B=1, ..., Z=25)
            int index = letter - 'A';

            // Add the letter's score to totalScore
            totalScore += letterScores[index];
        }
    }

    return totalScore;  // Return the total score of the word
}
```

</details>

**Explanation**:

- `public int ComputeScore(string word)` creates a method called `ComputeScore` that takes in a word (string) and returns an integer (the total score).
- `int totalScore = 0;` initializes the score to 0.
- `word = word.ToUpper();` converts the word to all uppercase letters, so that 'cat' becomes 'CAT'. This ensures we don’t have to worry about whether the player used lowercase or uppercase letters.
- The **for loop** goes through each letter in the word. It starts at the first letter (`i = 0`) and stops when it reaches the end (`i < word.Length`).
- `char.IsLetter(letter)` checks if the character is actually a letter (just in case the player types something else by mistake).
- `int index = letter - 'A';` calculates the position of the letter in the alphabet (e.g., 'A' is 0, 'B' is 1, 'Z' is 25).
- `totalScore += letterScores[index];` adds the score of the letter (based on the `letterScores` array) to the total score.
- `return totalScore;` returns the total score for the word.

---
![Game Time GIF](https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExMXlwNWZicDZ4eWQ0Z3k0eTljOXRwNXBvZ2UybjE4ZTVsd2M0cGp3aCZlcD12MV9naWZzX3NlYXJjaCZjdD1n/aNqEFrYVnsS52/giphy.gif)
## Step 6: Write a Method to Start the Game

Now we need a method that actually **starts** the game. This method will ask the players for their words, calculate their scores, and decide who wins.

### What to Do:

1. Inside the `ScrabbleGame` class, add the following method:

<details>
  <summary>Click here to reveal the code for starting the game</summary>

```csharp
public void StartGame()
{
    // Ask Player 1 for their word
    Console.Write("Player 1, enter your word: ");
    string player1Word = Console.ReadLine();

    // Ask Player 2 for their word
    Console.Write("Player 2, enter your word: ");
    string player2Word = Console.ReadLine();

    // Compute the scores for both words
    int player1Score = ComputeScore(player1Word);
    int player2Score = ComputeScore(player2Word);

    // Display the scores
    Console.WriteLine($"Player 1 Score: {player1Score}");
    Console.WriteLine($"Player 2 Score: {player2Score}");

    // Determine the winner
    if (player1Score > player2Score)
    {
        Console.WriteLine("Player 1 wins! 🏆");
    }
    else if (player2Score > player1Score)
    {
        Console.WriteLine("Player 2 wins! 🏆");
    }
    else
    {
        Console.WriteLine("It's a tie! 🤝");
    }
}
```

</details>

**Explanation**:

- `Console.Write("Player 1, enter your word: ");` prints a message asking Player 1 to enter their word.
- `string player1Word = Console.ReadLine();` captures the word that Player 1 types in.
- We do the same for Player 2.
- We call

 the `ComputeScore` method to calculate the score for both words.
- `if` and `else` statements compare the scores and decide who wins.

---



## Step 7: Add the Main Method to Run the Game

The **Main** method is the starting point of your program. It’s the first thing that runs when you start the program. Here, it will start the Scrabble game.

### What to Do:

1. Outside the `ScrabbleGame` class (below the closing brace `}`), add the following code:

<details>
  <summary>Click here to reveal the Main method code</summary>

```csharp
class Program
{
    static void Main(string[] args)
    {
        // Create a new instance of the game
        ScrabbleGame game = new ScrabbleGame();

        // Start the game
        game.StartGame();
    }
}
```

</details>

**Explanation**:

- `class Program` defines a new class called `Program`.
- The **Main** method (`static void Main(string[] args)`) is where the program starts.
- We create a new instance of `ScrabbleGame` and call the `StartGame()` method to begin the game.

---

## Step 8: Run Your Game!

Let’s see your game in action.

### What to Do:

1. **Save** your work:
   - Click `File` > `Save All`, or press `Ctrl + K, S` on Windows (`Cmd + Option + S` on Mac).

2. **Run the program**:
   - In the terminal, type:

     ```bash
     dotnet run
     ```

3. **Play the game**:
   - Enter words for Player 1 and Player 2 when prompted.
   - See the scores and find out who wins!

**Example**:

```
Player 1, enter your word: hello
Player 2, enter your word: world
Player 1 Score: 8
Player 2 Score: 9
Player 2 wins! 🏆
```

---
## Step 9: Congratulations!

You’ve just built a simple Scrabble-like game in C#! 🎉

![Game Time GIF](https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExZ3RsaTIwaGI2bWJjczhnZ2Eyc3NrNmo0cTJqaXExdzQ4Y2o1ZWNqbyZlcD12MV9naWZzX3NlYXJjaCZjdD1n/j0vs5H7Kcz3Pm9LRDa/giphy.gif)
---

## Optional Enhancements

Want to take it further? Try these:

1. **Input Validation**:
   - Ensure players only enter words containing letters.

2. **Play Again Option**:
   - After the game ends, ask the players if they want to play again.

3. **More Players**:
   - Modify the game to allow more than two players.

---

## Final Thoughts

Great job! You've learned:

- **Classes** for organizing code.
- **Methods** for performing tasks.
- **Arrays** for storing data.
- **Loops** for repeating actions.
- **User input** and **output** in the console.

Keep practicing, and you’ll keep improving. Happy coding! 💻

---
