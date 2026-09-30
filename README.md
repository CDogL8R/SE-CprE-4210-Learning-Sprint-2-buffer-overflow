Buffer Overflow Visualizer & Interactive Lab
An interactive, browser-based cybersecurity educational visualizer and simulator for exploring x86 stack frame memory layout, buffer overflow vulnerabilities (strcpy), and defensive engineering concepts (Stack Canaries & strncpy).
📌 Project Overview
Understanding call stack memory corruption can be challenging due to memory allocation nuances (e.g., stack frames growing downwards toward lower addresses while arrays write upwards toward higher addresses).
This tool visually bridges that gap by allowing students, security researchers, and developers to observe raw ASCII and Hex payload bytes directly filling stack frames, overwriting local variables (such as privilege flags isAdmin), knocking out Stack Guards (Canaries), and hijacking control flow by corrupting the Instruction Pointer (EIP).
✨ Key Features
Real-time Stack Memory Grid: Visualizes memory row-by-row on 4-byte (word) boundaries, showing byte modifications, ASCII characters, and hexadecimal values.
Dynamic Variable Overwrite: Simulates how contiguous memory spillover impacts adjacent local variables (isAdmin), Saved Base Pointer (EBP), and Return Address (EIP).
Interactive Security Toggles:
Stack Canary Protection: Toggle 0xDEADBEEF canary checks (__stack_chk_fail).
Bounded API Enforcement: Swap between vulnerable strcpy() and safe strncpy().
C Source Code Execution Inspector: Step through code line-by-line (Prologue, Copying, Checking, Epilogue/ret).
CPU Registers & Terminal Log: Live updates for EIP, EBP, isAdmin, and Stack Canary status alongside an execution log console.
Hands-on Challenges: Built-in challenge lab with 4 scenarios testing normal operation, privilege escalation, control flow hijacking, and defense bypass attempts.
GitHub Submission Companion: Automated README.md and reflection.md markdown generators built right into the app.
🚀 How to Run the Visualizer
Since the project is a self-contained, client-side web application built with HTML5, Tailwind CSS, and Vanilla JavaScript, no server-side compilation, Node.js, or complex installation is required.
Prerequisites
Any modern web browser (Google Chrome, Mozilla Firefox, Microsoft Edge, Safari, Brave).
An active internet connection (required to load Tailwind CSS and FontAwesome CDNs).
Method 1: Direct Browser Launch (Easiest)
Save the code into a file named index.html.
Locate the file on your computer:
Windows: Double-click index.html or right-click and choose Open with > Google Chrome (or your browser of choice).
macOS: Double-click index.html or open Terminal and run open index.html.
Linux: Double-click or run xdg-open index.html in Terminal.
Method 2: Live Server Extension (VS Code)
If you are using Visual Studio Code:
Install the Live Server extension by Ritwick Dey.
Open the folder containing index.html in VS Code.
Right-click index.html in the file explorer and select Open with Live Server.
The visualizer will launch automatically at http://127.0.0.1:5500/index.html.
Method 3: Local HTTP Server (Python)
If you prefer running a local terminal web server:
Open your terminal or command prompt.
Navigate to the directory where index.html is saved:
cd /path/to/your/project


Start a local HTTP server:
Python 3.x:
python3 -m http.server 8000


Python 2.x:
python -m SimpleHTTPServer 8000


Open your web browser and navigate to:
http://localhost:8000


🛠️ Usage & Preset Walkthrough
Preset Scenarios: Click any preset button at the top to quickly populate test payloads:
Safe Input (6B): Clean write fitting within buffer[16].
Buffer Full (16B): Maxes out buffer capacity without overflowing.
Privilege Escalation: Overwrites isAdmin variable to grant admin status.
Hijack EIP: Overwrites return address with 0x00401190 (secret_admin_function).
Segfault Crash: Causes invalid address jump triggering memory fault.
Execution Control:
Click Step Execution to step through C execution line-by-line.
Click Execute Function to run the full process immediately.
Payload Modes: Switch between ASCII string input or space-separated HEX bytes (41 41 41 41...).
Security Toggles: Toggle Stack Canary or Bounds Check (strncpy) in the control panel to see how memory protections intercept exploit attempts.
📚 Core Educational Concepts Covered
Concept
Explanation
Call Stack Direction
Stack frames grow downward (high to low addresses), while array writes move upward (low to high addresses).
Unsafe Functions
strcpy() copies until encountering a null terminator (\0), lacking bounds checks.
Privilege Escalation
Overflowing into local boolean variables adjacent to buffers on the stack.
EIP Hijacking
Overwriting saved return pointers to divert CPU execution flow to arbitrary code.
Stack Canaries
Secret stack integrity guard words checked prior to function epilogue (ret).

📄 License
This project is open-source under the MIT License. Free to use for educational and research purposes.
