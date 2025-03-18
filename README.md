# Activity
class Employee:
    def __init__(self, employee_id, name, salary, position):
        self.employee_id = employee_id
        self.name = name
        self.salary = salary
        self.position = position

    # Copy constructor to create a new object by copying another employee's data
    def __copy__(self):
        return Employee(self.employee_id, self.name, self.salary, self.position)

    def display_employee(self):
        print(f"Employee ID: {self.employee_id}")
        print(f"Name: {self.name}")
        print(f"Position: {self.position}")
        print(f"Salary: ${self.salary:,.2f}")
        print("-" * 30)

class PayrollSystem:
    def __init__(self):
        self.employees = []
    
    def add_employee(self, employee):
        """Add an Employee object to the payroll system."""
        self.employees.append(employee)

    def display_all_employees(self):
        """Display all employees' payroll information."""
        if not self.employees:
            print("No employees found.")
        else:
            for emp in self.employees:
                emp.display_employee()

    def duplicate_employee(self, employee_id):
        """Create a copy of an employee using the copy constructor."""
        for emp in self.employees:
            if emp.employee_id == employee_id:
                new_employee = emp.__copy__()
                self.add_employee(new_employee)
                print(f"Employee {employee_id} duplicated successfully.")
                return
        print(f"Employee with ID {employee_id} not found.")

# Example Usage
if __name__ == "__main__":
    payroll = PayrollSystem()

    # Adding some employees to the system
    emp1 = Employee(101, "John Doe", 50000, "Software Engineer")
    emp2 = Employee(102, "Jane Smith", 55000, "Project Manager")
    
    payroll.add_employee(emp1)
    payroll.add_employee(emp2)

    # Display all employees
    print("Employee Details:")
    payroll.display_all_employees()

    # Duplicating an employee
    payroll.duplicate_employee(101)

    # Display all employees again after duplication
    print("\nUpdated Employee Details:")
    payroll.display_all_employees()
