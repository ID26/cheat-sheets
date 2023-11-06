Error while opening Intellij IDEA due to an already running process
To fix this issue, you need to remove the .lock file in your configuration. It's in the config folder, examples for IntelliJIdea2023.2
linux:
~/.config/JetBrains/IntelliJIdea2023.2
Windows:
C:\Users\JohnS\AppData\Roaming\JetBrains\IntelliJIdea2023.2
macOS
~/Library/Application Support/JetBrains/IntelliJIdea2023.2
There can be multiple versions of your program in the JetBrains folder, such as IntelliJIdea2023.1 and IntelliJIdea2023.2. You need the latest.
Delete the .lock file and run the program, everything should work. At least it helped me.