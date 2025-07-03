import random
import string

def generate_password(length=12, use_upper=True, use_lower=True, use_digits=True, use_symbols=True):
    if not (use_upper or use_lower or use_digits or use_symbols):
        raise ValueError("At least one character type must be selected.")

    characters = ''
    if use_upper:
        characters += string.ascii_uppercase
    if use_lower:
        characters += string.ascii_lowercase
    if use_digits:
        characters += string.digits
    if use_symbols:
        characters += string.punctuation

    password = ''.join(random.choice(characters) for _ in range(length))
    return password

def password_strength(password):
    length = len(password)
    criteria = [
        any(c.islower() for c in password),
        any(c.isupper() for c in password),
        any(c.isdigit() for c in password),
        any(c in string.punctuation for c in password)
    ]
    score = sum(criteria)

    if length >= 12 and score == 4:
        return "Strong 💪"
    elif length >= 8 and score >= 3:
        return "Moderate 👍"
    else:
        return "Weak ⚠️"

def main():
    print("🔐 Password Generator 🔐")
    length = int(input("Enter password length (e.g., 12): "))
    use_upper = input("Include uppercase letters? (y/n): ").lower() == 'y'
    use_lower = input("Include lowercase letters? (y/n): ").lower() == 'y'
    use_digits = input("Include numbers? (y/n): ").lower() == 'y'
    use_symbols = input("Include symbols? (y/n): ").lower() == 'y'

    try:
        password = generate_password(length, use_upper, use_lower, use_digits, use_symbols)
        strength = password_strength(password)
        print("\n✅ Generated Password:", password)
        print("🔒 Password Strength:", strength)
    except ValueError as e:
        print("Error:", e)

if __name__ == "__main__":
    main()