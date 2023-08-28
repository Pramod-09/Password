import random
import string

class PasswordManager:
    def __init__(self):
        self.passwords = {}

    def generate_password(self, length=12):
        characters = string.ascii_letters + string.digits + string.punctuation
        password = ''.join(random.choice(characters) for _ in range(length))
        return password

    def store_password(self, account, password):
        self.passwords[account] = password

    def retrieve_password(self, account):
        if account in self.passwords:
            return self.passwords[account]
        else:
            return "Account not found."

    def list_accounts(self):
        return list(self.passwords.keys())

# Example usage
if __name__ == "__main__":
    manager = PasswordManager()

    while True:
        print("1. Generate Password")
        print("2. Store Password")
        print("3. Retrieve Password")
        print("4. List Accounts")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            length = int(input("Enter password length: "))
            password = manager.generate_password(length)
            print(f"Generated Password: {password}")

        elif choice == "2":
            account = input("Enter account name: ")
            password = input("Enter password: ")
            manager.store_password(account, password)
            print("Password stored successfully.")

        elif choice == "3":
            account = input("Enter account name: ")
            password = manager.retrieve_password(account)
            print(f"Password: {password}")

        elif choice == "4":
            accounts = manager.list_accounts()
            print("Accounts:", accounts)

        elif choice == "5":
            print("Exiting...")
            break

        else:
            print("Invalid choice. Please select again.")# Password
