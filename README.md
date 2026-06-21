# didactic-parakeet
Smart Shopping List
shopping_list = {}

while True:
    print("\n===== SMART SHOPPING LIST =====")
    print("1. Add Item")
    print("2. View Shopping List")
    print("3. Remove Item")
    print("4. Calculate Total Bill")
    print("5. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        item = input("Enter item name: ")

        try:
            price = float(input("Enter price per item: "))
            quantity = int(input("Enter quantity: "))

            shopping_list[item] = {
                "price": price,
                "quantity": quantity
            }

            print(f"{item} added successfully!")

        except ValueError:
            print("Invalid input! Please enter numbers.")

    elif choice == "2":
        if not shopping_list:
            print("Shopping list is empty.")
        else:
            print("\nShopping List")
            print("-" * 40)
            print(f"{'Item':<15}{'Price':<10}{'Qty':<10}{'Total'}")

            for item, details in shopping_list.items():
                total = details["price"] * details["quantity"]
                print(f"{item:<15}{details['price']:<10.2f}{details['quantity']:<10}{total:.2f}")

    elif choice == "3":
        item = input("Enter item name to remove: ")

        if item in shopping_list:
            del shopping_list[item]
            print(f"{item} removed successfully.")
        else:
            print("Item not found.")

    elif choice == "4":
        grand_total = 0

        print("\nBill Summary")
        print("-" * 40)

        for item, details in shopping_list.items():
            total = details["price"] * details["quantity"]
            grand_total += total
            print(f"{item}: ₹{total:.2f}")

        print("-" * 40)
        print(f"Grand Total = ₹{grand_total:.2f}")

    elif choice == "5":
        print("Thank you for using Smart Shopping List!")
        break

    else:
        print("Invalid choice! Please try again.")
        
