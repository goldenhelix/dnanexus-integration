# DNAnexus Integration Tasks

This repository contains Golden Helix server tasks for automating file uploads and downloads with DNAnexus.

## Prerequisites

- Access to DNAnexus Platform
- Valid DNAnexus account credentials

## Setup Instructions

### 1. Get DNAnexus API Token

1. Log in to your DNAnexus Platform account
2. Click on your avatar at the top right corner of the main Platform menu
3. Select "My Profile" from the dropdown menu
4. Click on the "API Tokens" tab
5. Click the "New Token" button
6. In the modal window that opens, you can create a new token
7. Copy the generated token - you'll need this for the tasks

Use [Workspace Settings](./manage/settings) to create a variable `DX_API_TOKEN` with the displayed token.

Alternatively, you can provide the token each time a upload or download task is run.

## Tasks

The repository contains the following tasks:

### Upload to DNAnexus (`dnanexus_upload.task.yaml`)

Uploads files or directories to a DNAnexus project.

Parameters:
- `input_directory`: Directory to upload (optional if input_file is specified)
- `input_file`: Single file to upload (optional if input_directory is specified)
- `dnanexus_project`: Target DNAnexus project name (optional - will use first project if not specified)
- `target_path`: Destination path in DNAnexus (optional - defaults to project root)
- `dnanexus_api_key`: Your DNAnexus API key (optional if set in workspace)

### Download from DNAnexus (`dnanexus_download.task.yaml`)

Downloads files or directories from a DNAnexus project.

Parameters:
- `dnanexus_path`: Path in DNAnexus to download (can be file or folder)
- `output_directory`: Local directory where files will be downloaded
- `dnanexus_project`: Source DNAnexus project name (optional - will use first project if not specified)
- `dnanexus_api_key`: Your DNAnexus API key (optional if set in workspace)

## Notes

- The tasks use the official DNAnexus CLI tools
- If no project is specified, the first project in your workspace will be used
- For uploads, you must specify either an input directory or file
- Downloads will preserve the directory structure from DNAnexus
- If DNAnexus has two files with the same name, only one will be downloaded locally