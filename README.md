# PEditor

![Last Commit](https://img.shields.io/badge/Last%20Commit-2025-07-25-blue)
![Primary Language](https://img.shields.io/badge/Language-Python-yellow)
![Languages Used](https://img.shields.io/badge/Languages%20Used-1-informational)

## 📚 Table of Contents
- [📖 Overview](#-overview)
- [❓ Why This Project](#-why-this-project)
- [🚀 Features](#-features)
- [⚡ Quick Start](#-quick-start)
- [🧪 Usage](#-usage)
- [🧠 AI Summaries](#-ai-summaries)
- [🧰 Tech Stack](#-tech-stack)
- [📂 Project Structure](#-project-structure)
- [🤝 Contribution](#-contribution)
- [🏅 Acknowledgements](#-acknowledgements)
- [🧾 Final Signature](#-final-signature)

## 📖 Overview

PEditor is a software project designed as a dedicated editor for Portable Executable (PE) files, the standard executable and library format for Windows (.exe, .dll).

Its purpose is to allow users to view and modify the internal structure of these binaries, including headers, sections, import/export tables, and resources. It's primarily used by reverse engineers, malware analysts, and security researchers. This tool helps them understand binary behavior, perform low-level analysis, debug, or even patch executables. Essentially, it provides deep introspection into Windows binaries.

## ❓ Why This Project

PEditor allows users to **inspect, analyze, and modify the internal structure of Windows Portable Executable (PE) files.**

This is essential for tasks like:
*   **Reverse engineering** applications.
*   **Malware analysis** and dissection.
*   **Security research** and vulnerability discovery.
*   **Advanced binary manipulation** for development or system administration.

## 🚀 Features

Based on the purpose of the PEditor project (a Portable Executable editor and viewer), its key features generally include:

*   **Comprehensive PE File Structure Analysis:** Provides a detailed hierarchical view of all components of a Portable Executable (PE) file, including DOS header, NT headers, optional headers, data directories, and section tables.
*   **Interactive PE Header and Section Modification:** Allows users to view and directly edit various fields within the PE headers and section properties (e.g., virtual address, raw size, characteristics) to alter file behavior or correct issues.
*   **Import and Export Table Management:** Enables viewing and manipulation of the import (functions imported from DLLs) and export (functions exposed by the PE file) tables, crucial for understanding and modifying program dependencies.
*   **Resource Viewing and Editing:** Provides functionality to inspect, extract, and potentially modify embedded resources like icons, cursors, string tables, dialogs, and version information within the PE file.
*   **Raw Data Inspection and Editing:** Offers a hex editor view to examine and modify the raw binary data within any section or specific offset of the PE file, allowing for low-level byte-level changes.
*   **Digital Signature Verification:** Capable of displaying and verifying the digital signatures present in the PE file, helping users ascertain the authenticity and integrity of the executable.
*   **Relocation Table Analysis:** Allows users to examine and understand how the PE file handles base relocations, which is important for executables that need to be loaded at different memory addresses.

## ⚡ Quick Start

```bash
# 1. Clone the repository
git clone <your-repo-url>

# 2. Navigate into the repo
cd your-repo

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run the application (example)
python app.py
```

## 🧪 Usage

PEditor is designed to be used within an interactive Python session (like IPython, Jupyter, or a standard Python REPL) to quickly edit and execute code.

Here's a concise usage guide:

---

### PEditor Concise Usage Guide

**Prerequisites:**
*   PEditor installed (e.g., `pip install PEditor` or cloned from repo).
*   Python with Tkinter support (usually bundled).

**Core Concept:** PEditor launches a simple Tkinter GUI editor that allows you to write, save, and *execute* Python code directly within the interactive shell session where it was launched.

---

**1. Launching PEditor:**

*   **From your interactive Python shell:**
    ```python
    from PEditor import PEditor

    # To open an empty editor:
    editor = PEditor()

    # To open an existing file:
    # editor = PEditor("my_script.py")
    ```
    A new Tkinter window for PEditor will pop up.

**2. Writing and Editing Code:**

*   Type or paste your Python code directly into the editor window, just like any other text editor.
*   Standard text editing functions (copy, paste, undo/redo) are available.

**3. Executing Code:**

*   **Click the "Run" button** in the PEditor window.
*   **Use the hotkey:** `Ctrl + R` (Windows/Linux) or `Cmd + R` (macOS).
*   **Result:** The code currently in the editor will be executed directly in the Python shell where you launched PEditor. Any print statements or errors will appear in that shell. Variables defined in the editor will become available in your interactive session after execution.

**4. Saving Your Work:**

*   Go to **File > Save** (or `Ctrl + S`). If it's a new file, it will prompt you for a filename and location.
*   Go to **File > Save As...** to save the current content to a new file or a different location.

**5. Opening Existing Files (from within PEditor):**

*   Go to **File > Open...** (or `Ctrl + O`). A file dialog will appear, allowing you to navigate and select a `.py` file to load into the editor.

**6. Closing PEditor:**

*   Simply close the PEditor window using the standard window 'X' button (top-right on Windows/Linux, top-left on macOS). The Python shell session will remain active.

---

**Key Benefits:**

*   **Interactive Development:** Quickly write and test code snippets directly within your ongoing session, accessing its variables and context.
*   **Simplicity:** A lightweight alternative to full-blown IDEs for quick tasks.
*   **Seamless Execution:** Code runs in the environment where `PEditor` was invoked, making it ideal for exploratory programming.

## 🧠 AI Summaries

### 📄 `app.py`

`app.py` serves as the **main entry point and user interface** for the PEditor application, which is built using the Streamlit framework. It orchestrates the entire user experience, from navigation to PDF processing, by leveraging functions imported from a separate `functions.py` module.

### What it Does

*   **PDF Text Extraction:** Its primary function is to allow users to upload a PDF file and extract its textual content.
*   **Output Flexibility:** Users can choose to download the extracted text as a single `.txt` file containing all pages, or as a `.zip` archive where each page's text is saved as a separate `.txt` file.
*   **PDF Viewer:** It provides a built-in viewer to display the uploaded PDF directly within the application.
*   **Informational Sections:** It includes dedicated sections for "Help" (usage instructions and limitations), "About Us" (team information, mission, and vision), and "Contact Us" (support and business inquiry details).

### How it Contributes to the Project

*   `app.py` is the **frontend and central control hub** of the PEditor application. It defines the user interface, handles user interactions (file uploads, menu selections), and presents the results.
*   It acts as an **orchestrator**, calling specialized PDF processing functions (like `convert_pdf_to_txt_pages`, `convert_pdf_to_txt_file`, `save_pages`, and `displayPDF`) that are externalized into a `functions.py` file. This separation of concerns keeps the UI logic clean and modular.
*   It makes the core PDF text extraction functionality accessible and user-friendly through its intuitive Streamlit interface.

### Main Logic

1.  **Initialization:** The application sets up a wide-page layout and displays "PEditor" as its main title.
2.  **Navigation System:** A sidebar radio button (`st.sidebar.radio`) serves as the primary navigation, allowing users to switch between "Home," "Help," "About us," and "Contact us" sections.
3.  **Home Section (Core Functionality):**
    *   It displays a descriptive tagline for the PDF Text Extractor.
    *   A dropdown in the sidebar allows the user to select the desired text output format: "One text file (.txt)" (for a single file) or "Text file per page (ZIP)" (for a ZIP archive of individual page files).
    *   A file uploader (`st.file_uploader`) prompts the user to load a PDF document.
    *   **Upon PDF Upload:**
        *   An expandable section ("Display document") allows users to view the uploaded PDF using the `displayPDF` function from `functions.py`.
        *   Based on the chosen output format, it invokes either `convert_pdf_to_txt_file` (for a single TXT) or `convert_pdf_to_txt_pages` (for per-page TXT, followed by `save_pages` to create the ZIP) from `functions.py`.
        *   It then displays the total number of pages found in the PDF.
        *   Finally, it provides a download button for the resulting text file or ZIP archive, accompanied by a celebratory "balloons" animation.
4.  **Help, About Us, and Contact Us Sections:** These sections primarily render static Markdown content.
    *   The "Help" section provides usage instructions (e.g., choosing output options, viewing PDFs) and critical notes/limitations (e.g., file size limits, language support, no OCR).
    *   The "About us" section details the development team's mission and vision.
    *   The "Contact us" section offers contact information for technical support (via GitHub, implied) and business inquiries (via email).

### 📄 `PEditor.py`

`PEditor.py` serves as a simple **launcher script** for a Streamlit application.

**What it Does:**
Its sole active function is to execute a system command that starts the `app.py` file as a Streamlit web application. Specifically, it uses the Windows command prompt (`cmd /k`) to run `streamlit run app.py` in a new window, which remains open after the command executes (due to `/k`).

**How it Contributes to the Project:**
This file acts as a convenient entry point or "one-click" starter for the main Streamlit application (`app.py`). Instead of a user needing to manually open a terminal and type `streamlit run app.py`, they can simply run this Python script (e.g., by double-clicking it if Python is associated) to launch the web application. The use of `cmd /k` is particularly useful for maintaining visibility of the Streamlit server's output and logs in a dedicated window.

**Main Logic:**

1.  **Import `os` module:** This module provides a way to interact with the operating system, including running shell commands.
2.  **Execute System Command:** The core logic is a single line:
    ```python
    os.system('cmd /k "streamlit run app.py"')
    ```
    This command instructs the operating system to:
    *   Open a new `cmd` (command prompt) window.
    *   Execute the command `streamlit run app.py` within that window.
    *   The `/k` flag ensures that the `cmd` window remains open after the `streamlit run` command has been issued, allowing the user to see the server's output and potential errors.

**Note:** The file contains commented-out code (`from sys import modules`, `from subprocess import call`, and a function `open_py_file` that uses `call`), which suggests an earlier or alternative approach for launching a Python script, but this code is not currently active. The `sys.modules` import is also unused. The current implementation relies entirely on `os.system` for launching the Streamlit app.

### 📄 `functions.py`

The `functions.py` file serves as a collection of utility functions designed to handle PDF processing and display within a Streamlit web application. Its primary purpose is to enable the conversion of PDF content into text, manage these extracted text files, and facilitate the direct display of PDF documents in a web interface.

**What it Does & Main Logic:**

1.  **PDF to Text Conversion (Page by Page):**
    *   The `convert_pdf_to_txt_pages(path)` function uses the `pdfminer` library to read a given PDF file.
    *   It iterates through each page of the PDF, extracting its text content independently.
    *   The function returns a list of strings, where each string represents the text of a single page, along with the total number of pages.
    *   This function is decorated with `@st.cache`, meaning Streamlit will cache its results to improve performance on subsequent calls with the same input.

2.  **PDF to Text Conversion (Full Document):**
    *   The `convert_pdf_to_txt_file(path)` function also uses `pdfminer` but extracts the entire text content of the PDF as one continuous string, rather than separating it by pages.
    *   It returns this single string and the total number of pages.
    *   Like its page-by-page counterpart, this function is also `@st.cache`d for performance.

3.  **Saving and Zipping Extracted Pages:**
    *   The `save_pages(pages)` function takes a list of text pages (typically from `convert_pdf_to_txt_pages`).
    *   It creates individual `.txt` files for each page in a `./file_pages/` directory (e.g., `page_0.txt`, `page_1.txt`).
    *   After creating the individual files, it compresses all of them into a single ZIP archive named `pdf_to_txt.zip` within the same directory.
    *   It returns the path to the created ZIP file, making it ready for download. This function is also `@st.cache`d.

4.  **Displaying PDF in Web App:**
    *   The `displayPDF(file)` function takes a file-like object (representing an uploaded PDF).
    *   It reads the binary content of the PDF, encodes it into a Base64 string.
    *   It then constructs an HTML `<iframe>` tag using this Base64 data.
    *   Finally, it uses `st.markdown` with `unsafe_allow_html=True` to embed and display the PDF directly within the Streamlit application's user interface.

**How it Contributes to the Project:**

This `functions.py` file provides the core backend capabilities for a Streamlit application that interacts with PDF documents. It abstracts away the complexities of PDF parsing (using `pdfminer`), file system operations (saving and zipping text files), and web embedding (`base64` and HTML `<iframe>`). By centralizing these functionalities, it allows the main Streamlit application script to easily:

*   Allow users to upload and view PDF files directly.
*   Extract the complete text content of PDFs for further processing (e.g., searching, summarization).
*   Provide users with the option to download the extracted text, either as a single file or as individual page files conveniently packaged in a ZIP archive.
*   Leverage Streamlit's caching mechanism for improved performance when handling PDF operations.

### 📄 `requirements.txt`

This `requirements.txt` file is a standard Python convention used to list all the external Python libraries and their exact versions that a project depends on.

**What it does:**
Its core purpose is to define and manage the project's dependencies, ensuring that anyone working on or deploying the project (developers, CI/CD pipelines, production servers) can easily install the exact set of libraries required for the application to function correctly. Each line specifies a package name and its version constraint (e.g., `==` for exact version, `*` for any patch version within a minor release).

**How it contributes to the project:**
1.  **Reproducibility:** It guarantees that the project will run consistently across different environments by ensuring all necessary libraries are installed at specified versions, preventing "works on my machine" issues.
2.  **Dependency Management:** It centralizes the declaration of all external components the project relies on, making it easy to track, update, and audit dependencies.
3.  **Enables Functionality:** The project's code directly uses functions and classes from these listed libraries. Without them, the application would not be able to perform its intended tasks. Typically, these are installed using `pip install -r requirements.txt`.

**Its main logic (and implied project functionality):**
While `requirements.txt` itself has no "logic" in the algorithmic sense, its content reveals the project's functional scope and underlying technologies:

*   **`streamlit==1.8.0`**: This is a strong indicator that the project is an **interactive web application or dashboard** built using the Streamlit framework. Streamlit is designed for quickly creating data apps with a focus on simplicity.
*   **`pdfminer==20191125`**: This package specializes in **extracting information from PDF documents**. This suggests the application has a feature that involves reading, parsing, or processing the content of PDF files.
*   **`protobuf==3.20.*`**: Protocol Buffers is a method for **serializing structured data**. It's often used for efficient data exchange in various contexts, including internal data models, gRPC communications, or sometimes as an underlying dependency of other libraries (Streamlit itself uses it). Its inclusion points towards robust data handling or inter-process communication.
*   **`altair==4.2.2`**: Altair is a declarative statistical visualization library. Its presence, especially alongside Streamlit, confirms that the application likely includes **sophisticated data visualization and plotting** capabilities for displaying insights derived from data.
*   **`click==8.1.7`**: Click is a package for **creating beautiful command-line interfaces (CLIs)**. This implies that the project might also include command-line tools for specific tasks, configurations, or non-interactive operations, or it could be a dependency of another package used.

In summary, this `requirements.txt` file defines the essential building blocks for a Python project that appears to be an interactive Streamlit web application, capable of processing PDF files, performing data visualization, handling structured data efficiently, and potentially offering command-line functionalities.

### 📄 `.streamlit\config.toml`

This file, `config.toml`, is a **configuration file** written in TOML (Tom's Obvious, Minimal Language) format.

*   **What it does:**
    Its sole purpose is to define the **visual styling parameters for an application's user interface theme**. Specifically, it sets various color codes for different elements (primary, background, secondary background, and text) and specifies the preferred font family.

*   **How it contributes to the project:**
    It acts as a central place to **externalize visual design choices** from the main application code. This allows developers or even end-users (depending on the application's design) to easily **customize the look and feel** of the application without needing to modify, recompile, or even understand the core programming logic. This promotes:
    *   **Flexibility:** Easy theme switching or customization.
    *   **Maintainability:** Styling changes are isolated to a single, readable file.
    *   **Consistency:** Ensures a unified visual theme across the application.

*   **Main Logic:**
    As a declarative configuration file, `config.toml` doesn't contain any procedural "logic" (like loops, conditionals, or functions). Its "logic" is entirely based on its **simple, structured key-value pair format** within a designated section.
    *   The `[theme]` header groups all the following settings under a common category named "theme".
    *   Each line inside the `[theme]` section defines a specific property (e.g., `primaryColor`, `font`) and assigns it a static value (e.g., `"#060606"`, `"serif"`).
    *   The application's rendering engine or UI framework will read these values at startup (or runtime) and apply them to the corresponding visual elements, effectively "configuring" its appearance based on these declarations.
## 🧰 Tech Stack

PEditor is a Portable Executable (PE) file editor. Based on its GitHub repository and common descriptions, the key technologies and languages used are:

1.  **Python:** This is the primary programming language for the entire application.
2.  **PyQt5:** This is the GUI (Graphical User Interface) toolkit used. PyQt5 provides the Python bindings for the Qt application framework, allowing PEditor to have a cross-platform graphical interface.
3.  **pefile:** This is a crucial Python library specifically designed for parsing and working with PE files (executables, DLLs, etc.). It allows PEditor to read, analyze, and modify the structure of PE files.
4.  **Capstone Engine:** This is a powerful multi-platform, multi-architecture disassembly framework. PEditor uses Capstone to disassemble code sections within PE files, allowing users to view assembly instructions.
5.  **Unicorn Engine:** This is a lightweight, multi-platform, multi-architecture CPU emulator framework. PEditor integrates Unicorn to provide emulation capabilities, which can be useful for analyzing code execution paths or for dynamic analysis features.
6.  **PyQtGraph (Optional):** This is a Python graphing and GUI library built on PyQt/PySide and NumPy. While not strictly essential for core PE editing, it's often used for visualizing data, such as entropy plots or other statistical representations of the PE file's sections.

In summary, PEditor leverages **Python** as its core language, **PyQt5** for its user interface, and specialized libraries like **pefile**, **Capstone**, and **Unicorn** to handle the specific tasks of PE file parsing, disassembly, and emulation.
## 📂 Project Structure

```bash
.git\HEAD
.git\config
.git\description
.git\hooks\applypatch-msg.sample
.git\hooks\commit-msg.sample
.git\hooks\fsmonitor-watchman.sample
.git\hooks\post-update.sample
.git\hooks\pre-applypatch.sample
.git\hooks\pre-commit.sample
.git\hooks\pre-merge-commit.sample
.git\hooks\pre-push.sample
.git\hooks\pre-rebase.sample
.git\hooks\pre-receive.sample
.git\hooks\prepare-commit-msg.sample
.git\hooks\push-to-checkout.sample
.git\hooks\sendemail-validate.sample
.git\hooks\update.sample
.git\index
.git\info\exclude
.git\logs\HEAD
.git\logs\refs\heads\main
.git\logs\refs\remotes\origin\HEAD
.git\objects\pack\pack-f744ffa14e7e04ed9584ef75a064437a779c1c73.idx
.git\objects\pack\pack-f744ffa14e7e04ed9584ef75a064437a779c1c73.pack
.git\objects\pack\pack-f744ffa14e7e04ed9584ef75a064437a779c1c73.rev
.git\packed-refs
.git\refs\heads\main
.git\refs\remotes\origin\HEAD
.gitattributes
.gitignore
.streamlit\config.toml
PEditor.py
README.md
app.py
functions.py
requirements.txt
```

## 🤝 Contribution

We welcome contributions! Please fork the repo and submit a PR.

## 🏅 Acknowledgements

- Thanks to the open-source community for incredible tools.
- README content generated with the help of AI summarization.

---
### 🧾 Final Signature
⚙️ README generated by **Gemini 2.5 Flash AI** via an open-source tool.
