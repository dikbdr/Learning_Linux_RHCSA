```markdown
## Process Management

### Understanding Processes
A process is an instance of a program in execution. Each process is assigned a unique Process ID (PID). Processes can be categorized as:
- **Foreground Processes**: Run interactively and occupy the terminal.
- **Background Processes**: Run without occupying the terminal.

#### Example:
To view the current shell's PID:
```bash
echo $$
```

### Managing Processes
Linux provides several tools to manage processes effectively:

#### Viewing Processes
- `ps`: Displays information about active processes.
    ```bash
    ps aux
    ```
    - `a`: Shows processes for all users.
    - `u`: Displays user-oriented output.
    - `x`: Includes processes without a controlling terminal.

- `top`: Provides a dynamic real-time view of running processes.
    ```bash
    top
    ```

#### Controlling Processes
- `kill`: Sends signals to processes to terminate or control them.
    ```bash
    kill -9 <PID>
    ```
    - `-9`: Forcefully terminates a process.

- `nice` and `renice`: Adjust process priority.
    ```bash
    nice -n 10 <command>
    renice 5 -p <PID>
    ```
    - Lower priority numbers indicate higher priority.

### Scheduling Tasks
Task scheduling allows you to automate commands or scripts at specific times.

#### Using `cron`
- `cron` is used for recurring tasks.
- Edit the crontab file:
    ```bash
    crontab -e
    ```
    Example entry to run a script daily at 5 AM:
    ```bash
    0 5 * * * /path/to/script.sh
    ```

#### Using `at`
- `at` is used for one-time tasks.
    ```bash
    at 2pm
    ```
    Enter the command to execute, then press `Ctrl+D`.

### Diagram: Process Lifecycle
```plaintext
+-------------------+
| Program (on disk) |
+-------------------+
                 |
                 v
+-------------------+
| Process (in RAM)  |
+-------------------+
                 |
                 v
+-------------------+
| Terminated State  |
+-------------------+
```
```