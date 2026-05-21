# Student Management System — CRUD Assignment Guide

**Using HTML, CSS, JavaScript and localStorage**

## Assignment Goal

You are going to build a Student Management System using only:

- HTML
- CSS
- JavaScript
- localStorage

The purpose of this assignment is not only to build a working CRUD application, but also to understand why frontend, backend, and database logic are separated in real-world systems.

## Project Scenario

A small training institute wants a simple system to manage student details.

The institute wants to:

- Add student details
- View student details
- Edit student details
- Delete student details
- Search students
- Store student data temporarily in the browser

Your task is to build this system using frontend technologies only.

## Project Name
Student Management System
## Required Files

Create one project folder:

- `student-management-localstorage`

Inside the folder, create these files:

- `index.html`
- `style.css`
- `script.js`
- `README.md`
## Step-by-Step Assignment Instructions
## Step 1: Understand the System Before Building

Before creating any file, think about the system.

Your system should manage student records.

Each student record should include:

- Student ID
- Full Name
- Age
- Email
- Course
- Contact Number
- Address
### Questions to Answer
- Why do we need a Student Management System?
- Why should each student have a unique Student ID?
- Why do we need to collect more than just the student name?
- Why is it important to plan the data before designing the page?
- If this system is used by a real institute, what problems can it solve?
## Step 2: Create the Project Folder

Create a folder for your project.

The folder should contain:

- `index.html`
- `style.css`
- `script.js`
- `README.md`
### Questions to Answer
- Why do we create a separate folder for one project?
- Why do we separate HTML, CSS, and JavaScript into different files?
- Why is file organization important in software development?
- What problems can happen if all code is written in one file?
## Step 3: Plan the User Interface

Before coding, draw or sketch your layout.

Your page should contain:

- Page title
- Student input form
- Search bar
- Student list area
- Clear all records button

You can display student records as:

- Table
- or
- Cards
### Questions to Answer
- Why does the system need a form?
- Why should the student list be clearly visible?
- Why do we need a search bar?
- Why should buttons have meaningful names like Add, Edit, Delete, and Clear?
- Why is user-friendly design important even for a simple project?
## Step 4: Build the HTML Structure

Create the basic structure of the web page.

Your HTML should include:

- Main heading
- Form fields
- Submit button
- Search input
- Student display section
- Clear all button

The form should collect:

- Student ID
- Full Name
- Age
- Email
- Course
- Contact Number
- Address
### Questions to Answer
- Why is HTML called the structure of a web page?
- Why do we use input fields in a form?
- Why should every input field have a clear label or placeholder?
- Why is a submit button needed?
- Why do we need a separate area to display saved students?
## Step 5: Design the Page with CSS

Use CSS to make your page clean and readable.

Your design should include:

- Proper spacing
- Readable font size
- Clear form layout
- Button styling
- Student card or table styling
- Mobile-friendly layout
### Questions to Answer
- Why do we use CSS in a web application?
- Why is spacing important in a form?
- Why should buttons have different styles for different actions?
- Why should delete buttons visually look different from edit buttons?
- Why is responsive design important?
## Step 6: Identify the Data Structure

Before writing JavaScript logic, decide how one student should be represented.

Think of one student as an object.

Think of many students as a list of objects.

Example idea:

- One student = one object
- Many students = array of objects

Do not copy code. Just understand the structure.

### Questions to Answer
- Why is one student stored as an object?
- Why are multiple students stored in an array?
- Why should each object have the same property names?
- Why is Student ID useful when editing or deleting records?
- How is this similar to rows in a database table or documents in MongoDB?
## Step 7: Connect JavaScript to the HTML Page

Use JavaScript to select form fields, buttons, and display areas.

Your JavaScript should be able to interact with:

- Student form
- Input fields
- Submit button
- Search input
- Student list area
- Clear all button
### Questions to Answer
- Why does JavaScript need to select HTML elements?
- Why do we use event listeners?
- What should happen when the form is submitted?
- Why should the page not reload when submitting the form?
- How does JavaScript make the page interactive?
## Step 8: Add Student Data

When the user fills the form and clicks submit, your system should:

- Collect the input values
- Validate the values
- Create a student record
- Add the record to the student list
- Save the updated list
- Display the new student on the page
- Clear the form
### Questions to Answer
- Why do we collect values from the form?
- Why should we validate data before saving it?
- Why should empty fields not be allowed?
- Why should duplicate Student IDs not be allowed?
- Why should the form clear after successfully adding a student?
## Step 9: Store Data in localStorage

After adding a student, save the student list in localStorage.

The data should remain even after refreshing the page.

### Questions to Answer
- Why do we need to store data?
- Why does normal JavaScript data disappear after refreshing the page?
- Why do we use localStorage in this project?
- Why do we convert data before saving it in localStorage?
- Is localStorage a real database? Why or why not?
## Step 10: Load Data from localStorage

When the page opens, the system should check whether student data already exists in localStorage.

If data exists, display it automatically.

### Questions to Answer
- Why should saved data appear after refreshing the page?
- Why do we need to read data when the page loads?
- What happens if localStorage is empty?
- Why should the application handle empty data safely?
- How is this similar to fetching data from a database?
## Step 11: Display Student Records

Create a function or logic to show all saved students on the page.

Each student should show:

- Student ID
- Full Name
- Age
- Email
- Course
- Contact Number
- Address
- Edit button
- Delete button
### Questions to Answer
- Why do we need to display saved data?
- Why should each student record have Edit and Delete buttons?
- Why should the displayed list update after every action?
- Why is it better to display data dynamically instead of manually writing it in HTML?
- How is this similar to showing data received from a backend API?
## Step 12: Edit Student Data

When the user clicks Edit:

- The selected student details should appear in the form
- The user should change the details
- The system should update the existing record
- The student list should refresh
- The updated data should be saved again in localStorage
### Questions to Answer
- Why do we need an edit feature?
- Why should the existing data appear in the form before editing?
- Why should the system update the same record instead of creating a new one?
- Why is Student ID important when finding the correct record?
- What problems can happen if the wrong record is updated?
## Step 13: Delete Student Data

When the user clicks Delete:

- Ask for confirmation
- Remove the selected student
- Update localStorage
- Refresh the displayed student list
### Questions to Answer
- Why do we need a delete feature?
- Why should the system ask for confirmation before deleting?
- Why should localStorage be updated after deleting?
- Why should the student list refresh immediately?
- What can happen if delete is done without confirmation?
## Step 14: Search Student Records

Add a search feature.

The user should be able to search by:

- Student ID
- Full Name
- Course

When the user types in the search box, matching students should be displayed.

### Questions to Answer
- Why is search useful in a student management system?
- Why is it difficult to find a student manually when records increase?
- Why should search work by Student ID, name, or course?
- Why do we use filtering logic for search?
- How is this similar to searching records in a database?
## Step 15: Clear All Records

Add a button to remove all student records.

Before clearing, ask for confirmation.

After clearing:

- Remove all records from localStorage
- Show an empty student list
### Questions to Answer
- Why might a user need to clear all records?
- Why is confirmation very important here?
- Why should this feature be used carefully?
- What is the difference between deleting one record and clearing all records?
- What would happen in a real system if all database records were deleted?
## Step 16: Add Form Validation

Your system should validate:

- Student ID is required
- Full Name is required
- Age is required and must be positive
- Email is required and must be valid
- Course is required
- Contact Number is required
- Address is required
- Duplicate Student ID is not allowed
### Questions to Answer
- Why is validation important?
- Why should incorrect data not be saved?
- Why should duplicate Student IDs be prevented?
- Why is frontend validation useful?
- Why is frontend validation alone not enough for real applications?
## Step 17: Test the Application

Test your application carefully.

You must test:

- Add one student
- Add multiple students
- Refresh the page
- Edit a student
- Delete a student
- Search for a student
- Clear all records
- Try empty form submission
- Try duplicate Student ID
- Try invalid email
### Questions to Answer
- Why is testing important?
- Why should we test both correct and incorrect inputs?
- Why should we refresh the page during testing?
- Why should we test duplicate Student IDs?
- What errors did you find while testing, and how did you fix them?
## Step 18: Inspect localStorage in Browser Developer Tools

Open browser developer tools and check localStorage.

You should be able to see the saved student data.

Take a screenshot for submission.

### Questions to Answer
- Where exactly is the student data stored?
- Why can we see localStorage data in developer tools?
- What happens if you manually delete localStorage data?
- Can another browser see this same data?
- Can another computer access this data? Why?
## Step 19: Compare localStorage with a Real Database

After completing the project, compare this system with a real full-stack system.

Use this idea:

This project:
- HTML form → JavaScript logic → localStorage → Display

Real system:
HTML form → JavaScript fetch request → Backend API → Database → Response → Display
### Questions to Answer
- In this project, which part acts like the database?
- In this project, which part handles the application logic?
- Why is localStorage not suitable for many users?
- Why do real systems need a backend?
- Why do real systems need a database like MongoDB?
## Step 20: Create README.md

Create a README file for your project.

Your README should include:

- Project title
- Project description
- Features
- How to run the project
- What you learned
- Answers to the reflection questions
- Limitations of localStorage

### Questions to Answer
- Why is README important in a project?
- Why should someone else be able to understand your project from the README?
- Why should we document features?
- Why should we explain how to run the project?
- Why is reflection important after completing a project?
## Step 21: Upload to GitHub

Upload your complete project to GitHub.

Your repository should contain:

- `index.html`
- `style.css`
- `script.js`
- `README.md`
- Screenshots if required
### Questions to Answer
- Why do developers use GitHub?
- Why is version control important?
- Why should project files be organized before uploading?
- Why should the README be included in GitHub?
- How can GitHub help when applying for internships or jobs?
## Final Submission Requirements

Students must submit:

- GitHub repository link
- README.md file
- Completed reflection answers
## Final Reflection Questions

Students must answer these after completing the project.

### Frontend Understanding
What role did HTML play in this project?
What role did CSS play in this project?
What role did JavaScript play in this project?
### CRUD Understanding
Which part of your project created data?
Which part displayed data?
Which part updated data?
Which part deleted data?
### Storage Understanding
Where was the student data stored?
What happened after refreshing the page?
What happened when opening the project in another browser?
### Backend and Database Thinking
Why is localStorage not enough for a real school system?
Why do we need a backend in real applications?
Why do we need a database in real applications?
What is the difference between localStorage and MongoDB?
What is the difference between JavaScript frontend logic and backend logic?
