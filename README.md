# FastAPI File Upload API

This is a simple FastAPI application that provides endpoints for uploading image files, checking their upload status, and retrieving the files.

## Features

- *File Upload*: Upload image files and store them on the server.
- *Status Check*: Check the upload status of a file by its unique identifier (UUID).
- *File Retrieval*: Retrieve and download uploaded files using their UUID.



## Installation

Follow these steps to set up the project locally:

### 1. Clone the Repository

bash
git clone <repository_url>
cd <repository_name>


### 2. Create a Virtual Environment

bash
python -m venv venv
source venv/bin/activate  # On Linux/Mac
venv\Scripts\activate   # On Windows


### 3. Install Dependencies

bash
pip install -r requirements.txt


### 4. Run the Application

bash
uvicorn main:app --reload


The application will be available at http://127.0.0.1:8000.

## Endpoints

### 1. Upload a File

*POST* /upload/

Upload an image file to the server.

#### Request
- *Headers*: Content-Type: multipart/form-data
- *Body*: File input field named file

#### Response
json
{
  "file_id": "<UUID>",
  "filename": "<original_filename>"
}


### 2. Check File Status

*GET* /status/{file_id}/

Check the upload status of a file.

#### Response
- *200 OK*:
json
{
  "filename": "<original_filename>",
  "status": "uploaded"
}

- *404 Not Found*:
json
{
  "detail": "File not found."
}


### 3. Retrieve a File

*GET* /files/{file_id}/

Download an uploaded file.

#### Response
- *200 OK*: Returns the file as a response.
- *404 Not Found*:
json
{
  "detail": "File not found."
}
