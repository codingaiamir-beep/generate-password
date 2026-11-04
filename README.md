# Password Generator

A simple command-line password generator written in Python. It uses the `secrets` module, which is designed for security-sensitive randomness (unlike `random`).

## Features

- Custom password length
- Generate multiple passwords in one run
- Every password contains at least one lowercase letter, one uppercase letter, one digit, and one special character
- Approximate strength rating based on entropy
- Input validation

## Requirements

- Python 3.6 or newer (needed for `secrets`)
- No external packages

## Usage

Save the script as `password_generator.py`, then run:

```
python password_generator.py
```

Example session:

```
Password length (min 4): 16
How many passwords: 3

Strength: Very strong 🟢 (~99 bits of entropy)

 1. k#9Qm-vT2xL_aB7=
 2. Zp4=wN8_cJ!r5hYd
 3. 3eU-gS&x7Fm=Kq2L
```

Note: if emojis do not display correctly on Windows, run `chcp 65001` in the terminal first.

## How It Works

1. One character is picked from each category (lowercase, uppercase, digits, special).
2. The remaining characters are picked at random from the full character set.
3. The list is shuffled so the guaranteed characters do not sit in fixed positions.
4. Entropy is estimated as `length * log2(size of character set)`.

## Strength Levels

| Entropy (bits) | Rating      |
|----------------|-------------|
| Below 40       | Weak 🔴      |
| 40 to 59       | Medium 🟠    |
| 60 to 79       | Strong 🟡    |
| 80 and above   | Very strong 🟢 |

The entropy value is an approximation. It assumes every character is chosen uniformly from the full set and does not account for the small effect of the "at least one of each type" rule.

## Configuration

Edit the constants at the top of the script:

```python
SPECIAL = "!@#$%^&*()-_="
```

Change `SPECIAL` to add or remove special characters. Limits for length (4 to 128) and count (1 to 50) are set in `ask_int` and `main`.

## Possible Improvements

- Choose which character categories to include
- Exclude look-alike characters (`O/0`, `l/1`)
- Save passwords to a file
- GUI with `tkinter`

## License

Free to use for learning and personal projects.
