# Regex Patterns for PoE Stash Tab Searches

GGG has [added regex search to stash tabs](https://www.reddit.com/r/pathofexile/comments/n3pxxc/when_did_we_get_regex_search_in_tabs/gwtxiqb/?context=10) in patch 3.14.

This is a collection of patterns I found useful <sup>- which maybe someday will be turned into small overlay app</sup>

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
  "quality: \+([12][0-9])"
  ```
- 70+ life
  ```
  "(1?[7-9][0-9].+life)"
  ```

### Item classes

#### Requirements of class x
- All of class x
  ```
  "class: x"
  ```

- Strength
  ```
  class x "^str" "!(^dex)"
  ```

- Dexterity
  ```
  class x "^dex" "!(^(str|int))"
  ```

- Intelligence
  ```
  class x "^int" "!(^(str|dex))"
  ```

- Strength / Dexterity
  ```
  class x str: dex:
  ```

- Strength / Intelligence
  ```
  class x dex: str:
  ```

- Dexterity / Intelligence
  ```
  class x dex: int:
  ```
