# Flow to import CVs from Multiple Platforms into the LarkSuite database

## Step 1: Retrieve CVs from Source Platforms
- Support for multiple CV source platforms:
  - TopCV
  - Other Platform 1
  - Other Platform 2
- Access the platform website
- View and select candidate CVs
- Download selected CV files
- Submit CVs to the CV Collection Service

## Step 2: Upload to Google Drive
- CV Collection Service uploads files to Google Drive
- Generate and store URL links for each CV
- Return storage links to the recruiter

## Step 3: Process CVs and Create Profiles
### 3.1. Extract Candidate Information
- Submit CV for processing to the CV Processor
- Forward to Information Extractor
- Use AI System for advanced processing:
  - OCR (Optical Character Recognition) to convert PDF content to text
  - NLP (Natural Language Processing) to structure information
  - Named Entity Recognition (NER) to detect specific information

#### Information to Extract:
- Name
- Email
- Phone
- CV Link
- LinkedIn Link
- GitHub Link
- Facebook Link
- Twitter Link
- Instagram Link
- Source Platform

### 3.2. Create a profile in the "LarkSuite" database
- Forward extracted candidate information to Profile Creator
- Create new candidate profile in LarkSuite database
- Confirm profile creation
- Return success status to recruiter
