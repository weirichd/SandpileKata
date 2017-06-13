# The Abelian Sandpile Kata

In this kata, you will be challanged to implement the abelian sandpile. See [this Wikipedia article](https://en.wikipedia.org/wiki/Abelian_sandpile_model) for a more technical description.

<img src="https://upload.wikimedia.org/wikipedia/commons/3/3a/Tannin_heap.jpeg" width=300>

## Description

A *sandpile* is a 2-dimensional square array with the following properties:

#### Each cell of the array contains an integer between zero and three.
You can think of this as being the number of grains of sand in that location on the pile.

|  | `0` | `1` | `2` | `3` |
|:-:|:-:|:-:|:-:|:-:|
| `0` | 2 | 0 | 1 | 1 |
| `1` | 2 | 3 | 0 | 1 |
| `2` | 1 | 0 | 0 | 2 |
| `3` | 3 | 1 | 1 | 0 |
*Example: A* `4 x 4` *sandpile.*

#### Sand can be added at any location.

We can add a grain of sand to any cell in the pile.

|  | `0` | `1` | `2` | `3` |
|:-:|:-:|:-:|:-:|:-:|
| `0` | 2 | 0 | 1 | 1 |
| `1` | 2 | 3 | 1 | 1 |
| `2` | 1 | 0 | 0 | 2 |
| `3` | 3 | 1 | 1 | 0 |
*Example: Adding one to the location* `(2, 1)`.

#### Sand cannot be removed directly.
There is no method to remove sand from a particular location on the pile.
It is possible to remove sand indirectly via the method described below.

#### If adding sand to a location brings it's value above four causes that location to "topple."
This causes its value to be reduced by four and then each adjacent neighbor to increse by one.

|  | `0` | `1` | `2` | `3` |
|:-:|:-:|:-:|:-:|:-:|
| `0` | 2 | 0 | 1 | 1 |
| `1` | 2 | 4 | 1 | 1 |
| `2` | 1 | 0 | 0 | 2 |
| `3` | 3 | 1 | 1 | 0 |

:arrow_down:

|  | `0` | `1` | `2` | `3` |
|:-:|:-:|:-:|:-:|:-:|
| `0` | 2 | 1 | 1 | 1 |
| `1` | 3 | 0 | 2 | 1 |
| `2` | 1 | 1 | 0 | 2 |
| `3` | 3 | 1 | 1 | 0 |
*Example: Adding one to the location* `(1, 1)` *increased it's value to* `4`. *This caused a topple, which resulted in* `(1, 1)` *being set to* `0` *and the four adjacent cells going up by one.*

#### If a cell on the boundary topples, grains fall off the pile and are removed.
Sand is removed from the table when a cell on the boundary topples. This could either be an edge cell, or a corner cell.

|  | `0` | `1` | `2` | `3` |
|:-:|:-:|:-:|:-:|:-:|
| `0` | 2 | 1 | 1 | 1 |
| `1` | 4 | 0 | 2 | 1 |
| `2` | 1 | 1 | 0 | 2 |
| `3` | 3 | 1 | 1 | 0 |

:arrow_down:

|  | `0` | `1` | `2` | `3` |
|:-:|:-:|:-:|:-:|:-:|
| `0` | 3 | 1 | 1 | 1 |
| `1` | 0 | 1 | 2 | 1 |
| `2` | 2 | 1 | 0 | 2 |
| `3` | 3 | 1 | 1 | 0 |
*Example: Adding a grain to cell* `(0, 1)` *caused it to topple. Because it was on the boundary, its three neighbors each increased by one, and the last grain "fell off the pile"*

#### Toppling could cause other cells to topple.
If a cell topples and one of its neighbors grows above four grains, then the toppling rule applies to that neighbor.
This will continue until all cells in the pile have less than four grains.

|  | `0` | `1` | `2` | `3` |
|:-:|:-:|:-:|:-:|:-:|
| `0` | 3 | 1 | 1 | 1 |
| `1` | 0 | 1 | 2 | 1 |
| `2` | 4 | 1 | 0 | 2 |
| `3` | 3 | 1 | 1 | 0 |

:arrow_down:

|  | `0` | `1` | `2` | `3` |
|:-:|:-:|:-:|:-:|:-:|
| `0` | 3 | 1 | 1 | 1 |
| `1` | 1 | 1 | 2 | 1 |
| `2` | 0 | 2 | 0 | 2 |
| `3` | 4 | 1 | 1 | 0 |

:arrow_down:

|  | `0` | `1` | `2` | `3` |
|:-:|:-:|:-:|:-:|:-:|
| `0` | 3 | 1 | 1 | 1 |
| `1` | 1 | 1 | 2 | 1 |
| `2` | 1 | 2 | 0 | 2 |
| `3` | 0 | 2 | 1 | 0 |
*Example: Adding two grains to* `(0, 2)` *caused that location to topple. This in turn caused the location* `(0, 3)` *to topple.* After this, each cell has less than four grains, so topplig ceases.
