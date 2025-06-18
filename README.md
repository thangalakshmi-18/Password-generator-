# Password-generator-
import string
import secrets

def secure_password_generator(length=12, use_upper=True, use_digits=True, use_symbols=True):
    if length < 4:
        return "Password too short! Minimum length is 4."

    # Base character sets
    lower = string.ascii_lowercase
    upper = string.ascii_uppercase if use_upper else ''
    digits = string.digits if use_digits else ''
    symbols = string.punctuation if use_symbols else ''

    all_chars = lower + upper + digits + symbols

    if not all_chars:
        return "Error: No character sets selected."

    # Ensure at least one of each selected type is included
    password = [
        secrets.choice(lower),
        secrets.choice(upper) if use_upper else '',
        secrets.choice(digits) if use_digits else '',
        secrets.choice(symbols) if use_symbols else ''
    ]

    # Fill the rest of the password length
    while len(password) < length:
        password.append(secrets.choice(all_chars))

    # Shuffle to make it random
    secrets.SystemRandom().shuffle(password)
    return ''.join(password)

# Example usage
print("🔐 Secure Password Generator 🔐")
try:
    length = int(input("Enter password length (min 4): "))
    upper = input("Include uppercase letters? (y/n): ").lower() == 'y'
    digits = input("Include numbers? (y/n): ").lower() == 'y'
    symbols = input("Include symbols? (y/n): ").lower() == 'y'

    print("Generated Password:", secure_password_generator(length, upper, digits, symbols))
except ValueError:
    print("Please enter a valid number!")