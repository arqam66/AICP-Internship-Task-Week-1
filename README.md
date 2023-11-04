# AICP-Internship-Task-Week-1
# Arrays to store item code, description, and price
item_codes = ["A1", "A2", "B1", "B2", "B3", "C1", "C2", "C3", "D1", "D2", "E1", "E2", "E3"]
descriptions = ["Compact", "Tower", "8 GB RAM", "16 GB RAM", "32 GB RAM", "1 TB HDD", "2 TB HDD", "4 TB HDD", "240 GB SSD", "480 GB SSD", "1 TB HDD", "2 TB HDD", "4 TB HDD"]
prices = [75.00, 150.00, 79.99, 149.99, 299.99, 49.99, 89.99, 129.99, 59.99, 119.99, 49.99, 89.99, 129.99]

# Basic set of components cost
basic_set_cost = 200.00

# Prompt for user input
print("Welcome to the online computer shop!")
print("Available items:")
for i in range(len(item_codes)):
    print(f"{item_codes[i]} - {descriptions[i]} - ${prices[i]}")

# Task 1 - Setting up the system and ordering the main items
case_choice = input("Enter the item code for the case (A1 or A2): ")
ram_choice = input("Enter the item code for the RAM (B1, B2, or B3): ")
hdd_choice = input("Enter the item code for the Main Hard Disk Drive (C1, C2, or C3): ")

# Validate user input for main items
while case_choice not in item_codes or ram_choice not in item_codes or hdd_choice not in item_codes:
    print("Invalid item code. Please try again.")
    case_choice = input("Enter the item code for the case (A1 or A2): ")
    ram_choice = input("Enter the item code for the RAM (B1, B2, or B3): ")
    hdd_choice = input("Enter the item code for the Main Hard Disk Drive (C1, C2, or C3): ")

# Calculate total price for main items
total_price = basic_set_cost + prices[item_codes.index(case_choice)] + prices[item_codes.index(ram_choice)] + prices[item_codes.index(hdd_choice)]

# Output chosen main items and total price
print("\nChosen main items:")
print(f"Case: {descriptions[item_codes.index(case_choice)]}")
print(f"RAM: {descriptions[item_codes.index(ram_choice)]}")
print(f"Main Hard Disk Drive: {descriptions[item_codes.index(hdd_choice)]}")
print(f"Total Price: ${total_price:.2f}")

# Task 2 - Ordering additional items
additional_items = input("Would you like to purchase additional items? (yes/no): ")

if additional_items.lower() == "yes":
    additional_item_codes = input("Enter the item codes for additional items separated by commas (D1, D2, E1, E2, E3): ").split(',')

    # Validate and calculate total price for additional items
    for item_code in additional_item_codes:
        if item_code.strip() in item_codes:
            total_price += prices[item_codes.index(item_code.strip())]
        else:
            print(f"Invalid item code: {item_code.strip()}")

    # Output chosen additional items and new total price
    print("\nAdditional items:")
    for item_code in additional_item_codes:
        print(f"{descriptions[item_codes.index(item_code.strip())]}")
    
    print(f"New Total Price: ${total_price:.2f}")

    # Task 3 - Offering discounts
    num_additional_items = len(additional_item_codes)

    if num_additional_items == 1:
        discount = 0.05
    elif num_additional_items >= 2:
        discount = 0.10
    else:
        discount = 0

    discount_amount = total_price * discount
    discounted_price = total_price - discount_amount

    print(f"\nDiscount Applied: {discount * 100}%")
    print(f"Amount Saved: ${discount_amount:.2f}")
    print(f"Final Price after Discount: ${discounted_price:.2f}")
else:
    print("Total Price: ${total_price:.2f}")
