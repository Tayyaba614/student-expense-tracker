import datetime

class ExpenseTracker:
    def __init__(self):
        self.expenses = []

    def add_expense(self, amount, category, description=""):
        """Add a new expense."""
        expense = {
            "amount": amount,
            "category": category,
            "description": description,
            "date": datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        }
        self.expenses.append(expense)
        print(f"Added expense: {expense}")

    def view_expenses(self):
        """View all recorded expenses."""
        if not self.expenses:
            print("No expenses recorded yet!")
            return
        print("\n--- Expense History ---")
        for idx, expense in enumerate(self.expenses, start=1):
            print(f"{idx}. Date: {expense['date']}, Amount: ${expense['amount']}, Category: {expense['category']}, Description: {expense['description']}")

    def calculate_total(self):
        """Calculate the total amount spent."""
        total = sum(expense["amount"] for expense in self.expenses)
        print(f"\nTotal Amount Spent: ${total}")

def main():
    tracker = ExpenseTracker()

    print("Welcome to the Student Expense Tracker!")
    while True:
        print("\nOptions:")
        print("1. Add Expense")
        print("2. View Expenses")
        print("3. Calculate Total Spent")
        print("4. Exit")
        choice = input("Enter your choice (1/2/3/4): ")

        if choice == "1":
            try:
                amount = float(input("Enter the amount: $"))
                category = input("Enter the category (e.g., Food, Travel, Books): ")
                description = input("Enter a description (optional): ")
                tracker.add_expense(amount, category, description)
            except ValueError:
                print("Invalid input. Please enter a valid amount.")
        elif choice == "2":
            tracker.view_expenses()
        elif choice == "3":
            tracker.calculate_total()
        elif choice == "4":
            print("Exiting the tracker. Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()# student-expense-tracker
