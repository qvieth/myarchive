# execute

- [source](source)
- [execution](execution)

---

- [What is the difference between executing a Bash script vs sourcing it?](https://superuser.com/questions/176783/what-is-the-difference-between-executing-a-bash-script-vs-sourcing-it)
     - Both sourcing and executing the script will run the commands in the script line by line, as if you typed those commands by hand line by line
          - When you execute the script you are opening a new shell,
               - type the commands in the new shell,
               - copy the output back to your current shell,
               - then close the new shell.
               - Any changes to environment will take effect only in the new shell
               - and will be lost once the new shell is closed.
          - When you source the script you are typing the commands in your current shell.
               - Any changes to the environment will take effect
               - and stay in your current shell.
