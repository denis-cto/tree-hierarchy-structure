# tree-hierarchy-structure
Database Tree hierarchy structure for FAST O(1) access search for children and parents, extension of Materialized Path
The main Idea is using 62-bit structure for storing path key and fixed-width of a path key. Combination of these statements allow us to use VARCHAR(255) field to store 85 deep nested levels, with maximum of 238'328 children on each level.
Why 62-bit? 
We will use numbers from 0..9, small letters a..z, capital letters A..Z, summary 10+26+26=62 bit.
Why use numbers, small and capital letters?
Beacause it's very easy to distinguish different child and parents with just looking at them. Another issue is sorting order - if we use numbers, then small letters, then capitlal letters, their char codes will be in in one sequence order. 
What does it mean 62-bit?
Well, we asssume that we have one byte to store the order of something.
If we will use numbers through 0..9 we will have 10 combinations.
if we will user small letters, we eill have a..z - 26 combinations,
If we will add Capital Letters, will will also have A..Z - 26 combinations,
So, if we combine these assumptions in one
We will have 10+26+26=62 combinations, which is equal to 62-bit value.
We know that DB are using ASCII i char codes (for sorting, ordering), so numbers, small letters, capital letters are the chains for 
