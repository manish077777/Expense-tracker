# Expense-tracker


This Python script creates an expense tracking application that allows users to add and delete expenses, store them in a CSV file, and view the list of expenses. The application includes input fields for the user to specify the date, category, amount, and description of an expense. It also provides features for adding, deleting, and displaying expenses in a listbox, and ensures that the data is persisted across sessions by saving it in a CSV file.

Components of the Code
Imports:

tkinter: A standard Python library for creating graphical user interfaces. It is used here to build the main window and input forms.
messagebox from tkinter: Used to show dialog boxes for warnings, errors, or success messages.
pandas: A powerful data manipulation library. It is used to manage the expense data in the form of a DataFrame and save it to a CSV file.
datetime: A Python module for working with dates and times. It is used to set the default date for new expenses to the current date.
Global Variables:

filename: The name of the CSV file (expenses.csv) where the expense data is saved.
expenses_df: A Pandas DataFrame that holds the expense data. It is initialized from the CSV file when the program starts. If the file doesn't exist, a new DataFrame is created.
Core Functions
save_data():

This function saves the current state of the expense data (expenses_df) to the CSV file (expenses.csv). It uses the to_csv() method from Pandas, which overwrites the existing file with the updated data.
add_expense():

This function is triggered when the user clicks the "Add Expense" button.
It collects the values entered in the input fields (entry_date, entry_category, entry_amount, entry_description).
It checks if all fields are filled out and if the Amount is a valid number. If any validation fails, an appropriate error or warning message is displayed using messagebox.
A new expense is added to the expenses_df DataFrame, and the updated data is saved to the CSV file.
The input fields are cleared, and the listbox of expenses is updated to show the new data.
A success message is shown when the expense is successfully added.
delete_expense():

This function is triggered when the user clicks the "Delete Expense" button.
It checks if an item is selected in the listbox (listbox_expenses). If no item is selected, a warning message is displayed.
The selected expense is removed from the expenses_df DataFrame, and the changes are saved back to the CSV file.
The listbox is updated to reflect the removal, and a success message is shown.
show_expenses():

This function populates the listbox (listbox_expenses) with the expenses currently stored in expenses_df.
It loops through the rows of the DataFrame and formats each expense as a string that includes the Date, Category, Amount, and Description.
Each formatted expense is inserted into the listbox for display.
This function is called initially when the application starts and whenever an expense is added or deleted.
clear_entries():

This function clears all the input fields (entry_date, entry_category, entry_amount, entry_description), allowing the user to start with empty fields after adding an expense.
set_today_date():

This function sets the date entry field to today's date by default.
It uses the datetime.now().strftime() method to get the current date in the "YYYY-MM-DD" format and inserts it into the entry_date field.
GUI Setup
Window Setup:

The Tk() instance (app) is created as the main window. The window's title is set to "Expense Tracker", and its size is defined as 600x400 pixels. The background color of the window is set to lightgray.
Input Fields:

Four labeled input fields are created for the user to enter the Date, Category, Amount, and Description of the expense.
These input fields are arranged in a grid layout using the grid() method, and each has a corresponding label.
The Date input field is pre-filled with the current date by calling set_today_date().
Buttons:

Two buttons are created:
"Add Expense": Triggers the add_expense() function to add a new expense.
"Delete Expense": Triggers the delete_expense() function to delete a selected expense.
Listbox:

A listbox is created to display the current list of expenses. Each expense is shown in the format: Date - Category - Amount - Description.
The listbox is updated every time an expense is added or deleted using the show_expenses() function.
Initial Population of the Listbox:

Upon startup, the show_expenses() function is called to populate the listbox with any existing data from the CSV file.
Running the Application
The script runs the Tkinter mainloop() which keeps the application open, allowing the user to interact with the GUI.
All changes (adding or deleting expenses) are saved to the CSV file, ensuring that data persists across sessions.
File Management
Expense Data File: All expenses are stored in a CSV file (expenses.csv). The columns in the file are Date, Category, Amount, and Description. If the file doesn’t exist, a new empty file is created when the app runs.
