# Regex Patterns for PoE Stash Tab Searches

GGG has [added regex search to stash tabs](https://www.reddit.com/r/pathofexile/comments/n3pxxc/when_did_we_get_regex_search_in_tabs/gwtxiqb/?context=10) in patch 3.14.

This is a collection of patterns I found useful <sup>- which maybe someday will be turned into a small overlay app</sup>



## How does it work?
With regex search you can search each line of the item text (CTRL+C) case-insensitvely. This is equivalent to the `m` and `i` modifiers.

### Example
Let's say you have two items (only relevant information below):

Item 1
```
Quality: +9%
--------
Requirements:
Level: 70
Str: 62
Dex: 62
--------
+15 to Strength
```

Item 2
```
Quality: +12%
--------
Requirements:
Level: 70
Dex: 62
--------
+23 to Strength
```

#### Basic search
If you want to search for the item with the strength requirement you can use:

This won't work:
```
str
```
since it also matches the mod.

This works:
```
str:
^str
```

#### At least 10% Quality
To do this, you have to define that you want the number after the text `Quality: +` to be 2 digits long and the first digit should be 1 or higher.
```
"quality: \+([1-9][0-9])"
```


This matches the beginning of the 

## Patterns

### Generic

- 6-links
  ```
  "sockets: ([rgbw]-?){6}"
  ```
- 6 number of sockets  
  ```
  "sockets: ([rgbw].?){6}"
  ```
- +10% and higher Quality
  ```
  "quality: \+([1-9][0-9])"
  ```
- 70+ life
  ```
  "(1?[7-9][0-9].+life)"
  ```
- 80+ item level
  ```
  "(level: [8-9][0-9])"
  ```

### Item classes

#### Requirements of class x
- All of class x
  ```
  "class: x"
  ```

- Strength
  ```
  "class: x" "^str" "!(^dex)"
  ```

- Dexterity
  ```
  "class: x" "^dex" "!(^(str|int))"
  ```

- Intelligence
  ```
  "class: x" "^int" "!(^(str|dex))"
  ```

- Strength / Dexterity
  ```
  "class: x" str: dex:
  ```

- Strength / Intelligence
  ```
  "class: x" dex: str:
  ```

- Dexterity / Intelligence
  ```
  "class: x" dex: int:
  ```
