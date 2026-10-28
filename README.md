
# Social Media Publishing Automation

**Automating Facebook and Instagram publishing with n8n, Google Sheets, Meta Graph API, and Cloudinary.**

Developed and maintained at **Pexdel Solution** to automate recurring social media publishing tasks and coordinate content delivery across client accounts.

## Project Overview

Managing social media publishing across multiple client accounts involves repetitive tasks, including preparing content, handling images, checking publishing schedules, and publishing posts on the correct platforms.

This project uses **n8n workflow automation** to connect client data, scheduling logic, media processing, and social media APIs into a centralized workflow.

The automation retrieves client records from Google Sheets, evaluates posting conditions, and routes eligible records through Facebook and Instagram publishing workflows.

## Key Features

- **Scheduled Automation:** Starts the workflow according to a configured schedule.
- **Centralized Client Data:** Uses Google Sheets to manage client information, captions, posting conditions, and account details.
- **Conditional Routing:** Evaluates posting-day conditions before processing client records.
- **Facebook Publishing:** Sends images and captions through the Meta Graph API.
- **Instagram Publishing:** Downloads media, uploads assets to Cloudinary, creates Instagram media containers, checks processing status, and publishes eligible posts.
- **Workflow Coordination:** Uses loops, conditional branches, and delays to manage publishing sequences.
- **Publishing Status Updates:** Updates Google Sheets as records move through the workflow.

## Technology Stack

| Technology | Purpose |
|---|---|
| n8n | Workflow orchestration and automation |
| Google Sheets | Client data and publishing configuration |
| Meta Graph API | Facebook and Instagram publishing |
| Cloudinary | Image hosting and media processing |
| JavaScript | Data transformation and workflow expressions |
| HTTP Request | Communication with external APIs |

## System Architecture

```text
              Scheduled Trigger
                     |
                     v
            Google Sheets Data
                     |
                     v
          Posting-Day Conditions
                     |
              +------+------+
              |             |
              v             v
         Facebook        Instagram
         Workflow         Workflow
              |             |
              v             v
        Prepare Image   Download Image
        and Caption          |
              |              v
              |         Cloudinary Upload
              |              |
              |              v
              |       Create Media Container
              |              |
              |              v
              |       Check Processing Status
              |              |
              v              v
         Meta Graph API Publishing
              |             |
              v             v
        Facebook Post   Instagram Post
                            |
                            v
                    Google Sheets Update
```

*This diagram summarizes the main workflow. Refer to the project screenshots for the actual n8n implementation.*

## How It Works

### 1. Scheduled Execution

The Schedule Trigger starts the workflow according to its configured schedule.

### 2. Client Data Retrieval

The workflow reads client records from Google Sheets, including captions, account identifiers, access tokens, and posting conditions.

### 3. Conditional Processing

The workflow evaluates the configured posting-day condition and routes eligible records into the appropriate publishing branches.

### 4. Facebook Publishing

The Facebook branch prepares the image URL, page identifier, caption, and access token, then sends an HTTP request to the Meta Graph API to publish the image post.

### 5. Instagram Publishing

The Instagram branch downloads the image, uploads it to Cloudinary, creates a media container, waits for processing, checks the media status, and proceeds to publishing when the required status is reached.

### 6. Spreadsheet Updates

Google Sheets is updated at designated points in the workflow to reflect processing outcomes and manage subsequent automation behavior.

## Engineering Focus

This project demonstrates practical experience with:

- Designing multi-branch automation workflows.
- Integrating third-party APIs through HTTP requests.
- Mapping and transforming structured data between nodes.
- Managing client-specific configuration through a centralized spreadsheet.
- Coordinating asynchronous media-processing operations.
- Working with Meta API permissions and access-token configuration.
- Troubleshooting workflow execution and publishing issues.

## Security and Privacy

This public repository documents the project through sanitized screenshots and technical explanations.

- Production workflow exports and credentials are not included.
- Access tokens, app secrets, and private client data must remain confidential.
- API credentials should be managed securely within n8n.
- Publishing requires appropriate Meta permissions and access to the relevant Pages and Instagram accounts.

## Professional Context

**Organization:** Pexdel Solution  
**Project:** Social Media Publishing Automation  
**Primary Role:** Workflow development, maintenance, and troubleshooting

The project reflects hands-on experience building and maintaining business automation that connects client data, media processing, and social media publishing APIs.

---

**Note:** Screenshots are intended to document the workflow architecture and implementation. They do not expose production credentials or private client information.
