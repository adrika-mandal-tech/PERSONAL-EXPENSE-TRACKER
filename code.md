# PERSONAL-EXPENSE-TRACKER
'''Reference books(Basic Python Data Structures):
1.DSA made easy by Narasimha Karumanchi    
2.Core Python Programming by Dr.R.Nageswara Rao.'''
print("---------------------MY PERSONAL BUDGET TRACKER------------------")                                                                       
import numpy as np
# Node class for the Linked List
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
# Linked List class
class LinkedList:
    def __init__(self):
        self.head = None
    def append(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
        else:
            current = self.head
            while current.next:
                current = current.next
            current.next = new_node
    def __iter__(self):
        current = self.head
        while current:
            yield current.data
            current = current.next
# Function to input all expenses
def input_expenses(weekdays):
    daily_expenses = []
    for day in weekdays:
        while True:
            try:
                expense = float(input(f"Enter expenses on {day} (in $): "))
                daily_expenses.append(expense)
                break
            except ValueError:
                print("Please enter a valid number.")
    return np.array(daily_expenses)

# Function to find the highest expense
def highest(expenses):
    return np.max(expenses)
# Function to find the lowest expense
def lowest(expenses):
    return np.min(expenses)
# Function to calculate total expenses
def calculate_total(expenses):
    return np.sum(expenses)
# Function to calculate average expenses
def calculate_average(expenses):
    return np.mean(expenses)
# Main function
def main():

# Creating a linked list for weekdays
    weekdays = LinkedList()
    for day in ["MONDAY", "TUESDAY", "WEDNESDAY", "THURSDAY", "FRIDAY", "SATURDAY", "SUNDAY"]:
        weekdays.append(day)
    try:
        my_monthly_income = float(input("Enter your Monthly Salary (in $): "))
        bonuses = float(input("Enter your Bonus of this year (in $)[Optional]: "))
    except ValueError:
        print("Invalid input for salary or bonus. Please enter numbers.")
        return
    budget = my_monthly_income + bonuses
    print("MY BUDGET (in $)=", budget)
    daily_expenses = input_expenses(weekdays)
    total_expenses = calculate_total(daily_expenses)
    average_expenses = calculate_average(daily_expenses)
    highest_expense = highest(daily_expenses)
    lowest_expense = lowest(daily_expenses)
    print("\n--------------MY PERSONAL EXPENDITURES FOR THIS WEEK--------------")
    for day, expense in zip(weekdays, daily_expenses):
        print(f"{day}: ${expense:.2f}")
    print(f"\nTotal Expenses for the week: ${total_expenses:.2f}")
    print(f"\nHighest Expense this week: ${highest_expense:.2f}")
    print(f"Lowest Expense this week: ${lowest_expense:.2f}")
    print(f"\nAverage Daily Expense: ${average_expenses:.2f}")
    print("\nTotal Savings made this week: $",budget - total_expenses)

# Decision making based on the budget and expenses
    if budget > total_expenses:
        print(f"\nCHEERS FRIEND!! You have SAVED an amount of ${budget - total_expenses:.2f} this week!")

    elif budget < total_expenses:
        print(f"\nOH NOO!!! You had an EXTRA EXPENDITURE this week and had crossed your budget. Your balance is low: ${budget - total_expenses:.2f}")

    elif budget == 0:
        print("\nZERO BALANCE ALERT!!! Try to save your budget for future use....")

    elif budget / 2 == total_expenses:
        print("\nOOPS!!! You flushed out HALF of your savings this week....")

    elif budget / 4 == total_expenses:
        print("\nYou already spent one-fourth of this week's savings....")

    elif budget == total_expenses:
        print("\nCOOL!! You balanced your budget perfectly this week.")

# Run the main function
if __name__ == "__main__":
    main()
print("\n\n*********************THANK-YOU!!****************************")
