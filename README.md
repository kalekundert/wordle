Best Wordle Starting Guesses
============================
Wordle is a simple online game, with the goal being to correctly guess a 
5-letter word in 6 or fewer attempts.  Each letter in each guess is colored 
yellow if it is in the unknown word, and green if it is both in the word and in 
the correct position.  The key to doing well is to start by guessing words that 
have common letters in common positions.  This repository hosts a script that 
calculates optimal starting guesses.  Some unique features of this script:

- Correctly account for letter positions and correlations by comparing every 
  possible guess to every possible word in the Wordle database.

- Correctly account for the number of starting guesses.  If only one word is 
  being guessed, all the best letters need to fit into that word.  If two or 
  more words are being guessed, it may be possible to do better by distributing 
  the best letters over words that wouldn't be optimal on their own.

- Find guesses that are Pareto-optimal.  What does this mean?  Each guess can 
  be ranked in two ways: by the number of green letters it is expected to 
  contain, and by the same for yellow letters.  While there may be some overlap 
  between these rankings, they are not the same.  For example, a word that ends 
  in 'y' would rank relatively high in terms of green letters (because 'y' is 
  common at the end of words), but relatively low in terms of yellow letters 
  (because 'y' is not that common overall).  It's not clear *a priori* how much 
  we should factor each ranking when picking the best guess.

  One way to avoid this problem is to not pick a single best guess, but instead 
  to find all the Pareto-optimal guesses.  Collectively, these guesses are 
  called the Pareto front.  A Pareto-optimal guess is one for which no other 
  guess has both more expected green letters and more expected yellow letters.  
  In other words: no matter how much value you personally assign to yellow and 
  green letters, your personal "best guess" will be in the Pareto front.  Think 
  of the Pareto front as a collection of reasonable guesses, from which you can 
  pick the one that best suits your taste.

Here are the commands to run the script:
```
$ git clone git@github.com:kalekundert/wordle.git
$ cd wordle
$ pip install -r requirements.txt
$ py wordle.py -h
```

Here are the results for 1 starting guess:

|   Word | Avg. Green | Avg. Yellow |
|:-------|-----------:|------------:|
|  slate |   0.620734 |    1.683801 |
|  saner |   0.578402 |    1.714903 |
|  stare |   0.572786 |    1.765443 |
|  arose |   0.538661 |    1.768035 |
|  irate |   0.505832 |    1.777970 |
|  later |   0.446220 |    1.778402 |

Here are the results for 2 starting guesses:

| Word 1 | Word 2 | Avg. Green | Avg. Yellow |
|:-------|:-------|-----------:|------------:|
|  sooty |  crane |   1.196544 |    2.667387 |
|  slate |  crony |   1.162851 |    2.947300 |
|  irony |  slate |   1.092009 |    3.033261 |
|  stair |  clone |   1.023326 |    3.046652 |
|  route |  slain |   0.982289 |    3.050540 |

