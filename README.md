# List-Application

import java.util.ArrayList;
import java.util.Scanner;

public class TaskListApp {
    public static void main(String[] args) {
        TaskList taskList = new TaskList();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            displayMenu();
            int choice = getUserChoice(scanner);

            switch (choice) {
                case 1:
                    taskList.addTask(getTaskName(scanner));
                    break;
                case 2:
                    if (!taskList.isEmpty()) {
                        taskList.listTasks();
                        int taskNumber = getUserInput(scanner, "Enter the task number to remove: ");
                        if (taskList.isValidTaskNumber(taskNumber)) {
                            taskList.removeTask(taskNumber);
                        } else {
                            System.out.println("Invalid task number.");
                        }
                    } else {
                        System.out.println("No tasks to remove.");
                    }
                    break;
                case 3:
                    if (!taskList.isEmpty()) {
                        taskList.listTasks();
                    } else {
                        System.out.println("No tasks to list.");
                    }
                    break;
                case 4:
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid option. Please try again.");
            }
        }
    }

    private static void displayMenu() {
        System.out.println("Task List Application");
        System.out.println("1. Add Task");
        System.out.println("2. Remove Task");
        System.out.println("3. List Tasks");
        System.out.println("4. Quit");
        System.out.print("Select an option: ");
    }

    private static int getUserChoice(Scanner scanner) {
        return scanner.nextInt();
    }

    private static String getTaskName(Scanner scanner) {
        System.out.print("Enter task name: ");
        return scanner.next();
    }

    private static int getUserInput(Scanner scanner, String prompt) {
        System.out.print(prompt);
        return scanner.nextInt();
    }
}

class TaskList {
    private ArrayList<String> tasks = new ArrayList<>();

    public void addTask(String name) {
        tasks.add(name);
        System.out.println("Task added.");
    }

    public void removeTask(int taskNumber) {
        tasks.remove(taskNumber - 1);
        System.out.println("Task removed.");
    }

    public void listTasks() {
        for (int i = 0; i < tasks.size(); i++) {
            System.out.println((i + 1) + ". " + tasks.get(i));
        }
    }

    public boolean isEmpty() {
        return tasks.isEmpty();
    }

    public boolean isValidTaskNumber(int taskNumber) {
        return taskNumber >= 1 && taskNumber <= tasks.size();
    }
}

"C:\Program Files\Java\jdk-17\bin\java.exe" "-javaagent:C:\Program Files\JetBrains\IntelliJ IDEA Community Edition 2023.2.3\lib\idea_rt.jar=55056:C:\Program Files\JetBrains\IntelliJ IDEA Community Edition 2023.2.3\bin" -Dfile.encoding=UTF-8 -classpath "C:\Users\akash\IdeaProjects\java intern\out\production\java intern" TaskListApp
Task List Application
1. Add Task
2. Remove Task
3. List Tasks
4. Quit
Select an option: 1
Enter task name: Task 1
Task added.
Task List Application
1. Add Task
2. Remove Task
3. List Tasks
4. Quit
Select an option: Enter task name: Task 1
Task added.
Task List Application
1. Add Task
2. Remove Task
3. List Tasks
4. Quit
Select an option: Enter task name: task 1
Task added.
Task List Application
1. Add Task
2. Remove Task
3. List Tasks
4. Quit
Select an option: Enter task name: 1
Task added.
Task List Application
1. Add Task
2. Remove Task
3. List Tasks
4. Quit
Select an option: 2
1. Task
2. Task
3. task
4. 1
Enter the task number to remove: 1
Task removed.
Task List Application
1. Add Task
2. Remove Task
3. List Tasks
4. Quit
Select an option: 3
1. Task
2. task
3. 1
Task List Application
1. Add Task
2. Remove Task
3. List Tasks
4. Quit
Select an option: 4

Process finished with exit code 0


