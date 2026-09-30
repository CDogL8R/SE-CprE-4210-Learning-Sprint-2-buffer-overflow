This project solidified how buffer overflow works by writing more data than it can hold by representing it in a visual way. It also helped show how a canary works and how safe API's such as strncpy can prevent buffer overflows. 

Development Workflow
Our workflow was all about using AI prompts to bring our vision to life. We wanted to build a visual buffer overflow tool that also included key definitions, showed the real effects of stack corruption, and demonstrated both how safeguards protect memory and how overflows bypass them.

Here is the process I followed to build it:

Building the Base App: I fed our concepts and requirements into Gemini and asked it to generate a single, self-contained index.html file.

Polishing & Adding Defenses: I refined the app by adding interactive toggles for stack canaries (0xDEADBEEF) and strncpy so users could test safe vs. vulnerable memory behavior in real time.

Technical Double-Check: Once the layout was built, I verified the memory offsets, Little-Endian byte ordering, and crash logic to make sure everything accurately mirrored how C stack frames behave in real life.

Documentation: Finally, I used AI to help draft the README.md file with clear instructions on how to run and use the HTML app.
