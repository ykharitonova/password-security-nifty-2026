

# Password Security
In today's digital age, the security of online accounts and personal data heavily relies on the strength of passwords. Passwords act as the first line of defense against unauthorized access to sensitive information such as financial records, personal communications, and private identification details. Despite their crucial role, many users continue to choose simple, easily guessable passwords, making them vulnerable to cyber threats.

## What is a Brute Force Attack?

A brute force attack is a method used by attackers to gain unauthorized access by systematically trying every possible combination of characters until the correct password is found. Modern computers can perform millions of guesses per second, which means that weak passwords, especially those that are short or follow predictable patterns, are highly susceptible to being cracked in a short amount of time.

## Real-World Implications

Weak passwords can have severe consequences:
* **Personal Risks**: Unauthorized access to personal accounts can lead to identity theft, financial loss, and privacy violations.
* **Business Risks**: For companies, weak passwords can result in data breaches, loss of customer trust, financial penalties, and legal consequences.
* **Societal Impact**: Large-scale security breaches can have widespread effects, potentially impacting national security and economic stability.

## Assignment Overview

In this assignment, you will explore the principles of password security and implement functions in Python to:

1. Generate secure passwords.
2. Enforce strong password requirements.
3. Calculate the number of possible password combinations.
4. Estimate the time it would take to crack a password using brute force.
5. Simulate a dictionary attack.

Through this process, you will enhance your understanding of cybersecurity concepts while practicing fundamental Python programming skills such as string manipulation, control flow, functions, and file handling.

You’ll be working with the `funcs.py` file and can run the `main.py` file to create a Tkinter interface where you can interactively test your implementation.


## Part 1: Generating a Secure Password

Randomly generated passwords that include a mix of character types are significantly more resistant to brute force attacks and other password-cracking techniques.

### Requirements

#### **Character Inclusion**: 
The password must contain at least one character from each selected character pool:
- Lowercase letters
- Uppercase letters
- Digits
- Special characters

#### **Randomization**:
The remaining characters (after including one from each selected pool) should be randomly selected from the combined pool of all selected character types.
The final password should be shuffled to ensure randomness and prevent predictable patterns.

#### **Function Specifications**:

- Function Name: `generate_password`
- Parameters:
	- `length (int)`: The desired length of the password.
	- `use_lowercase (bool)`: Include lowercase letters (default True).
	- `use_uppercase (bool)`: Include uppercase letters (default True).
	- `use_digits (bool)`: Include digits (default True).
	- `use_special_chars (bool)`: Include special characters (default True).
	
#### **Error Handling**: 
If none of the character types are selected (all `use_*` parameters are False), the function should return an error message:  `"Error: At least one character type must be selected!"`. If the specified `length` is less than the number of selected character pools, the function should return an error message: `"Error: Length is too short to include all selected character types!"`

#### Example Usage
```
print(generate_password(12, use_lowercase=True, use_uppercase=True, use_digits=True, use_special_chars=True))
# Example Output: 'aB3$dE5&hI2@'

print(generate_password(3, use_lowercase=True, use_uppercase=True))
# Example Output: "Error: Length is too short to include all selected character types!"
```

---


## Part 2: Enforcing Strong Password Requirements

Validating password strength helps prevent the use of weak passwords.

### Requirements

#### **Function Specifications:**

* Function Name: `enforce_strong_password_requirements`
* Parameter:
		* `password (str)`: The password string to be evaluated.
* Password Strength Criteria:
	- Minimum Length: At least 8 characters.
	- Character Types:
		- At least one lowercase letter.
		- At least one uppercase letter.
		- At least one digit.
		- At least one special character.

#### **Error Handling**: 
If the password meets all requirements, the function should return a success message: 
`"Your password is strong and meets all requirements!"`.
If the password does not meet all requirements, the function should return a message indicating which requirements are missing.

#### **Example Usage**
```
print(enforce_strong_password_requirements("P@ssw0rd"))
# Output: "Your password is strong and meets all requirements!"

print(enforce_strong_password_requirements("password"))
# Output:
# Your password is missing:
# - At least one uppercase letter
# - At least one digit
# - At least one special character
```

---


## Part 3: Calculating Password Possibilities

Calculating the total number of possible combinations helps assess how difficult a password is to crack via brute force.

### Requirements

#### Function Specifications:
* Function Name: `calculate_possibilities`
* Parameter:
		* `password (str)`: The password string to be analyzed.
* Calculations:
		- Determine Character Sets Used: Identify which character sets are present in the password (lowercase, uppercase, digits, special characters).
		- Calculate Total Possibilities: Use the formula: `total_possibilities = (character_set_size) ** (password_length)`
			- `character_set_size`: The total number of unique characters from the sets used.
			- `password_length`: The length of the password.

#### Example Usage
```
possibilities = calculate_possibilities("P@ssw0rd")
print(f"Total possible combinations: {possibilities}")

# Example Output: Total possible combinations: 1517108809906561
```

---

## Part 4: Estimating Time to Crack a Password

Estimating cracking time helps evaluate the practical security of a password.

### Requirements

#### Function Specifications:
Function Name: `estimate_password_cracking_time`
