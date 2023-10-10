# Lab Report 1
## `cd`
**Command with *no* arguments**

![Screenshot 2023-10-08 at 7 16 29 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/c507ab1d-1eeb-47e3-9be3-14271bd3e0b9)


The `cd` command, short for "Change Directory," is used to alter the current working directory in a shell or command prompt session. When used without any arguments, it defaults to changing the directory to the user's home directory, providing a convenient way to return to the starting directory associated with their user account in a terminal.

**Command with a path to a *directory* argument**

![Screenshot 2023-10-09 at 2 37 53 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/2bea33e7-a099-4746-84a9-d9c06703db48)

When the command `cd` is used with an argument which in this case is first a relative path `lecture1/` we can observe that the working directory changes to the absolute path `/home/lecture1/`. The same happens if we use the command `cd` with the absolute path `/home/lecture1/` which we can use from any working directory as shown in line 4. The command `cd` alone used in the third line just changes our current directory back to our home directory as descibed above.

**Command with a path to a *file* argument**

![Screenshot 2023-10-09 at 2 48 58 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/1ee81821-16f4-4481-bdcd-9f021a68ddb4)

When you use the `cd` command with a file path as its argument, the terminal responds with an error message stating that the specified file path, such as `/home/lecture1/Hello.java`, is not a directory. This occurs because the `cd` command is designed to change directories, not access files. Hence, it expects a directory as its argument, not a file. Consequently, using `cd` with a file path will result in an error, and it won't alter the current working directory. In summary, attempting to use `cd` with a file path is an invalid use of the command, as its sole purpose is to switch the current working directory to another directory and cannot be used to interact with individual files.


## `ls`
**Command with *no* arguments**

![Screenshot 2023-10-09 at 3 12 39 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/299e650e-cd98-4376-bf67-f529a6b2524e)

The `ls` command is utilized to display the files and directories within a specific directory. Its primary purpose is to offer information about the contents of a directory, including file and directory names. When you run the `ls` command with no arguments, the terminal defaults to listing the contents of the user's home directory. In this scenario, the terminal displays the contents of the home directory, which includes `lecture1.` To enhance visual clarity, the output of `ls` can be colorized, making it easier to distinguish between directories and files; for instance, directories may appear in blue. Overall, the `ls command plays a crucial role in providing essential information about files and directories, facilitating efficient organization and viewing of directory contents.


**Command with a path to a *directory* argument**

![Screenshot 2023-10-09 at 3 13 28 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/4d108d94-aa40-4826-8a4e-3801c65c3121)

When the `ls` command is employed with a directory path as its argument, it generates a listing of the contents within the specified directory, rather than the current working directory. As demonstrated earlier, when you use `ls` with the path `/home/lecture1/messages`, it displays the contents of that particular directory, which includes the files `de-mx.txt`,`en-us.txt`, `es-mx.txt` and `zh-cn.txt.` Typically, the `ls` command organizes the list of files and directories into multiple columns, improving readability, especially when there's a substantial amount of content. The list is sorted alphabetically, with directories listed first, followed by files. In summary, using the `ls` command with a directory path provides a convenient means of inspecting the contents of a specific directory without altering the current working directory, instead of listing the contents of the current working directory. This functionality proves valuable for examining the contents of a particular directory without changing one's current location in the file system.

**Command with a path to a *file* argument**

![Screenshot 2023-10-09 at 3 14 17 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/65920d54-f2f6-4fb7-836f-65190fce467c)

When you employ the `ls` command with a file path as its argument, it simply displays the path to the file in the terminal. This action confirms the existence of the specified file at the provided location but doesn't offer any additional detailed information about the file; it merely presents the entered file path. This functionality is valuable for quickly verifying the presence of a file at a specific location without revealing the file's contents. Importantly, running the `ls` command with a file path does not alter the current working directory; it remains unchanged both before and after executing the `ls` command.

## `cat`

**Command with *no* arguments**

![Screenshot 2023-10-09 at 3 15 22 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/b3ab981d-e807-474d-8a91-7092a1188840)

![Screenshot 2023-10-09 at 3 15 49 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/965cd3d1-470d-4f6f-a6f6-ce8bcf950030)

The `cat` command, which is short for concatenate, serves primarily to combine the content of files into a single file and to display the contents of one or more files. When used with no arguments, `cat` operates in interactive mode, awaiting input from the user in the terminal. In this mode, you can input lines of text, and upon pressing `Enter`, the `cat` command displays your input on the screen as shown in the above screenshot. You can continue entering text until you choose to exit the interactive mode by pressing command + c. It's important to note that when used interactively, the `cat` command does not create or directly modify any files; it solely displays the text you input in the terminal. Additionally, the current working directory remains unchanged throughout this process.


**Command with a path to a *directory* argument**

![Screenshot 2023-10-09 at 3 17 32 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/f6810294-cfa2-4c20-a09b-a95dabfa924e)

Using the `cat` command with a directory path as an argument is not valid, and it will result in an error. The `cat` command is specifically designed to work with the contents of files, not directories. When you attempt to use `cat` with a directory path, it recognizes that it cannot read and display the contents of a directory. Consequently, it generates an error message, indicating that the provided argument, such as `/home/lecture1`, is a directory and not a file. As a result, it cannot perform its usual function of displaying file contents.


**Command with a path to a *file* argument**

![Screenshot 2023-10-09 at 3 18 26 PM](https://github.com/Ludwigvsch/cse15l-lab-reports/assets/51019288/ee877b62-e09b-4d8f-9e71-18783fc19cdd)

When the `cat` command is used with a file path as an argument, it reads the content of the specified file and presents that content on the terminal. In this specific case, we provided the path to the text file `Hello.java` as the argument to the `cat` command, which then proceeded to read the text within that file and display the text:

```
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
    System.out.println(content);
  }

  ```
 on the terminal. The `cat` command displays the content line by line, exactly as it appears in the file, with no additional formatting or content alterations.

Importantly, the `cat` command does not alter the current working directory; it remains the same before and after executing the command. This is because the command is solely designed for reading and displaying the content of files and does not involve any directory navigation. It operates exclusively on the specified files, making it a useful tool for examining and displaying file content.

