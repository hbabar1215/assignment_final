# Architecture Plan

## High-Level Architecture
The application is implemented as a web-based system using a Flask application and Google Cloud SQL as our relational database. The architecture is made to support low-volume usage and ease of deployment. 

```mermaid
flowchart TD
  A[User Web Browser] --> B[Flask App];
  B --> C[(Google Cloud SQL)];
```

## Data Flow Narrative 
- User enters data in the Flask web form
This is when a user (like a research assistant) types information into the webpage, for example, a participant ID, whether they are enrolled, or whether medication was taken.

- Flask would upload CSVs to Cloud Storage
In a real cloud setup, instead of storing files locally, Flask could upload CSV files to Google Cloud Storage. This would allow data to be stored centrally and accessed securely from anywhere.

- Dashboard displays totals from the database
The dashboard page pulls information from the database to show simple summaries, such as how many participants are enrolled or how many participants are adhering to medication. 

- Data export and CSV storage in Google Cloud storage (GCS)
The CSV files can be exported and used to present KPIs to research team during meetings. The files will also be stored in Google Cloud storage for sharing and end of study analysis. GCS is a general- purpose storage service that provides a low-cost option for companies of all sizes. 

## Security & Governance

To protect PHI and minimize the risk of a breach of confidentiality, user roles can be assigned to limit access to the database and cloud storage to authorized research team members. Instead of relying on personal user credentials, the system can implement dedicated user accounts for each team member. Additionally, sensitive information such as database passwords would be stored as environment variable secrets rather than being hardcoded into the application, ensuring secure handling of confidential data.

## Cost Considerations 

Regarding costs considerations, the managed database (Cloud SQL) represents the largest expense due to its storage and management features. Cloud Run is relatively inexpensive because it only consumes resources when requests are made, making it cost-efficient. Cloud Storage costs are minimal for small files such as CSVs, making it a practical option for storing participant enrollment and medication data.


|Layer| Service (Cloud) | Role in Solution| Related Assignment/Module |
|-------|-----------------|-----------------|-------------------------|
|Storage|GCP Cloud Storage|Store raw uploaded CSV files |Module 6| 
|Compute|Cloud Run|Run containerized Flask API|Module 3|
|Database/SQL|Cloud SQL|Store cleaned/aggregated tables for reporting|Module 7|
