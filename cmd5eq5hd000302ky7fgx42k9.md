---
title: "Week 1: Arrays & Hashmaps – Kicking Off the NeetCode Grind"
seoTitle: "Arrays & Hashmaps: Week 1 Guide"
seoDescription: "NeetCode's array and hashmap challenges enhance problem-solving, optimize runtimes, and improve coding interview strategies with key takeaways"
datePublished: Wed Jul 16 2025 03:34:06 GMT+0000 (Coordinated Universal Time)
cuid: cmd5eq5hd000302ky7fgx42k9
slug: week-1-arrays-and-hashmaps-kicking-off-the-neetcode-grind
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1752635501548/9d2d33cd-874b-4643-a433-baf86351e0d8.png
tags: interview, algorithms, python, data-structures, technical-interview

---

Ok so this week I tackled the first batch of array and hashmap problems from NeetCode. I went from dreading edge cases to actually enjoying some of the challenges. Still working on speeding up my runtime and trusting my initial instincts and honestly I still did struggled through some of the Medium problems like Valid Sudoku. I think I have to take another stab at that one next week.

The problems I did manage to complete were:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752634906670/67257f52-c7ca-453b-b568-b59d12f90243.png align="center")

If you want to take a look at my solutions, you can find my code here:

%[https://github.com/ChicanaCodes/neetcode-150] 

I’m following this strategy every time I start working on a problem.

1. I time myself for 60 minutes using a Pomodoro timer - [https://pomodorokitty.com/](https://pomodorokitty.com/)
    
2. I create a function signature and use python doc strings to
    
    * restate the problem
        
    * come up with example inputs/outputs
        
    * identify edge cases
        
    * pseudocode my approach
        
    * draw out any data structures I will use during my problem
        

```python
def group_anagrams(strs: list[str]) -> list[list[str]]:
    """
    Given an array of strings, group the anagrams together
    and return a 2D array of the grouped anagrams.

    Example:
    Input: strs = ["eat","tea","tan","ate","nat","bat"]
    Output: [["bat"],["nat","tan"],["ate","eat","tea"]]

    Edge Cases: 
    - Can there be an empty string?
    - Can there be strings with only one character?
    - Can there be the same string repeated?
    - Can there be null strings?
    - Can the strings have trailing spaces?
    - What to return if there are no anagrams?

    Approach:
    - Create a dictionarty to store the anagrams
    - Iterate through the strings and sort the characters in each string
    - If the sorted string is not in the dictionary, add it as a key and the original string as a value
    - If the sorted string is in the dictionary, add the original string to the value list
    - Return the values of the dictionary as a list of lists

    Sample anagrams for following input: ["eat","tea","tan","ate","nat","bat"]
    {
        "aet": ["eat","tea","ate"],
        "ant": ["tan","nat"],
        "abt": ["bat"]
    }
    """
    pass
```

3. After writing out the pseudocode, I actually code out my solution and add test cases using Python’s doctest library
    
4. As I wrap up my solution I add comments and discus Time and Space complexity of my solution
    
5. If I come up with a more optimal solution, I’d update my code and then again discuss the optimizations
    

```python
def group_anagrams(strs: list[str]) -> list[list[str]]:
    """
    Given an array of strings, group the anagrams together
    and return a 2D array of the grouped anagrams.

    Example:
    Input: strs = ["eat","tea","tan","ate","nat","bat"]
    Output: [["bat"],["nat","tan"],["ate","eat","tea"]]

    Edge Cases: 
    - Can there be an empty string?
    - Can there be strings with only one character?
    - Can there be the same string repeated?
    - Can there be null strings?
    - Can the strings have trailing spaces?
    - What to return if there are no anagrams?

    Approach:
    - Create a dictionarty to store the anagrams
    - Iterate through the strings and sort the characters in each string
    - If the sorted string is not in the dictionary, add it as a key and the original string as a value
    - If the sorted string is in the dictionary, add the original string to the value list
    - Return the values of the dictionary as a list of lists

    >>> group_anagrams(["eat","tea","tan","ate","nat","bat"])
    [['ate', 'eat', 'tea'], ['bat'], ['nat', 'tan']]

    >>> group_anagrams(["x"])
    [['x']]

    >>> group_anagrams(["",""])
    [['', '']]

    >>> group_anagrams(["act","pots","tops","cat","stop","hat"])
    [['act', 'cat'], ['hat'], ['pots', 'stop', 'tops']]

    Sample anagrams for following input: ["eat","tea","tan","ate","nat","bat"]
    {
        "aet": ["eat","tea","ate"],
        "ant": ["tan","nat"],
        "abt": ["bat"]
    }
    """
    anagrams = {}
    for string in strs:
        sorted_string = ''.join(sorted(string))
        if sorted_string in anagrams: 
            anagrams[sorted_string].append(string)
        else:
            anagrams[sorted_string] = [string]

    # Sort each group and then sort the list of groups for consistent output
    result = [sorted(group) for group in anagrams.values()]
    result.sort()
    return result

# Time complexity: O(n * k log k) - n is the number of strings, k is the length of the longest string
# Space complexity: O(n * k) - storing the strings in the dictionary

if __name__ == "__main__":
    import doctest
    if doctest.testmod().failed == 0:
        print("\n** ALL TESTS PASSED. AWESOME WORK! **\n")
```

Although I haven't participated in many coding interviews, I've gained valuable insights from several informational interviews with senior engineers. A significant aspect of the interview process is evaluating how candidates solve problems and articulate their strategies. This involves gathering requirements and identifying edge cases, much like the tasks we perform as software engineers.

I believe I'm starting to grasp the process, and I plan to practice thinking out loud, even if it feels a bit awkward. The more I practice verbalizing my thoughts while tackling these problems, the more natural it will become.

## 💡 Key Takeaways  

* **Dictionaries (hashmaps) reduce time complexity** when you need constant-time lookups. They’re game-changers for frequency counts, index tracking, and pairing values (e.g., Two Sum).
    

* **Sorting isn’t always the most optimal solution.** While it can simplify some problems (like grouping anagrams), it adds O(n log n) time, which isn’t ideal if you can solve it in O(n) using hashing.
    
* **Think about what data structure gives you the fastest access.** If you’re looping + checking something frequently, ask: “Can I store this in a set or dict instead?”
    
* **Start with brute force, then optimize.** Sometimes writing the naive solution first helps you identify bottlenecks before jumping to hashmap/set optimizations.
    

> I still catch myself second-guessing every answer, but I’m trying to focus on consistency over perfection. One problem a day is more progress than no problems a week.