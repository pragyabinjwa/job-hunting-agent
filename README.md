# job-hunting-agent
An autonomous AI agent that wakes up every morning, scrapes LinkedIn for fresh job listings, rewrites your resume to match each job's ATS keywords using Google Gemini, and delivers a ready-to-apply email to your inbox — all while you sleep.


Every day at 7 AM, this agent automatically:

Scrapes LinkedIn for jobs posted in the last 24 hours matching your search query
Filters and selects the top 10 most relevant listings
Rewrites your resume using Google Gemini AI to match each job's exact ATS keywords
Creates a tailored Google Doc for each application
Emails you a summary table with job details, apply links, and resume links — ready to send

Schedule Trigger (7 AM daily)
        ↓
Workflow Configuration
(Resume Doc ID, Job Query, Email, Apify Token)
        ↓
Google Drive → Download Resume PDF
        ↓
Extract Text from PDF (JavaScript)
        ↓
Build LinkedIn Search URL
        ↓
Apify → Scrape LinkedIn Jobs
        ↓
Poll Apify Status (Loop until SUCCEEDED)
        ↓
Fetch Results → Parse Jobs → Limit to 10
        ↓
ATS Optimizer Agent (Google Gemini)
Rewrites resume per job, keyword by keyword
        ↓
Create Google Doc per resume
        ↓
Insert tailored resume text
        ↓
Gmail → Send summary table with all links
