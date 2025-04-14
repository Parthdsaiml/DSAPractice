
### **Core Concepts**  
1. **Operating System (OS)**  
   - **What?** Software that acts as a "middleman" between hardware (CPU, RAM) and apps/users.  
   - **Example:** Windows, Linux, macOS, Android.  

2. **Kernel**  
   - **What?** The core part of the OS that talks directly to hardware.  
   - **Example:** Like a "manager" controlling CPU, memory, and devices.  

3. **Shell**  
   - **What?** The interface for users to interact with the OS (e.g., command line or GUI).  
   - **Example:** Bash (Linux terminal), PowerShell (Windows).  

4. **System Call**  
   - **What?** A request by a program to the OS for a service (e.g., read a file).  
   - **Example:** `open()` in Linux to open a file.  

5. **User Mode vs Kernel Mode**  
   - **User Mode:** Apps run here (restricted access to hardware).  
   - **Kernel Mode:** OS runs here (full hardware access).  

---

### **Process Management**  
6. **Process**  
   - **What?** A running instance of a program.  
   - **Example:** Opening Chrome starts a process.  

7. **Thread**  
   - **What?** A lightweight "sub-process" within a process.  
   - **Example:** A browser tab loading a webpage uses a thread.  

8. **Process Control Block (PCB)**  
   - **What?** A data structure storing process info (ID, state, registers).  

9. **Scheduling**  
   - **What?** Deciding which process runs next on the CPU.  
   - **Algorithms:**  
     - **FCFS (First-Come, First-Served):** Like a grocery queue.  
     - **Round Robin:** Each process gets a time slice (e.g., 10ms).  

10. **Inter-Process Communication (IPC)**  
    - **What?** Processes sharing data.  
    - **Methods:** Pipes, shared memory, message queues.  

11. **Deadlock**  
    - **What?** Two processes waiting forever for each other’s resources.  
    - **Example:** Process A holds a printer, Process B holds a scanner; both wait for the other.  

---

### **Memory Management**  
12. **Virtual Memory**  
    - **What?** Illusion of infinite RAM using disk space.  
    - **Example:** Your PC runs 10 apps even with 8GB RAM.  

13. **Paging**  
    - **What?** Splits memory into fixed-size chunks (pages).  
    - **Example:** Like dividing a book into pages for easy access.  

14. **Segmentation**  
    - **What?** Splits memory into logical chunks (e.g., stack, heap).  

15. **Page Replacement Algorithms**  
    - **FIFO:** Remove the oldest page.  
    - **LRU:** Remove the least recently used page.  

---

### **File Systems**  
16. **File System**  
    - **What?** Organizes files on a disk (e.g., NTFS, ext4).  
    - **Example:** Folders like `Documents`, `Downloads`.  

17. **Inode**  
    - **What?** A data structure storing file metadata (size, permissions).  

18. **FAT (File Allocation Table)**  
    - **What?** Table tracking file locations on disk (used in USB drives).  

19. **RAID**  
    - **What?** Combining disks for performance or redundancy.  
    - **Example:** RAID 1 (mirroring) copies data to two disks.  

---

### **Advanced Concepts**  
20. **Multithreading**  
    - **What?** Running multiple threads in a process.  
    - **Example:** A game rendering graphics while playing sound.  

21. **Real-Time OS**  
    - **What?** OS for time-critical tasks (e.g., robots, airbags).  

22. **Virtualization**  
    - **What?** Running multiple OS instances on one machine.  
    - **Example:** VMware running Windows on a Linux PC.  

23. **Distributed OS**  
    - **What?** Manages resources across multiple computers.  
    - **Example:** Google’s servers working together.  

---

### **Boot Process**  
1. **BIOS/UEFI**  
   - **What?** Firmware that starts the OS. Checks hardware (POST).  
2. **Bootloader**  
   - **What?** Loads the OS kernel (e.g., GRUB for Linux).  
3. **Kernel Initialization**  
   - **What?** Kernel starts processes (e.g., `systemd` in Linux).  

---

### **CLI vs GUI**  
- **CLI (Command Line Interface):**  
  - **Example (Linux):** `ls` (list files), `cd` (change directory).  
  - **Example (Windows):** `dir`, `ipconfig`.  
- **GUI (Graphical User Interface):**  
  - **Example:** Windows Desktop, macOS Finder.  

---

### **Troubleshooting**  
1. **Task Manager (Windows) / `top` (Linux):** Monitor processes.  
2. **Logs:** Check system errors (e.g., `/var/log` in Linux).  
3. **Safe Mode:** Boot with minimal drivers to fix issues.  

---

### **Example Exam Questions**  
1. **Q:** What’s the difference between a process and a thread?  
   **A:** A process is a standalone program; a thread is a part of a process.  

2. **Q:** Explain deadlock with an example.  
   **A:** Two processes waiting for each other’s resources forever (e.g., printer and scanner).  

3. **Q:** What is virtual memory?  
   **A:** Using disk space as "fake RAM" to run more apps.  

---

**Quick Revision Tips:**  
- **Deadlock Conditions:** Mutual Exclusion, Hold and Wait, No Preemption, Circular Wait.  
- **Scheduling Algorithms:** FCFS (fair but slow), Round Robin (time slices).  
- **Memory Management:** Paging (fixed chunks) vs Segmentation (logical chunks).  
- **File Systems:** NTFS (Windows), ext4 (Linux), FAT32 (USB drives).  

---

