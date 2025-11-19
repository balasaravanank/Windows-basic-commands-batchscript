# Windows-basic-commands-batchscript
Ex08-Windows-basic-commands-batchscript

# AIM:
To execute Windows basic commands and batch scripting

# DESIGN STEPS:

### Step 1:

Navigate to any Windows environment installed on the system or installed inside a virtual environment like virtual box/vmware 

### Step 2:

Write the Windows commands / batch file . Save each script in a file with a .bat extension. Ensure you have the necessary permissions to perform the operations. Adapt paths as needed based on your system configuration.
### Step 3:

Execute the necessary commands/batch file for the desired output. 




# WINDOWS COMMANDS:
## Exercise 1: Basic Directory and File Operations
Create a directory named "my-folder"

## COMMAND AND OUTPUT
```
mkdir my-folder
```
<img width="381" height="38" alt="Screenshot from 2025-11-02 18-35-48" src="https://github.com/user-attachments/assets/c6b437ef-0376-486a-8f4a-83f9cfde0508" />



Remove the directory "my-folder"

## COMMAND AND OUTPUT
```
rmdir my-folder
```

<img width="381" height="38" alt="Screenshot from 2025-11-02 18-36-10" src="https://github.com/user-attachments/assets/480b0632-f392-4a48-9970-22b38ab7d482" />


Create the file Rose.txt

## COMMAND AND OUTPUT
```
touch Rose.txt
```

<img width="381" height="38" alt="Screenshot from 2025-11-02 18-36-26" src="https://github.com/user-attachments/assets/dc23d186-0a07-467c-99b1-8a8ca29c6fb0" />




Create the file hello.txt using echo and redirection

## COMMAND AND OUTPUT
```
echo "Hello, world!" > hello.txt

```
<img width="557" height="40" alt="Screenshot from 2025-11-02 18-36-45" src="https://github.com/user-attachments/assets/f0b15263-f7ca-460d-b975-ae25b4bea9cc" />




Copy the file hello.txt into the file hello1.txt

## COMMAND AND OUTPUT
```
cp hello.txt hello1.txt

```
<img width="461" height="36" alt="Screenshot from 2025-11-02 18-37-12" src="https://github.com/user-attachments/assets/5930ea45-bae9-4c65-8f87-09c3289a720a" />




Remove the file hello1.txt

## COMMAND AND OUTPUT
```
rm hello1.txt

```
<img width="383" height="26" alt="Screenshot from 2025-11-02 18-43-44" src="https://github.com/user-attachments/assets/98a81afc-a87a-49d7-ba1b-7d168a94cebc" />




List out the file hello1.txt in the current directory

## COMMAND AND OUTPUT
```
ls hello1.txt

```
<img width="595" height="47" alt="Screenshot from 2025-11-02 18-43-57" src="https://github.com/user-attachments/assets/e1d16270-4335-46af-a588-b6801f8356d4" />




List out all the associated file extensions 

## COMMAND AND OUTPUT
```
ls | awk -F. 'NF>1 {print $NF}' | sort | uniq

```

<img width="682" height="97" alt="Screenshot from 2025-11-02 18-44-06" src="https://github.com/user-attachments/assets/b915d588-f579-46fc-a6b1-6a4b853878ac" />


Compare the file hello.txt and rose.txt

## COMMAND AND OUTPUT
```
diff hello.txt rose.txt

```
<img width="682" height="28" alt="Screenshot from 2025-11-02 18-45-58" src="https://github.com/user-attachments/assets/878b6911-4de2-4fbd-a0c3-54fa9035bab5" />


## Exercise 2: Advanced Batch Scripting
Create a batch file named on the desktop. The batch file need to have a variable assigned with a desired name for ex. name="John" and display as "Hello, John".
```
@echo off
set name=John
echo Hello, %name%!
pause
```

## OUTPUT

<img width="770" height="233" alt="image" src="https://github.com/user-attachments/assets/ffd0bbb4-2bd0-4cf8-8ab8-9b4488d76d02" />





Create a batch file  on the desktop that checks whether a user-input number is odd or not. The script should:
Prompt the user to enter a number.
Calculate the remainder when the number is divided by 2.
Display whether the number is odd or not.
Ask the user if they want to check another number.
Repeat the process if the user enters Y, and exit with a thank-you message if the user enters N.
Handle invalid inputs for the continuation prompt (Y/N) gracefully.
```
@echo off
:main
set /p number=Enter a number: 
rem Calculate remainder when divided by 2
set /a remainder=%number% %% 2
if %remainder%==1 (
    echo %number% is an odd number.
) else (
    echo %number% is not an odd number.
)
:choice
set /p continue=Do you want to check another number? (Y/N): 
if /i "%continue%"=="Y" goto main
if /i "%continue%"=="N" goto end
echo Invalid choice, please enter Y or N.
goto choice
:end
echo Thank you for using the odd number checker!
pause
```
## OUTPUT
<img width="1076" height="549" alt="image" src="https://github.com/user-attachments/assets/e2dee31a-4527-466b-8de3-d24626f2b0f0" />




Write a batch file that uses a FOR loop to iterate over a sequence of numbers (1 to 5) and displays each number with the label Number:. The output should pause at the end.
```
@echo off
for %%i in (1 2 3 4 5) do (
    echo Number: %%i
)
pause

```

## OUTPUT

<img width="820" height="392" alt="image" src="https://github.com/user-attachments/assets/3210184e-71d7-4142-94a6-678553da5e35" />




Write a batch script to check whether a file named sample.txt exists in the current directory. If the file exists, display the message sample.txt exists. Otherwise, display sample.txt does not exist. Pause the script at the end to view the result.

Instructions:
Use the IF EXIST conditional statement.
Make sure the script works for files located in the same directory as the batch file.
Use pause to keep the command window open after displaying the message.
Expected Output (if the file exists):
```
@echo off
if exist sample.txt (
    echo sample.txt exists.
) else (
    echo sample.txt does not exist.
)
pause
```
## OUTPUT
<img width="792" height="234" alt="image" src="https://github.com/user-attachments/assets/8841ec57-82bd-445b-9a9a-e02e987de110" />



Write a batch script that displays a simple menu with three options:
Say Hello – Displays the message Hello, World!
Create a File – Creates a file named newfile.txt with the content This is a new file
Exit – Exits the script with a goodbye message
The script should repeatedly display the menu until the user chooses to exit. Use goto statements to handle menu navigation.
```
@echo off
:menu
echo 1. Say Hello
echo 2. Create a File
echo 3. Exit
set /p choice=Choose an option: 
if "%choice%"=="1" goto hello
if "%choice%"=="2" goto createfile
if "%choice%"=="3" goto end

:hello
echo Hello, World!
goto menu

:createfile
echo Creating a file...
echo This is a new file > newfile.txt
goto menu
:end
echo Goodbye!
pause

```
## OUTPUT

<img width="776" height="867" alt="image" src="https://github.com/user-attachments/assets/e3f63183-82fe-4388-922e-fff48d3ea295" />


# RESULT:
The commands/batch files are executed successfully.

