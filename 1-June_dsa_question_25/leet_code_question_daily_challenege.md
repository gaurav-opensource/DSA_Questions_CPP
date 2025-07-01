# Re-run after code execution state reset to regenerate the markdown file

alice_typing_md = """
# 🧠 Clumsy Typist – Possible Original Strings

---

## ✅ Question: Total Possible Original Strings

**🧾 Problem Statement:**  
Alice is attempting to type a specific string on her computer. However, she may be clumsy and could press a key for too long, resulting in a character being typed **multiple times**.

Although Alice tried to focus, she might have made **at most one** such repetition mistake.

You're given a string `word`, which represents the final output displayed on Alice's screen.

🔁 Return the total number of **possible original strings** Alice might have intended to type.

---

## 🧪 Example:

- Input: `"aab"`  
  Possible original strings: `"ab"`, `"aab"` → Output: `2`

- Input: `"abc"`  
  No repeated characters → Output: `1`

- Input: `"aabb"`  
  Possible original strings: `"abb"`, `"aab"`, `"aabb"` → Output: `3`

---

## 🧠 Approach:

1. We iterate through the string.
2. Whenever we see a **pair of repeated characters**, that could be due to Alice's clumsy typing.
3. For each such repetition, it might be **optional**, so it increases the number of possible interpretations.
4. Since Alice can make **at most one mistake**, the total number of possible original strings = **number of repeated positions + 1**

---

## 💻 Pseudocode (C++ Style):

```cpp
class Solution {
public:
    int possibleStringCount(string word) {
        int count = 1;

        for (int i = 1; i < word.length(); i++) {
            if (word[i] == word[i - 1]) {
                count++;
            }
        }

        return count;
    }
};
