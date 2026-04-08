# Initial phonebook
phonebook = {
    "AMIT": "9876543210",
    "RIYA": "9123456780"
}

# Function to add contact
def add_contact():
    name = input("Enter name: ").upper()
    
    if name in phonebook:
        print("Contact already exists! (Duplicate not allowed)")
    else:
        number = input("Enter phone number: ")
        phonebook[name] = number
        print("Contact added successfully!")

# Function to search contact
def search_contact():
    name = input("Enter name to search: ").upper()
    
    if name in phonebook:
        print(f"{name} : {phonebook[name]}")
    else:
        print("Contact not found!")

# Bonus: Partial search
def partial_search():
    keyword = input("Enter partial name: ").upper()
    found = False
    
    for name in phonebook:
        if keyword in name:
            print(f"{name} : {phonebook[name]}")
            found = True
    
    if not found:
        print("No matching contacts found!")

# Function to delete contact
def delete_contact():
    name = input("Enter name to delete: ").upper()
    
    if name in phonebook:
        del phonebook[name]
        print("Contact deleted successfully!")
    else:
        print("Contact not found!")

# Function to display all contacts
def display_contacts():
    if not phonebook:
        print("Phonebook is empty!")
    else:
        print("\n--- Phonebook ---")
        for name, number in phonebook.items():
            print(f"{name} : {number}")

# Main menu
while True:
    print("\n--- PHONEBOOK MENU ---")
    print("1. Add Contact")
    print("2. Search Contact")
    print("3. Delete Contact")
    print("4. Display All Contacts")
    print("5. Partial Search (Bonus)")
    print("6. Exit")
    
    choice = input("Enter your choice: ")
    
    if choice == "1":
        add_contact()
    elif choice == "2":
        search_contact()
    elif choice == "3":
        delete_contact()
    elif choice == "4":
        display_contacts()
    elif choice == "5":
        partial_search()
    elif choice == "6":
        print("Exiting Phonebook...")
        break
    else:
        print("Invalid choice! Please try again.")
