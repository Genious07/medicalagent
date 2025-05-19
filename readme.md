#🏥 Medical Imaging Diagnosis Agent

A Streamlit-based web application that leverages Google’s Gemini AI and DuckDuckGo search tools to perform automated radiological analysis of uploaded medical images. Designed for educational and informational purposes, this tool provides structured diagnostic insights, patient-friendly explanations, and relevant research references.

---

## Table of Contents

1. [Features](#features)
2. [Prerequisites](#prerequisites)
3. [Installation](#installation)
4. [Configuration](#configuration)
5. [Usage](#usage)
6. [Project Structure](#project-structure)
7. [Cache & Performance](#cache--performance)
8. [Troubleshooting](#troubleshooting)
9. [Contributing](#contributing)
10. [License](#license)

---

## Features

* **Automated Imaging Analysis**: Uses Google Gemini AI ("gemini-2.0-flash") for detailed radiological interpretation.
* **DuckDuckGo Research**: Integrates a search tool to fetch recent literature and treatment protocols.
* **Structured Reporting**:

  * Modality & region identification
  * Key findings with measurements
  * Diagnostic assessment & differential diagnoses
  * Patient-friendly explanation
  * Research context with references
* **Interactive UI**: Simple Streamlit interface for image upload and result display.
* **Environment-Driven**: API key loaded from environment variable; no hard-coded secrets.
* **Optimized Performance**: Cached agent initialization, efficient image resizing, and temporary file management.

---

## Prerequisites

* Python 3.8 or higher
* A valid Google API key with access to the Gemini model
* `pip` package manager

---

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/Genious07/medicalagent.git
   cd medical-imaging-agent
   ```

2. **Create a virtual environment** (recommended)

   ```bash
   python -m venv .venv
   source .venv/bin/activate   # macOS/Linux
   .\.venv\Scripts\activate  # Windows
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

---

## Configuration

1. **Environment Variable**

   * Set your Google API key in the `GOOGLE_API_KEY` environment variable before running:

     ```bash
     export GOOGLE_API_KEY="your_real_api_key_here"   # macOS/Linux
     set GOOGLE_API_KEY="your_real_api_key_here"      # Windows
     ```

2. **Supported Image Formats**

   * JPG, JPEG, PNG, DICOM

---

## Usage

1. **Start the app**

   ```bash
   streamlit run main.py
   ```

2. **Open the UI**

   * By default, Streamlit opens at `http://localhost:8501`.

3. **Workflow in the UI**

   1. Upload your medical image.
   2. Click **🔍 Analyze Image**.
   3. Await AI analysis—results will appear with headers:

      * Image Type & Region
      * Key Findings
      * Diagnostic Assessment
      * Patient-Friendly Explanation
      * Research Context

---

## Project Structure

```
medical-imaging-agent/
├── main.py              # Streamlit application code
├── requirements.txt     # Python dependencies
├── README.md            # Project documentation (this file)
└── .gitignore           # Excluded files and folders
```

---

## Cache & Performance

* **@st.cache\_resource** is used to persist the `Agent` across reruns, reducing API initialization overhead.
* **PILImage.thumbnail** with the `LANCZOS` filter ensures fast, high-quality image resizing.
* Temporary image files are managed via Python’s `tempfile` for safe cleanup.

---

## Troubleshooting

* **Missing API Key**: The app will display an error if `GOOGLE_API_KEY` is unset. Ensure you’ve exported it in your shell.
* **Unsupported File**: Verify your upload format (JPG, PNG, or DICOM).
* **Analysis Errors**: Exceptions from the AI agent will surface in the UI—check logs for stack traces.
* **Slow Performance**: Large image files may take longer. Pre-rescale externally if needed.

---

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork this repository.
2. Create a new branch: `git checkout -b feature/my-awesome-feature`.
3. Commit your changes: `git commit -m 'Add some feature'`.
4. Push to the branch: `git push origin feature/my-awesome-feature`.
5. Open a Pull Request.

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
