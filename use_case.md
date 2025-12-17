# Use Case: Clinical Trial Enrollment & Medication Compliance Tracking System

**Problem:** Research teams need a way to track participant enrollment to ensure timelines are being met while also making sure participants are adhering to mediciation.

Currently teams track this manually via REDCap or Excel which leads to error, missed data, and delays. This project proposes a simple cloud-based system that allows staff to upload enrollment data and track medication compliance automatically in one place.

## Users:
- Study coordinators (upload data, view dashboards)
- Principal investigators (review enrollment and compliance numbers)

## Data Sources: 
- Survey/form that records medication check-ins and participant enrollment information 

Example data:
- participants.csv  
participant_id, enrollment_status, consent_date  
- medication_events.csv  
participant_id, date, dose_taken  

## Basic Workflow:
1. Study team accesses the web application
    - The research assistant (RA) opens the web application in a browser and logs participant information using a simple data entry form which includes participant enrollment info and medication compliance. 
2. Flask application processes the request
    - The Flask application receives the submitted data, performs data validation, and prepares it for storage.
3. Data is stored in the relational database
    - The validated data is stored in the relational database (Google Cloud SQL). 
4. Dashboard queries the database
    - The application queries the database to retrieve stored records and calculate summary metrics for each participant. This is crucial for KPIs. 
5. Results are displayed to the RA/study team 
    - The dashboard displays basic summaries, such as total enrolled participants and compliance counts, to support monitoring and decision-making. This lets the study team know who needs to be contacted to increase study engagement and guides future medication adherence research. 