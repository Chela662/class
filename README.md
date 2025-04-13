# Base Class: Book
class Book:
    def __init__(self, title, author, genre, year):
        self.title = title
        self.author = author
        self.genre = genre
        self.year = year
    
    def display_details(self):
        """Display details about the book"""
        return f"Title: {self.title}\nAuthor: {self.author}\nGenre: {self.genre}\nYear: {self.year}"

    def update_genre(self, new_genre):
        """Update the genre of the book"""
        self.genre = new_genre
        return f"Genre updated to: {self.genre}"

    def is_bestseller(self):
        """Check if the book is a bestseller"""
        bestsellers = ["The Great Gatsby", "1984", "To Kill a Mockingbird"]  # Example
        return self.title in bestsellers

# Derived Class: EBook
class EBook(Book):
    def __init__(self, title, author, genre, year, file_size, format_type):
        super().__init__(title, author, genre, year)  # Call to parent constructor
        self.file_size = file_size  # in MB
        self.format_type = format_type  # e.g., PDF, ePub, MOBI
    
    def display_details(self):
        """Display details about the eBook, including file size and format"""
        base_details = super().display_details()
        return f"{base_details}\nFile Size: {self.file_size}MB\nFormat: {self.format_type}"

    def is_bestseller(self):
        """Check if the eBook is a bestseller (can be overridden)"""
        if super().is_bestseller():
            return True
        return False

# Base Class: Animal
class Animal:
    def move(self):
        pass  # This method will be overridden by subclasses

# Derived Class: Car (Animal)
class Car(Animal):
    def move(self):
        print("Driving ")

# Derived Class: Plane (Animal)
class Plane(Animal):
    def move(self):
        print("Flying ")

# Derived Class: Fish (Animal)
class Fish(Animal):
    def move(self):
        print("Swimming ")

# Derived Class: Dog (Animal)
class Dog(Animal):
    def move(self):
        print("Running ")

# Creating instances of Book and EBook
book1 = Book("1984", "George Orwell", "Dystopian", 1949)
ebook1 = EBook("The Great Gatsby", "F. Scott Fitzgerald", "Classic", 1925, 2.5, "ePub")

# Using Book and EBook methods
print(book1.display_details())
print(f"Is bestseller? {book1.is_bestseller()}")
print("\n" + ebook1.display_details())
print(f"Is bestseller? {ebook1.is_bestseller()}")

# Test Polymorphism with Animal classes
print("\n--- Animal Movement ---")
animals = [Car(), Plane(), Fish(), Dog()]

for animal in animals:
    animal.move()  # Each animal calls its own move() method
# class
