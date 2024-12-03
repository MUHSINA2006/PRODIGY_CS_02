from PIL import Image
import numpy as np

# Function to encrypt an image
def encrypt_image(input_path, output_path, key):
    # Open the image
    img = Image.open(input_path)
    img_array = np.array(img)
    
    # Apply encryption (simple XOR operation with a key)
    encrypted_array = img_array ^ key
    encrypted_image = Image.fromarray(encrypted_array)
    
    # Save the encrypted image
    encrypted_image.save(output_path)
    print(f"Encrypted image saved at {output_path}")

# Function to decrypt an image
def decrypt_image(input_path, output_path, key):
    # Open the encrypted image
    img = Image.open(input_path)
    img_array = np.array(img)
    
    # Apply decryption (XOR again with the same key)
    decrypted_array = img_array ^ key
    decrypted_image = Image.fromarray(decrypted_array)
    
    # Save the decrypted image
    decrypted_image.save(output_path)
    print(f"Decrypted image saved at {output_path}")

# Example usage
encrypt_image("input_image.jpg", "encrypted_image.png", key=123)
decrypt_image("encrypted_image.png", "decrypted_image.jpg", key=123)