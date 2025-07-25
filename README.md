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
- [🧰 Tech Stack](#-tech-stack)
- [📂 Project Structure](#-project-structure)
- [🤝 Contribution](#-contribution)
- [🏅 Acknowledgements](#-acknowledgements)
- [🧾 Final Signature](#-final-signature)

## 📖 Overview

The project 'PEditor' is a web application built using **Streamlit** that primarily functions as a **PDF Text Extractor**. Despite its name, which might suggest PDF editing capabilities, its core functionality, as revealed by the provided code, is focused solely on **extracting text content from PDF documents**.

Here's a breakdown of what PEditor does:

1.  **PDF Text Extraction:**
    *   It allows users to upload a PDF file.
    *   It offers two main modes for text extraction:
        *   **One text file (.txt):** Extracts all text from the entire PDF document and consolidates it into a single `.txt` file for download.
        *   **Text file per page (ZIP):** Extracts text from each page individually, creating a separate `.txt` file for each page. These individual text files are then bundled into a `.zip` archive for download.
    *   It leverages the `pdfminer.six` library (indicated by imports like `pdfminer.pdfinterp`, `pdfminer.converter`, `pdfminer.pdfpage`) to parse the PDF structure and extract text.

2.  **PDF Display:**
    *   After a PDF is uploaded, users have the option to "Display document." This embeds the PDF directly within the web application interface, allowing the user to view the uploaded PDF in their browser.

3.  **User Interface and Navigation:**
    *   The application is built with Streamlit, providing a simple and interactive web-based interface.
    *   It features a sidebar menu with navigation options:
        *   **Home:** Contains the main PDF text extraction functionality.
        *   **Help:** Provides instructions on how to use the app, including limitations (e.g., file size, language support, issues with tables/graphs, no OCR).
        *   **About us:** Information about the developers and their mission/vision.
        *   **Contact us:** Details for technical support and business inquiries.

**Key Clarification regarding the Name "PEditor":**
Based on the provided source code, the application *does not* offer any features for editing, modifying, merging, splitting, or otherwise manipulating the content or structure of PDF files beyond extracting their text. The "Display document" option might allow a user's *browser's native PDF viewer* to offer some basic interaction (like printing or saving locally), but this functionality is not provided by the PEditor application itself. The primary and only evident function is text extraction.

## ❓ Why This Project

A developer would use the project 'PEditor' primarily as a **rapidly deployable, user-friendly, and efficient tool for extracting plain text from PDF documents**.

Here's a breakdown of why a developer would find this project useful, based on the provided code:

1.  **Solves a Common Problem (PDF Text Extraction):** Many applications require extracting textual content from PDFs for further processing (e.g., data analysis, NLP, indexing, content management). PEditor provides a straightforward solution for this fundamental task.

2.  **Rapid Development & Deployment (Streamlit):**
    *   **Streamlit's Simplicity:** The project leverages Streamlit, which allows developers to build interactive web applications with pure Python quickly. This means a developer can get a functional UI for PDF text extraction up and running in a fraction of the time it would take with traditional web frameworks (like Flask/Django + HTML/CSS/JS).
    *   **Minimal Frontend Code:** No need to write complex HTML, CSS, or JavaScript. Streamlit handles the UI rendering based on Python commands.

3.  **Abstraction of PDF Parsing (pdfminer Integration):**
    *   The `functions.py` file encapsulates the `pdfminer.six` library. A developer doesn't need to delve into the intricate details of `PDFResourceManager`, `PDFPageInterpreter`, `TextConverter`, etc., every time they need to extract text.
    *   **Clean API:** `convert_pdf_to_txt_file` and `convert_pdf_to_txt_pages` provide simple function calls to get the desired text output.

4.  **Flexible Output Formats:**
    *   **Single `.txt` file:** Ideal for overall content analysis or when the entire document's text is needed as a contiguous block.
    *   **`.zip` of individual page `.txt` files:** Crucial for tasks where page-level granularity is important (e.g., processing specific pages, maintaining original document structure, or analyzing content page by page).

5.  **Performance Optimization (`@st.cache`):**
    *   The use of `@st.cache` on the conversion functions is a significant advantage. It ensures that if the same PDF is uploaded again within a session, or if the function is called with identical parameters, the results are retrieved from a cache rather than re-processing the PDF, making the application faster and more responsive for the user.

6.  **Ready-to-Use UI with User Guidance:**
    *   Beyond just the core functionality, `app.py` includes a complete UI with menu options ("Home," "Help," "About us," "Contact us").
    *   The "Help" section is particularly useful, providing clear instructions and important "Notes" (limitations, best practices). This makes the tool more user-friendly and reduces support queries for the developer.

7.  **Foundation for Further Development:**
    *   A developer might use PEditor as a starting point or a module within a larger system. For example:
        *   **Data Pipeline:** Integrate PEditor to be the first step in a data pipeline that extracts text, then feeds it into an NLP model, a database, or a search index.
        *   **Internal Tooling:** Provide a simple web interface for non-technical team members to extract text from documents they receive.
        *   **Proof-of-Concept:** Quickly demonstrate PDF text extraction capabilities for a new project or idea.

8.  **Open Source & Modifiable:** While the full license isn't provided, the full code implies it's intended to be shared and modified. A developer can customize it to fit specific needs, add new features (e.g., OCR integration, specific data parsing, output to other formats), or integrate it into other projects.

In essence, PEditor offers a **quick, effective, and well-structured solution for a common PDF processing task**, making it an attractive choice for developers looking to build applications that involve extracting text from PDF documents without starting from scratch.

## 🚀 Features

Based on the provided code, here are 7 features of this project:

1.  **PDF to Text Conversion:** The core functionality allows users to extract text content from uploaded PDF documents.
2.  **Flexible Text Output Options:** Users can choose to download the extracted text as a single `.txt` file containing all content, or as a `.zip` archive where each page's text is saved as a separate `.txt` file.
3.  **In-App PDF Display:** The application provides a feature to display the uploaded PDF document directly within the web interface, allowing users to view the file before or after extraction.
4.  **Interactive Streamlit Web Interface:** Built using Streamlit, the project offers a user-friendly and interactive web application with a wide layout and responsive elements like file uploaders, select boxes, and download buttons.
5.  **Multi-Section Navigation:** A clear sidebar menu (Home, Help, About us, Contact us) organizes the application's content, allowing users to easily navigate between different sections.
6.  **Comprehensive User Guidance & Support:** The "Help" section provides detailed instructions on how to use the app and important notes regarding file size, language support, and content limitations. A "Contact Us" section offers technical support and business inquiry details.
7.  **Direct File Upload and Download:** Users can easily upload their PDF files via a dedicated uploader and download the processed text directly through integrated download buttons.

## ⚡ Quick Start

```bash
# 1. Clone the repository
git clone <your-repo-url>

# 2. Navigate into the repo
cd your-repo

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run the application
python app.py
```

## 🧪 Usage

The PEditor project, as described by the provided `app.py` and `functions.py` code, is a Streamlit application designed for extracting text from PDF files.

Here's how a user can utilize the project after successful setup (i.e., having Python, Streamlit, `pdfminer.six`, etc., installed, and running the application):

---

### How to Use the PEditor Application

**Step 1: Launch the Application**

1.  Open your terminal or command prompt.
2.  Navigate to the directory where you have saved `app.py` and `functions.py` (and potentially created a `file_pages` directory if not automatically handled by `save_pages` function's execution).
3.  Run the Streamlit application using the command:
    ```bash
    streamlit run app.py
    ```
4.  This command will open a new tab in your default web browser displaying the PEditor application.

**Step 2: Navigate the Application (Sidebar Menu)**

Upon launching, you will see the PEditor title and a sidebar on the left with a "Menu" radio button. You can switch between different sections of the app:

*   **Home:** This is the main functionality section for PDF text extraction.
*   **Help:** Provides instructions on how to use the app and important notes/limitations.
*   **About us:** Contains information about the development team's mission and vision.
*   **Contact us:** Provides contact details for technical support and business inquiries.

**Step 3: Extract Text from a PDF (Home Section)**

1.  **Select "Home"** from the sidebar menu (it's the default view upon launch).
2.  **Choose Output Format:** In the sidebar, under "PDF to Text", use the dropdown menu to select how you want the extracted text:
    *   **`One text file (.txt)`:** This option will extract all text from all pages into a single `.txt` file.
    *   **`Text file per page (ZIP)`:** This option will extract text from each page into a separate `.txt` file, then package all these individual `.txt` files into a single `.zip` archive.
3.  **Upload Your PDF File:** In the main content area, click the **`Browse files`** button next to "Load your PDF file". Select the PDF document you wish to process from your computer. The app supports `.pdf` file types.
4.  **Display Document (Optional):** After uploading, an expandable section titled **`Display document`** will appear. Click on it to view a preview of your uploaded PDF directly within the app.
    *   *Note: The `displayPDF` function is declared in `app.py` but not defined in the provided `functions.py` or `app.py` code. Assuming it's a placeholder for a Streamlit PDF viewer, it would render the PDF for viewing purposes.*
5.  **Download Extracted Text:**
    *   If you selected **`One text file (.txt)`**: A **`Download txt file`** button will appear. Click it to download your PDF's text content as a single `.txt` file.
    *   If you selected **`Text file per page (ZIP)`**: A **`Download ZIP (txt)`** button will appear. Click it to download a `.zip` file containing individual `.txt` files for each page of your PDF.
6.  **Visual Feedback:** After successful download, `st.balloons()` will trigger a celebratory balloon animation.

**Step 4: Access Help and Information (Help, About us, Contact us Sections)**

*   **Help:**
    1.  Select **"Help"** from the sidebar menu.
    2.  Read the "How to use..." section for quick tips on extraction.
    3.  Review the "Note:" section for important limitations, such as file size limits (200MB), the need to refresh for reusing the same file, English language support only, potential issues with tables/graphs, and no OCR support.
*   **About us:**
    1.  Select **"About us"** from the sidebar menu.
    2.  Read about the development team's mission and vision for the project.
*   **Contact us:**
    1.  Select **"Contact us"** from the sidebar menu.
    2.  Find information for "Technical Support" (directs to GitHub profile, though no specific link is in the provided code) and "Business Inquiry" (email: `yashamr192@gmail.com`). A clickable Gmail badge link is provided for convenience.

---

By following these steps, a user can effectively utilize the PEditor application for its intended purpose of extracting text from PDF documents and accessing related information.

## 🧰 Tech Stack

Based on the provided codebase, here are the technologies and languages used:

1.  **Programming Language:**
    *   **Python:** The entire codebase is written in Python, evident from the syntax (`import`, `def`, `class`, `st.`, `with open`, etc.).

2.  **Key Libraries/Frameworks:**
    *   **Streamlit:** Used as `st`, it's the primary framework for building the web application's user interface and handling the overall application flow.
    *   **PDFMiner (specifically `pdfminer.pdfinterp`, `pdfminer.converter`, `pdfminer.layout`, `pdfminer.pdfpage`):** Explicitly mentioned and imported, this library is used for parsing PDF files and extracting text content.
    *   **`zipfile` (Python Standard Library):** Used for creating ZIP archives, specifically to bundle multiple text files (one per page) for download.
    *   **`io` (Python Standard Library):** Specifically `StringIO`, used for handling text data in memory as a file-like object, which is useful for `pdfminer` and later for creating downloadable content.
    *   **`base64` (Python Standard Library):** Imported in `functions.py`, though not explicitly used in the provided `save_pages` function snippet, it indicates a potential intended use for encoding/decoding data.

3.  **Other:**
    *   **Markdown:** Used within `st.markdown` for formatting the text content displayed in the Streamlit application's UI.
## 📂 Project Structure

```bash
reposage_gqrarzp2/
│   .gitattributes
│   .gitignore
│   app.py
│   functions.py
│   PEditor.py
│   README.md
│   requirements.txt
│   ├── .git/
│   │   config
│   │   description
│   │   HEAD
│   │   index
│   │   packed-refs
│   │   ├── hooks/
│   │   │   applypatch-msg.sample
│   │   │   commit-msg.sample
│   │   │   fsmonitor-watchman.sample
│   │   │   post-update.sample
│   │   │   pre-applypatch.sample
│   │   │   pre-commit.sample
│   │   │   pre-merge-commit.sample
│   │   │   pre-push.sample
│   │   │   pre-rebase.sample
│   │   │   pre-receive.sample
│   │   │   prepare-commit-msg.sample
│   │   │   push-to-checkout.sample
│   │   │   sendemail-validate.sample
│   │   │   update.sample
│   │   ├── info/
│   │   │   exclude
│   │   ├── logs/
│   │   │   HEAD
│   │   │   ├── refs/
│   │   │   │   ├── heads/
│   │   │   │   │   main
│   │   │   │   ├── remotes/
│   │   │   │   │   ├── origin/
│   │   │   │   │   │   HEAD
│   │   ├── objects/
│   │   │   ├── info/
│   │   │   ├── pack/
│   │   │   │   pack-c6bf5b0cf09fff42a666906fc5da214f5e8f4ba1.idx
│   │   │   │   pack-c6bf5b0cf09fff42a666906fc5da214f5e8f4ba1.pack
│   │   │   │   pack-c6bf5b0cf09fff42a666906fc5da214f5e8f4ba1.rev
│   │   ├── refs/
│   │   │   ├── heads/
│   │   │   │   main
│   │   │   ├── remotes/
│   │   │   │   ├── origin/
│   │   │   │   │   HEAD
│   │   │   ├── tags/
│   ├── .streamlit/
│   │   config.toml
```

## 🤝 Contribution

We welcome contributions! Please fork the repo and submit a PR.

## 🏅 Acknowledgements

- Thanks to the open-source community for incredible tools.
- README content generated with the help of AI summarization.

---
### 🧾 Final Signature
⚙️ README generated by **Gemini 2.5 Flash AI** via an open-source tool.
