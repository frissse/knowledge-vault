---
alias: lempel-ziv compressions
definition: compression that works using pointers to repeating patterns
type: term
port: N/A
OSI-layer: physical
more-info: "https://en.wikipedia.org/wiki/Lempel%E2%80%93Ziv%E2%80%93Welch"
---
[[NT Networking MOC]]

a lossless data compression algorithm that works by replacing repeated sequences of data with references to earlier occurrences of the same sequence

for example, if the phrase "the cat" appears many times, instead of writing "the cat" again and again, you could use a symbol, like "", to stand for it. Whenever "" appears in the text, the reader knows it means "the cat." This saves space, making the file smaller.

2 types:
- sliding window
- dictionary based encoding