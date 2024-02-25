# Drink items and prices
drinks = {
    '1': {'name': '100plus', 'price': 2.00},
    '2': {'name': 'Coke', 'price': 2.00},
    '3': {'name': 'Milk', 'price': 4.00},
    '4': {'name': 'Milo', 'price': 3.00},
    '5': {'name': 'Mineral Water', 'price': 1.00}
}

# Showing available drink items and prices
print("Welcome to the Vending Machine!")
print("Please select your drink:")

for key, drink in drinks.items():
    print(f"{key}. {drink['name']} : ${drink['price']:.2f}")

# Prompt user for drink item number input
selected_drink = input("Please enter the item number you want to purchase: ")

# Check if the selected item is valid
if selected_drink in drinks:
    selected_item = drinks[selected_drink]
    print(f"You have selected {selected_item['name']}.")
    amount_due = selected_item['price']
    
    # Prompt user to insert money
    while amount_due > 0:
        try:
            payment = float(input(f"Please insert ${amount_due:.2f}: "))
            
            if payment >= amount_due:
                change = payment - amount_due
                print(f"Thank you for your purchase! Your change is ${change:.2f}.")

                # Calculate and display change
                notes = [50, 20, 10, 5, 2, 1]
                amount_return = change

                print("Change:")
                for note in notes:
                    if amount_return >= note:
                        count = amount_return // note
                        amount_return %= note
                        print(f"${note:} note(s): {count}")
                        
                break
            else:
                print("Insufficient amount. Please insert more money.")
                amount_due -= payment

        except ValueError:
            print("Invalid payment amount. Please enter a valid number.")
else:
    print("The selection is invalid. Please choose another drink.")
