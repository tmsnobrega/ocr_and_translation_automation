# OCR and Translation Automation

This project automates the process of downloading images from Google Drive, performing Optical Character Recognition (OCR) to extract text, translating the text from English to Portuguese, and organising the content into Word documents for easy review. The entire workflow is designed to streamline the management and translation of biblical content.

## Features

1. **Google Drive Integration**:

   - Automatically downloads image files from a specified Google Drive folder.
   - Supports incremental downloads to avoid redundant data transfer.

2. **Image Renaming**:

   - Renames downloaded images into a structured format (`d{x}_p{y}.jpg`), where `x` represents the day, and `y` is the photo number.

3. **OCR with Google Vision API**:

   - Extracts text from images using Google's Vision API.
   - Processes each image to ensure accurate text extraction.

4. **Translation to Portuguese**:

   - Uses Google Translate API to convert English text into Portuguese.
   - Ensures high-quality and context-aware translations.
   - It is important to note that using the Google Translate API could result in additional costs.

5. **Content Organisation**:

   - Groups translated text by day and saves it into Word documents (`d1.docx`, `d2.docx`, etc.).
   - Ensures each document contains the complete translated content for a given day.

6. **File Upload to Google Drive**:

   - Uploads the final Word documents back to the specified Google Drive folder for easy sharing and access.

7. **Temporary File Cleanup**:

   - Deletes all temporary files and directories after the upload process is completed.

## Project Structure

```plaintext
.
├── main.py               # Main script to execute the workflow
├── creds.py              # Contains credentials and configuration settings
├── temp_files/           # Temporary storage for images and Word documents
│   ├── photos/           # Local folder for downloaded images
│   └── docs/             # Local folder for processed Word documents
├── .gitignore            # Git ignore file to exclude sensitive data and temporary files
└── README.md             # Project documentation
```

## Prerequisites

### Google Cloud APIs

1. Enable the following APIs on your Google Cloud project:
   - Google Drive API
   - Google Vision API
   - Google Cloud Translation API
2. Create a service account and download the JSON credentials file.

### Python Environment

1. Install **Python 3.7 or higher**.
2. Install the required libraries:
   ```bash
   pip install google-api-python-client google-auth google-cloud-vision google-cloud-translate python-docx
   ```

### Environment Variables

Set up the `creds.py` file with the following variables:

```python
FOLDER_ID = "your-google-drive-folder-id"
GOOGLE_SERVICE_ACCOUNT = "/path/to/service_account.json"
LOCAL_IMAGE_FOLDER = "./temp_files/photos"
LOCAL_WORD_FOLDER = "./temp_files/docs"
SCOPES = [
    "https://www.googleapis.com/auth/drive",
    "https://www.googleapis.com/auth/cloud-platform"
]
```

## How It Works

1. **User Input**:

   - Take a photo of each page individually, ensuring no other content (e.g., other pages) is visible.
   - Upload these photos to a public Google Drive folder.

2. **Authentication**:

   - Authenticates with Google APIs using a service account JSON file.

3. **Image Processing**:

   - Downloads images from Google Drive.
   - Renames files to maintain a consistent naming format.

4. **Text Extraction and Translation**:

   - Performs OCR to extract text from images.
   - Translates extracted text into Portuguese.

5. **Custom Formatting**:

   - Adds headers, bullet points, and specific formatting for readability.

6. **Document Organisation**:

   - Groups content by day and saves it into Word documents.

7. **Upload Results**:

   - Uploads the final Word documents back to Google Drive.

8. **Temporary File Cleanup**:

   - Deletes all temporary files after the upload process.

## Usage

1. Clone the repository:

   ```bash
   git clone https://github.com/tmsnobrega/ocr_and_translation_automation.git
   cd ocr_and_translation_automation
   ```

2. Install the necessary libraries.

3. Configure the `creds.py` file with your credentials and folder IDs.

4. Upload the photos to a public Google Drive folder.

5) Run the script:
   ```bash
   python main.py
   ```

## Security Notes

- **Avoid Committing Sensitive Files**:
  Ensure `service_account.json` and `creds.py` or any other sensitive files are added to `.gitignore`.

- **Environment Variables**:
  Use environment variables or a secure `creds.py` file to manage sensitive configurations.

