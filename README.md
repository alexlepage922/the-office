# the-office
# Clue 6: Abstract Base Class
class Employee(ABC):
    def work(self):
        pass

# Clue 1: Manager Class
class Manager(Employee):
    def __init__(self, name, department, employees=[]):  # Clue 3: __init__
        self.name = name
        self.department = department
        self.employees = employees

    def farm_beets(self):  # Clue 2: Method for actions
        print("Farming beets")

    def __del__(self):  # Clue 5: Destructor
        print("Manager object deleted")

# Clue 7: Class method
    def from_string(cls, manager_str):
        name, department, _ = manager_str.split("-")
        return cls(name, department)

# Clue 8: Static method
    def is_valid_department(department):
        return department in ["Sales", "Accounting", "HR", "Customer Service"]

# Clue 9: Property method
    def full_name(self):
        return f"{self.name} ({self.department})"

# Clue 4: Inheritance (Salesperson Subclass)
class Salesperson(Manager):
    def __init__(self, name, department, sales_target, employees=[]):
        super().__init__(name, department, employees)
        self.sales_target = sales_target

    def farm_beets(self):  # Clue 10: Override method
        print("Selling paper")

# Example Usages
michael = Manager("Michael Scott", "Sales", ["Jim", "Dwight", "Pam"])
print(michael.full_name)  # Clue 9

dwight = Salesperson("Dwight Schrute", "Sales", 100)
dwight.farm_beets()  # Clue 10

# Clue 7 Example
new_manager = Manager.from_string("Michael-Scott-Sales")
print(new_manager.full_name)

# Clue 8 Example
print(Manager.is_valid_department("Sales"))  # True
print(Manager.is_valid_department("Marketing"))  # False
