# Task 3 - Password Generator
import random
import string
def generate_password(length=12, use_digits=True, use_special=True):
    # Base characters: letters
    characters = string.ascii_letters      
    if use_digits:
        characters += string.digits
    if use_special:
        characters += string.punctuation
    if length < 4:
        return "Password length should be at least 4 characters."
    password = ''.join(random.choice(characters) for _ in range(length))
    return password
def main():
    print("===== CODSOFT TASK 3: PASSWORD GENERATOR =====")
    try:
        length = int(input("Enter password length: "))
    except ValueError:
        print("Invalid input! Please enter a number.")
        return
    use_digits = input("Include digits? (y/n): ").lower() == 'y'
    use_special = input("Include special characters? (y/n): ").lower() == 'y'   
    password = generate_password(length, use_digits, use_special)
    print(f"\n Generated Password: {password}")
if _name_ == "_main_":
    main()
