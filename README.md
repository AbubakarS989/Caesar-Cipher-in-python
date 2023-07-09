# Caesar-Cipher-in-python
In this encoder or decder You guys can decode or encode any type of message. Without shift you can't decode or encode any msg

from art import logo

# Define the list of characters that can be encrypted/decrypted
alphabet = [
    'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z',
    '1', '2', '3', '4', '5', '6', '7', '8', '9', '0',
    '!', '@', '$', '%', '&', '*', '(', ')', '+', '-', '_', '/', '?', ' ', '>', '<', '{', '}', '[', ']', ',', '.', ';', ':', '"',
    'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z',
    '1', '2', '3', '4', '5', '6', '7', '8', '9', '0',
    '!', '@', '$', '%', '&', '*', '(', ')', '+', '-', '_', '/', '?', ' ', '>', '<', '{', '}', '[', ']', ',', '.', ';', ':', '"'
]

def caesar(start_text, shift_amount, cipher_direction):
    """
    Encrypts or decrypts the given text using the Caesar cipher algorithm.

    Args:
        start_text (str): The text to be encrypted or decrypted.
        shift_amount (int): The number of positions each character should be shifted.
        cipher_direction (str): The direction of the cipher, either "encode" or "decode".

    Returns:
        None
    """
    end_text = ""
    if cipher_direction == "decode":
        shift_amount *= -1
    for char in start_text:
        if char in alphabet:
            position = alphabet.index(char)
            new_position = position + shift_amount
            end_text += alphabet[new_position]
        else:
            end_text += char
    print(f"Here's the {cipher_direction}d result: {end_text}")

print(logo)
should_end = False
while not should_end:
    direction = input("Type 'encode' to encrypt, type 'decode' to decrypt:\n")
    text = input("Type your message:\n").lower()
    shift = int(input("Type the shift number:\n"))

    # Ensure the shift value is within the valid range
    shift = shift % 122

    # Call the caesar function to perform the encryption/decryption
    caesar(start_text=text, shift_amount=shift, cipher_direction=direction)

    restart = input("Type 'yes' if you want to go again. Otherwise type 'no'.\n")
    if restart == "no":
        should_end = True
        print("Goodbye")
