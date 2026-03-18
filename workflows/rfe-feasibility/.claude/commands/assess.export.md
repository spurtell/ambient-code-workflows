# /assess.export - Export Assessment to Google Drive

## Purpose

Upload completed assessment artifacts to a Google Drive folder for team sharing and stakeholder review.

## Prerequisites

- At least one assessment document exists in `artifacts/rfe-feasibility/`
- Google Drive MCP integration is available

## Process

1. **Locate Assessment Artifacts**
   - Read `artifacts/rfe-feasibility/` to find completed documents for the target RFE
   - List what will be exported (assessment, API verification, quick assessment, context)

2. **Confirm Target Location**
   - Ask the user for the Google Drive folder URL or folder ID
   - Use `list_drive_items` to verify the folder exists and is writable
   - If no folder specified, ask the user where to upload

3. **Upload Documents**
   - Use `create_drive_file` to upload each assessment artifact
   - Upload as markdown files (or convert to Google Docs if preferred)
   - Provide the shareable link for each uploaded file

4. **Provide Summary**
   - List all uploaded files with their Google Drive links
   - Confirm successful export

## Output

- Assessment documents uploaded to the specified Google Drive folder
- Shareable links provided to the user

## Notes

- If Google Drive integration is not available, suggest alternative sharing methods (copy to clipboard, email, etc.)
- Documents are uploaded as-is in markdown format; recipients can view them directly or import into Google Docs
