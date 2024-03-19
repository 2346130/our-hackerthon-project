class Product:
    def __init__(self, name, price, quantity):
        self.name = name
        self.price = price
        self.quantity = quantity

class Marketplace:
    def __init__(self):
        self.products = []

    def add_product(self, product):
        self.products.append(product)

    def display_products(self):
        print("Available Products:")
        for i, product in enumerate(self.products, start=1):
            print(f"{i}. {product.name} - Price: ${product.price} - Quantity: {product.quantity}")

    def buy_product(self, product_index, quantity):
        if product_index < 1 or product_index > len(self.products):
            print("Invalid product index.")
            return

        product = self.products[product_index - 1]
        if product.quantity < quantity:
            print("Insufficient quantity available.")
            return

        total_cost = product.price * quantity
        print(f"You have bought {quantity} {product.name}(s) for ${total_cost}.")
        product.quantity -= quantity

def main():
    # Create a marketplace
    marketplace = Marketplace()

    # Add some products to the marketplace
    marketplace.add_product(Product("Apples", 1.5, 100))
    marketplace.add_product(Product("Oranges", 1.0, 150))
    marketplace.add_product(Product("Potatoes", 0.75, 200))

    # Display available products
    marketplace.display_products()

    # Simulate buying a product
    product_index = int(input("Enter the index of the product you want to buy: "))
    quantity = int(input("Enter the quantity you want to buy: "))
    marketplace.buy_product(product_index, quantity)

    # Display updated product list
    marketplace.display_products()

if __name__ == "__main__":
    main()
