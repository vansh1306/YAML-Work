# **Python YAML Use Case - Student Data Processing**

## **Overview**
This Python project reads student information from a **YAML** file, displays the student data, and allows filtering students based on their **GPA**. The project demonstrates how to work with YAML files in Python using the `PyYAML` library.

---

## **Table of Contents**
1. [Installation](#installation)
2. [Project Structure](#project-structure)
3. [Step-by-Step Guide](#step-by-step-guide)
   - [Creating the YAML File](#creating-the-yaml-file)
   - [Writing the Python Script](#writing-the-python-script)
   - [Running the Application](#running-the-application)
4. [Expected Output](#expected-output)
5. [GitHub Setup](#github-setup)
6. [Conclusion](#conclusion)

---

## **Installation**
1. Ensure you have Python installed (Version **3.x** recommended). Check with:
   ```sh
   python --version
   ```
2. Install the `PyYAML` package:
   ```sh
   pip install pyyaml
   ```

---

## **Project Structure**
Your project directory should look like this:

```
Python-YAML-Project/
│── students.yaml      # YAML file containing student data
│── app.py             # Main Python script
│── README.md          # Documentation
```

---

## **Step-by-Step Guide**

### **1. Creating the YAML File**
Create a **students.yaml** file in the project directory with the following content:

```yaml
students:
  - name: Alice
    age: 21
    major: Computer Science
    gpa: 3.8

  - name: Bob
    age: 22
    major: Mathematics
    gpa: 3.5

  - name: Charlie
    age: 20
    major: Physics
    gpa: 3.9

  - name: David
    age: 23
    major: Chemistry
    gpa: 3.2

  - name: Eva
    age: 21
    major: Computer Science
    gpa: 3.7
```

### **2. Writing the Python Script**
Create a **Python script (app.py)** to read and process the YAML data.

```python
import yaml

def load_data(file_path):
    """Load data from a YAML file."""
    with open(file_path, 'r') as file:
        data = yaml.safe_load(file)
    return data

def display_students(students):
    """Display all student details."""
    print("\nAll Students:")
    for student in students:
        print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")

def filter_students_by_gpa(students, min_gpa):
    """Filter students based on minimum GPA."""
    filtered_students = [s for s in students if s['gpa'] >= min_gpa]
    print(f"\nStudents with GPA >= {min_gpa}:")
    
    if filtered_students:
        for student in filtered_students:
            print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")
    else:
        print("No students found.")

def main():
    data = load_data('students.yaml')
    students = data['students']

    display_students(students)

    min_gpa = float(input("\nEnter minimum GPA to filter students: "))
    filter_students_by_gpa(students, min_gpa)

if __name__ == "__main__":
    main()
```

### **3. Running the Application**
To execute the script:
1. Ensure `students.yaml` and `app.py` are in the same directory.
2. Run the script:
   ```sh
   python app.py
   ```

---

## **Expected Output**
When you run `python app.py`, the program will:
1. Display all students.
2. Ask for a **minimum GPA**.
3. Show students with GPA greater than or equal to the input.

### **Example Output**
```
All Students:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Bob, Age: 22, Major: Mathematics, GPA: 3.5
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: David, Age: 23, Major: Chemistry, GPA: 3.2
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7

Enter minimum GPA to filter students: 3.6

Students with GPA >= 3.6:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7

```

---

## **GitHub Setup**
### **1. Initialize Git Repository**
```sh
git init
```

### **2. Add Files to Git**
```sh
git add .
git commit -m "Initial commit - YAML processing script"
```

### **3. Create a Repository on GitHub**
1. Go to [GitHub](https://github.com/) → Click **New Repository**.
2. Name it **Python-YAML-Project**.
3. Copy the repository URL (e.g., `https://github.com/your-username/Python-YAML-Project.git`).

### **4. Connect Local Repository to GitHub**
```sh
git remote add origin https://github.com/your-username/Python-YAML-Project.git
git branch -M main
git push -u origin main
```

---

## **Conclusion**
This project is a basic introduction to handling **YAML** data in Python. You can enhance it by:
- Adding **sorting** options.
- Allowing **updates** to student records.
- Saving **filtered results** back to YAML.
