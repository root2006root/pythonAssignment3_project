# pythonAssignment3_project

import fitz  # PyMuPDF
import re

# Load PDF and extract text
file_path = input("Enter PDF file path: ")
doc = fitz.open(file_path)
text = ""
for page in doc:
    text += page.get_text()

# Extract name (first line)
lines = text.strip().split("\n")
name = lines[0] if lines else "Not found"

# Extract email
email_match = re.search(r'\S+@\S+', text)
email = email_match.group(0) if email_match else "Not found"

# Extract phone number (10 digits)
phone_match = re.search(r'\d{10}', text)
phone = phone_match.group(0) if phone_match else "Not found"

# Print results
print("\n--- Resume Info ---")
print("Name :", name)
print("Email:", email)
print("Phone:",phone)
