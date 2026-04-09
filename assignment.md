

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

**Learning Objectives:**
- **Cybersecurity Concept:** 
  - Demonstrate the importance of randomness and diversity in secure password generation.  
  - Implement proper random generation and validation to make passwords harder to crack.


- **Programming Skills:**  
  - Use Python’s `random` and `string` modules for randomization and character handling.  
  - Implement **control flow** to handle user input and conditions (e.g., missing character sets, length checks).  
  - Apply **string manipulation** and **list operations** to combine and shuffle characters.  
  - Write **robust error handling** for input validation.  



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

#### **Example Usage**
```
print(generate_password(12, use_lowercase=True, use_uppercase=True, use_digits=True, use_special_chars=True))
# Example Output: 'aB3$dE5&hI2@'

print(generate_password(3, use_lowercase=True, use_uppercase=True))
# Example Output: "Error: Length is too short to include all selected character types!"
```

---


## Part 2: Enforcing Strong Password Requirements

Validating password strength helps prevent the use of weak passwords.

**Learning Objectives:**
- **Cybersecurity Concept:** 
  -  Show what constitutes a strong password and why enforcing complexity reduces vulnerability to attacks.  
  -  Implement real-world password policies like those used in authentication systems.


- **Programming Skills:**  
  - Use **conditional logic** to validate multiple password strength rules.  
  - Apply **string methods** and possibly **regular expressions** to detect character types.  
  - Generate **user-friendly feedback** describing missing security components.  


### **Requirements**

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

**Learning Objectives:**
- **Cybersecurity Concept:** 
  -  Quantify password strength mathematically by computing the number of possible combinations. 
  -  Demonstrate how password complexity directly affects the theoretical difficulty of brute-force attacks.

- **Programming Skills:**  
  - Use **mathematical formulas and exponents** to compute possibilities.  
  - Identify which **character sets** a given password uses.  
  - Strengthen **logical decomposition skills** (breaking down the problem into character set detection and calculation).  


### **Requirements**

#### **Function Specifications:**

* Function Name: `calculate_possibilities`
* Parameter:
	* `password (str)`: The password string to be analyzed.
* Calculations:
	- Determine Character Sets Used: Identify which character sets are present in the password (lowercase, uppercase, digits, special characters).
	- Calculate Total Possibilities: Use the formula: `total_possibilities = (character_set_size) ** (password_length)`
		- `character_set_size`: The total number of unique characters from the sets used.
		- `password_length`: The length of the password.

#### **Example Usage**
```
possibilities = calculate_possibilities("P@ssw0rd")
print(f"Total possible combinations: {possibilities}")

# Example Output: Total possible combinations: 1517108809906561
```

---

## Part 4: Estimating Time to Crack a Password

Estimating cracking time helps evaluate the practical security of a password.

**Learning Objectives:**
- **Cybersecurity Concept:** 
  -  Relate theoretical password strength to practical cracking difficulty (introducing brute-force attack modeling).  
  -  Show how exponential growth in possible combinations affects cracking times, reinforcing the value of password complexity.

- **Programming Skills:**  
  - Integrate results from **other functions** (`calculate_possibilities`), encouraging **modular programming**.  
  - Perform **unit conversions** and arithmetic calculations for time estimation.  
  - Use **formatting** for a clear output presentation.  


### **Requirements**

#### **Function Specifications:**

* Function Name: `estimate_password_cracking_time`
* Parameter:
	- `password (str)`: The password string to be evaluated.
* Assumptions:
	- Attack Speed: Assume an attacker can attempt 1,000,000 passwords per second.
* Calculations:
	- Time in Seconds: `time_in_seconds = total_possibilities / guesses_per_second`
	- Time in Years: `time_in_years = time_in_seconds / (60 * 60 * 24 * 365.25)`
* Use Previous Function:
     -  Utilize the `calculate_possibilities` function to get `total_possibilities`.

#### Example Usage

```
seconds, years = estimate_password_cracking_time("P@ssw0rd")
print(f"Estimated time to crack: {seconds} seconds (~{years} years)")

# Example Output: Estimated time to crack: 1517108809.906561 seconds (~48.07427719175605 years)
```


---

## Part 5: Simulating a Dictionary Attack

A dictionary attack is a method used by attackers to crack passwords by systematically testing all words in a predefined list, typically a list of common passwords or words from a dictionary. This attack exploits the tendency of users to choose simple and common passwords.

**Learning Objectives:**
- **Cybersecurity Concept:** 
  -  Simulate dictionary attacks to see how attackers exploit weak passwords.  
  -  Provide hands-on insight into how attackers approach password cracking and why using uncommon passwords is essential.
- **Programming Skills:**  
  - Perform **file handling** (reading password lists safely).  
  - Use **loops** and **conditions** to simulate attack attempts.  
  - Apply **timing functions** (`time` module) to measure performance.  
  - Implement **exception handling** for missing files or other runtime issues.  
  - Track **iterations and progress metrics**.  

### Requirements
#### Function Specifications:

* Function Name: `dictionary_attack`
* Parameters:
	- `target_password (str)`: The password string that the attacker is trying to guess.
	- `dictionary_file (str)`: The path to the file containing a list of common passwords (default is "Rockyou.txt").

#### **Functionality:**
* Read Passwords from File:
	- The function should read a list of passwords from the specified `dictionary_file`.
	- Use a try-except block to handle the case where the file does not exist.
* Simulate Attack:
	- Start a timer to measure how long the attack takes.
	- Initialize an `attempts` counter to keep track of the number of passwords tried.
	- Loop through each password in the file:
		- Increment the `attempts` counter.
		- Compare the current password (after stripping whitespace) with the `target_password`.
		- If a match is found:
			- Calculate the elapsed time.
			- Return the elapsed time and the number of attempts.
   
#### **Return Value:**
* If the `target_password` is found in the list, return the time taken and the number of attempts.
* If the `target_password` is not found after checking all passwords, return `None` and the total number of attempts.

#### **Error Handling:**
If the `dictionary_file` does not exist, the function should handle the `FileNotFoundError` and return an appropriate message or value.

#### **Example Usage**
```
elapsed_time, attempts = dictionary_attack("password123")
if elapsed_time:
    print(f"Password found in {elapsed_time:.2f} seconds after {attempts} attempts.")
else:
    print(f"Password not found after {attempts} attempts.")
```

#### **Sample Outputs:**
If the password is found: 
```
Password found in 0.05 seconds after 123 attempts.
```

If the password is not found: 
```
Password not found after 1000 attempts.
```




