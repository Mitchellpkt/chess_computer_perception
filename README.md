# chess_computer_perception
A curious method for creating computational chess intuition through perceptual heshes (for pruning)

## Motivation 

This project is inspired by Matthew Lei's paper [Giraffe: Using Deep Reinforcement Learning to Play Chess](https://arxiv.org/abs/1509.01549) - specificially section 7.1.4 under 'Future Work'

```
7.1.4    Similarity Pruning
Although  Giraffe  already  has  much  smaller  search  trees  than  other  engines  of  similar  strength,
they are still many orders of magnitudes larger than what humans can achieve.  One of the causes
for the difference is in how accurately positions are evaluated.  When positions are not evaluated
accurately, deeper and wider searches are required to compensate.  Closing this gap has been the
primary focus of this project.

Another reason for humans’ high search efficiency is the concept of position similarity.  Humans
can often decide that some moves are effectively equivalent in some situations, and avoid searching
all of them.  This dramatically reduces the average branching factor of search trees.
One possible way to implement this using machine learning is to use a neural network that takes
positions  as  inputs,  and  outputs  sequences  of  numbers  that  can  work  as  ”signatures”  for  each
position.  Unsupervised learning (for example,  clustering) can then be used on the signatures to
gauge degrees of similarity between positions.  However,  it is unclear how such networks can be
trained.

Being able to accurately predict equivalence between positions and moves, whether using machine
learning or other techniques (such as inductive reasoning), is likely going to lead to another major
milestone in achieving more efficient searches.
```

## Approach

Given a board position, generate an appropriate visual representation (e.g. 1 or more PNG images) that encodes the salient features, then send through a perceptual hash function to generate a string that serves as the "signature"

## Example Posotions

*(Note, in retrospect, this isn't the greatest example set, since there's a bishop mobility difference, but it still illustrates the approach)*

Suppose a game begins: 
```
1. e4 e5
2. Nf6 Nc6
```
And now the computer, playing white, wishes to consider whether any of the moves `{3. a3, 3. b3, 3. Bb5}` are similar to each other.

![images/ruy_candidates.png](images/ruy_candidates.png)
