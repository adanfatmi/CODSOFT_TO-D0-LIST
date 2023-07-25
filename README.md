# to_do_list

Let me explain the main functions and their purpose:

`add_task()`: This function adds a new task to the list and updates the database. It checks if the task field is empty, and if not, adds the task to the list and the database.

`list_update()`: This function updates the task listbox widget with the current list of tasks. It is called after adding or deleting a task to refresh the displayed tasks.

 `delete_task()`: This function deletes the selected task from the list and the database. It first gets the selected task from the listbox, then removes it from the list and updates the database accordingly.

`delete_all_tasks()`: This function asks for confirmation from the user and then deletes all tasks from the list and the database.

`clear_list()`: This function clears all tasks from the listbox widget. It is called before updating the list to avoid duplicates.

`close()`: This function is not used in the code provided, but it seems to be intended to close the application window and print the current tasks before exiting.

`retrieve_database()`: This function retrieves all tasks from the database and stores them in the tasks list. It is probably used to populate the list with previously saved tasks when the application starts.









- ![#f03c15] `### Import required libraries`

```python

import tkinter as tk
from tkinter import ttk
from tkinter import messagebox
import sqlite3 as sql
```





### Add Task

```python

def add_task():
    task_string = task_field.get()
    if len(task_string) == 0:
        messagebox.showinfo('Error', 'Field is Empty.')
    else:
        tasks.append(task_string)
        the_cursor.execute('insert into tasks values (?)', (task_string,))
        list_update()
        task_field.delete(0, 'end')

```
