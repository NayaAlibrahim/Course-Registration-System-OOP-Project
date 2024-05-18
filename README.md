# Course-Registration-System-OOP-Project

The purpose behind this project: 

The Course Registration System is designed to facilitate the management of various types of courses offered by an educational institution. It enables users, including students, administrative staff, and faculty advisors, to interact with the system to handle course registrations, scheduling, and administrative procedures. The system is capable of managing different forms of courses, such as lectures, seminars, and labs, each with its own scheduling and registration requirements. Additionally, it handles special course types, such as honours courses or remote learning options, which may involve unique enrolment criteria or administrative procedures. 

 

 

Features of the system : 

1.the system allows the user to login into their accounts using the userID and password . The login page may include a "Forgot Password" link that allows users to reset their password if they have forgotten it. Clicking on the "Forgot Password" link should redirect users to a password reset page where they can verify their identity (e.g., by answering security questions or receiving a reset link via email) and create a new password.  

 

2.The Dashboard provides users with an overview of relevant information and activities within the Course Registration System. It may include summary statistics such as the number of courses available, the number of registered students, upcoming deadlines, and recent notifications. Graphical representations such as charts or graphs can be used to visualize data trends and patterns. 

 

3. Users can click on a course listing to view detailed information about the selected course. The course details view presents comprehensive information, including course description, learning objectives, syllabus, grading policy, textbook requirements, and instructor contact information. Buttons or links allow users to add the course to their registration cart or wish list, view course prerequisites, or access related resources. 

 

4. After selecting courses and reviewing their registration cart, users can proceed to confirm enrollment. The system prompts users to review their course selections, confirm their intent to enroll, and submit the registration request. Upon successful enrollment, users receive a confirmation message and notification confirming their course registrations. 

 

The overall structure of the system :  

The system provides multiple classes that communicate with each other in order to accomplish the requirements of the system .  

 

1.In our code the first defined class was the “Account” class :  

The Account class is designed to manage user account information in a software application. This class encapsulates various attributes related to an account, such as the account ID, password, username, role, and additional profile details. It provides methods for setting and retrieving these attributes, as well as for validating the account's password. 

#Class Attributes :  

The Account class includes the following private attributes:  

AccountId (int): A unique identifier for the account.  

password (string): The password for the account, stored as a string to accommodate complex passwords. 

username (string): The username associated with the account.  

role (string): The role of the account holder. 

profileDetails (string): Additional details about the account holder. 

 

#Constructors : 

The class provides two constructors: 

Default Constructor: Initializes an account with default values (0 for AccountId and empty strings for other attributes). 

 Parameterized Constructor: Allows initializing an account with specific values for each attribute. 

#Member Functions 

The Account class provides several public member functions to interact with and manipulate account data: 

-Validation Function: Validates the provided pin against the account's stored password. 

- Setter Functions: Allow modification of each attribute of the account. 

- Getter Functions: to return the values of each member variable .  

 

2.In our code the second defined class was the “Data Base” class : 

The DataBase class is designed to manage a collection of Account objects, providing functionalities for user authentication and account retrieval. This class serves as a simple in-memory database that stores account information and allows for user authentication based on account ID and password.  

#Class Attributes : 

The DataBase class includes the following private attribute: 

-accounts (vector<Account>): A vector that holds a collection of Account objects. This serves as the storage for all account information in the database. 

#Constructors : 

-The class provides a default constructor: initializes the DataBase object with a predefined Account. In our code , the account created has the following attributes: Account ID: 2315 Password: "0000" Username: "Naya Alibrahim" Role: "Student" Profile Details: "Computer Science Major” .  

#Member Functions 

The DataBase class provides several public member functions to interact with the stored accounts: 

- authenticateUser : This function authenticates a user by verifying their account ID and password (PIN). It takes an AccountId and a Pin as arguments and returns a bool. The function first retrieves the account corresponding to the provided AccountId using the getAccount method. If the account exists and the provided PIN matches the account's password, the function returns true; otherwise, it returns false. This function is used during the login process to ensure that the user provides correct credentials. 

- Account* getAccount : this function retrieves an account by its account ID. It takes an AccountId as an argument and returns a pointer to the Account object if found, or nullptr if no account with the given ID exists.This function is used to access the account details for various operations, such as authentication or profile updates. 

 

3.In our code the third defined class was the “course” class : 

The Course class is designed to represent a course in an educational system. It encapsulates information about the course such as the title, description, schedule, capacity, and the number of enrolled students. Additionally, it manages the relationship with student enrollments, supporting functionalities to enroll students and update course details.  

#Class Attributes : 

The Course class includes the following private attributes:  

title (string): The title of the course.  

description (string): A brief description of the course content.  

schedule (string): The schedule of the course, detailing when the course sessions are held. 

capacity (int): The maximum number of students that can enroll in the course.  

enrolledStudents (int): The current number of students enrolled in the course.  

*enrollments (vector<Enrollment>)**: A vector holding pointers to Enrollment objects. 

#Constructors : 

The class provides the following constructor: 

Parameterized Constructor: This constructor initializes a Course object with specified values for the title, description, schedule, and capacity. The enrolledStudents attribute is initialized to 0, indicating that no students are enrolled initially. 

t: The title of the course. 

d: The description of the course. 

s: The schedule of the course. 

c: The capacity of the course. 

#Member Functions 

The Course class provides several public member functions to interact with and manipulate course data: 

-getters : functions return the respective attributes of the course, allowing access to the course's title, description, schedule, capacity, and the number of enrolled students.         

-Enroll Student: This function attempts to enroll a student in the course. If the current number of enrolled students is less than the course capacity, it creates a new Enrollment object, adds it to the enrollments vector, increments the enrolledStudents count, and returns true. If the course is at full capacity, it returns false.Parameters: student: A pointer to the Student object to be enrolled. This function is used to enroll students in the course, ensuring the course does not exceed its capacity. 

-Create Course: This function sets the course attributes to the specified values, essentially creating or reinitializing a course with new details. Parameters: 

title: The new title of the course. 

description: The new description of the course. 

schedule: The new schedule of the course. 

capacity: The new capacity of the course. 

 

4.In our code the forth defined class was the “special course” class : 

The SpecialCourse class is a derived class that inherits from the Course class, extending its functionality to include additional attributes specific to special types of courses. This class encapsulates information about special courses, including their type and specific enrollment criteria. It provides methods to access these additional attributes while leveraging the functionality of the base Course class.  

#Class Attributes : 

The SpecialCourse class includes the following private attributes in addition to those inherited from the Course class: 

specialType (string): Describes the special type of the course (e.g., Honors, Advanced Placement). 

enrollmentCriteria (string): Specifies the criteria for enrolling in the special course (e.g., prerequisites, grade requirements). 

#Constructors : 

The class provides the following constructor:  

Parameterized Constructor: This constructor initializes a SpecialCourse object with specified values for the title, description, schedule, capacity, special type, and enrollment criteria. It uses an initializer list to call the base Course class constructor for the common attributes and directly initializes the new attributes. Parameters: 

title: The title of the course. 

description: The description of the course. 

schedule: The schedule of the course. 

capacity: The capacity of the course. 

specialType: The special type of the course. 

enrollmentCriteria: The criteria for enrolling in the special course. 

#Member Functions 

The SpecialCourse class provides the following public member functions in addition to those inherited from the Course class: 

 - Get Special Type:  This function returns the specialType attribute of the special course. 

 -Get Enrollment Criteria:This function returns the enrollmentCriteria attribute of the special course.  

 

** Relationship with the Course Class** 

The SpecialCourse class inherits from the Course class, making use of its attributes and methods while adding new attributes specific to special courses. This inheritance relationship allows SpecialCourse to benefit from the existing functionality of the Course class and extend it with additional capabilities. This design promotes code reuse and ensures that special courses are managed consistently with regular courses while accommodating their unique requirements. 

 

5.”user” class 

The User class is an abstract base class designed to represent general user information in a system. It provides a foundation for various types of users by encapsulating common attributes and defining a pure virtual function for displaying user information. This class ensures that all derived classes implement their own specific way of displaying user information while sharing common properties and behaviors. 

#Class Attributes 

The User class includes the following protected attributes: 

name (string): The name of the user. 

email (string): The email address of the user. 

userId (int): The unique identifier for the user. 

role (string): The role of the user within the system . 

profileDetails (string): Additional details about the user's profile. 

These attributes store essential information about the user, accessible to derived classes. 

 #Constructor 

The class provides the following parameterized constructor: 

 Parameterized Constructor: This constructor initializes a User object with specified values for the name, email, userId, role, and profile details. It sets up the initial state of the user with these attributes. Parameters: 

name: The name of the user. 

email: The email address of the user. 

userId: The unique identifier for the user. 

role: The role of the user within the system. 

profileDetails: Additional details about the user's profile. 

#Member Functions 

The User class provides the following public member functions: 

-Pure Virtual Function: This pure virtual function enforces that all derived classes must implement their own version of displayInfo, which displays the user's information. Being a pure virtual function makes User an abstract class, meaning it cannot be instantiated directly.  

-Getters:These functions return the respective attributes of the user, allowing access to the user's role and profile details.   

 

6. class “student” 

The Student class is a derived class that extends the functionality of the User class to represent students within an educational system. It encapsulates student-specific attributes and behaviors, such as enrollment in courses and displaying student information.          

#Class Attributes 

The Student class includes the following private attribute in addition to those inherited from the User class: 

 *enrolledCourses (vector<Course>)**: A vector holding pointers to Course objects representing the courses in which the student is enrolled. This attribute tracks the courses in which the student is currently enrolled.                         

#Constructor 

The class provides the following constructor: 

Parameterized Constructor : this constructor initializes a Student object with specified values for the name, email, userId, role, and profile details by calling the constructor of the base User class. It sets up the initial state of the student with these attributes.        

 #Member Functions     

The Student class provides the following public member functions: 

- Enroll Course: This function attempts to enroll the student in a given course. It calls the enrollStudent method of the Course class to enroll the student and adds the course to the enrolledCourses vector if successful. It returns true if the enrollment is successful, indicating that the student has been successfully added to the course, and false otherwise.Parameters: course: A pointer to the Course object in which the student intends to enroll.               

 -Display Info (Override):  This overridden function displays the student's information, including their name, email, and user ID, as well as the titles of the courses in which they are enrolled. It iterates over the enrolledCourses vector and prints the title of each course.      

 

7. “AdministrativeStaff”class 

The AdministrativeStaff class is a derived class that extends the functionality of the User class to represent administrative staff within a system. It encapsulates administrative staff-specific attributes and behaviors, such as managing administrative tasks and displaying staff information.  

 #Class Attributes 

The AdministrativeStaff class inherits all attributes from the base User class. It does not introduce any additional attributes of its own. 

 #Constructor 

The class provides the following constructor: 

Parameterized Constructor: This constructor initializes an AdministrativeStaff object with specified values for the name, email, userId, role, and profile details by calling the constructor of the base User class. It sets up the initial state of the administrative staff member with these attributes.           

#Member Functions 

 The AdministrativeStaff class provides the following public member function: 

-Display Info (Override):This overridden function displays the administrative staff member's information, including their name, email, and user ID. It provides a concise representation of the staff member's profile. This function is called to display the administrative staff member's information, providing insight into their profile within the system. 

 

8.” FacultyAdvisor” class  

The FacultyAdvisor class is a derived class that extends the functionality of the User class to represent faculty advisors within an educational system. It encapsulates faculty advisor-specific attributes and behaviors, such as advising students and displaying advisor information.  

#Class Attributes 

The FacultyAdvisor class includes the following private attribute in addition to those inherited from the User class :  

*advisees (vector<Student>)**: A vector holding pointers to Student objects representing the students advised by the faculty advisor. This attribute tracks the students assigned to the faculty advisor for guidance and support .  

#Constructor 

The class provides the following constructor: 

Parameterized Constructor: This constructor initializes a FacultyAdvisor object with specified values for the name, email, userId, role, and profile details by calling the constructor of the base User class. It sets up the initial state of the faculty advisor with these attributes. 

#Member Functions 

The FacultyAdvisor class provides the following public member functions: 

-Add Advisee:his function adds a student to the list of advisees assigned to the faculty advisor. It takes a pointer to a Student object as a parameter and adds it to the advisees vector. Parameters:student: A pointer to the Student object representing the student to be added as an advisee. 

-Display Info (Override):This overridden function displays the faculty advisor's information, including their name, email, and user ID, as well as the names of the students assigned to them as advisees. It iterates over the advisees vector and prints the name of each student. This function is called to display the faculty advisor's information, providing insight into their profile within the system and the students they advise. 

 

9. “enrollment” class  

The Enrollment class represents the enrollment of a student in a course within an educational system. It encapsulates information about the enrolled course, the student enrolled in the course, enrollment status, and grade.   

#Class Attributes 

The Enrollment class includes the following private attributes: 

*course (Course)**: A pointer to the Course object representing the enrolled course. 

*student (Student)**: A pointer to the Student object representing the enrolled student. 

status (string): The status of the enrollment . 

grade (float): The grade received by the student in the course. 

These attributes store essential information about the enrollment, including the course details, student details, enrollment status, and grade. 

#Constructor 

The class provides the a parameterized constructor: This constructor initializes an Enrollment object with specified values for the enrolled course, enrolled student, enrollment status, and grade. It sets up the initial state of the enrollment with these attributes. 

Parameters: 

c: A pointer to the Course object representing the enrolled course. 

s: A pointer to the Student object representing the enrolled student. 

st: The status of the enrollment (defaulted to "enrolled"). 

g: The grade received by the student in the course (defaulted to 0.0). 

#Member Functions 

The Enrollment class provides the following public member functions: 

-Getters:These functions return the respective attributes of the enrollment, allowing access to the enrolled course, enrolled student, enrollment status, and grade.these getters provide a way to retrieve specific information about the enrollment, which can be used for various purposes such as generating reports or checking student progress. 

-Update Status:his function updates the status of the enrollment to the provided new status. It allows for changes in the enrollment status as needed, such as marking it as withdrawn or completed. Parameters: newStatus: The new status to be assigned to the enrollment. 

-Update Grade:This function updates the grade received by the student in the course to the provided new grade. It enables the recording of grades as they are assigned or updated throughout the course. Parameters: newGrade: The new grade to be assigned to the student in the course. 

10.” schdule” class  

The Schedule class represents the timing and location details of an event or activity within a system. It encapsulates information about when and where an event or activity is scheduled to occur.  

#Class Attributes 

The Schedule class includes the following private attributes: 

timing (string): Represents the timing details of the scheduled event or activity. 

location (string): Represents the location details where the event or activity is scheduled to take place. 

These attributes store essential information about the schedule, allowing users to determine when and where an event or activity is scheduled. 

#Constructor 

The class provides the following constructor: 

Parameterized Constructor: This constructor initializes a Schedule object with specified values for the timing and location attributes. It sets up the initial state of the schedule with these details. Parameters: 

t: Represents the timing details of the scheduled event or activity. 

l: Represents the location details where the event or activity is scheduled to take place. 

#Member Functions 

The Schedule class provides the following public member functions: 

-Getters : These functions return the respective attributes of the schedule, allowing access to the timing and location details . These getters provide a way to retrieve specific information about the schedule, which can be used to display schedule details or perform scheduling-related operations. 

 

11.” CourseSchedule” class  

The CourseSchedule class extends the functionality of the Schedule class to represent the schedule of a specific course within an educational system. It encapsulates information about the timing and location of the course, along with details about the course itself. This report provides an overview of the design, attributes, methods, and usage of the CourseSchedule class, emphasizing its role in managing course schedule-related data. 

#Class Attributes 

The CourseSchedule class includes the following private attribute in addition to those inherited from the Schedule class: 

 *course (Course)**: A pointer to the Course object representing the course associated with the schedule. This attribute stores information about the course associated with the schedule, allowing users to access course-specific details when needed. 

#Constructor 

The class provides the following constructor : 

Parameterized Constructor : This constructor initializes a CourseSchedule object with specified values for the associated course, timing, and location attributes. It sets up the initial state of the course schedule with these details. 

Parameters: 

c: A pointer to the Course object representing the course associated with the schedule. 

t: Represents the timing details of the course schedule. 

l: Represents the location details where the course is scheduled to take place. 

#Member Functions 

The CourseSchedule class provides the following public member functions: 

-Get Course:This function returns the pointer to the Course object representing the course associated with the schedule. It allows users to access course-specific details associated with the schedule. This getter provides a way to retrieve the course object associated with the schedule, enabling access to course-specific information and functionalities.  

-Display Course Details:This function displays detailed information about the associated course, including its title, description, timing, location, and current enrollment status. It provides a comprehensive overview of the course details associated with the schedule. 

12.”requiremnt “ class  

The Requirement class encapsulates information about the prerequisites and eligibility criteria for a course within an educational system. It provides a structured representation of the requirements that students must fulfill to be eligible for enrollment in a particular course.  

 #Class Attributes 

The Requirement class includes the following private attributes: 

prerequisites (vector<string>): Represents a list of prerequisites required for enrollment in the course, expressed as strings. 

eligibilityCriteria (string): Represents additional eligibility criteria that students must meet to enroll in the course. 

These attributes store essential information about the requirements for course enrollment, allowing users to determine the prerequisites and eligibility criteria for specific courses. 

 #Constructor 

The class provides the following constructor:  

Parameterized Constructor: this constructor initializes a Requirement object with specified values for the prerequisites and eligibility criteria attributes. It sets up the initial state of the requirement with these details. 

Parameters: 

prereqs: A vector containing strings representing the prerequisites required for enrollment in the course. 

criteria: A string representing additional eligibility criteria that students must meet to enroll in the course. 

# Member Functions 

The Requirement class provides the following public member functions: 

-Get Prerequisites:This function returns the list of prerequisites required for enrollment in the course. It allows users to access the prerequisites associated with the requirement.    --Get Eligibility Criteria:This function returns the additional eligibility criteria that students must meet to enroll in the course. It allows users to access the eligibility criteria associated with the requirement. 

 

13.” SystemAccess”class 

The SystemAccess class manages permissions within a system by granting or revoking access rights to various functionalities or resources. It provides functionalities to grant, revoke, and retrieve permissions associated with users or roles.  

#Class Attributes 

The SystemAccess class includes the following private attribute: 

permissions (vector<string>): Represents a collection of permissions granted within the system. Each permission is stored as a string. 

This attribute stores essential information about the permissions granted within the system, allowing for efficient management and retrieval of access rights. 

 #Constructor 

The class provides the following constructor: 

Parameterized Constructor This constructor initializes a SystemAccess object with the initial set of permissions provided as input. It sets up the initial state of the system access with the specified permissions.  

Parameters: 

initialPermissions: A vector containing strings representing the initial set of permissions granted within the system. 

#Member Functions 

The SystemAccess class provides the following public member functions: 

-Grant Permission: This function grants a new permission to the system. It checks if the permission is not already granted before adding it to the permissions list. It provides feedback to the user indicating whether the permission was successfully granted or if it was already present. 

Parameters: 

permission: A string representing the permission to be granted. 

-Revoke Permission:This function revokes a permission from the system. It searches for the specified permission in the permissions list and removes it if found. It provides feedback to the user indicating whether the permission was successfully revoked or if it was not found. 

Parameters: 

permission: A string representing the permission to be revoked. 

-Get Permissions:his function retrieves the list of permissions currently granted within the system. It allows users to access the current set of permissions for auditing, reporting, or other purposes. 

Return Value: A vector of strings containing the permissions granted within the system. 

14.”gradereport”class  

The GradeReport class manages and generates reports on student grades within an educational system. It stores student-grade pairs and provides functionalities to add grades, generate reports, provide feedback, and track progress for individual students.  

# Class Attributes 

The GradeReport class includes the following private attribute : 

*gradeList (vector<pair<Student, float>>)**: Represents a collection of student-grade pairs, where each pair consists of a Student object pointer and the corresponding grade. 

This attribute stores essential information about student grades, allowing for efficient management and retrieval of performance data. 

 # Constructor 

The class provides a default constructor : This constructor initializes a GradeReport object. It sets up the initial state of the grade report. 

#Member FunctionsMember Functions 

The GradeReport class provides the following public member functions: 

-Generate Report:This function generates a report displaying student grades. It iterates over the gradeList and prints each student's ID and corresponding grade to the console.               

-Provide Feedback:This function provides feedback to a specific student. It takes a Student object pointer and feedback message as input and prints the feedback to the console.     

-Track Progress:This function tracks the progress of a specific student. It searches for the student's grade in the gradeList and prints the student's ID along with their current grade to the console. 

-Get Grade List:This function retrieves the list of student-grade pairs stored in the grade report. It allows users to access the performance data for further analysis or processing. 

-Add Grade:This function adds or updates a student's grade in the grade report. It takes a Student object pointer and the corresponding grade as input. If the student already exists in the report, the grade is updated; otherwise, a new student-grade pair is added to the gradeList. 

15.”notification” class 

The Notification class facilitates the dissemination of messages to users within a system. It allows messages to be sent to multiple recipients and supports user-specific notification settings.   

#Class Attributes 

The Notification class includes the following private attributes: 

message (string): Represents the content of the notification message. 

*recipients (vector<User>)**: Stores pointers to users who are recipients of the notification. 

*notificationSettings (map<User, string>)**: Maps each user to their respective notification settings, allowing customization of notification behavior for individual users. 

These attributes facilitate the storage and management of notification-related data, including the message content, recipients, and user-specific settings. 

#Constructor 

The class provides the following constructor: 

Parameterized Constructor: Initializes a Notification object with the specified message content. It sets up the initial state of the notification with the provided message. 

# Member Functions 

The Notification class provides the following public member functions :  

-Add Recipient:Adds a user to the list of recipients for the notification. It also initializes a default notification setting for the added user. 

Parameters: user: A pointer to the user to be added as a recipient. 

-Get Message:Retrieves the message content of the notification. 

Return Value: A string representing the notification message.             

-Get Recipients:Retrieves the list of recipients for the notification. 

Return Value: A vector of pointers to users who are recipients of the notification.    

- Send Notification: Sends the notification message to all recipients. It iterates through the list of recipients and prints the message content along with the recipient's user ID. 

-Manage Notification Settings:Updates the notification settings for a specific user. It allows customization of notification behavior for individual users by modifying their notification settings. 

Parameters: 

user: A pointer to the user whose notification settings are to be updated. 

settings: A string representing the new notification settings for the user. 

 

The main function discerption: 

The main() function serves as the entry point and control center for the Course Registration System. It interacts with the user, facilitates authentication, and manages various system functionalities through a series of menu-driven options. Here's a brief description of its functionality: 

1.Authentication: 

The user is prompted to log in by providing their user ID and PIN. If authentication is successful, the corresponding Account object is retrieved from the DataBase. 

2.Menu Display: 

Upon successful authentication, the main menu is displayed, presenting different options based on the user's role. 

Administrators have access to administrative functionalities such as registering, updating, and deleting courses. 

Students can enroll or drop courses and view their enrolled courses or grade reports. 

Faculty members can manage grades for students. 

3.User Interaction: 

Users select options by entering the corresponding numeric choice. 

Each choice triggers specific actions based on the user's role and the selected option. 

Input validation ensures that only valid choices are accepted. 

4.Functionality Execution: 

 Based on the selected option, the system executes various functionalities such as course registration, enrollment, grade management, etc. 

The execution involves interactions with the DataBase object to perform CRUD operations on courses and manage grades. 

5.Logout and Exit: 

 Users can choose to log out, which resets the authentication status. 

The system can be exited by choosing the exit option, terminating the program execution. 

6.Error Handling: 

Invalid choices or unauthorized accesses are handled by displaying error messages and prompting the user to try again. 

 

Overall, the main() function orchestrates the interaction between users and the Course Registration System, ensuring seamless navigation through the available functionalities while maintaining security and integrity. 

 

Conclusion :  

The Course Registration System represents a comprehensive and efficient solution for managing course registration, enrollment, and grade management within an educational institution. Through a combination of user-friendly interfaces, robust data management, and role-based access control, the system provides students, faculty, and administrators with the tools they need to streamline administrative processes and enhance the educational experience. 
