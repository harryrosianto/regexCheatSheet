# Regular Expressions (Regex) Cheatsheet

## Basics of Regular Expressions

### Literal Characters
- **Characters**: `a`, `b`, `1`, etc. match themselves.
  - Example: `abc` matches the string "abc".

### Metacharacters
- Special characters with specific meanings in regex:
  - `^`, `$`, `.`, `*`, `+`, `?`, `\`, `[`, `]`, `|`, `(`, `)`, `{`, `}`.

### Character Classes
- **[abc]**: Matches any one of the characters a, b, or c.
- **[a-z]**: Matches any one character from a to z.
- **[^abc]**: Matches any one character except a, b, or c.

### Predefined Character Classes
- **\d**: Matches any digit (equivalent to `[0-9]`).
- **\D**: Matches any non-digit.
- **\w**: Matches any word character (alphanumeric + underscore).
- **\W**: Matches any non-word character.
- **\s**: Matches any whitespace character.
- **\S**: Matches any non-whitespace character.

### Anchors
- **^**: Matches the start of a string.
- **$**: Matches the end of a string.

### Quantifiers
- **\***: Matches 0 or more occurrences.
- **+**: Matches 1 or more occurrences.
- **?**: Matches 0 or 1 occurrence.
- **{n}**: Matches exactly n occurrences.
- **{n,}**: Matches n or more occurrences.
- **{n,m}**: Matches between n and m occurrences.

### Groups and Alternation
- **()**: Groups patterns together.
- **|**: Alternation, matches either the pattern before or the pattern after.
  - Example: `(abc|def)` matches either "abc" or "def".

## Reading a Regex Example

### Example: `/^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$/`
- **Anchors**:
  - `^`: Asserts the position at the start of the string.
  - `$`: Asserts the position at the end of the string.

- **Positive Lookahead**:
  - `(?=...)`: Asserts that what follows the position is ... (the lookahead condition).
  - `(?=.*[A-Za-z])`: Asserts that there is at least one letter (upper or lower case) somewhere in the string.
  - `(?=.*\d)`: Asserts that there is at least one digit somewhere in the string.

- **Character Class and Quantifier**:
  - `[A-Za-z\d]`: Matches any letter (uppercase or lowercase) or digit.
  - `{8,}`: Matches 8 or more of the preceding character class.

### How the Regex Works Together
- `^`: Ensures the pattern matches from the start of the string.
- `(?=.*[A-Za-z])`: Ensures there is at least one letter.
- `(?=.*\d)`: Ensures there is at least one digit.
- `[A-Za-z\d]{8,}`: Matches a sequence of at least 8 characters, where each character is either a letter or a digit.
- `$`: Ensures the pattern matches until the end of the string.

## Practical Examples

### Email Validation
- **Regex**: `/^[^\s@]+@[^\s@]+\.[^\s@]+$/`
- **Breakdown**:
  - `^[^\s@]+`: Starts with one or more characters that are not spaces or @.
  - `@`: Followed by an @ symbol.
  - `[^\s@]+`: Followed by one or more characters that are not spaces or @.
  - `\.`: Followed by a dot.
  - `[^\s@]+$`: Ends with one or more characters that are not spaces or @.

### Phone Number Validation (10 digits)
- **Regex**: `/^\d{10}$/`
- **Breakdown**:
  - `^`: Ensures the match starts at the beginning of the string.
  - `\d{10}`: Matches exactly 10 digits.
  - `$`: Ensures the match ends at the end of the string.

### URL Validation
- **Regex**: `/^(https?:\/\/)?([\da-z.-]+)\.([a-z.]{2,6})([\/\w .-]*)*\/?$/`
- **Breakdown**:
  - `^(https?:\/\/)?`: Optionally matches `http://` or `https://`.
  - `([\da-z.-]+)`: Matches the domain name (one or more digits, letters, dots, or hyphens).
  - `\.([a-z.]{2,6})`: Matches the domain extension (e.g., `.com`, `.org`).
  - `([\/\w .-]*)*`: Matches the path (optional).
  - `\/?$`: Optionally matches a trailing slash.
