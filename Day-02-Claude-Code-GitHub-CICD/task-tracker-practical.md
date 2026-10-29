# Practical – Build and Test a Python Task Tracker

## Objective
Use Claude Code to create a small command-line task tracker, then verify that the generated application behaves as expected before publishing it.

## Requirements Demonstrated in Class
The requested application should:
- Add a task.
- List saved tasks.
- Mark a task as completed.
- Assign each task a unique ID.
- Persist tasks locally in JSON so they remain available after the program exits.
- Validate input and report errors clearly.
- Handle missing, empty, or malformed data safely.
- Use clean, organized Python code.
- Include automated unit tests.
- Include a README with setup, usage, and test instructions.
- Avoid secrets and personal data.
- Avoid running Git operations until explicitly requested.

## Example Prompt
Use this as a starting point and adapt it to your actual repository:

> Act as a senior Python engineer. Inspect the current repository before making changes. Build a working command-line task tracker in Python. It must support adding tasks, listing saved tasks, and marking tasks complete. Give every task a unique ID and persist tasks in a local JSON file. Validate inputs, handle missing or malformed data safely, and display useful error messages. Organize the code into sensible modules. Add automated unit tests using Python's built-in `unittest` framework and a README with setup, usage examples, and test instructions. Do not include secrets or personal data. Do not run Git commands or push changes. After implementation, run the tests, fix failures, rerun the tests, and report the files changed and test results.

## Suggested Workflow
1. Open the project directory in the terminal.
2. Start Claude Code from the project directory.
3. Give the requirements in small, explicit steps.
4. Ask Claude to explain the proposed file structure before or after implementation.
5. Review the generated source code and tests.
6. Run the test suite, for example:

```bash
python -m unittest discover -v
```

7. Ask Claude to test each required feature and inspect failures.
8. Review all changes before accepting them.
9. Run the application using the command documented in its README.

## Optional Start Script
In the session, Claude generated a `start.sh` script to help run tests and demonstrate the application. If you create one, inspect its contents before executing it.

For a script that is not executable yet:

```bash
chmod +x start.sh
./start.sh
```

Only use those commands if a `start.sh` file exists and its contents are understood.

## Verification Checklist
- [ ] Adding a valid task works.
- [ ] Listing tasks displays saved tasks.
- [ ] Completing an existing task works.
- [ ] Invalid or empty input is handled.
- [ ] Data persists after restarting the program.
- [ ] Missing or malformed JSON data is handled safely.
- [ ] Unit tests pass.
- [ ] README commands match the actual application.
- [ ] No credentials, tokens, or personal data are included.

## About Test Counts
The class transcript reported 97 checks and 150 crash-safety tests passing in the demonstrated run. These are the instructor's demo results, not a guarantee that your own generated project will have the same tests or results. Record the actual output from your own run.
