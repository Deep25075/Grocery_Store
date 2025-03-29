grocery_items = {
    1: {"name": "Rice (1kg)", "price": 50},
    2: {"name": "Wheat (1kg)", "price": 40},
    3: {"name": "Milk (1L)", "price": 60},
    4: {"name": "Sugar (1kg)", "price": 45},
    5: {"name": "Tea (250g)", "price": 120}
}

cart = []

def display_items():
    print("\nAvailable Grocery Items:")
    print("ID   Name            Price (INR)")
    print("---------------------------------")
    for item_id, details in grocery_items.items():
        print(f"{item_id}. {details['name']:15} ₹{details['price']}")

def add_to_cart():
    item_id = int(input("\nEnter Item ID to Add to Cart: "))
    if item_id in grocery_items:
        cart.append(grocery_items[item_id])
        print(f"{grocery_items[item_id]['name']} added to cart!")
    else:
        print("Invalid Item ID. Try Again.")

def view_cart():
    if not cart:
        print("\n🛒 Your Cart is Empty!")
        return

    print("\nYour Cart:")
    total = 0
    for index, item in enumerate(cart, start=1):
        print(f"{index}. {item['name']} - ₹{item['price']}")
        total += item['price']

    print(f"\nTotal Amount: ₹{total}")

def checkout():
    view_cart()
    if cart:
        confirm = input("\nProceed to Checkout? (yes/no): ").strip().lower()
        if confirm == "yes":
            print("\n🎉 Thank You for Shopping! Your Order is Placed.")
            cart.clear()
        else:
            print("\nCheckout Cancelled.")

def main():
    while True:
        print("\nGrocery Store Menu")
        print("1. View Items")
        print("2. Add to Cart")
        print("3. View Cart")
        print("4. Checkout")
        print("5. Exit")
        choice = input("Enter your choice: ").strip()

        if choice == "1":
            display_items()
        elif choice == "2":
            add_to_cart()
        elif choice == "3":
            view_cart()
        elif choice == "4":
            checkout()
        elif choice == "5":
            print("\nThank you for visiting! Have a great day!")
            break
        else:
            print("1Invalid choice. Try again!")
