def encrypt(text, shift):
    """Encrypt the text using Caesar cipher with the given shift."""
    encrypted_text = ""
    for char in text:
        # Check if the character is a letter
        if char.isalpha():
            # Handle uppercase and lowercase letters separately
            ascii_offset = 65 if char.isupper() else 97
            # Shift the character and wrap around if necessary
            encrypted_char = chr(((ord(char) - ascii_offset + shift) % 26) + ascii_offset)
            encrypted_text += encrypted_char
        else:
            # Keep non-alphabetic characters unchanged
            encrypted_text += char
    return encrypted_text

def decrypt(text, shift):
    """Decrypt the text using Caesar cipher with the given shift."""
    return encrypt(text, -shift)

def main():
    """Main function to run the Caesar cipher program."""
    # Get user input
    choice = input("Do you want to encrypt or decrypt? (e/d): ").lower()
    text = input("Enter the message: ")
    shift = int(input("Enter the shift value: "))

    if choice == 'e':
        encrypted_message = encrypt(text, shift)
        print(f"Encrypted message: {encrypted_message}")
    elif choice == 'd':
        decrypted_message = decrypt(text, shift)
        print(f"Decrypted message: {decrypted_message}")
    else:
        print("Invalid choice. Please enter 'e' to encrypt or 'd' to decrypt.")

if __name__ == "__main__":
    main()
