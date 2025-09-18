# **ER Diagram - Disability-Friendly Job Portal DBMS**

## **Core Entities**

### **USER**
- **user_id** (PK)
- email
- password_hash
- first_name
- last_name
- phone
- date_of_birth
- disability_type
- created_at
- updated_at

### **ACCESSIBILITY_PREFERENCES**
- **preference_id** (PK)
- **user_id** (FK)
- high_contrast_mode
- large_text_enabled
- voice_navigation_enabled
- keyboard_only_mode
- screen_reader_compatible
- font_size_preference

### **ACCOMMODATION_NEEDS**
- **accommodation_id** (PK)
- **user_id** (FK)
- flexible_hours_needed
- remote_work_required
- assistive_technology_used
- physical_workspace_adjustments
- communication_preferences
- interview_accommodations

### **SUPPORT_PERSON**
- **support_id** (PK)
- **user_id** (FK)
- support_name
- relationship
- contact_email
- contact_phone
- permission_level

### **USER_PROFILE**
- **profile_id** (PK)
- **user_id** (FK)
- skills
- experience_level
- education
- certifications
- resume_file_path
- profile_summary

### **JOB**
- **job_id** (PK)
- **employer_id** (FK)
- title
- description
- requirements
- salary_range
- location
- remote_available
- flexible_hours_offered
- disability_friendly
- accommodation_support
- posted_date
- application_deadline

### **EMPLOYER**
- **employer_id** (PK)
- company_name
- contact_email
- phone
- website
- disability_confident_status
- accessibility_rating
- location

### **APPLICATION**
- **application_id** (PK)
- **user_id** (FK)
- **job_id** (FK)
- application_date
- status
- cover_letter
- custom_message
- accommodation_requested
- accommodation_details

### **SAVED_JOBS**
- **saved_id** (PK)
- **user_id** (FK)
- **job_id** (FK)
- saved_date
- notes

### **JOB_ALERTS**
- **alert_id** (PK)
- **user_id** (FK)
- keywords
- location_preference
- salary_min
- remote_only
- alert_frequency
- is_active

## **Key Relationships**

**USER → ACCESSIBILITY_PREFERENCES** (1:1)
- One user has one set of accessibility preferences

**USER → ACCOMMODATION_NEEDS** (1:1)
- One user has one accommodation profile

**USER → SUPPORT_PERSON** (1:0..1)
- One user may have one support person

**USER → USER_PROFILE** (1:1)
- One user has one profile

**USER → APPLICATION** (1:M)
- One user can submit multiple applications

**USER → SAVED_JOBS** (1:M)
- One user can save multiple jobs

**USER → JOB_ALERTS** (1:M)
- One user can create multiple job alerts

**JOB → APPLICATION** (1:M)
- One job can receive multiple applications

**EMPLOYER → JOB** (1:M)
- One employer can post multiple jobs

## **Database Constraints**

**Primary Keys** - Each entity has a unique identifier
**Foreign Keys** - Maintain referential integrity between related tables
**NOT NULL** - Essential fields like email, disability_type cannot be empty
**UNIQUE** - Email addresses must be unique across users
**CHECK** - Status fields have predefined valid values
**DEFAULT** - Created_at timestamps default to current time

## **Indexes for Performance**

- Index on user_id for quick profile lookups
- Index on job_id for application searches
- Index on disability_type for targeted job matching
- Index on location for geographic searches
- Index on posted_date for recent job filtering

This ER diagram supports comprehensive accessibility features while maintaining efficient data relationships for the disability-friendly job portal.[1][2]

[1](https://ijireeice.com/wp-content/uploads/2025/04/IJIREEICE.2025.13450.pdf)
[2](https://ijarsct.co.in/Paper26051.pdf)
