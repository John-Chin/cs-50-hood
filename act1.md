# Activity 1: Billboard Hot 100

### July 1, 2025

### Skiers (John Chin, Ian Olson)

1. List without header  
   `tail -n +3 billboard.tsv `
2. Sorted list 100 to 1  
   `sed '1,2d' billboard.tsv > sh_billboard.tsv`  
   `sort -nr sh_billboard.tsv`

3. List of artists  
   (assume `sed '1,2d' billboard.tsv > sh_billboard.tsv`)  
   `cut -f 3 sh_billboard.tsv `

4. "Justin" count  
   `grep -wc "Justin" billboard.tsv`  
   Gives: 13

5. Number of unique artists  
   `cut -f3 sh_billboard.tsv | sort -n | uniq | wc -l`  
   OR  
   `sed '1,2d' billboard.tsv | cut -f3 | sort | uniq | wc -l`  
   Gives 89

6. Artist with most hits  
   `sed '1,2d' billboard.tsv | cut -f3 | sort | uniq -c | sort`  
   Gives: Justin Bieber - 7

7. List of titles  
   `cut -f2 sh_billboard.tsv`  
   OR  
   `sed '1,2d' billboard.tsv | cut -f2`

8. Most common word in a title  
   `sed '1,2d' billboard.tsv | cut -f2 | tr ' ' '\n' | sort | uniq -c | sort`  
   Gives: You - 11 occurrences
