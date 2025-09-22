md
# MISINFORMATION-DETECTOR

## Project Overview

This repository contains code for a misinformation detection system. While no formal description was provided, the file structure and included files suggest it is a web application with a Chrome/Firefox extension component that likely analyzes text on web pages and provides a verdict on its truthfulness, confidence score, supporting evidence  and educational resources. The backend uses Python (FastAPI) and the frontend/extension uses Javascript.

## Key Features & Benefits (Inferred)

*   **Misinformation Detection:** Identifies potentially false or misleading information online.
*   **Verdict and Confidence Score:** Provides a judgment on the truthfulness of the content and a measure of confidence in that judgment.
*   **Evidence Snippets:** Highlights supporting evidence for the verdict with clickable sources.
*   **Transparency Panel:** Shows the factors contributing to the verdict.
*   **Educational Resources:** Offers educational tips to help users understand the issue.
*   **Chrome Extension:** Integrates directly with the user's web browsing experience.
*   **API Backend:** Provides a robust and scalable infrastructure for the system.

## Prerequisites & Dependencies

Before you begin, ensure you have the following installed:

*   **Python:** Version 3.11 or higher.
*   **Docker:** For containerization and simplified deployment (optional).
*   **Node.js and npm:** For building the Chrome extension (if modifying extension).
*   **Web Browser:** Google Chrome (required for the extension).

The Python backend also depends on the following libraries, which are listed in `backend/requirements.txt`:

*   fastapi==0.101.0
*   uvicorn[standard]==0.22.0
*   requests==2.31.0
*   python-dotenv==1.0.0
*   google-generativeai==0.8.5

## Installation & Setup Instructions

### Backend Setup

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/Garvnanda/MISINFORMATION-DETECTOR.git
    cd MISINFORMATION-DETECTOR
    ```

2.  **Navigate to the backend directory:**

    ```bash
    cd backend
    ```

3.  **Create a virtual environment (recommended):**

    ```bash
    python3 -m venv venv
    source venv/bin/activate  # On Linux/macOS
    # venv\Scripts\activate  # On Windows
    ```

4.  **Install the dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

5. **Set up environment variables:**

   *   Copy the content of `.env.example` (if provided, create your own version of it named `.env`)
   *   Populate the `.env` file with the necessary keys and values, such as API keys (if applicable).

6.  **Run the backend using Uvicorn:**

    ```bash
    uvicorn main:app --host 0.0.0.0 --port 8000
    ```

    Alternatively, you can use the `run_local.sh` script (if available):

    ```bash
    ./run_local.sh
    ```

### Chrome Extension Setup

1.  **Navigate to the `extension` directory:**

    ```bash
    cd extension
    ```

2.  **Open Chrome and go to `chrome://extensions/`**

3.  **Enable "Developer mode" in the top right corner.**

4.  **Click "Load unpacked" and select the `extension` directory in this repository.**

5.  The extension should now be installed and active in your Chrome browser.

### Docker Setup (Optional)

1.  **Build the Docker image:**

    ```bash
    docker build -t misinformation-detector-backend .
    ```

2.  **Run the Docker container:**

    ```bash
    docker run -d -p 8000:8000 misinformation-detector-backend
    ```

    This will start the backend server in a Docker container, accessible at `http://localhost:8000`.

## Usage Examples & API Documentation

### Backend API (Examples)

The backend provides a REST API. Here are some example endpoints (inferred based on the code):

*   **`/` (GET):**  Likely a health check or simple welcome message.

    ```bash
    curl http://localhost:8000/
    ```

*   **`/analyze` (POST):** Likely takes text as input and returns the analysis results. Example:

    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{"text": "This is a test sentence."}' http://localhost:8000/analyze
    ```

    The response would likely be a JSON object containing the verdict, confidence score, evidence snippets, and the transparency panel data.

*Note:* Without further documentation or descriptions, the exact API endpoints and request/response formats are speculative and require further investigation of `backend/main.py`.

### Chrome Extension Usage

1.  Browse to a webpage.
2.  Highlight a text snippet you want to analyze, or activate page analysis.
3.  The extension will send the text to the backend API.
4.  The extension will display the analysis results (verdict, confidence score, evidence, etc.) in a popup or embedded panel.

## Configuration Options

The backend can be configured using environment variables. The following variables are likely used (inferred from `backend/main.py` and the presence of `python-dotenv`):

*   **PORT:** The port the backend server listens on (default: 8000).
*   **Any API keys:** Possibly Google API key for GenAI or Search API keys.  These should be stored as environment variables.

These environment variables can be set in a `.env` file in the `backend` directory, or directly in the system's environment.

## Contributing Guidelines

We welcome contributions to improve this project! Here are some guidelines:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Make your changes and commit them with clear and concise messages.
4.  Submit a pull request with a detailed description of your changes.

## License Information

This project is licensed under the MIT License - see the `LICENSE` file for details.

## Acknowledgments

*   The project structure suggests the use of certain technologies such as FastAPI, Google Generative AI, and potentially other third-party resources. These libraries and resources are acknowledged for their contribution to this project.