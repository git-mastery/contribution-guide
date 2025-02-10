# Contribution Guide

This document contains all the necessary information to get started with contributing to Git Mastery

## Adding a new exercise?

We have created repository templates to get started with creating new exercise.

Exercises are comprised of two components:

1. Exercise packet: stores the instructions for students and the necessary instructions to initialize the exercise for the student
2. Solution: private repository that houses the autograding script, along with any necessary unit tests to verify the grading behavior

### Exercises

Exercises are comprised of the following components:

1. README.md: contains instructions for students
2. submit.sh: standardized script to allow students to make a submission
3. post-download.sh: used to initialize the repository after the initial clone was made
4. .github/workflows/grade.yml: autograding workflow, DO NOT TOUCH

### Solutions

Solutions are comprised of the following components:

1. README.md: contains any information for other contributors about the solution repository
2. grade.py: contains the primary autograding script, relies on [`git-autograder`](https://github.com/git-mastery/git-autograder) to perform grading
3. requirements.txt: stores the dependencies of the solution, the autograding workflow will use this file to initialize all dependencies
4. spec.yml: [`repo-smith`](https://github.com/git-mastery/repo-smith) configuration file for unit testing
5. test-grade.py: `pytest` compatible unit test file for validating the `grade.py` autograding script, uses the `spec.yml` to simulate the exercise repository with hooks to initialize a submission state

To setup the solution for local testing:

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt -U
python -m pytest -s -vv
```
