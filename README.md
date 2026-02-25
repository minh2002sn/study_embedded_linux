# Study Linux Programming

## Unit 2: First Device Driver

- Kernel modules require a different set of header files than user programs require.

- Module code should not invoke user space Libraries or API or System calls.

- `init` function is called when the module is loaded by using ismod.

- `exit` function is called when the module is removed by using rmmod.

- `printk()` is the print function for kernel code.
    - Macro for `printf`:
        - **KERN_EMERG**: Used for emergency messages, usually those that precede a crash.
        - **KERN_ALERT**: A situation requiring immediate action.
        - **KERN_CRIT**: Critical conditions are often related to serious hardware or software failures.
        - **KERN_ERR**: Used to report error conditions; device drivers often use **KERN_ERR** to report hardware difficulties.
        - **KERN_WARNING**: Warnings about problematic situations that do not, in themselves, create serious problems with the system.
        - **KERN_NOTICE**: Situations that are normal, but still worthy of note. A number of security-related conditions are reported at this level.
        - **KERN_INFO**: Informational messages. Many drivers print information about the hardware they find at startup time at this level.
        - **KERN_DEBUG**: Used for debugging messages.
    - Examples:
      ```C
      printk(KERN_INFO "Welcome To EmbeTronicX");
      ```
    - Compare with `printf()`:
        - `printk()` is a kernel-level function, which has the ability to print out to different log levels as defined in. We can see the prints using dmesg command.
        - `printf()` will always print to a file descriptor – STD_OUT. We can see the prints in the STD_OUT console.

- Note:
    - `pr_info` – Print an info-level message. (ex. pr_info("test info message\n")).
    - `pr_cont` – Continues a previous log message in the same line.
    - `pr_debug` – Print a debug-level message conditionally.
    - `pr_err` – Print an error-level message. (ex. pr_err(“test error message\n”)).
    - `pr_warn` – Print a warning-level message.

- Compile: Use the below command for Beagle Bone:
    ```
    sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabi-
    ```