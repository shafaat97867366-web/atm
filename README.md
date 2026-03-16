# atm
class ATM:
    def __init__(self, balance=0, pin=1234):
        self.balance = balance
        self.pin = pin

    def check_balance(self):
        print(f"\nYour current balance is: ${self.balance}")

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            print(f"${amount} deposited successfully.")
            self.check_balance()
        else:
            print("Invalid deposit amount.")

    def withdraw(self, amount):
        if 0 < amount <= self.balance:
            self.balance -= amount
            print(f"${amount} withdrawn successfully.")
            self.check_balance()
        elif amount > self.balance:
            print("Insufficient funds!")
        else:
            print("Invalid withdrawal amount.")

def run_atm():
    # Initialize ATM with $1000 and default PIN 1234
    my_atm = ATM(balance=1000)
    
    print("--- Welcome to the Python ATM ---")
    user_pin = int(input("Please enter your 4-digit PIN: "))

    if user_pin != my_atm.pin:
        print("Incorrect PIN. Access Denied.")
        return

    while True:
        print("\n1. Check Balance")
        print("2. Deposit Money")
        print("3. Withdraw Money")
        print("4. Exit")
        
        choice = input("\nSelect an option (1-4): ")

        if choice == '1':
            my_atm.check_balance()
        elif choice == '2':
            amt = float(input("Enter deposit amount: "))
            my_atm.deposit(amt)
        elif choice == '3':
            amt = float(input("Enter withdrawal amount: "))
            my_atm.withdraw(amt)
        elif choice == '4':
            print("Thank you for using the ATM. Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    run_atm()
