# Bash Scripting Notes

## Getting Started

- **Check your shell:**
  ```bash
  echo $SHELL
  ```
  Example output: `/bin/bash`

- **Shebang (`#!`)**
  ```bash
  #!/bin/bash
  ```
  This is placed at the top of a script. Ensures the script runs in Bash.

## Variables
A variable stores data (text, numbers, paths) for later use.
```bash
#!/bin/bash
FILE=/home/ayush/bash/ayush.txt
DESTINATION=/home/ayush/ayush/
cp $FILE $DESTINATION
```
Here `FILE` and `DESTINATION` are variables.

Use `chmod` to make your script executable:
```bash
chmod u+x script.sh
```

## Input & Output
- **Reading input:**
  ```bash
  echo "What is your first name?"
  read FIRST_NAME
  ```
`read` Command
Takes user input and stores it in a variable.

- **Using positional arguments:**
  ```bash
  #!/bin/bash
  echo Hello $1 $2
  ```
`$0`: Script name
`$1`: First argument
`$2`: Second argument

Run with:
```bash
bash hello.sh Ayush Kumar
```

## Piping and Redirection

- **Pipe (`|`)**:
Sends the output of one command as input to another.
  ```bash
  ps | awk '{print $1}'
  ```

- **Redirection:**
  - Overwrite:
    ```bash
    echo "Hello World" > hello.txt
    ```
  - Append:
    ```bash
    echo "Welcome back" >> hello.txt
    ```
`>` to write to a file (Will overwrite the file everytime)
`>>` to append to a file

## Arithmetic Operators in Bash
Arithmetic operators include`+`, `-`, `*`, `/`, and `%` (modulo)
```bash
#!/bin/bash

a=10
b=3

echo "Addition: $((a + b))"
echo "Subtraction: $((a - b))"
echo "Multiplication: $((a * b))"
echo "Division: $((a / b))"
echo "Modulo: $((a % b))"
```

## Test Operators
Used in condition checks (returns `0` for true, `1` for false).
```bash
[ hello = hello ] && echo $?   # Output: 0 (true)
[ hello = ayush ] && echo $?   # Output: 1 (false)
```

## Conditionals

### `if` / `elif` / `else`

```bash
#!/bin/bash
if [ ${1,,} = ayush ]; then
  echo "You are the admin"
elif [ ${1,,} = help ]; then
  echo "Enter your username"
else
  echo "You are not the admin"
fi
```
`${1,,}` converts input to lowercase.

### `case` Statements
Checks multiple conditions in a cleaner way than `if-elif-else`.
```bash
#!/bin/bash
case ${1,,} in
  ayush | administrator)
    echo "You are the admin"
    ;;
  help)
    echo "Enter your username"
    ;;
  *)
    echo "You are not the admin"
    ;;
esac
```

## Arrays
Stores multiple values in a single variable.
```bash
MY_FIRST_LIST=(one two three four five)
echo ${MY_FIRST_LIST[@]}
```
`[@]` will show all the values stored in the variable. `[0]` can be used to show the first value only.

## Loops
Repeats commands for each item in a list.
```bash
MY_FIRST_LIST=(one two three four five)
for word in "${MY_FIRST_LIST[@]}"
do
  echo "${#word}"
done
```

## Functions
Reusable block of code.
```bash
#!/bin/bash
showuptime(){
  up=$(uptime -p | cut -c4- )
  since=$(uptime -s)
  cat << EOF
-----
This machine has been up for ${up}
It has been running since ${since}
-----
EOF
}
showuptime
```

Use `local` variables:
Can be used if you have similar varibales above the function and you wanna execute them after the function ends.
```bash
local up=$(uptime -p | cut -c4- )
```

## Exit Codes
`0` = Success
`1` = Failure
```bash
#!/bin/bash
showname(){
  echo Hello $1
  if [ ${1,,} = ayush ]; then
    return 0
  else
    return 1
  fi
}
showname $1
if [ $? = 1 ]; then
  echo "You are not the admin"
fi
```
