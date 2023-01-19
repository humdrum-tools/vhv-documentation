

## Selective analysis ##

In addition to calculating the scale degrees of all `**kern` spines in
a file, The deg filter can select a subset of the music to analyzed.
Spines can be selected either by using `-s` to select the nth spine in
the file, or with `-k` to select the nth `**kern` spine in the file.



### Selecting spines with -s ###


| Example | Meaning |
| ------- | ------- |
| `-s 1`  | Analyze only the first (leftmost) spine in the input data. |
| `-s 1,4` | Analyze the first and fourth spine. |
| `-s 2-4` | Analyze the second, third and fourth spines. |
| `-s $`    | Analyze the last spine. |
| `-s 3,$`  | Analyze the thrid and last spines. |
| `-s 1-4,6,9-$` | Analyze the first, second, third, fourth, sixth, and nineth through last spines. |
| `-s $1` | Analyze the penultimate spine. |
| `-s $2-$` | analyze from two spines before the end to the last spine. |



### Selecting spines with -k ###

| Example | Meaning |
| ------- | ------- |
| `-k 1`  | Analyze only the first (leftmost) kern spine in the input data. |
| `-k 1,4` | Analyze the first and fourth kern spine. |
| `-k 2-4` | Analyze the second, third and fourth kern spines. |
| `-k $`    | Analyze the last kern spine. |
| `-k 3,$`  | Analyze the thrid and last kern spines. |
| `-k 1-4,6,9-$` | Analyze the first, second, third, fourth, sixth, and nineth through last kern spines. |
| `-k $1` | Analyze the penultimate kern spine. |
| `-k $2-$` | analyze from two kern spines before the end to the last kern spine. |



