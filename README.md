#python code for password generator 
import string
import secrets

def generate_password(length=12, use_upper=True, use_lower=True, use_digits=True, use_special=True):
    """
    Generates a random password based on selected character sets.
    - length: total length of password
    - use_upper: include uppercase letters
    - use_lower: include lowercase letters
    - use_digits: include digits
    - use_special: include punctuation/symbols
    """
    charset = ""
    if use_upper:
        charset += string.ascii_uppercase
    if use_lower:
        charset += string.ascii_lowercase
    if use_digits:
        charset += string.digits
    if use_special:
        charset += string.punctuation

    if not charset:
        raise ValueError("At least one character type must be selected.")
    
    # Use secrets.choice for cryptographic randomness :contentReference[oaicite:1]{index=1}
    return ''.join(secrets.choice(charset) for _ in range(length))

def main():
    print("🔐 Secure Password Generator")
    length = int(input("Enter password length (e.g., 12): "))
    u = input("Include uppercase? (y/n): ").lower().startswith('y')
    l = input("Include lowercase? (y/n): ").lower().startswith('y')
    d = input("Include digits? (y/n): ").lower().startswith('y')
    s = input("Include special chars? (y/n): ").lower().startswith('y')

    pwd = generate_password(length, use_upper=u, use_lower=l, use_digits=d, use_special=s)
    print("\nYour new secure password is:\n", pwd)

if __name__ == "__main__":
    main()