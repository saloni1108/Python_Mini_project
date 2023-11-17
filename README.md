# Python_Mini_project

# Views
CustomLoginView
The CustomLoginView class handles user authentication and redirects authenticated users to the task list upon successful login.

- Template: task_done/login.html
- Fields: All fields are included.
- Redirects authenticated users to the task list.
- 
# RegisterPage
The RegisterPage class is a form view for user registration.

- Template: task_done/register.html
- Form: UserCreationForm
Redirects authenticated users to the task list upon successful registration.
Overrides form_valid method to log in the user upon successful registration.

# TaskList
The TaskList class is a list view that displays tasks associated with the logged-in user.

- Model: Task
- Context Object Name: 'tasks'
Requires login to access.

#TaskDetail
The TaskDetail class is a detail view for displaying information about a specific task.

- Model: Task
- Context Object Name: 'task'
Filters tasks to show only those associated with the logged-in user.
Counts incomplete tasks.

#TaskCreate
The TaskCreate class is a create view for adding new tasks.

- Model: Task
- Form fields: ['title', 'description', 'complete']
Requires login to access.
Sets the task's user to the currently logged-in user.

#TaskUpdate
The TaskUpdate class is an update view for modifying existing tasks.

- Model: Task
- Form fields: ['title', 'description', 'complete']
Requires login to access.


#DeleteView
The DeleteView class is a delete view for removing tasks.

- Model: Task
- Context Object Name: 'task'
Requires login to access.


#URL Patterns
The URL patterns in urls.py map views to specific URLs.

- Login: /login/
- Logout: /logout/
- Register: /register/
- Task List: /
- Task Detail: /task/<int:pk>/
- Task Create: /task-create/
- Task Update: /task-update/<int:pk>/
- Task Delete: /task-delete/<int:pk>/



#Models
Task Model
The Task model represents a user's task.

- Fields:
  - user: ForeignKey to the User model.
  - title: CharField with a maximum length of 200 characters.
  - description: TextField (nullable).
  - complete: BooleanField with a default value of False.
  - create: DateTimeField set to auto_now_add.
- Ordering: Tasks are ordered by completion status.
