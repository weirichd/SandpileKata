# The Abelian Sandpile Kata

In this kata, you will be challanged to implement the abelian sandpile. See [this Wikipedia article](https://en.wikipedia.org/wiki/Abelian_sandpile_model) for a more technical description.

<img src="https://upload.wikimedia.org/wikipedia/commons/3/3a/Tannin_heap.jpeg" width=300>

## Description

A *sandpile* is a 2-dimensional square array with the following properties:

* Each cell of the array contains an integer between zero and three. You can think of this as being the number of grains of sand in that location on the pile.

|  | `0` | `1` | `2` | `3` |
|:-:|:-:|:-:|:-:|:-:|
| `0` | 2 | 0 | 1 | 1 |
| `1` | 3 | 3 | 0 | 1 |
| `2` | 1 | 0 | 0 | 2 |
| `3` | 3 | 1 | 1 | 0 |

Adding a grain of sand at `(2,1)`:

|  | `0` | `1` | `2` | `3` |
|:-:|:-:|:-:|:-:|:-:|
| `0` | 2 | 0 | 1 | 1 |
| `1` | 3 | 3 | <span style="color:red">1</span> | 1 |
| `2` | 1 | 0 | 0 | 2 |
| `3` | 3 | 1 | 1 | 0 |



* A grain of sand can be added at any location, but no grains can ever be removed.
