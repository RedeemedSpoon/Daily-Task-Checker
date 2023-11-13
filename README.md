# Daily Task-Checker

This is the Daily Task-Checker, a bash script tool for evaluating your day using the symbols (+/-/~) based on user-defined criteria. It helps you assess your daily activities and track your progress toward self-mastery. The evaluations are stored in a progress database (`TaskDB.txt`), and criteria can be customized in the `Criterions.txt` file.

## How to Use

### 1. Download the Script

Clone the repository:

```bash
git clone https://github.com/RedeemedSpoon/Daily-Task-Checker.git
cd Daily-Task-Checker
```

### 2. Customize Criteria

Open `Criterions.txt` and add or modify criteria. Each line in the file represents a different criterion/question for your daily evaluation.

### 3. Run the Script

Run the script with the following command:

```bash
bash ~/Daily-Task-Checker/journey
```

Follow the on-screen instructions to evaluate your day using the symbols (+/-/~) based on the customized criteria.

### 4. Visualize Progress

To visualize your progress, you can use commands like:

```bash
cat ~/Daily-Task-Checker/Necessary\ Files/TaskDB.txt | sort -u | uniq -c
```

This command will display a summary of the occurrences of each evaluation symbol in your progress database.

For example, to check the count of "good sleep" (depend on your own personalized question) evaluations:

```bash
grep "good sleep" ~/Daily-Task-Checker/Necessary\ Files/TaskDB.txt | sort -u | uniq -c
```

Adjust the criteria and paths based on your specific evaluations and file locations.

## Features

### Preventing Multiple Daily Checks

The script has a built-in system to prevent multiple evaluations on the same day. If you've already performed the evaluation for the current day, the script will inform you and exit to avoid duplicate entries.

### Handling Night Owl Evaluations

The script considers evaluations near the 6 AM mark as part of the previous day for night owls. If the time is before 6 AM, the script will prompt you to evaluate for the previous day.

### Important Note for Users

**Make sure you do not run this program as root!**

The script is designed to work with a regular user's home directory (`~`). Running it as root may lead to unexpected behavior, as it messes with the home directory path.

**Compatibility:**
- The script is designed for Unix-based systems.

## Progress Database

The progress database is stored in a text file (`TaskDB.txt`). It stores the evaluations based on the user-defined criteria.

## (OPTIONAL) Adding to $PATH

To add the script to your $PATH (preferably /usr/bin), you can use the following steps:

```bash
sudo cp ~/Daily-Task-Checker/journey /usr/bin/journey
```

Now, you can run the script from any directory:

```bash
journey
```

Note that you can change the name of 'journey' in `/usr/bin/journey` to any name you want and then run the script by typing it. Make sure to use a unique name to avoid conflicts with existing commands.

## (OPTIONAL) Running with Cron Daily

You can automate the daily task evaluation using cron while displaying in the terminal and requiring user input. Open the crontab configuration:

```bash
crontab -e
```

Add the following line to run the script daily:

```bash
0 17 * * * bash -i -c '/path/to/journey.sh'
```

Replace `/path/to/journey.sh` with the correct path to your script. (just 'journey' if you have put it in the $PATH)

This command uses `/bin/bash -i -c` to run the script in interactive mode, ensuring it displays in the terminal and requires user input.

you can change the hour or the minute where this program will run on each day by modifying the first option in the crontab job. the fist part '0' is the minute timer and the second part '17' is the hour timer. keep the rest '*' to allow it to run daily

Ex : '30 21 * * * bash -i -c 'journey' will run the program everyday at 09:30 PM

## Contribution

Contributions are welcome! If you have ideas for new criteria or improvements, feel free to open an issue or submit a pull request.

## License

This project is licensed under the [MIT License](LICENSE).
