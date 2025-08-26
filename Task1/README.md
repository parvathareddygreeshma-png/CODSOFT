This folder contains my Task 1 project files.
import os

FILENAME = "tasks.txt"

def load_tasks():
    if os.path.exists(FILENAME):
        with open(FILENAME, "r") as f:
            return [line.strip() for line in f.readlines()]
    return []
def save_tasks(tasks):
    with open(FILENAME, "w") as f:
        for task in tasks:
            f.write(task + "\n")
def show_tasks(tasks):
    if not tasks:
        print("No tasks yet!")
    else:
        for i, task in enumerate(tasks, 1):
            print(f"{i}. {task}")
tasks = load_tasks()
while True:
    print("\n--- To-Do List ---")
    print("1. Show tasks\n2. Add task\n3. Mark as done\n4. Exit")
    choice = input("Choose: ")
    if choice == "1":
        show_tasks(tasks)
    elif choice == "2":
        task = input("Enter task: ")
        if task.strip():  
            tasks.append(task.strip())
            save_tasks(tasks)
        else:
            print("Task cannot be empty!")
    elif choice == "3":
        if not tasks:
            print("No tasks to mark as done!")
        else:
            show_tasks(tasks)
            try:
                num = int(input("Enter task number to mark done: "))
                if 0 < num <= len(tasks):
                    if not tasks[num - 1].endswith(""):  
                        tasks[num - 1] += ""
                        save_tasks(tasks)
                        print("Task marked as done!")
                    else:
                        print("Task already marked done.")
                else:
                    print("Invalid task number.")
            except ValueError:
                print("Please enter a valid number.")
    elif choice == "4":
        print("Exiting... Goodbye!")
        break
    else:
        print("Invalid choice, please try again!")
