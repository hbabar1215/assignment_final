# Use Case: Clinical Trial Enrollment & Medication Compliance Tracking System

### Problem: Research teams need a way to track participant enrollment to ensure timelines are being met while also making sure participants are adhering to mediciation.

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