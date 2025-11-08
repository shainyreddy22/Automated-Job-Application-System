# Automated Job Application Workflow

I always wanted a personal assistant 🪑 who could handle all my work, and now I see that dream coming true with AI agents doing it for me. 🤖 I have built a project that acts like a **smart assistant**, automating the entire job application process—from discovering relevant jobs to sending out personalized applications with my customized resume included.

## What it Does
- Scrapes job listings from **LinkedIn**
- Matches them against my resume 📝
- Finds recruiter emails 📧
- Generates personalized emails with a custom resume 📎
- Tracks everything in Google Sheets 📊

## How it Works
- **Apify** → pulls fresh job listings
- **Google Gemini 2.5 Flash** → job-fit analysis, resume customization, and email generation
- **Hunter.io** → finds recruiter emails
- **Gmail API** → sends emails with the resume
- **Google Sheets** → tracks applications

🚀 With this workflow, I can send **hundreds of applications in just one click**, each tailored to the specific job. 🎯

---

## 🛠️ Setup Instructions

Setting up this workflow is straightforward. Here’s what you’ll need to get started:

### Prerequisites

Before you begin, make sure you have accounts and API keys for the following services:
* An **n8n** instance (Cloud or self-hosted)
* A **Google Account** (for Google Docs and Gmail)
* An **Apify** API Key
* A **Google Gemini** API Key
* A **Hunter.io** API Key

### Step-by-Step Guide

1.  **Import the Workflow**
    * Download the `workflow.json` file from this repository.
    * In your n8n canvas, click `Import from File` and select the JSON file.

2.  **Configure Your Credentials** 🔑
    * Navigate to the `Credentials` section in your n8n sidebar.
    * Click `Add credential` and create a new credential for each of the following services, then connect them to the appropriate nodes in the workflow:
        * **Google:** Create one `Google OAuth2 API` credential. Connect it to all the **Google Docs** and **Gmail** nodes.
        * **Apify:** Create a `Header Auth` credential. In the `HTTP Request` node for Apify, set the `Authentication` to `Header Auth` and select your credential.
        * **Hunter.io:** Create a `Query Auth` credential. In the `Get HR Email` node, set the `Authentication` to `Query Auth` and select your credential.
        * **Google Gemini:** Create a `Google Gemini(PaLM) API` credential. Connect it to the **Filter Jobs**, **Resume Modification**, and **Mail Body Generation** nodes.

3.  **Update Your Resume Link** 📄
    * Open the `Get a document` node (the second node in the workflow).
    * Replace the existing Document ID with the ID of your own resume from its Google Doc URL.

4.  **Activate and Run!** ✅
    * Click the toggle switch to `Active` in the top-right corner of the editor.
    * You can now run the workflow manually by clicking `Execute workflow`.
