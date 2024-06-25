# Github actions workflow for simple python

## Overview

This is a tutorial on how to create a GitHub Actions workflow to run a simple Python code. 

## **Step 1: Create a new GitHub Actions workflow**

The first step is to create a new GitHub Actions workflow. These steps are based on console, you can do the same with cli commands. 
To do this using console, follow these steps:

1. Navigate to the repository that contains your Python code. If you don’t have a repo create new one with the following code snippet. Save it as `**main.py`** 
    
    ```bash
    print("Hello from github actions commit1")
    ```
    Source code:  https://github.com/chandradeoarya/devops-githubactions-python
    
2. Click on the "Actions" tab.
3. Click on the "New workflow" button.
4. Select "Python application" from the list of suggested workflows.
5. Replace the contents of the newly created **`main.yml`** file with the following code:

```yaml
name: Python application

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Set up Python
      uses: actions/setup-python@v2
      with:
        python-version: '3.9'
    - name: Install dependencies
      run: pip install -r requirements.txt
    - name: Run Python script
      run: python main.py
```

This workflow will run your Python code whenever changes are pushed to the **`main`** branch or when pull requests are created against the **`main`** branch.

## **Step 2: Commit and push the workflow file**

After creating the workflow file, you need to commit and push it to the repository. To do this, follow these steps:

1. Save the changes you made to the workflow file.
2. Add the workflow file to your Git staging area by running the following command:
    
    ```bash
    git add .github/workflows/main.yml
    ```
    
3. Commit the changes by running the following command:
    
    ```bash
    git commit -m "Add GitHub Actions workflow for Python code"
    ```
    
4. Push the changes to the repository by running the following command:
    
    ```bash
    git push
    ```
    

## **Step 3: Verify that the workflow runs successfully**

Once you've pushed the workflow file to your repository, GitHub Actions will automatically start running the workflow whenever changes are pushed to the **`main`** branch or when pull requests are created against the **`main`** branch.

To verify that the workflow runs successfully, follow these steps:

1. Navigate to the repository that contains your Python code.
2. Click on the "Actions" tab.
3. Select the "Python application" workflow.
4. Verify that the workflow runs successfully and that your Python code is executed.

If the workflow fails, you can click on the individual steps to see more details about what went wrong.
