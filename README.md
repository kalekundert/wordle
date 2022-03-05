Best Wordle Starting Guesses
============================
Wordle is a simple online game, with the goal being to correctly guess a 
5-letter word in 6 or fewer attempts.  Each guess gives you more information 
about (i) what letters are not in the word, (ii) what letters are in the word, 
but in the wrong position, and (iii) what letters are in the right position.  
The key to doing well is to start by guessing words that give you as much 
information as possible.

This repository hosts as script that calculates optimal starting guesses.  More 
specifically, this means the starting guesses that leave the fewest possible 
words that the answer could be, on average.  Some other noteworthy features of 
this script:

- Correctly account for letter positions and correlations by comparing every 
  possible guess to every possible word in the Wordle database.

- Correctly account for the number of starting guesses.  If only one word is 
  being guessed, all the best letters need to fit into that word.  If two or 
  more words are being guessed, it may be possible to do better by distributing 
  the best letters over words that wouldn't be optimal on their own.

Here are the commands to run the script:
```
$ git clone git@github.com:kalekundert/wordle.git
$ cd wordle
$ pip install -r requirements.txt
$ py wordle.py -h
```

Here are the top 10 results for 1 starting guess:

| Word  | Avg. Remaining |
|:------|---------------:|
| raise |        61.0009 |
| arise |        63.7257 |
| irate |        63.7793 |
| arose |        66.0212 |
| alter |        69.9918 |
| saner |        70.1257 |
| later |        70.2233 |
| snare |        71.0976 |
| stare |        71.2946 |
| slate |        71.5728 |

Here are the top 10 results for 2 starting guesses:

| Word 1 | Word 2 | Avg. Remaining |
|:-------|:-------|---------------:|
|  trice |  salon |        4.36328 |
|  stole |  cairn |        4.39784 |
|  train |  close |        4.48337 |
|  coast |  liner |        4.49546 |
|  stair |  clone |        4.50324 |
|  scone |  trail |        4.56285 |
|  crate |  solid |        4.77019 |
|  trace |  solid |        4.77711 |
|  decor |  slant |        4.77970 |
|  slant |  cried |        4.79179 |
