# TO-DO-LIST
# Simple To-Do List Application

# Function to display the menu
def display_menu():
    print("\nTo-Do List Menu")
    print("1. View Tasks")
    print("2. Add Task")
    print("3. Mark Task as Completed")
    print("4. Exit")

# Function to view tasks
def view_tasks(tasks):
    if not tasks:
        print("\nYour to-do list is empty!")
    else:
        print("\nYour Tasks:")
        for i, task in enumerate(tasks, start=1):
            status = "✅ Completed" if task['completed'] else "❌ Pending"
            print(f"{i}. {task['task']} - {status}")

# Function to add a task
def add_task(tasks):
    task_name = input("Enter the task: ")
    tasks.append({"task": task_name, "completed": False})
    print(f"Task '{task_name}' added!")

# Function to mark a task as completed
def mark_task_completed(tasks):
    view_tasks(tasks)
    if tasks:
        try:
            task_number = int(input("Enter the task number to mark as completed: "))
            if 1 <= task_number <= len(tasks):
                tasks[task_number - 1]['completed'] = True
                print(f"Task {task_number} marked as completed!")
            else:
                print("Invalid task number!")
        except ValueError:
            print("Please enter a valid number!")

# Main function
def main():
    tasks = []
    while True:
        display_menu()
        choice = input("Choose an option (1-4): ")
        if choice == "1":
            view_tasks(tasks)
        elif choice == "2":
            add_task(tasks)
        elif choice == "3":
            mark_task_completed(tasks)
        elif choice == "4":
            print("Goodbye!")
            break
        else:
            print("Invalid choice! Please try again.")

if __name__ == "__main__":
    main()
