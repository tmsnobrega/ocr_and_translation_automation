# Bible in a Year - OCR and Translation Automation

This project automates the process of downloading images from Google Drive, performing Optical Character Recognition (OCR) to extract text, translating the text from English to Portuguese, and organizing the content into Word documents for easy review. The entire workflow is designed to streamline the management and translation of biblical content.

## Features

1. **Google Drive Integration**:
   - Automatically downloads image files from a specified Google Drive folder.

2. **Image Renaming**:
   - Renames downloaded images into a structured format (`d{x}_p{y}.jpg`), where `x` represents the day, and `y` is the photo number.

3. **OCR with Google Vision API**:
   - Extracts text from images using Google's Vision API.
   - Processes each image to ensure accurate text extraction.

4. **Translation to Portuguese**:
   - Uses Google Translate API to convert English text into Portuguese.

5. **Content Organisation**:
   - Groups translated text by day and saves it into Word documents (`d1.docx`, `d2.docx`, etc.).

6. **File Upload to Google Drive**:
   - Uploads the final Word documents back to the specified Google Drive folder for easy sharing and access.

## Project Structure

```plaintext
.
├── main.py               # Main script to execute the workflow
├── creds.py              # Contains credentials and configuration settings
├── data/                 # Local folder for storing downloaded images and Word documents
│   ├── photos/           
│   └── docs/             
├── .gitignore            # Git ignore file to exclude sensitive data and large files
└── README.md             # Project documentation
```

## Prerequisites

### Google Cloud APIs
1. Enable the **Google Drive API** and **Vision API** on your Google Cloud project.
2. Create a service account and download the JSON credentials file.

### Python Environment
1. Install **Python 3.9 or higher**.
2. Install the required libraries:
   ```bash
   pip install google-api-python-client google-auth google-cloud-vision google-cloud-translate python-docx
   ```

### Environment Variables
1. Configure it directly in the `creds.py` file:
   ```python
   GOOGLE_SERVICE_ACCOUNT = "/path/to/service_account.json"
   ```

## How It Works

1. **Authentication**:
   - Authenticates with Google APIs using the provided service account credentials.

2. **Image Processing**:
   - Downloads images from Google Drive.
   - Renames files to maintain a consistent naming scheme.

3. **Text Extraction and Translation**:
   - Performs OCR to extract text from images.
   - Translates extracted text into Portuguese.

4. **Document Organisation**:
   - Groups translated content by day.
   - Saves the content into structured Word documents.

5. **Upload Results**:
   - Uploads the final Word documents back to Google Drive for easy sharing.

## Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/username/bible_in_a_year_ocr_translation.git
   cd bible_in_a_year_ocr_translation
   ```

2. Set up the environment:
   Configure the `creds.py` file with the following variables:
   ```python
   FOLDER_ID = "your-google-drive-folder-id"
   GOOGLE_SERVICE_ACCOUNT = "/path/to/service_account.json"
   LOCAL_IMAGE_FOLDER = "./data/photos"
   LOCAL_WORD_FOLDER = "./data/docs"
   SCOPES = [
       "https://www.googleapis.com/auth/drive"
   ]
   ```

3. Run the script:
   ```bash
   python main.py
   ```

## Security Notes

- **Avoid Committing Sensitive Files**:
  Ensure `service_account.json` and `creds.py` are added to `.gitignore`.

- **Environment Variables**:
  Use environment variables to securely manage credentials.
