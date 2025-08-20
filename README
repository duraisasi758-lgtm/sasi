# sasi
#ATM MINI project
import datetime

# User database
users = {
    "1234": {"name": "Sasikumar", "balance": 10000.0, "transactions": []},
    "5678": {"name": "Anjali", "balance": 7500.0, "transactions": []},
    "4321": {"name": "Ravi", "balance": 12000.0, "transactions": []}
}

# Log transaction
def log_transaction(user, type, amount):
    time = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    users[user]["transactions"].append(f"{time} - {type}: ₹{amount:.2f}")

# ATM Menu
def atm_menu():
    print("\n💳 ----- ATM MENU ----- 💳")
    print("1. Check Balance")
    print("2. Deposit")
    print("3. Withdraw")
    print("4. View Transaction History")
    print("5. Change PIN")
    print("6. Transfer Money")
    print("7. Mini Statement")
    print("8. Logout")
    print("9. Exit")

# Main loop
while True:
    pin = input("\n🔑 Enter your 4-digit PIN: ")
    if pin in users:
        user = users[pin]
        print(f"\n👋 Welcome, {user['name']}!")

        while True:
            atm_menu()
            choice = input("👉 Choose an option (1-9): ")

            if choice == "1":
                print(f"💼 Balance: ₹{user['balance']:.2f}")

            elif choice == "2":
                amount = float(input("💵 Deposit amount: ₹"))
                if amount > 0:
                    user['balance'] += amount
                    log_transaction(pin, "Deposit", amount)
                    print("✅ Deposit successful!")
                else:
                    print("⚠️ Invalid amount!")

            elif choice == "3":
                amount = float(input("💸 Withdraw amount: ₹"))
                if 0 < amount <= user['balance']:
                    user['balance'] -= amount
                    log_transaction(pin, "Withdraw", amount)
                    print("✅ Withdrawal successful!")
                else:
                    print("⚠️ Insufficient funds!")

            elif choice == "4":
                print("\n📜 Transaction History:")
                for entry in user['transactions']:
                    print("🔹", entry)

            elif choice == "5":
                new_pin = input("🔐 Enter new PIN: ")
                if len(new_pin) == 4 and new_pin.isdigit():
                    users[new_pin] = users.pop(pin)
                    pin = new_pin
                    print("✅ PIN changed!")
                else:
                    print("⚠️ Invalid PIN format!")

            elif choice == "6":
                target_pin = input("🔁 Enter recipient PIN: ")
                if target_pin in users and target_pin != pin:
                    amount = float(input("💸 Transfer amount: ₹"))
                    if 0 < amount <= user['balance']:
                        user['balance'] -= amount
                        users[target_pin]['balance'] += amount
                        log_transaction(pin, f"Transfer to {users[target_pin]['name']}", amount)
                        log_transaction(target_pin, f"Received from {user['name']}", amount)
                        print("✅ Transfer successful!")
                    else:
                        print("⚠️ Insufficient funds!")
                else:
                    print("⚠️ Invalid recipient!")

            elif choice == "7":
                print("\n🧾 Mini Statement (Last 5):")
                for entry in user['transactions'][-5:]:
                    print("🔹", entry)

            elif choice == "8":
                print("🔓 Logging out...")
                break

            elif choice == "9":
                print("🙏 Thank you for using our ATM!")
                exit()

            else:
                print("⚠️ Invalid option!")

    else:
        print("❌ Incorrect PIN.")

