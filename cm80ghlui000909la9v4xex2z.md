---
title: "Understanding GitHub Hooks: A Simple Guide for Everyone"
seoTitle: "GitHub Hooks Explained – How to Automate Your Development Workflow"
seoDescription: "Learn how GitHub Hooks automate workflows, trigger actions, and enhance your development process. A beginner-friendly guide to mastering GitHub automation."
datePublished: Sat Mar 08 2025 17:06:04 GMT+0000 (Coordinated Universal Time)
cuid: cm80ghlui000909la9v4xex2z
slug: understanding-github-hooks-a-simple-guide-for-everyone
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1741495402050/66d1c2a3-f131-4d79-9a0a-0cf8eb543ad0.png
tags: devops

---

![](https://www.hostinger.in/tutorials/wp-content/uploads/sites/2/2022/02/git-hooks.jpg align="center")

GitHub is a popular platform for developers to collaborate on code, but did you know it can also automate tasks? This is where **GitHub Hooks** come in! Whether you're from a technical background or not, this blog will break it down in a simple and easy-to-understand way.

### What are GitHub Hooks?

GitHub Hooks are like **automatic triggers** that perform specific actions when something happens in a repository. Imagine you have a vending machine: when you press a button (trigger), the machine delivers a snack (action). Similarly, GitHub Hooks listen for events and then take action automatically.

### Why Use GitHub Hooks?

GitHub Hooks help in automating tasks like:

* Sending notifications when someone makes a change in the code.
    
* Running tests to check if the code is working correctly.
    
* Deploying updates to a live website automatically.
    
* Logging activities for tracking changes and security.
    
* **Preventing sensitive information (like passwords or API keys) from being accidentally pushed to GitHub.**
    
* Git Hooks are scripts that run on your local machine before or after specific Git actions.
    
* Example: Running a script to check code formatting before committing changes.
    

### Pre-Commit Hooks: Stopping Secrets from Getting Pushed 🚫

One of the most useful Git Hooks is the **pre-commit hook**. This helps prevent accidental commits of sensitive information before they are pushed to GitHub. (Api Keys , Passwords , Database Url )

#### How does a pre-commit hook work?

1. **Before committing the code**, the pre-commit hook runs a script that checks the staged files.
    
2. **It scans for sensitive information**, such as API keys, passwords, or database credentials.
    
3. **If sensitive data is found**, it stops the commit and warns the developer.
    
4. **The developer must remove or secure the secret** before committing the code again.
    

#### Example Use Case

Imagine you're working on a project that connects to a payment system:

* You accidentally add your **secret API key** in the code.
    
* Without a pre-commit hook, this API key could be pushed to GitHub, making it publicly visible.
    
* With a pre-commit hook, the script detects the key and stops the commit, **protecting your sensitive data**.
    

### How to Set Up a Pre-Commit Hook

Setting up a pre-commit hook is easy:

1. In VS Code, go to **Settings** → search for `code.exclude` → remove `**/.git` to make the hidden `.git` folder accessible.
    
2. Navigate to your repository folder and open the `.git/hooks/` directory.
    
3. Create a new file named `pre-commit` (no file extension needed).
    
4. Add a simple script to check for sensitive data. Example:
    
    ## Python ( Flake8 )
    
    Flake8 is a powerful Python linter that enforces PEP 8 standards, detects syntax errors, unused imports, and checks code complexity. It helps maintain clean, efficient, and readable code, making it essential for developers.
    
    ```python
    """This module contains utility functions."""
    
    def add(a, b):
        """Returns the sum of two numbers."""
        return a + b
    
    def subtract(a, b):
        """Returns the difference between two numbers."""
        return a -b
    
    
    def multiply(a, b):
        """Returns the product of two numbers."""
        return a *b
    
    def divide(a, b):
        """Returns the quotient of two numbers, handling division by zero."""
        return a / b if b != 0 else "Error: Division by zero"
    ```
    
    ```plaintext
    #!/bin/bash
    
    files=$(git diff --cached --name-only --diff-filter=ACM | grep -E "\.py")
    
    if [ -n "$files" ]; then  # Check if Python files exist
        echo "Running flake8 on Python files"
    
        # Check if flake8 is installed
        if ! command -v flake8 &> /dev/null; then
            echo "flake8 not found. Install it manually using:"
            echo "  python3 -m pip install --user flake8"
            exit 1
        fi
    
        # Run flake8
        flake8 $files
        if [ $? -ne 0 ]; then  # If flake8 fails
            echo "flake8 failed, commit aborted"
            exit 1
        fi
    fi
    ```
    
5. Save the file and give it execute permission:
    
    ```plaintext
    chmod +x .git/hooks/pre-commit
    ```
    
6. Now, every time you try to commit, the hook will run first and stop the commit if it detects sensitive data.
    

## Output

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1740649006681/c7b34209-ba4c-455f-8a3b-e78bbbe3be41.png align="center")

### Benefits of Using GitHub Hooks

* **Saves Time** ⏳ – Automates repetitive tasks.
    
* **Reduces Errors** ✅ – Ensures code quality and consistency.
    
* **Improves Collaboration** 🤝 – Keeps teams informed through notifications.
    
* **Enhances Security** 🔐 – Helps track and monitor changes effectively.
    
* **Protects Sensitive Data** 🛡️ – Prevents accidental leaks of passwords or API keys.
    

### Conclusion

GitHub Hooks, especially pre-commit hooks, are a powerful way to automate tasks and **protect your code from accidental mistakes**. Whether you're a tech enthusiast or just getting started, understanding these hooks can help you work smarter, not harder!

Want to learn more? Drop your questions in the comments! 🚀