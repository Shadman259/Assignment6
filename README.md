import unittest

class User:
    # Attribute
    
    # Constructor
    def __init__(self, first, last, ID):
        self.first = first
        self.last = last
        self.ID = ID
        self.logged_in = False
        
    # Methods
    def login(self):
        self.logged_in = "enter a number"
        print("Logged In\n")
    
    def setFirst(self, first):
        self.first = first
    
    def setLast(self, last):
        self.last = last
    
    def setID(self, ID):
        self.ID = ID
    
    def getInfo(self):
        print("First Name: ", self.first, "\nLast Name: ", self.last, "\nID: ", self.ID)

class Student(User):
    # Constructor
    def __init__(self, first, last, ID):
        super().__init__(first, last, ID)
        
    # Methods
    def AddCourse(self):
        print("Add Course was Successfully Used")
        
    def RemoveCourse(self):
        print("Remove Course was Successfully Used")
        
    def Print(self):
        print("Print Schedule was Successfully Used")

class Instructor(User):
    # Constructor
    def __init__(self, first, last, ID):
        super().__init__(first, last, ID)
    
    # Methods
    def Assemble(self):
        print("Assemble was Successfully Used")
        
    def Print_roster(self):
        print("Print Class List was Successfully Used")

class Admin(User):
    # Constructor
    def __init__(self, first, last, ID):
        super().__init__(first, last, ID)
    
    # Methods
    def add_courses(self):
        print("Add Courses was Successfully Used")
        
    def remove_courses(self):
        print("Remove Courses was Successfully Used")

    def add_remove_student(self):
        print("Add/Remove Student from Course was Successfully Used")
        
    def roster(self):
        print("Search/Print Roster and Courses was Successfully Used")

# Test cases

class TestUser(unittest.TestCase):
    def setUp(self):
        self.user = User("John", "Doe", "123")
        
    def test_initialization(self):
        self.assertEqual(self.user.first, "John")
        self.assertEqual(self.user.last, "Doe")
        self.assertEqual(self.user.ID, "123")
        self.assertFalse(self.user.logged_in)

    def test_set_first(self):
        self.user.setFirst("Jane")
        self.assertEqual(self.user.first, "Jane")
        
    def test_set_last(self):
        self.user.setLast("Smith")
        self.assertEqual(self.user.last, "Smith")
        
    def test_set_id(self):
        self.user.setID("456")
        self.assertEqual(self.user.ID, "456")
        
    def test_get_info(self):
        self.assertEqual(self.user.getInfo(), None)  # Testing the output can be done by capturing stdout
    
    def test_login(self):
        self.user.login()
        self.assertEqual(self.user.logged_in, "enter a number")

class TestStudent(unittest.TestCase):
    def setUp(self):
        self.student = Student("John", "Doe", "123")

    def test_add_course(self):
        self.assertEqual(self.student.AddCourse(), None)

    def test_remove_course(self):
        self.assertEqual(self.student.RemoveCourse(), None)

    def test_print_schedule(self):
        self.assertEqual(self.student.Print(), None)

class TestInstructor(unittest.TestCase):
    def setUp(self):
        self.instructor = Instructor("Jane", "Smith", "456")

    def test_assemble(self):
        self.assertEqual(self.instructor.Assemble(), None)

    def test_print_roster(self):
        self.assertEqual(self.instructor.Print_roster(), None)

class TestAdmin(unittest.TestCase):
    def setUp(self):
        self.admin = Admin("Alice", "Johnson", "789")

    def test_add_courses(self):
        self.assertEqual(self.admin.add_courses(), None)

    def test_remove_courses(self):
        self.assertEqual(self.admin.remove_courses(), None)

    def test_add_remove_student(self):
        self.assertEqual(self.admin.add_remove_student(), None)

    def test_roster(self):
        self.assertEqual(self.admin.roster(), None)

if __name__ == '__main__':
    unittest.main()
