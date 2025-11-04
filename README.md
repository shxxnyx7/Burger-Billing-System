# Burger-Billing-System
Designed an automated billing system using Python and Excel to streamline restaurant order processing. Implemented formula-based calculations for pricing, discounts, and taxes, reducing manual input errors. Tools: Python, MS Excel Key Skills: Automation • Data Validation • Excel Formulas




# Display Menu Function
def show_menu():
    print("*************** BURGER MENU ***************")
    print("Sr.\tName\t\tPrice ($)")
    print("1.\tAloo Tikki\t5")
    print("2.\tMaharaja\t10")
    print("3.\tMac Special\t15")
    print("*******************************************")

# Main Billing Function
def burger_billing_system():
    menu = {
        1: {"name": "Aloo Tikki", "price": 5},
        2: {"name": "Maharaja", "price": 10},
        3: {"name": "Mac Special", "price": 15}
    }

    orders = []  # list to store multiple items

    while True:
        show_menu()
        choice = int(input("Enter item number you want to order: "))

        if choice not in menu:
            print("Invalid choice. Please select again.")
            continue

        quantity = int(input(f"How many {menu[choice]['name']} burgers do you want? "))

        # Store order details
        orders.append({
            "sr": len(orders) + 1,
            "name": menu[choice]['name'],
            "price": menu[choice]['price'],
            "quantity": quantity,
            "total": menu[choice]['price'] * quantity
        })

        more = input("Do you want to order another item? (yes/no): ").strip().lower()
        if more != 'yes':
            break

    # Ask additional questions once after all orders are taken
    student = input("Are you a student? (yes/no): ").strip().lower()
    delivery = input("Do you want delivery? (yes/no): ").strip().lower()
    tip_choice = input("Do you want to give a tip? (yes/no): ").strip().lower()

    tip = 0
    if tip_choice == 'yes':
        tip = int(input("Enter tip amount (2 / 5 / 10): "))

    # Billing Calculations
    subtotal = sum(item['total'] for item in orders)
    student_discount = 0.2 * subtotal if student == 'yes' else 0
    delivery_charge = 0.05 * subtotal if delivery == 'yes' else 0
    total_bill = subtotal - student_discount + delivery_charge + tip

    # Print Final Bill
    print("\n****************** FINAL BILL **********************")
    print("Sr.\tName\t\tPrice\tQty\tTotal($)")
    for item in orders:
        print(f"{item['sr']}\t{item['name']}\t{item['price']}\t{item['quantity']}\t{item['total']}")
    print("----------------------------------------------------")
    print(f"Subtotal\t\t\t\t{subtotal}$")
    print(f"Student Discount 20%\t\t\t-{student_discount}$")
    print(f"Delivery Charge 5%\t\t\t+{delivery_charge}$")
    print(f"Tip\t\t\t\t\t+{tip}$")
    print("----------------------------------------------------")
    print(f"Total Bill\t\t\t\t{total_bill}$")
    print("Thank you and come again >>>>>>>>>>>>>>>>>>>>>>>>>>>")

# Run Program
burger_billing_system()











Chat
