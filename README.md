class Task:
    def __init__(self, task_id, description, due_date, priority, status):
        self.task_id = task_id
        self.description = description
        self.due_date = due_date
        self.priority = priority
        self.status = status

class TaskManager:
    def __init__(self):
        self.tasks = []

    def create_task(self, description, due_date, priority, status):
        task_id = len(self.tasks) + 1
        task = Task(task_id, description, due_date, priority, status)
        self.tasks.append(task)
        print(f"Task {task_id} created successfully!")

    def read_tasks(self):
        if not self.tasks:
            print("No tasks available.")
        else:
            for task in self.tasks:
                print(f"Task ID: {task.task_id}, Description: {task.description}, Due Date: {task.due_date}, Priority: {task.priority}, Status: {task.status}")

    def update_task(self, task_id, description=None, due_date=None, priority=None, status=None):
        for task in self.tasks:
            if task.task_id == task_id:
                if description:
                    task.description = description
                if due_date:
                    task.due_date = due_date
                if priority:
                    task.priority = priority
                if status:
                    task.status = status
                print(f"Task {task_id} updated successfully!")
                return
        print(f"Task {task_id} not found.")

    def delete_task(self, task_id):
        for task in self.tasks:
            if task.task_id == task_id:
                self.tasks.remove(task)
                print(f"Task {task_id} deleted successfully!")
                return
        print(f"Task {task_id} not found.")

    def sort_tasks(self, sort_by):
        if sort_by == "due_date":
            self.tasks.sort(key=lambda x: x.due_date)
        elif sort_by == "priority":
            self.tasks.sort(key=lambda x: x.priority)
        elif sort_by == "status":
            self.tasks.sort(key=lambda x: x.status)
        else:
            print("Invalid sort option.")
            return
        print("Tasks sorted successfully!")

    def mark_task_completed(self, task_id):
        for task in self.tasks:
            if task.task_id == task_id:
                task.status = "completed"
                print(f"Task {task_id} marked as completed!")
                return
        print(f"Task {task_id} not found.")

def main():
    task_manager = TaskManager()

    while True:
        print("\nTask Management System")
        print("1. Create Task")
        print("2. View Tasks")
        print("3. Update Task")
        print("4. Delete Task")
        print("5. Sort Tasks")
        print("6. Mark Task as Completed")
        print("7. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            description = input("Enter task description: ")
            due_date = input("Enter due date (YYYY-MM-DD): ")
            priority = input("Enter priority (high/medium/low): ")
            status = "pending"
            task_manager.create_task(description, due_date, priority, status)
        elif choice == "2":
            task_manager.read_tasks()
        elif choice == "3":
            task_id = int(input("Enter task ID: "))
            description = input("Enter new task description (press enter to skip): ")
            due_date = input("Enter new due date (YYYY-MM-DD, press enter to skip): ")
            priority = input("Enter new priority (high/medium/low, press enter to skip): ")
            status = input("Enter new status (pending/completed, press enter to skip): ")
            task_manager.update_task(task_id, description if description else None, due_date if due_date else None, priority if priority else None, status if status else None)
        elif choice == "4":
            task_id = int(input("Enter task ID: "))
            task_manager.delete_task(task_id)
        elif choice == "5":1
if __name__ == "__main__":
    main()
