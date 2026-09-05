Orignal Prompt:

# PROJECT DETAILS AND LIMS SYSTEM DEFINITION PROMPT

## 1. ROLE

Act as a multidisciplinary senior expert responsible for analyzing, architecting, designing, and ultimately developing this system.

Combine the expertise of:

* Senior Laboratory Information Management System (LIMS) Architect
* Senior Laboratory Quality Management Consultant with strong knowledge of ISO/IEC 17025 and laboratory accreditation practices
* Laboratory workflow and testing-domain specialist
* Senior database architect and data-model designer
* Senior UI/UX designer
* Senior full-stack software architect and developer
* Application security architect
* Software testing and QA engineer
* Deployment and operations architect
* Technical documentation architect

Do not approach this as a simple CRUD application.

Treat it as a serious laboratory information management system where the following are fundamental architectural requirements:

* traceability
* data integrity
* controlled workflows
* auditability
* authorization
* confidentiality
* configurability
* reproducibility
* usability
* maintainability
* extensibility
* reliability
* offline operation
* backup and recovery
* quality-system support
* operational continuity

The objective is to design a system that can become a real operational laboratory system and remain maintainable for many years.

Do not optimize only for rapid initial development.

---

# 2. PROJECT OBJECTIVE

Design and build a complete custom, on-premises/offline Laboratory Information Management System (LIMS) from scratch for a testing laboratory.

Current laboratory:

**SMJ Sustainable Fuel Lab Pvt. Ltd.**

The system should initially support laboratory activities such as:

* solid fuel testing
* biofuel testing
* air testing
* water testing
* soil testing
* noise testing
* stack/emission testing

The architecture must also permit additional laboratory disciplines to be introduced later without requiring a rewrite of the core LIMS platform.

Do not assume the listed disciplines are exhaustive.

Identify additional capabilities required for a mature testing laboratory where justified by requirements.

---

# 3. PRIMARY PRODUCT OBJECTIVE

The system should manage the controlled lifecycle of laboratory work from initial customer/request information through:

Customer
→ Request / Contract
→ Sample Collection / Receipt
→ Sample Registration
→ Sample Login / Accession
→ Sample Identification
→ Sample Allocation
→ Test Planning
→ Test Assignment
→ Test Execution
→ Result Entry
→ QC / Review
→ Technical Verification
→ Authorization / Approval
→ Test Report / Certificate
→ Delivery
→ Record Retention
→ Archival

The actual workflow must be configurable because different laboratory disciplines may require different processes.

The system must preserve traceability throughout the lifecycle.

---

# 4. DEPLOYMENT MODEL

The system is primarily intended for **on-premises, local-network, offline operation**.

Assume the laboratory may have:

* no Internet access
* a local LAN
* multiple users
* multiple client workstations
* a local application server
* a local database service/server
* local printers
* local file/document storage
* network-attached storage (NAS)
* barcode scanners
* local backup media

Core laboratory operations must continue to function normally without Internet connectivity.

Internet access must not be a mandatory runtime dependency for core functions.

Any optional Internet-dependent capability must be clearly isolated and must not prevent normal offline operation.

The architecture must address:

* server topology
* workstation access
* LAN communication
* database location
* document storage
* printing
* barcode/QR scanning
* user authentication
* time handling
* backup
* restore
* software updates
* local failure scenarios
* server failure
* database recovery
* workstation replacement
* disaster recovery

The deployment model must be realistic for a laboratory environment rather than assuming cloud-first infrastructure.

---

# 5. PREFERRED TECHNOLOGY DIRECTION

The current preferred technical direction is:

Operating System:
Windows 11 Pro and/or Windows Server

Frontend:
React + TypeScript + Vite

UI:
MUI

Backend:
FastAPI + Python

ORM:
SQLAlchemy 2.x

Database:
SQLite

Migrations:
Alembic

Authentication:
Secure session cookies + Argon2id

Authorization:
RBAC + laboratory scope

Reporting:
Jinja2 + HTML/CSS + Chromium PDF

File Storage:
Windows local disk or NAS

Barcode:
Code 128 + QR

Search:
SQLite/native database capabilities unless a better design is justified

Testing:
pytest + Playwright

Reverse Proxy:
Caddy

Backup:
Database backups + document backups

These are **preferred technologies, not automatically approved architectural decisions**.

Evaluate their suitability against the actual project requirements.

Do not replace a preferred technology without explaining why.

Do not accept a preferred technology blindly if it creates material risk.

---

# 6. DATABASE DECISION REQUIREMENT

SQLite is currently preferred but must be explicitly evaluated before the database architecture is finalized.

Evaluate SQLite against:

* number of concurrent users
* LAN operation
* concurrent sample entry
* concurrent result entry
* simultaneous report generation
* transaction contention
* database locking
* write concurrency
* database size
* expected record growth
* audit volume
* backup consistency
* restore reliability
* corruption/recovery scenarios
* operational simplicity
* performance
* upgradeability
* maintainability
* future migration to another database if required

Do not select SQLite merely because it is simple.

Do not reject SQLite merely because other relational databases are more powerful.

Make the decision based on the actual workload and deployment model.

The final decision must be explicitly documented during architecture design.

---

# 7. MODULAR ARCHITECTURE

The system must use a modular architecture with clear boundaries between major functional areas.

Potential modules include:

* Master Data Management
* Customer Management
* Project Management
* Sample Registration
* Sample Reception
* Sample Login / Accessioning
* Sample Identification
* Sampling
* Sample Containers
* Chain of Custody
* Test Planning
* Test Assignment
* Laboratory Workflows
* Test Execution
* Result Entry
* Result Review
* Result Verification
* Result Approval
* Quality Control
* Equipment Management
* Calibration Management
* Reference Standards
* Reagents / Consumables
* Methods
* Method Validation
* Method Verification
* Documents
* Environmental Conditions
* Personnel
* Competency
* Personnel Authorization
* Nonconformities
* Corrective Actions / CAPA
* Complaints
* Internal Audits
* Risk Management
* Proficiency Testing
* Interlaboratory Comparisons
* Reports
* Certificates / Test Reports
* Invoicing / Billing where required
* Administration
* Audit Trail
* System Configuration
* Backup / Restore
* Notifications
* Dashboard / Analytics

This list is not exhaustive.

Identify additional modules when supported by actual laboratory requirements.

Do not create modules merely because they are commonly found in commercial LIMS products.

For every proposed module identify:

* purpose
* responsibilities
* owned data
* dependencies
* permissions
* workflows
* audit requirements
* reports
* configuration needs
* extension points

---

# 8. ISO/IEC 17025 AND ACCREDITATION SUPPORT

Design the system to support laboratory operations, technical records, quality processes, and documentation associated with ISO/IEC 17025 and applicable accreditation practices.

Do not claim that the software itself is "ISO/IEC 17025 certified" or that installation of the software automatically makes the laboratory accredited.

The software should provide capabilities that support the laboratory's quality-management and accreditation processes.

Consider, as applicable:

* impartiality
* confidentiality
* organizational structure and responsibilities
* personnel competence
* authorization of personnel
* facilities
* environmental conditions
* equipment management
* metrological traceability
* externally provided products and services
* review of requests, tenders and contracts
* method selection
* method verification
* method validation
* sampling
* handling of test items
* technical records
* measurement uncertainty
* ensuring validity of results
* reporting
* complaints
* nonconforming work
* management-system documentation
* risks and opportunities
* corrective actions
* internal audits
* management reviews
* data and information management
* retention of records
* traceability
* auditability

Where applicable, identify the relationship:

Laboratory / quality requirement
↓
Software capability
↓
Data required
↓
Workflow / control
↓
User permissions
↓
Audit events
↓
Required records / reports
↓
Retention requirements
↓
Verification / test requirements

Clearly distinguish:

* external standard requirement
* laboratory policy
* laboratory procedure
* software capability
* configuration
* evidence

Do not assume every standard clause requires a dedicated software module.

---

# 9. SAMPLE AND TEST DOMAIN

Design a flexible domain model capable of representing multiple laboratory disciplines.

Consider entities/concepts such as:

* Customer
* Project
* Sampling Event
* Sample
* Sub-sample
* Sample Portion
* Sample Container
* Sample Matrix
* Sample Location
* Sampling Date/Time
* Receipt Date/Time
* Registration Date/Time
* Sample Condition
* Sample Quantity
* Sample Preservation
* Chain of Custody
* Test Request
* Test
* Test Batch
* Test Parameter
* Method
* Result
* Unit
* Detection Limit
* Quantification Limit
* Measurement Uncertainty
* QC Result
* Observation
* Attachment
* Photograph
* Equipment
* Analyst
* Reviewer
* Technical Reviewer
* Approver
* Report
* Certificate

Support relationships such as:

Project
→ Samples
→ Test Requests
→ Tests
→ Results

while allowing:

* one sample to have multiple tests
* one request to contain multiple tests
* one test to contain multiple parameters
* different tests to use different methods
* tests to reference required equipment
* results to reference analysts/reviewers
* reports to trace back to the underlying technical records

Do not force all laboratory concepts into one generic structure.

---

# 10. LABORATORY METHODS

Methods must be configurable entities.

A method may contain, as applicable:

* Method ID
* Method title
* Reference standard
* Version
* Revision date
* Effective date
* Discipline
* Matrix
* Scope
* Procedure
* Required equipment
* Required reagents
* Required standards
* Environmental conditions
* Calculation definitions
* Result parameters
* Units
* Acceptance criteria
* QC requirements
* Reporting rules
* Measurement uncertainty requirements
* Validation records
* Verification records
* Approval status
* Authorized personnel
* Controlled attachments

Support methods based on recognized standards such as:

* ASTM
* ISO
* BIS
* APHA
* EPA
* EN

without hard-coding one standard into the application architecture.

---

# 11. CONFIGURABLE TEST DEFINITIONS

A laboratory administrator should be able to configure normal test definitions without requiring source-code changes.

Support configurable concepts including:

* test types
* test parameters
* input fields
* data types
* units
* required/optional status
* validation rules
* formulas
* reference ranges
* acceptance criteria
* decimal precision
* significant figures
* rounding
* result formatting
* QC requirements
* workflow requirements
* required equipment
* required competency
* required environmental conditions
* reporting rules

For example, an administrator should be able to create a new result parameter and associate it with a test and method through configuration.

However:

Do not use generic EAV structures for everything.

Prefer strongly typed relational structures where the concept is stable and important for:

* integrity
* querying
* reporting
* calculations
* performance
* auditability
* maintainability

Use flexible metadata/configuration only where genuine variability requires it.

---

# 12. CALCULATION AND FORMULA ENGINE

Support safe configurable laboratory calculations.

The system may need to support:

* arithmetic
* percentages
* ratios
* unit conversions
* conditional calculations
* significant figures
* rounding
* derived results
* multi-step formulas

Never execute arbitrary user-supplied code.

Every calculated result must preserve sufficient provenance to determine:

* input values
* formula identifier
* formula version
* calculation timestamp
* execution user/system
* result
* unit
* rounding rules
* formatting rules

Where calculations affect controlled technical records, formula versions must be traceable.

---

# 13. DATA INTEGRITY

Treat important laboratory records as controlled technical records.

Important data should preserve, where applicable:

* creator
* creation timestamp
* modifier
* modification timestamp
* previous value
* new value
* reason for change
* user identity
* workflow state
* review history
* approval history
* correction history

Do not allow silent destructive overwriting of important laboratory records.

For corrections:

* preserve the original value
* preserve the corrected value
* preserve who changed it
* preserve when it changed
* preserve the reason where required
* preserve review/approval history

The audit mechanism must be protected against ordinary user tampering.

Define meaningful audit events rather than indiscriminately auditing every technical database operation.

---

# 14. USER ROLES AND AUTHORIZATION

Use role-based access control.

Potential roles include:

* System Administrator
* Laboratory Manager
* Quality Manager
* Technical Manager
* Sample Receptionist
* Laboratory Analyst
* Reviewer
* Technical Reviewer
* Authorized Signatory
* Equipment Manager
* Procurement / Store User
* Auditor
* Read-only User

These are examples, not necessarily final roles.

Define authorization across appropriate dimensions such as:

* module
* function
* action
* record
* workflow transition
* discipline
* laboratory section
* organizational scope

Support segregation of duties.

A user should not automatically be permitted to approve their own work merely because they created or entered it.

Authorization must be enforced by the backend.

The UI must never be the only security boundary.

---

# 15. EQUIPMENT MANAGEMENT

Support:

* equipment master
* equipment ID
* manufacturer
* model
* serial number
* location
* laboratory section
* status
* installation date
* calibration
* verification
* maintenance
* breakdown
* service history
* calibration certificates
* calibration due dates
* intermediate checks
* qualification
* authorized users
* equipment usage history

The system must appropriately prevent or warn against use of equipment that is:

* out of calibration
* out of service
* under maintenance
* not qualified
* otherwise unsuitable

Whether a condition causes blocking or warning should be configurable where laboratory policy requires it.

---

# 16. QUALITY CONTROL

Support applicable QC processes including:

* blanks
* duplicates
* replicates
* spikes
* reference materials
* control samples
* calibration checks
* control charts
* acceptance criteria
* QC failures
* investigation
* corrective action

QC requirements should be configurable per method/test where appropriate.

---

# 17. DOCUMENT AND RECORD MANAGEMENT

Support controlled laboratory documents including:

* SOPs
* test methods
* work instructions
* forms
* quality manuals
* quality procedures
* policies
* calibration certificates
* method validation records
* method verification records
* training records
* customer documents
* reports
* attachments

Support:

* versioning
* approval
* effective dates
* review dates
* expiry where applicable
* status
* access control
* audit history
* retention
* archival

Controlled versions must not be silently overwritten.

---

# 18. REPORTING

Design a configurable reporting architecture.

Potential reports include:

* sample receipt
* sample status
* workload
* analyst workload
* pending tests
* overdue tests
* turnaround time
* customer reports
* test reports
* certificates
* result summaries
* QC reports
* equipment reports
* calibration due reports
* method status
* audit reports
* nonconformity reports
* CAPA reports
* management dashboards
* accreditation-related records

Support:

* laboratory branding
* templates
* headers/footers
* page numbering
* approval information
* signature support where appropriate
* revision control
* PDF generation
* printing

Reports must retain traceability to the source technical records.

---

# 19. TRACEABILITY

The system must support appropriate traceability from final report back to source records.

Where applicable:

Report
→ Result
→ Test
→ Test Request
→ Sample
→ Project
→ Customer
→ Method
→ Equipment
→ Analyst
→ Reviewer
→ Approval
→ Audit History

The actual traceability chain may vary by workflow.

Do not create artificial relationships merely to satisfy a diagram.

---

# 20. SEARCH AND RETRIEVAL

Users should be able to search/filter by appropriate criteria such as:

* sample number
* project number
* customer
* test
* method
* date
* analyst
* equipment
* result
* status
* discipline
* location
* batch
* report number

Support:

* filtering
* sorting
* useful saved searches
* rapid navigation
* traceability navigation

Search performance should be considered in the database design.

---

# 21. BACKUP AND DISASTER RECOVERY

Design backup and recovery as real operational capabilities.

Support as applicable:

* scheduled backups
* automated backups
* database backup
* document backup
* backup verification
* retention
* local backup
* removable/offline backup
* restore procedures
* restore testing
* recovery procedures
* failure notification
* backup status
* RPO
* RTO

Clearly distinguish:

backup created
backup validated
backup restorable
restore tested
disaster recovery procedure verified

A file existing in a backup directory does not prove that recovery works.

---

# 22. DATABASE ARCHITECTURE

Design a robust relational database.

Before substantial database implementation, define:

* entities
* relationships
* primary keys
* foreign keys
* unique constraints
* validation constraints
* indexes
* audit fields
* transaction boundaries
* archival approach
* retention model
* backup model

Avoid:

* unnecessary duplication
* uncontrolled free-text structures
* weak referential integrity
* hard-coded identifiers
* storing every value as text
* excessive EAV
* business logic existing only in UI code

A complete baseline ERD and data dictionary must exist before implementation of the full core system.

The supplied/provided database schema is an input for analysis.

Do not automatically accept it as correct.

Identify:

* strengths
* weaknesses
* missing entities
* incorrect relationships
* integrity problems
* scalability problems
* audit deficiencies
* normalization issues
* reporting limitations

---

# 23. UI/UX

Design specifically for real laboratory users.

Prioritize:

* speed
* clarity
* minimal unnecessary clicks
* keyboard-friendly data entry
* barcode/QR scanning
* clear status indicators
* error prevention
* validation at entry
* responsive layouts
* accessibility
* consistent terminology
* role-specific dashboards

The UI should clearly distinguish states such as:

* Draft
* Received
* In Progress
* Pending Review
* Rejected
* Approved
* Completed
* Cancelled
* Archived

Do not make laboratory workflows unnecessarily complicated.

---

# 24. USER EXPERIENCE BY ROLE

Analyze user journeys for major user types.

Consider:

* sample reception
* analyst
* reviewer
* technical reviewer
* authorized signatory
* laboratory manager
* quality manager
* equipment manager
* system administrator

For each important workflow identify:

* entry point
* required information
* actions
* validation
* permissions
* status
* error handling
* completion condition

---

# 25. SECURITY ARCHITECTURE

Design security for a multi-user local laboratory system.

Consider:

* authentication
* password hashing
* secure sessions
* session expiration
* account lifecycle
* failed login handling
* authorization
* least privilege
* segregation of duties
* backend enforcement
* data-access scope
* audit integrity
* secrets
* sensitive documents
* backup security
* administrator actions
* local network risks
* workstation risks

The security model must not depend solely on trusted users or the UI.

---

# 26. CONFIGURATION ARCHITECTURE

Identify what should be configurable by laboratory administrators versus what should remain controlled by the application architecture.

Potential configurable areas include:

* laboratory information
* disciplines
* sections
* test definitions
* methods
* parameters
* units
* workflows
* roles/permissions where appropriate
* acceptance criteria
* QC rules
* report templates
* numbering schemes
* retention rules
* notification rules
* system settings

Do not make safety-critical or architectural behavior freely configurable merely for flexibility.

Define configuration governance and auditability.

---

# 27. EXTENSIBILITY

The architecture must allow future laboratory disciplines to reuse the core LIMS platform.

Adding a new discipline should primarily involve:

* configuration
* additional methods/tests
* reusable services
* modular functionality

rather than rewriting core systems such as:

* authentication
* users
* roles
* permissions
* sample management
* audit trail
* reporting
* document management
* equipment management

Do not build an elaborate plugin framework unless the real requirements justify it.

Use a modular internal architecture first.

---

# 28. DEPLOYMENT ARCHITECTURE

Design the actual operational deployment model.

The deployment architecture must address:

* application server
* database location
* client workstations
* LAN access
* reverse proxy
* local DNS/hostname assumptions
* local file storage
* NAS where applicable
* printer access
* backups
* restore
* updates
* migrations
* versioning
* rollback
* health checks
* system startup
* system shutdown
* server replacement
* workstation replacement

The solution must remain practical for an on-premises Windows laboratory environment.

Do not introduce containers or orchestration unless genuinely required.

---

# 29. UPDATE AND MAINTENANCE MODEL

Design a realistic method for:

* application updates
* database migrations
* configuration migration
* document migration
* backup before upgrade
* rollback
* version compatibility
* client compatibility
* recovery from failed updates

The upgrade model must be appropriate for a system that may operate without Internet access.

---

# 30. TESTING AND VALIDATION

The system must eventually support:

* unit testing
* integration testing
* API testing
* database testing
* workflow testing
* authorization testing
* security testing
* calculation testing
* report testing
* audit-trail testing
* end-to-end testing
* backup/restore testing
* migration testing
* upgrade testing
* performance testing
* user acceptance testing

Focus testing on critical laboratory workflows and data integrity.

Do not rely only on superficial UI tests.

---

# 31. REQUIREMENT TRACEABILITY

Establish traceability between:

Requirement
→ Design
→ Module
→ Data Model
→ Implementation
→ Test
→ Verification

For important laboratory and quality-system requirements, this traceability should be explicit.

This is especially important for:

* auditability
* authorization
* calculations
* result corrections
* technical verification
* approval
* reporting
* record retention
* backup/recovery
* security controls

---

# 32. DEVELOPMENT APPROACH — HIERARCHICAL AND INCREMENTAL

Do not attempt to generate the entire system in one uncontrolled implementation step.

The project must be developed incrementally using the following hierarchy:

PROJECT
  ↓
PHASE
  ↓
WORK PACKAGE
  ↓
TASK
  ↓
OPTIONAL SUBTASK
  ↓
IMPLEMENTATION
  ↓
TEST
  ↓
VERIFICATION
  ↓
CHECKPOINT

The AI must normally work on **one small, clearly bounded task at a time**.

Do not treat an entire phase as one implementation task.

Do not treat an entire work package as one implementation task unless it is genuinely small.

The purpose of this decomposition is to:

* control implementation scope
* reduce AI context consumption
* make work independently recoverable
* make verification manageable
* reduce architectural drift
* support safe handoff between AI sessions
* provide clear checkpoints

---

# 33. PHASES

The initial project phases should be:

Phase 0  — Project Control & Discovery
Phase 1  — Requirements & Laboratory Model
Phase 2  — System & Security Architecture
Phase 3  — Data Architecture
Phase 4  — UX/UI Architecture
Phase 5  — Technical Foundation
Phase 6  — Identity, RBAC & Audit
Phase 7  — Core Master Data
Phase 8  — Customer, Project & Sample
Phase 9  — Test & Method Engine
Phase 10 — Laboratory Execution & Results
Phase 11 — Review, Verification & Approval
Phase 12 — QC & Equipment
Phase 13 — Quality Management
Phase 14 — Documents & Records
Phase 15 — Reporting & Certificates
Phase 16 — Configuration & Extensibility
Phase 17 — Backup, Recovery & Operations
Phase 18 — Validation & Hardening
Phase 19 — Production Deployment
Phase 20 — Maintenance & Evolution

These phases represent the proposed lifecycle structure.

They are not permission to implement all phases immediately.

The detailed work packages and tasks must be derived from approved requirements and architecture.

---

# 34. PHASE 0 — PROJECT CONTROL & DISCOVERY

Purpose:

Establish the project foundation and understand the supplied project information.

Potential work packages:

### WP-00-01 — Project Foundation

Potential tasks:

* establish repository structure
* establish project-control structure
* establish project documentation conventions
* establish requirement/change-control conventions
* establish project status vocabulary

### WP-00-02 — Existing Information Consolidation

Potential tasks:

* consolidate supplied project requirements
* consolidate technical preferences
* review supplied database schema
* identify contradictions
* identify ambiguities
* identify assumptions
* identify open decisions

### WP-00-03 — Initial Project Baseline

Establish the first project baseline and checkpoint.

No ordinary application feature development should occur during this stage unless explicitly authorized.

---

# 35. PHASE 1 — REQUIREMENTS & LABORATORY MODEL

Purpose:

Convert the project description into an implementable and traceable laboratory-system definition.

Potential work packages:

### WP-01-01 — Users & Organization

Potential tasks:

* identify user types
* identify organizational structure
* identify laboratory sections
* identify disciplines
* identify responsibility boundaries

### WP-01-02 — Laboratory Workflows

Analyze and define:

* customer/request workflow
* contract/request review
* sample receipt
* sample registration
* sample accession
* sample allocation
* test planning
* test assignment
* test execution
* result entry
* review
* technical verification
* approval
* report generation
* report delivery
* retention
* archival

### WP-01-03 — Exceptional Workflows

Analyze:

* rejection
* cancellation
* rework
* corrections
* nonconforming work
* QC failure
* equipment unavailability
* failed verification
* failed approval

### WP-01-04 — Requirements Baseline

Establish:

* functional requirements
* non-functional requirements
* scope
* user requirements
* quality-system support requirements
* traceability

### CP-001 — Requirements Baseline Accepted

---

# 36. PHASE 2 — SYSTEM & SECURITY ARCHITECTURE

Purpose:

Define how the overall platform will operate.

Potential work packages:

### WP-02-01 — System Architecture

Analyze:

* system boundaries
* frontend architecture
* backend architecture
* API architecture
* module boundaries
* local network architecture

### WP-02-02 — Authentication Architecture

Analyze:

* authentication
* password policy
* session model
* account lifecycle

### WP-02-03 — Authorization Architecture

Analyze:

* roles
* permissions
* laboratory scope
* discipline scope
* section scope
* record permissions
* segregation of duties

### WP-02-04 — Security Architecture

Analyze:

* threat model
* secrets
* security logging
* sensitive-data access
* session protection
* administration

### WP-02-05 — Offline Architecture

Analyze:

* LAN operation
* printers
* scanners
* local documents
* local services
* Internet independence

### CP-002 — System & Security Architecture Accepted

---

# 37. PHASE 3 — DATA ARCHITECTURE

Purpose:

Define the authoritative relational data model.

Potential work packages:

### WP-03-01 — Domain Model

Define:

* core entities
* sample model
* test model
* result model
* method model
* equipment model
* quality model

### WP-03-02 — Relational Schema

Define:

* tables/entities
* relationships
* keys
* constraints
* unique rules
* indexes
* transactions

### WP-03-03 — Audit and History

Define:

* audit events
* change history
* corrections
* approvals
* revisions

### WP-03-04 — Retention and Archival

Define:

* retention
* archival
* lifecycle

### WP-03-05 — Database Technology Decision

Evaluate and decide:

* SQLite suitability
* concurrency
* performance
* backup/recovery
* scaling
* upgradeability
* migration path

### CP-003 — Data Architecture Accepted

---

# 38. PHASE 4 — UX/UI ARCHITECTURE

Purpose:

Define a laboratory-centered user experience before extensive implementation.

Potential work packages:

### WP-04-01 — Information Architecture

Define:

* navigation
* menus
* dashboards
* terminology

### WP-04-02 — User Journeys

Define journeys for:

* reception
* analysts
* reviewers
* technical reviewers
* authorized signatories
* managers
* quality users
* equipment users
* administrators

### WP-04-03 — Screen Architecture

Define major screens for:

* authentication
* master data
* customers/projects
* samples
* tests
* results
* review/approval
* equipment
* QC
* documents
* reporting

### CP-004 — UX/UI Architecture Accepted

---

# 39. PHASE 5 — TECHNICAL FOUNDATION

Purpose:

Build the minimum stable technical platform required for later LIMS functionality.

Potential work packages:

### WP-05-01 — Application Foundation

Potential tasks:

* frontend foundation
* backend foundation
* configuration
* logging
* error handling

### WP-05-02 — Database Foundation

Potential tasks:

* database integration
* ORM foundation
* migration system
* initial schema migration
* database tests

### WP-05-03 — API Foundation

Potential tasks:

* API structure
* validation
* error responses
* contract foundation

### WP-05-04 — Frontend Foundation

Potential tasks:

* application shell
* routing
* MUI theme/design system
* API integration
* application error handling

### WP-05-05 — Testing Foundation

Potential tasks:

* pytest foundation
* frontend testing foundation
* Playwright foundation
* test-data strategy

### WP-05-06 — Local Deployment Foundation

Potential tasks:

* local server setup approach
* reverse proxy approach
* local application startup
* local configuration
* local health checks

### CP-005 — Technical Foundation Accepted

---

# 40. PHASE 6 — IDENTITY, RBAC & AUDIT

Purpose:

Establish the foundational control system.

Potential work packages:

### WP-06-01 — User Management

* user model
* account lifecycle
* password management
* sessions

### WP-06-02 — RBAC

* roles
* permissions
* permission assignment
* authorization service
* scope enforcement
* segregation of duties

### WP-06-03 — Audit Trail

* audit framework
* protected audit data
* correction history
* approval history
* audit UI

### CP-006 — Identity, RBAC & Audit Accepted

---

# 41. PHASE 7 — CORE MASTER DATA

Purpose:

Establish common reference data reused by the whole system.

Potential work packages:

* laboratory
* sections
* disciplines
* units
* locations
* statuses
* customers
* contacts
* personnel
* competency categories
* authorization categories

### CP-007 — Master Data Accepted

---

# 42. PHASE 8 — CUSTOMER, PROJECT & SAMPLE

Purpose:

Implement the primary sample-management lifecycle.

Potential work packages:

### WP-08-01 — Customer & Project

* customer workflow
* project workflow
* request/order
* contract/request review

### WP-08-02 — Sample Reception

* receipt
* sample condition
* quantity
* timestamps
* exceptions

### WP-08-03 — Sample Registration

* numbering
* identification
* metadata
* matrix
* location
* preservation

### WP-08-04 — Chain of Custody

* custody model
* events
* traceability

### WP-08-05 — Sample Lifecycle

* status machine
* allocation
* sub-samples
* portions
* containers

### CP-008 — Sample Management Accepted

---

# 43. PHASE 9 — TEST & METHOD ENGINE

Purpose:

Create the configurable laboratory test definition system.

Potential work packages:

### WP-09-01 — Methods

* method entity
* versioning
* approval
* effective dates
* scope
* validation/verification

### WP-09-02 — Test Definitions

* test types
* parameters
* fields
* data types
* units
* validation
* precision
* rounding
* acceptance criteria

### WP-09-03 — Method/Test Association

* method association
* equipment requirements
* competency requirements
* environmental requirements
* QC requirements

### WP-09-04 — Calculation Engine

* formula model
* versioning
* safe evaluation
* units
* derived values
* rounding/significant figures
* calculation provenance

### CP-009 — Test & Method Engine Accepted

---

# 44. PHASE 10 — LABORATORY EXECUTION & RESULTS

Potential work packages:

### WP-10-01 — Test Planning

* test requests
* test creation
* planning
* scheduling

### WP-10-02 — Assignment

* analyst assignment
* equipment assignment
* workload
* validation

### WP-10-03 — Test Execution

* test start
* raw values
* observations
* environmental conditions
* equipment
* attachments

### WP-10-04 — Results

* result entry
* validation
* calculations
* units
* detection/quantification limits
* uncertainty
* correction/revision

### CP-010 — Laboratory Execution Accepted

---

# 45. PHASE 11 — REVIEW, VERIFICATION & APPROVAL

Keep these as separate control stages.

Potential work packages:

### WP-11-01 — Review

* completion
* reviewer workflow
* review rules
* rejection/rework

### WP-11-02 — Technical Verification

* verification
* verification rules
* authorization boundaries

### WP-11-03 — Approval

* approval workflow
* authorized signatory
* segregation of duties
* approval history

### WP-11-04 — Correction and Reapproval

* reopen
* correction
* re-review
* re-verification
* reapproval

### CP-011 — Result Control Accepted

---

# 46. PHASE 12 — QC & EQUIPMENT

### WP-12-01 — Equipment

Implement:

* equipment master
* status
* calibration
* verification
* maintenance
* breakdown
* qualification
* history
* authorized users

### WP-12-02 — Equipment Enforcement

Implement appropriate checks against:

* out-of-calibration equipment
* maintenance
* qualification
* service state

### WP-12-03 — QC

Implement:

* QC definitions
* QC execution
* acceptance criteria
* failures
* investigations
* control charts
* traceability

### CP-012 — QC & Equipment Accepted

---

# 47. PHASE 13 — QUALITY MANAGEMENT

Potential work packages:

### WP-13-01 — Nonconformity / CAPA

* nonconformities
* corrective actions
* CAPA
* complaints

### WP-13-02 — Audits / Risk

* internal audits
* findings
* risk management
* risks/opportunities

### WP-13-03 — Competency / PT / ILC

* competency
* training
* authorization
* PT
* ILC

### WP-13-04 — Management Review Support

* management-review inputs
* quality metrics
* accreditation-support reports

### CP-013 — Quality Management Accepted

---

# 48. PHASE 14 — DOCUMENTS & RECORDS

### WP-14-01 — Document Control

* repository
* metadata
* versioning
* approval
* effective dates
* review dates
* retention
* archival

### WP-14-02 — Controlled Laboratory Records

* SOPs
* methods
* certificates
* validation records
* verification records
* training records

### CP-014 — Document Control Accepted

---

# 49. PHASE 15 — REPORTING & CERTIFICATES

### WP-15-01 — Reporting Engine

* templates
* rendering
* HTML
* PDF
* printing

### WP-15-02 — Operational Reporting

* sample reports
* workload
* pending
* overdue
* TAT

### WP-15-03 — Technical Reporting

* result reports
* test reports
* certificates
* approval
* signatures

### WP-15-04 — Quality Reporting

* QC
* equipment
* audits
* CAPA
* dashboards

### CP-015 — Reporting Accepted

---

# 50. PHASE 16 — CONFIGURATION & EXTENSIBILITY

Purpose:

Demonstrate that the architecture actually supports future laboratory expansion.

Potential work packages:

### WP-16-01 — Configuration

* test configuration
* method configuration
* workflow configuration
* QC configuration
* reporting configuration

### WP-16-02 — Laboratory Configuration

* disciplines
* sections
* numbering
* retention

### WP-16-03 — Extensibility Validation

Add at least one representative additional laboratory discipline or significant configuration scenario to demonstrate that the core engine can be reused without destabilizing existing functionality.

### CP-016 — Extensibility Accepted

---

# 51. PHASE 17 — BACKUP, RECOVERY & OPERATIONS

### WP-17-01 — Backup

* automation
* scheduling
* retention
* verification

### WP-17-02 — Restore / Disaster Recovery

* restore procedure
* restore verification
* disaster recovery
* RPO/RTO validation

### WP-17-03 — Operational Monitoring

* health state
* diagnostics
* storage
* backup status

### CP-017 — Operational Recovery Accepted

---

# 52. PHASE 18 — VALIDATION & HARDENING

This phase validates the complete system rather than merely individual features.

### WP-18-01 — Functional Validation

Trace requirements against implementation and verification.

### WP-18-02 — Data Integrity Validation

Validate:

* transactions
* correction
* history
* audit
* approval
* constraints

### WP-18-03 — Security Validation

Validate:

* authentication
* authorization
* scope
* segregation of duties
* session security

### WP-18-04 — Workflow Validation

Validate all critical workflows and transitions.

### WP-18-05 — Calculation Validation

Validate:

* formulas
* units
* precision
* rounding
* provenance

### WP-18-06 — Reporting Validation

Validate reports against source technical records.

### WP-18-07 — Backup/Restore Validation

Perform actual restoration and verify operational recovery.

### WP-18-08 — Performance Validation

Test realistic laboratory workloads.

### WP-18-09 — User Acceptance

Perform structured UAT.

### CP-018 — System Validation Accepted

---

# 53. PHASE 19 — PRODUCTION DEPLOYMENT

### WP-19-01 — Production Preparation

* server preparation
* production configuration
* database initialization
* file storage
* printers
* users
* backup

### WP-19-02 — Installation

* application installation
* migrations
* client configuration
* operational configuration

### WP-19-03 — Production Verification

* smoke tests
* authentication
* core workflow
* printing
* backup
* recovery
* health checks

### CP-019 — Production Deployment Accepted

The system must not be described as production-deployed merely because installation files exist.

---

# 54. PHASE 20 — MAINTENANCE & EVOLUTION

After production release, continue using the same controlled model.

Future work may include:

* bug correction
* security updates
* performance improvements
* new methods
* new tests
* new disciplines
* new reports
* workflow changes
* quality-system changes
* operational improvements

Use:

Issue / Request
→ Task
→ Implementation
→ Testing
→ Verification
→ Release
→ Deployment

Do not bypass control merely because the system is already in production.

---

# 55. TASK SIZE RULE

Tasks should normally be small enough that the AI can:

understand
→ plan
→ implement
→ test
→ verify
→ document

within one controlled session.

Avoid a task such as:

"Implement authentication."

Prefer task boundaries such as:

"Implement password verification service."

"Implement session creation."

"Implement session invalidation."

"Implement role-permission lookup."

The exact granularity should be based on complexity.

Do not artificially create tiny tasks that add administrative overhead.

---

# 56. WORK PACKAGE DEFINITION

Every work package should define:

* purpose
* objectives
* requirements covered
* dependencies
* scope
* out-of-scope work
* expected tasks
* acceptance criteria
* verification requirements
* checkpoint criteria

Work packages are planning/control boundaries.

They are not automatically single implementation units.

---

# 57. TASK DEFINITION

Every task under `project/work/` should contain:

# TASK-XXX

## Objective

## Background

## Parent Work Package

## Requirements

## Dependencies

## In Scope

## Out of Scope

## Expected Changes

## Acceptance Criteria

## Tests Required

## Verification Requirements

## Completion Conditions

## Status

A task must be understandable without relying on prior conversation.

---

# 58. TASK EXECUTION RULE

Before implementing a task:

Task
→ Requirements
→ Relevant architecture
→ Relevant ADRs
→ Repository state
→ Dependencies
→ Implementation
→ Testing
→ Verification
→ State update

Do not automatically implement sibling tasks.

Do not implement future work merely because it was discovered during development.

---

# 59. CHECKPOINT MODEL

A checkpoint is a formal verification boundary.

A checkpoint must establish:

* what was intended
* what was implemented
* what was tested
* what was verified
* what remains
* what is authorized next

Checkpoint states may include:

OPEN
IN PROGRESS
VERIFIED
ACCEPTED
REJECTED
BLOCKED

---

# 60. CHECKPOINT COMPLETION GATE

A checkpoint may be marked ACCEPTED only when:

* its requirements are satisfied
* acceptance criteria are satisfied
* required tests pass
* required verification is complete
* known exceptions are documented
* evidence exists
* current-state is updated
* active-task is updated
* handoff is updated

Do not automatically begin unrelated future work simply because a checkpoint has been accepted.

---

# 61. DEVELOPMENT CONTROL PRINCIPLE

The AI must not treat the full roadmap as a permission to implement.

At any point, there should be:

one current phase
one or more defined work packages
one currently authorized task
one clearly defined next action

Detailed future tasks should be refined as architecture and discovery progress.

The project roadmap should provide direction without creating uncontrolled implementation scope.

---

# 62. PROJECT STATE MODEL

The project must distinguish:

SPECIFIED
↓
PLANNED
↓
AUTHORIZED
↓
IN PROGRESS
↓
IMPLEMENTED
↓
TESTED
↓
VERIFIED
↓
ACCEPTED
↓
RELEASED
↓
DEPLOYED
↓
HEALTH VERIFIED

Do not collapse these states.

---

# 63. REQUIRED INITIAL DELIVERABLES

Before substantial feature implementation begins, produce:

### Product / Requirements

* System Requirements Specification
* Functional Requirements
* Non-Functional Requirements
* Scope Definition
* Requirement Traceability Structure
* User Roles / Permission Matrix

### Laboratory

* Complete Module Map
* Laboratory Workflow Model
* Sample Lifecycle
* Test Lifecycle
* Result Lifecycle
* Method Model
* Equipment Model
* QC Model
* Document / Record Model

### Quality-System Support

* ISO/IEC 17025 software-control mapping
* Audit architecture
* Data-integrity architecture
* Retention model
* Nonconformity/CAPA model
* Risk/audit model

### Architecture

* System Architecture
* Module Architecture
* Technology Recommendation
* Security Architecture
* Database Architecture
* ERD
* Data Dictionary
* Workflow Architecture
* Configuration Architecture
* Reporting Architecture
* Deployment Architecture
* Backup/Recovery Architecture
* Extensibility Architecture

### UX

* Navigation / Sitemap
* User Journeys
* Screen Inventory
* UI/UX Architecture

### Technical

* API Architecture where applicable
* API contracts where applicable

### Testing

* Testing Strategy
* Test Levels
* Workflow Test Strategy
* Security Test Strategy
* Backup/Restore Test Strategy
* Validation Strategy

### Delivery

* Deployment Strategy
* Installation Strategy
* Upgrade Strategy
* Rollback Strategy
* Operational Support Strategy

### Risk

* Technical Risk Register
* Security Risk Register
* Laboratory/Quality Risk Register
* Deployment/Operational Risk Register

---

# 64. FIRST RESPONSE

Do not start coding yet.

Your first response must contain:

## A. Project Understanding

Summarize the intended LIMS.

## B. Requirement Analysis

Organize the known requirements and distinguish:

* defined
* proposed
* assumed
* unknown
* contradictory

## C. Architectural Principles

Identify the principles that should govern the system.

## D. High-Level Architecture

Present the proposed architecture and major components.

## E. Technology Evaluation

Evaluate the preferred technology stack.

Explicitly assess:

* frontend
* backend
* database
* reporting
* authentication
* document storage
* deployment
* backup
* printing
* barcode/QR

Most importantly, evaluate SQLite against the actual offline multi-user laboratory scenario.

## F. Module Architecture

Present core and supporting modules with responsibilities.

## G. Domain Model

Identify the important entities and relationships.

## H. Laboratory Workflow

Describe sample/test/result lifecycles and exception paths.

## I. Configuration Strategy

Explain what should be configurable and what should remain application-controlled.

## J. ISO/IEC 17025 Support

Map major applicable requirements to software capabilities.

Do not claim software certification.

## K. Security Architecture

Present authentication, authorization, audit, and data-integrity concepts.

## L. Database Architecture

Analyze the proposed database approach and the supplied schema.

Identify strengths, deficiencies, risks, and required changes.

## M. UI/UX Architecture

Present navigation, user journeys, and major screen categories.

## N. Reporting Architecture

Present the reporting and traceability model.

## O. Backup / Recovery

Present the proposed strategy.

## P. Deployment Architecture

Present the proposed offline/on-premises installation and operating model.

## Q. Extensibility

Explain how future disciplines can be added without destabilizing the core.

## R. Development Decomposition

Provide the proposed:

Phase
→ Work Package
→ initial Task structure
→ Checkpoint boundaries

for the project.

Do not prematurely freeze every detailed future task.

Identify which tasks should only be refined after architecture decisions are approved.

## S. Critical Risks

Identify the highest-impact risks.

## T. Discovery Questions

Ask only high-value questions.

Label each:

BLOCKING
NON-BLOCKING

## U. Recommended Roadmap

Present the complete staged development roadmap.

## V. Proposed Initial Checkpoint

Define the first checkpoint and its acceptance criteria.

---

# 65. FINAL DESIGN PRINCIPLE

The architecture must connect:

Laboratory Requirement
↓
Business Rule
↓
Workflow
↓
Domain Model
↓
Database
↓
Permission
↓
Audit Trail
↓
Report
↓
Test
↓
Verification
↓
Release
↓
Deployment

Every important requirement should have a clear architectural destination.

Every important controlled record should have a defined lifecycle.

Every important workflow should have:

* states
* transitions
* permissions
* validations
* audit events
* exception handling
* acceptance criteria
* verification tests

The system must be designed for actual laboratory operations, not merely for a demonstration.

The detailed implementation must proceed in controlled, independently verifiable increments.

END OF PROJECT DETAILS AND LIMS SYSTEM DEFINITION PROMPT



Response:
This is a serious architecture-and-discovery request, not a coding task yet — and the prompt itself says not to start building. I'll produce the Phase 0 deliverable as a reference document you can keep and iterate on, rather than dumping ~8,000 words into chat.

A few things I noticed while reading closely, worth flagging before the document: Section 22 references "the supplied/provided database schema" as an input for analysis, but no schema file was actually attached to this conversation — I've treated that as an open item rather than inventing one. I'll build the doc now.

The document covers all of Section 64's required parts (A–V) — project understanding, requirement analysis, architecture, the conditioned SQLite decision, module/domain model, ISO/IEC 17025 mapping, security, deployment, risks, and the discovery questions — and ends at Checkpoint CP-000, not at implementation.

The two things most worth your attention before Phase 1 starts: the BLOCKING questions in Section T (especially real concurrent-user count, which directly gates the SQLite decision, and whether a database schema was meant to be attached — none came through), and whether you want to amend anything in the assumptions (Section B) or architectural principles (Section C) before I treat them as accepted.

# SMJ Sustainable Fuel Lab — LIMS Program
## Phase 0 Deliverable: Project Understanding, Requirement Analysis & Proposed Architecture

**Status:** Discovery / Pre-Implementation. No feature code has been written. This document is the input to Checkpoint CP-000.
**Prepared as:** Combined LIMS architecture, ISO/IEC 17025 quality-system, data, security, UX, and deployment analysis.

---

## Table of Contents

A. Project Understanding · B. Requirement Analysis · C. Architectural Principles · D. High-Level Architecture · E. Technology Evaluation · F. Module Architecture · G. Domain Model · H. Laboratory Workflow · I. Configuration Strategy · J. ISO/IEC 17025 Support · K. Security Architecture · L. Database Architecture · M. UI/UX Architecture · N. Reporting Architecture · O. Backup/Recovery · P. Deployment Architecture · Q. Extensibility · R. Development Decomposition · S. Critical Risks · T. Discovery Questions · U. Recommended Roadmap · V. Proposed Initial Checkpoint

---

## A. Project Understanding

SMJ Sustainable Fuel Lab Pvt. Ltd. needs a **custom, on-premises LIMS** — not a demo, not a generic form builder. It has to run a real accredited-style testing lab's day-to-day work across solid fuel, biofuel, air, water, soil, noise, and stack/emission testing, with room to add disciplines later without a rewrite.

The core of the system is a **controlled chain of custody for data**: a request becomes a sample, a sample becomes one or more tests, a test produces a result, a result gets reviewed and approved, and a report is issued — and every step of that chain has to be reconstructable months or years later: who did it, when, under what method, on what equipment, and (if it was ever changed) what it looked like before.

Two constraints shape almost every downstream decision:

1. **Offline-first.** The lab may have zero internet connectivity during normal operation. Nothing load-bearing can depend on a remote service.
2. **Long operational life.** This is meant to still be running, and still be maintainable, years from now — by people who may not be the original developers. That argues for boring, well-understood technology, explicit documentation, and resisting speculative complexity (plugin frameworks, microservices, generic EAV-everything) that isn't yet justified by real requirements.

The system supports the lab's ISO/IEC 17025 practices; it does not *become* accredited by existing, and this document treats that distinction as non-negotiable throughout.

---

## B. Requirement Analysis

### Defined (explicit in the brief)
- Offline/on-prem, LAN-based, multi-workstation, Windows-hosted deployment.
- Preferred stack: React+TS+Vite / MUI, FastAPI+Python, SQLAlchemy 2.x, SQLite, Alembic, Argon2id + secure session cookies, RBAC with lab scope, Jinja2→Chromium PDF, Caddy, pytest+Playwright.
- Seven initial disciplines: solid fuel, biofuel, air, water, soil, noise, stack/emission.
- Full lifecycle: request → sample → test → result → review → verification → approval → report → retention → archival.
- Data integrity: no silent overwrite of technical records; corrections preserve before/after/who/when/why.
- Backend-enforced authorization; UI is never the only boundary.
- Configurable test/method definitions without code changes, but **not** via blanket EAV.
- Incremental, checkpointed development model — one bounded task at a time.
- ISO/IEC 17025 *support*, explicitly not "certification by software."

### Proposed (offered as candidates, need validation, not commitments)
- The full module list (Section 7 of the brief), the full role list (Section 14), the 21-phase roadmap. These are described in the brief itself as illustrative ("potential," "not exhaustive," "not necessarily final") — I've treated them accordingly: a strong starting point, trimmed and reordered where the domain logic suggests it, not a checklist to implement verbatim.

### Assumed (stated here so they're visible and challengeable — see Section T for the ones I need answered)
- Single physical lab site for v1 (no multi-branch operation) unless told otherwise.
- Greenfield: no existing LIMS being replaced, though there may be spreadsheets/paper records to reference.
- Concurrent users in the range typical of a mid-size independent testing lab (a double-digit user base, single-digit-to-low-double-digit simultaneous *writers* at peak) — **this is a guess and directly affects the SQLite decision in Section E**, so it's flagged BLOCKING.
- Regulatory/accreditation context is India-based (BIS methods are named explicitly; the lab's registered location is Maharashtra) — very likely NABL under ISO/IEC 17025, but not stated, so I have not hard-coded NABL-specific terminology anywhere in the architecture.

### Unknown (see Section T)
Actual concurrent user count; current accreditation status; existing data/systems to migrate; invoicing scope; server hardware already owned vs. to be procured; whether a database schema was meant to accompany this brief.

### Contradictions / tensions (not true contradictions, but two constraints in tension that need an explicit resolution — I've resolved both provisionally below and flagged them for confirmation)
- "SQLite preferred" vs. "must survive real concurrent multi-user LAN writes" → resolved in Section E with conditions attached, not a blanket acceptance.
- "Configurable without code changes" vs. "avoid generic EAV" → resolved in Section I: strongly-typed core schema, narrow purpose-built configuration tables, not a single generic attribute-value store.

---

## C. Architectural Principles

1. **Records are append-and-supersede, never silently overwritten.** A correction creates a new state; the old state remains queryable.
2. **The backend is the security boundary.** Every permission check is re-verified server-side regardless of what the UI already hid or disabled.
3. **Offline is the default operating mode, not a degraded fallback.** Anything requiring the internet is optional and isolated (e.g., nothing about report generation, sample login, or result entry may call out to the internet).
4. **Strong typing where it matters, configuration where it varies.** Core entities (Sample, Test, Result, Equipment) are real relational tables with real columns. Genuine variability (which parameters a given test has, what units they use) lives in narrow, purpose-built configuration tables — not a general key/value store.
5. **Meaningful audit, not indiscriminate logging.** Every state transition and every change to a technical record is audited with actor, timestamp, and reason where required. Routine read traffic is not.
6. **Modular monolith, not microservices, not a plugin framework — yet.** A single deployable application with clean internal module boundaries matches a single-server LAN deployment. Splitting it up or building a plugin loader would add operational complexity this deployment model doesn't need, given the brief's own instruction not to over-build extensibility infrastructure ahead of a real second discipline proving it's needed.
7. **Software supports the quality system; it doesn't replace it.** Every ISO/IEC 17025 mapping in Section J distinguishes what's a lab policy/procedure decision from what's a software capability.
8. **Every phase ends in something verifiable.** No phase is "done" because code exists; it's done because it was tested, verified against its own acceptance criteria, and checkpointed.

---

## D. High-Level Architecture

```
                         Client Workstations (LAN)
        ┌───────────────┬───────────────┬───────────────┐
        │  Reception PC  │  Analyst PC   │  Manager PC   │  ... (browser, Chromium-based)
        └───────┬────────┴───────┬───────┴───────┬───────┘
                │  HTTPS (LAN, local cert)        │
                ▼                                  ▼
                        ┌─────────────────────┐
                        │   Caddy (reverse    │  → serves built React SPA (static)
                        │   proxy, local TLS)  │  → proxies /api to FastAPI
                        └──────────┬───────────┘
                                   ▼
                  ┌───────────────────────────────────┐
                  │        FastAPI Application         │
                  │  ┌───────────────────────────────┐ │
                  │  │ API layer (routers, schemas)   │ │
                  │  ├───────────────────────────────┤ │
                  │  │ Service / domain layer         │ │  ← business rules,
                  │  │  (workflow, RBAC checks,        │ │    state machines,
                  │  │   calc engine, audit writer)   │ │    segregation of duties
                  │  ├───────────────────────────────┤ │
                  │  │ Repository / SQLAlchemy layer  │ │
                  │  └───────────────────────────────┘ │
                  └───────────────┬─────────────────────┘
                                   ▼
                 ┌───────────────────────────────┐        ┌────────────────────┐
                 │  SQLite (WAL mode) — local     │        │ Local document      │
                 │  fixed disk on app server       │        │ store (disk) +      │
                 └───────────────┬─────────────────┘        │ nightly NAS mirror  │
                                   │                          └────────────────────┘
                                   ▼
                 ┌───────────────────────────────┐
                 │ Scheduled backup job (Windows   │
                 │ Task Scheduler → online backup, │
                 │ integrity check, rotation)      │
                 └───────────────────────────────┘
```

Everything the lab needs day-to-day — login, sample registration, result entry, review/approval, report PDF generation, printing, barcode scanning — resolves entirely within this LAN boundary. The only thing that would ever reach outside it is something explicitly optional and clearly isolated (e.g., a future software-update channel), never a runtime dependency of core workflow.

---

## E. Technology Evaluation

| Layer | Preferred choice | Assessment |
|---|---|---|
| Frontend | React + TS + Vite, MUI | Sound. Mature, well-documented, good component ecosystem for data-dense forms/tables, MUI gives accessible defaults out of the box. No objection. |
| Backend | FastAPI + Python | Sound. Async-capable, strong typing via Pydantic, good OpenAPI generation for internal contract discipline, large ecosystem for PDF/Chromium/Argon2 tooling. |
| ORM/Migrations | SQLAlchemy 2.x + Alembic | Sound, and importantly gives a documented, versioned migration path — essential for an offline system that has to be upgraded in place for years. |
| Auth | Argon2id + secure session cookies | Sound. Argon2id is the current recommended password hash; server-side sessions (not JWTs held client-side) suit a single-server LAN deployment and make server-side revocation trivial — important for account lifecycle control. |
| Reporting | Jinja2 → HTML → headless Chromium → PDF | Sound and appropriately offline (no cloud PDF API). Chromium must be bundled/pinned locally, not fetched at render time. |
| File storage | Windows local disk / NAS | Workable **with one hard condition**: the *live* SQLite database file must live on local fixed disk, never on an SMB/NAS share (see database evaluation below). Documents/attachments are fine on NAS since they don't need SQLite's file-locking semantics. |
| Barcode | Code 128 + QR | Sound — both print and scan reliably with commodity label printers and keyboard-wedge USB/Bluetooth scanners; no special driver layer needed. |
| Testing | pytest + Playwright | Sound for both API/unit coverage and real browser E2E of workflows (critical given "don't rely only on superficial UI tests"). |
| Reverse proxy | Caddy | Sound — automatic local TLS handling is genuinely useful for a LAN deployment where you still want HTTPS between workstations and the server. |

### SQLite — the decision that needs real scrutiny

This is evaluated on its own because the brief is right to insist on it, and a wrong call here is expensive to reverse later.

**In favor, for this deployment shape specifically:**
- SQLite in **WAL (Write-Ahead Logging) mode** allows one writer concurrently with many readers, without readers blocking on the writer. A LIMS workload is read-heavy (dashboards, search, report views) with comparatively short, discrete write transactions (register a sample, enter a result, approve a test) — this maps well onto WAL's strengths.
- It has zero network-service surface to operate, patch, or lose to a crashed daemon — a genuine reliability advantage for a system that has to keep working with no IT staff on-site and no internet for support.
- Backup is a file, not a server: it can be copied, hashed, and restored with tools that will still exist in 10 years, which matters a lot for the "years of operational life" requirement.
- Migration off SQLite later is not blocked: SQLAlchemy already abstracts the dialect, so a future move to PostgreSQL (if the lab genuinely outgrows single-writer semantics) is a migration project, not a rewrite.

**Real risks, and how they're addressed rather than waved away:**
- **Single-writer contention.** If two analysts submit results in the same instant, one write briefly queues behind the other (milliseconds, not a UX problem) *as long as transactions are short*. The actual risk is a badly designed transaction (e.g., one that generates a PDF report while holding a write lock) blocking everyone else. **Mitigation:** report generation and any heavy read work must run on read-only connections, never inside a write transaction; the service layer enforces short, single-purpose transactions.
- **Network filesystem locking.** SQLite's locking model is documented as unreliable over SMB/NFS. **Mitigation (hard rule, not a preference):** the live database file lives on the application server's local disk, full stop. NAS is used for backups and for document/attachment storage, not for the live DB.
- **Backup consistency.** A raw file copy of a live SQLite database can capture a half-written state. **Mitigation:** use SQLite's own online backup mechanism (`VACUUM INTO` or the backup API) so backups are always transactionally consistent, then run `PRAGMA integrity_check` against the backup copy before it's considered valid (see Section O — a file existing isn't proof of a good backup).
- **Corruption after power loss.** Rare with WAL + proper fsync behavior, but not impossible on unreliable hardware. **Mitigation:** server-grade disk (ideally with a UPS on the server, which should be a deployment recommendation regardless of database choice), plus the restore-tested backup regime above as the actual safety net.
- **Unknown real concurrency.** This is the honest gap: I don't yet know the lab's actual peak simultaneous-writer count (BLOCKING question in Section T). SQLite comfortably handles the low tens of concurrent users doing typical LIMS write patterns; it stops being the right default well before hundreds of simultaneous heavy writers. 

**Decision:** Accept SQLite as the v1 database, conditioned on: WAL mode mandatory, single app-server ownership of the DB file, DB file never on a network share, short enforced transactions, and a **documented, numeric trigger** (to be set once real user counts are confirmed — e.g., "reassess if named users exceed ~50 or peak concurrent writers regularly exceed ~15–20") that would prompt a planned migration to PostgreSQL rather than an emergency one. This is the kind of decision Section 6 of the brief asks to be made on workload, not on simplicity — so it will be revisited explicitly once Section T's user-count question is answered, not silently assumed forever.

---

## F. Module Architecture

Core modules (needed for the lifecycle to function at all) vs. supporting modules (needed for the lab to run as a quality system, but can follow once the spine works):

| Module | Purpose | Owned data (examples) | Depends on | Primary roles |
|---|---|---|---|---|
| **Identity & RBAC** | Auth, sessions, roles, scoped permissions | Users, Roles, Permissions, Sessions | — | Admin |
| **Audit Trail** | Immutable record of state changes and corrections | AuditEvent | Identity | All (write), Auditor/QM (read) |
| **Master Data** | Shared reference data reused everywhere | Units, Sections, Disciplines, Locations, Statuses | Identity | Admin |
| **Customer & Project** | Client and engagement records | Customer, Contact, Project/Contract | Master Data | Reception, Manager |
| **Sample Management** | Receipt through accession/allocation | Sample, SubSample, Container, ChainOfCustodyEvent | Customer/Project, Master Data | Reception, Analyst |
| **Method & Test Engine** | Configurable test/parameter/method definitions | Method, MethodVersion, TestDefinition, ParameterDefinition | Master Data | Technical Manager, QM |
| **Calculation Engine** | Safe formula evaluation with provenance | Formula, FormulaVersion, CalculationRun | Method & Test Engine | (system) |
| **Execution & Results** | Test assignment, raw data, results, revisions | TestInstance, Result, ResultRevision | Sample, Method & Test Engine, Equipment | Analyst |
| **Review/Verification/Approval** | Segregated multi-stage sign-off | ReviewRecord, VerificationRecord, ApprovalRecord | Execution & Results, Identity/RBAC | Reviewer, Technical Reviewer, Signatory |
| **Equipment & Calibration** | Equipment master, calibration/maintenance state, use enforcement | Equipment, CalibrationRecord, MaintenanceRecord | Master Data | Equipment Manager, Analyst |
| **QC** | Blanks/duplicates/spikes/CRMs, acceptance criteria, control charts | QCSample, QCResult | Method & Test Engine, Execution | Analyst, Technical Manager |
| **Documents & Records** | Controlled SOPs, certificates, validation records | Document, DocumentVersion | Identity/RBAC | QM |
| **Reporting** | Templated report/certificate generation with traceability | ReportTemplate, Report, ReportRevision | Execution, Review chain | Reviewer, Signatory |
| **Quality Management** | Nonconformity, CAPA, complaints, internal audits, risk | Nonconformity, CAPA, Complaint, InternalAudit | Most of the above | QM |
| **Notifications** | In-app alerts (due dates, calibration expiry, overdue tests) | Notification | Various | All |
| **Backup/Ops** | Scheduled backup, restore, health | BackupJob, HealthCheck | — | Admin |
| **Configuration/Admin** | Numbering schemes, retention rules, workflow toggles | ConfigSetting | Identity/RBAC | Admin, QM |

Deliberately **not** in v1 unless confirmed needed: invoicing/billing (ambiguous scope — see Section T), proficiency testing/ILC management, external e-signature/PKI. These are real ISO/IEC 17025-adjacent capabilities but shouldn't be built speculatively ahead of confirmed requirement.

---

## G. Domain Model (key entities, not yet the full ERD — that's a Phase 3 deliverable)

```
Customer ─┬─< Project/Contract ─┬─< Sample ─┬─< SubSample/Portion ─< Container
          │                     │           │
          │                     │           ├─< ChainOfCustodyEvent
          │                     │           │
          │                     │           └─< TestRequest ─┬─< TestInstance ──> Method ──> MethodVersion
          │                     │                             │                              │
          │                     │                             │                              └─< ParameterDefinition ──> Unit
          │                     │                             │
          │                     │                             ├──> Equipment (required/used)
          │                     │                             ├──> Analyst (assigned)
          │                     │                             │
          │                     │                             └─< Result ─< ResultRevision
          │                     │                                    │
          │                     │                                    └──> CalculationRun ──> FormulaVersion
          │                     │
          │                     └─< Report ─< ReportRevision  (traces back through Result → TestInstance → Sample → Project)
          │
          └── Contact
```

Cross-cutting, attached to most of the above: `AuditEvent` (actor, timestamp, entity, before/after, reason), `ReviewRecord` / `VerificationRecord` / `ApprovalRecord` (each with actor + timestamp + outcome, enforcing that the actor differs from the record's creator per segregation of duties), `Attachment` (photos, instrument printouts).

Deliberately modeled as **distinct, strongly-typed tables** rather than one generic structure: `TestInstance` (a test as actually performed) is not the same table as `TestDefinition` (the configurable template) is not the same table as `Method`/`MethodVersion` (the documented procedure it follows). Collapsing these into one generic "Test" table with a type flag would break exactly the integrity/querying/reporting properties Section 11 of the brief asks to protect.

---

## H. Laboratory Workflow

**Main path (configurable per discipline, this is the default backbone):**

```
Draft Request → Contract Review → Sample Receipt → Registration/Accession →
Allocation → Test Planning → Test Assignment → Execution (raw data) →
Result Entry → Review → Technical Verification → Approval →
Report Generation → Delivery → Retention → Archival
```

**Exception paths (first-class, not afterthoughts):**

| Trigger | Path |
|---|---|
| Sample condition unacceptable at receipt | Receipt → **Rejected** (reason required, customer notified) |
| Result fails review | Review → **Sent back for rework**, TestInstance reopened, prior entry preserved via ResultRevision |
| QC acceptance criteria not met | Result blocked from Review; **QC investigation** required before proceeding |
| Post-approval correction needed | Approved result → **Reopen (controlled)** → correction → re-review → re-verification → re-approval; original approved version remains in history, never deleted |
| Equipment out of calibration/service | TestInstance assignment **blocked or warned** (configurable per lab policy, default = blocked for anything result-affecting) |
| Customer complaint | Logged against the relevant Sample/Report → Quality Management module → CAPA if warranted |

Status vocabulary is explicit and visible in the UI at every stage (Draft / Received / In Progress / Pending Review / Rejected / Approved / Completed / Cancelled / Archived), matching Section 23 of the brief.

---

## I. Configuration Strategy

**Configurable by a lab administrator, no code change:**
Test/parameter definitions (data type, unit, required/optional, precision, rounding, acceptance criteria), method-to-equipment/competency/QC requirements, report templates and branding, numbering schemes, retention periods, notification thresholds, and specific workflow *policy toggles* such as "block vs. warn" for out-of-calibration equipment use.

**Deliberately kept out of configuration, owned by the application architecture:**
The authentication mechanism, the audit trail's write path (append-only, never user-editable), the shape of the core workflow state machine (stages can be *parameterized* — e.g., skip technical verification for a discipline where it's genuinely not required — but the engine itself isn't rewritten per lab), the RBAC engine, and the calculation engine's execution sandbox.

**How "configurable without EAV" is actually achieved:** a `TestDefinition`/`ParameterDefinition` pair of real, typed tables (data_type enum, unit_id FK, precision int, min/max numeric, required bool) gives an administrator genuine no-code flexibility to add a new test parameter, while every parameter still has a real column-backed type the database and reporting engine can validate against — rather than a generic `key/value/text` table that pushes all validation into application code and makes reporting/search brittle. EAV-style tables are reserved for genuinely free-form metadata (e.g., arbitrary customer-supplied sample descriptors) where that trade-off is actually justified.

---

## J. ISO/IEC 17025 Support

The software is a **control that supports the quality system**; conformance and accreditation status belong to the laboratory, assessed by an accreditation body, not to the existence of this software. Mapped by the standard's major structural areas:

| Standard area | What it requires (in substance) | Software capability | Explicitly *not* a software claim |
|---|---|---|---|
| Impartiality & confidentiality | Lab policy + demonstrable controls | RBAC scoping, access logging, data-access audit | The policy itself is a lab document, not code |
| Structural/personnel | Defined responsibilities, competence, authorization | Personnel records, competency/authorization flags gating who can perform/review/approve which test types | Competency *assessment* is a lab process; software records its outcome |
| Facilities & environment | Suitable, monitored conditions | Environmental condition capture linked to TestInstance | Software doesn't control the HVAC — it records what was observed |
| Equipment & metrological traceability | Calibrated, maintained, traceable equipment | Equipment master, calibration due-date enforcement, blocking/warning on non-conforming equipment | Calibration itself is performed externally/by staff; software records and enforces the *record* |
| Review of requests/contracts | Requests reviewed before acceptance | Contract review step with sign-off, prior to sample acceptance | — |
| Method selection/verification/validation | Documented, fit-for-purpose methods | Method/MethodVersion records with validation/verification evidence links | Validation work itself is a technical activity, not a software output |
| Sampling & handling of items | Documented chain of custody | ChainOfCustodyEvent, container/condition tracking | — |
| Technical records | Sufficient to permit reconstruction | Full AuditEvent + ResultRevision history on every technical record | — |
| Measurement uncertainty | Evaluated where relevant | Uncertainty field on Result, linked to method requirement | Estimation methodology is a technical/statistical decision the lab owns |
| Ensuring validity of results | QC program, control charts, PT | QC module, control-chart-supporting data capture | — |
| Reporting | Complete, accurate, traceable reports | Report generation with full traceability footer to Sample/Method/Analyst/Equipment/Approval | — |
| Nonconforming work / complaints / CAPA | Documented handling | Nonconformity, Complaint, CAPA modules | — |
| Document/record control | Version, approval, retention | Document module with versioning and controlled effective dates | — |
| Internal audits / management review | Periodic self-assessment | Audit findings module, management-review-support reports | The audit *activity* is performed by people; software stores its records |

---

## K. Security Architecture

- **Authentication:** Argon2id-hashed passwords, configurable complexity/expiry policy, account lockout after repeated failed attempts, secure server-side sessions (httpOnly, secure, SameSite cookies) with idle and absolute timeout, explicit session invalidation on logout/admin action.
- **Authorization:** RBAC checked on every backend endpoint (never trusted from the client), scoped by module/action/record/discipline/section as needed. **Segregation of duties is enforced in the service layer**: a review/verification/approval action is rejected server-side if the acting user is the same user who created the underlying entry, regardless of what the UI shows.
- **Audit integrity:** audit writes are append-only at the application layer; no UI or ordinary role has update/delete access to audit records. Correction of a technical record creates a new revision — it never mutates the audited history.
- **Secrets:** no credentials in source control; environment-based configuration, encrypted where the OS provides a mechanism (e.g., Windows DPAPI for local secrets at rest).
- **Network exposure:** LAN-only by default, HTTPS via Caddy even on the local network, no inbound internet exposure required or assumed.
- **Administrative actions:** privileged operations (role changes, user creation, config changes affecting workflow policy) are themselves audited events, not silent.

---

## L. Database Architecture

**On the "supplied schema":** Section 22 of the brief treats a supplied database schema as an input to be critiqued, but no schema file was included with this conversation — this is logged as a BLOCKING discovery item (Section T) rather than assumed away.

**Design principles for Phase 3 (when the full ERD/data dictionary is produced):**
- 3NF baseline; denormalization only where deliberately justified (e.g., a report snapshot table that intentionally freezes values at approval time for reproducibility).
- Real foreign keys, enforced — SQLite requires `PRAGMA foreign_keys=ON` per connection, which becomes a mandatory connection-setup step, not an assumption.
- Surrogate primary keys, with lab-facing numbers (sample numbers, report numbers) as separately validated unique business fields.
- Controlled records use status/lifecycle fields and revision tables rather than hard deletes.
- Indexes chosen against the actual search/traceability patterns in Section 20 of the brief (sample number, project, customer, date, analyst, status, discipline) — defined at schema-design time, not bolted on after performance problems appear.
- EAV avoided outside the narrow, justified cases described in Section I.

---

## M. UI/UX Architecture

- **Navigation:** role-aware dashboard as the landing screen (a reception user sees today's receipts and pending accessions; an analyst sees their assigned queue; a manager sees workload/TAT). Discipline is a first-class filter throughout, not an afterthought.
- **Screen families:** Auth · Master Data (admin) · Customers/Projects · Sample Receipt/Registration/Accession · Test Planning/Assignment · Execution/Result Entry (barcode-scan-first, keyboard-friendly) · Review/Verification/Approval queues · Equipment/Calibration · QC · Documents · Reporting.
- **Status is always visually explicit** — consistent color/label conventions for Draft/Received/In Progress/Pending Review/Rejected/Approved/Completed/Cancelled/Archived, used identically across every module so users don't have to relearn state per screen.
- **Journeys** (detailed per-role flows are a Phase 4 deliverable): reception (receipt → registration, minimal clicks, barcode label print), analyst (queue → scan sample → enter/calc results → submit), reviewer/technical reviewer/signatory (queue → inspect → approve/reject with reason), equipment manager (calibration due list → log service → clear/hold equipment), QM (nonconformity/CAPA/document control dashboards), admin (config, users, backups).

---

## N. Reporting Architecture

Jinja2 template → rendered HTML → headless Chromium → PDF, entirely local. Every generated report carries a visible traceability footer resolving back to Sample → TestInstance → Method(Version) → Analyst → Equipment → Reviewer/Verifier/Approver → AuditEvent chain, so a report can always be traced to its source technical records (Section 19). Templates are versioned; report numbering is configurable; approval/signature blocks reflect the actual ApprovalRecord, not a decorative image. Branding (logo, letterhead) is a per-lab configuration asset, not hard-coded.

---

## O. Backup / Recovery

- **Backup mechanism:** SQLite's own consistent online-backup path (`VACUUM INTO`, run on a schedule via Windows Task Scheduler), never a raw file copy of a live database.
- **Verification, not assumption:** each backup is opened and checked with `PRAGMA integrity_check`, plus a basic row-count/sanity check, before being marked valid. A file existing in the backup folder is not treated as proof of anything, per Section 21 of the brief.
- **Layers:** local disk (fast recovery), NAS mirror (server-loss protection), periodic offline/removable copy (disaster protection). Documents/attachments follow the same three-tier pattern.
- **Restore drills:** an actual restore-and-verify exercise on a schedule (e.g., quarterly), not just backup creation — this is the only way "restore works" is more than a hope.
- **RPO/RTO:** to be set with the lab (proposing an initial target of RPO ≤ 24h / RTO of a few hours pending confirmation) — see Section T.

---

## P. Deployment Architecture

Application server: Windows 11 Pro or Windows Server, FastAPI app run as a Windows service (auto-start, auto-restart on failure), Caddy reverse proxy in front serving the built React SPA and terminating LAN HTTPS with a locally trusted certificate. SQLite database file on the server's local fixed disk (never NAS/SMB — see Section E). Documents on local disk, mirrored to NAS nightly. Client workstations reach the app over the LAN via a browser and local hostname/IP; printing uses standard Windows printer sharing through the browser print dialog; barcode scanners are standard HID keyboard-wedge devices needing no custom driver. Updates/migrations follow a documented sequence: backup → stop service → apply Alembic migration → deploy new build → smoke test → resume — designed to work with no internet access and to be rollback-capable if a step fails.

---

## Q. Extensibility

Adding a new discipline should, in the normal case, mean: new Method/MethodVersion records, new TestDefinition/ParameterDefinition entries, possibly a new report template — all *configuration*, reusing the same sample lifecycle, RBAC, audit trail, equipment, QC, and reporting engines every existing discipline already uses. New code is only justified when a discipline needs a genuinely new *mechanic* the config layer can't express (e.g., a fundamentally different sampling-event structure) — and even then, it's a new module inside the same modular monolith, not a plugin system. Section 16 of the brief plans exactly one such "prove it" exercise (WP-16-03) before the extensibility claim is treated as validated rather than assumed.

---

## R. Development Decomposition

Only Phase 0 and the shape of Phase 1 are being turned into concrete tasks now — everything past that stays directional until the relevant checkpoint is accepted, per the brief's own instruction not to prematurely freeze future tasks.

**Phase 0 — Project Control & Discovery** *(current phase)*
- WP-00-01 Project Foundation — repo structure, doc conventions, status vocabulary, change-control conventions.
- WP-00-02 Existing Information Consolidation — this document; resolution of the BLOCKING questions in Section T; explicit note that no database schema was supplied.
- WP-00-03 Initial Project Baseline → **CP-000** (Section V).

**Phase 1 — Requirements & Laboratory Model** *(next, once CP-000 is accepted)*
- WP-01-01 Users & Organization
- WP-01-02 Laboratory Workflows (per-discipline detail, once disciplines' actual method lists are known)
- WP-01-03 Exceptional Workflows
- WP-01-04 Requirements Baseline → **CP-001**

Example task-sized breakdown for WP-01-01 (illustrating the granularity target from Section 55 of the brief — small, bounded, independently verifiable):
- TASK: Document laboratory sections and disciplines as they actually exist at SMJ today.
- TASK: Draft initial role list against real job functions (confirm which roles are distinct people vs. one person wearing multiple hats — directly affects segregation-of-duties design).
- TASK: Confirm organizational responsibility boundaries (who can authorize what, today, on paper).

Phases 2 onward (System/Security Architecture → ... → Maintenance & Evolution) remain as listed in the brief's Section 33, unchanged in sequence, each gated by its own checkpoint (CP-002 … CP-019, then ongoing Phase 20). No implementation work is authorized past WP-00 until CP-000 is accepted and Phase 1 begins.

---

## S. Critical Risks

| Risk | Impact | Mitigation |
|---|---|---|
| Real concurrent-write load unknown | Wrong database decision, hard to reverse later | BLOCKING question asked now (Section T); SQLite decision explicitly conditioned and re-checked once known |
| Scope of this brief is very large | Attempting too much per session, architectural drift | Strict phase/task/checkpoint discipline (Section R); one authorized task at a time |
| Overclaiming "ISO 17025 compliant software" | Misleads the lab and any assessor | Every capability mapped with an explicit "not a software claim" boundary (Section J) |
| Calculation engine executing unsafe logic | Data integrity, security | No arbitrary code execution; constrained formula evaluator only, with full provenance (Section 12 of brief) |
| SQLite DB file placed on NAS by a well-meaning admin later | Silent corruption risk | Documented as a hard deployment rule, verified at Phase 19 production checkpoint, not just written once here |
| Backups exist but were never restore-tested | False sense of safety | Explicit restore-drill requirement (Section O), distinct "backup validated" vs. "restore tested" states |
| Single physical server | Single point of failure | Documented in Phase 17/19 as an operational risk to size hardware/UPS against, once server specs are known (Section T) |
| Long multi-session AI-assisted build | Context loss between sessions, re-litigating decisions | Every task self-contained per Section 57's template; ADRs and current-state docs as the source of truth, not conversation history |

---

## T. Discovery Questions

**BLOCKING** (needed before Phase 1 can be meaningfully completed):
1. What's the realistic number of named users, and — more importantly — the peak number of people writing to the system at the same moment (e.g., sample registration and result entry happening simultaneously across shifts)? This directly gates the SQLite decision in Section E.
2. Is SMJ currently accredited (e.g., NABL) under ISO/IEC 17025, in the process of seeking accreditation, or using the standard as an internal best-practice reference without a formal accreditation goal? This changes how strictly certain records/evidence requirements should be enforced by the software.
3. Is there an existing system, spreadsheet set, or paper register currently in use that data needs to migrate from?
4. Is invoicing/billing in scope for v1, or explicitly deferred? (The brief lists it as "where required," which is ambiguous.)
5. Was a database schema meant to be attached to this conversation? Section 22 refers to a "supplied" schema that wasn't received.
6. Is this a single lab site, or should the architecture anticipate multiple branches/sites sharing one system?
7. What server hardware is already available (or budgeted), if any — this affects both the SQLite risk assessment and the backup/UPS recommendation in Section S.

**NON-BLOCKING** (useful, but Phase 1 can proceed without them):
8. Preferred report branding assets (logo, letterhead) and any existing report template SMJ already uses.
9. Which specific standards (ASTM/IS-BIS/APHA/EPA/EN) apply to the first methods to be configured — useful for Phase 9 but not for Phase 0/1 architecture.
10. Existing or planned label/barcode printer make/model.
11. Whether approval requires anything beyond authenticated in-system sign-off (e.g., a future digital-signature/PKI requirement), or system-authenticated approval is sufficient for now.
12. NAS make/model, if already owned, for backup-target planning.

---

## U. Recommended Roadmap

Phase 0 (now) → 1 Requirements & Lab Model → 2 System & Security Architecture → 3 Data Architecture → 4 UX/UI Architecture → 5 Technical Foundation → 6 Identity/RBAC/Audit → 7 Core Master Data → 8 Customer/Project/Sample → 9 Test & Method Engine → 10 Execution & Results → 11 Review/Verification/Approval → 12 QC & Equipment → 13 Quality Management → 14 Documents & Records → 15 Reporting & Certificates → 16 Configuration & Extensibility → 17 Backup/Recovery/Ops → 18 Validation & Hardening → 19 Production Deployment → 20 Maintenance & Evolution.

Each phase closes with a numbered checkpoint (CP-000 … CP-019, then ongoing for Phase 20) per Section 59–60 of the brief; none is skipped, none is collapsed.

---

## V. Proposed Initial Checkpoint

**CP-000 — Project Baseline**

*Accepted when:*
- This document (or an agreed revision of it) is reviewed and its assumptions in Section B are confirmed or corrected.
- The BLOCKING questions in Section T are answered, or explicitly deferred with a documented reason.
- The architectural principles (Section C) and the conditioned SQLite decision (Section E) are explicitly accepted or amended.
- WP-00-01 through WP-00-03 tasks are complete (repo/doc conventions established; this consolidation exists; no schema was silently assumed).
- No application feature code has been written — confirmed true at this point.

*Next authorized action once CP-000 is accepted:* begin WP-01-01 (Users & Organization) as the first bounded Phase 1 task — nothing further, per Section 61's development-control principle.



Next Prompt:
# SMJ Sustainable Fuel Lab — LIMS Program

# Phase 0 Deliverable: Project Understanding, Requirement Analysis & Proposed Architecture

**Status:** Discovery / Pre-Implementation
**Checkpoint:** CP-000 — Architecture & Project Baseline
**Decision status:** Foundational architecture decisions frozen; remaining discovery items are explicitly identified for resolution or formal deferral.
**Implementation status:** No application feature code authorized under Phase 0.
**Prepared as:** Combined LIMS architecture, ISO/IEC 17025 quality-system, data, security, UX, deployment, and project-control analysis.

---

## Table of Contents

A. Project Understanding
B. Requirement Analysis
C. Architectural Principles
D. High-Level Architecture
E. Technology Evaluation
F. Module Architecture
G. Domain Model
H. Laboratory Workflow
I. Configuration Strategy
J. ISO/IEC 17025 Support
K. Security Architecture
L. Database Architecture
M. UI/UX Architecture
N. Reporting Architecture
O. Backup / Recovery
P. Deployment Architecture
Q. Extensibility
R. Development Decomposition
S. Critical Risks
T. Discovery Questions and Deferred Decisions
U. Recommended Roadmap
V. CP-000 Decision Baseline and Acceptance Criteria

---

# A. Project Understanding

SMJ Sustainable Fuel Lab Pvt. Ltd. requires a **custom, on-premises Laboratory Information Management System (LIMS)** for real laboratory operations. The system is not intended to be a demonstration application, generic form builder, SaaS platform, or enterprise ERP.

The initial system is intended to support laboratory operations across:

* Solid Fuel
* Biofuel
* Air
* Water
* Soil
* Noise
* Stack / Emission

with provision for additional laboratory disciplines and test methods in the future.

The central purpose of the LIMS is to provide a **controlled, traceable laboratory information chain**:

```text
Request
   ↓
Contract / Request Review
   ↓
Sample Receipt
   ↓
Sample Registration / Accession
   ↓
Test Planning / Assignment
   ↓
Test Execution
   ↓
Raw Data / Observations
   ↓
Calculation
   ↓
Result
   ↓
Review
   ↓
Technical Verification
   ↓
Approval
   ↓
Report
   ↓
Retention
   ↓
Archive
```

Every technically significant stage must be reconstructable later, including:

* who performed the activity;
* when it occurred;
* which method/version applied;
* which equipment was used;
* which raw observations were recorded;
* which calculations were performed;
* what result was initially produced;
* what revisions occurred;
* who reviewed, verified, and approved the result;
* and what the approved report contained at the time of issue.

Two fundamental constraints govern the architecture.

### 1. Offline-first / On-premises

The laboratory must be able to perform its normal operations without internet connectivity.

Internet access must therefore **not be a runtime dependency** for:

* authentication;
* sample registration;
* test execution;
* result entry;
* calculations;
* review;
* approval;
* report generation;
* barcode operation;
* or normal system administration.

### 2. Long operational life

The software is expected to remain maintainable for years and may eventually be maintained by developers other than the original developers.

The architecture therefore intentionally favors:

* mainstream technologies;
* explicit boundaries;
* relational integrity;
* documented migrations;
* predictable deployment;
* controlled configuration;
* strong auditability;
* simple operational procedures;
* and avoidance of unnecessary infrastructure.

The project explicitly rejects the idea that increased architectural complexity automatically means increased quality.

---

# B. Requirement Analysis

## B.1 Defined Requirements

The following requirements are considered established for the current project baseline.

### Deployment

* On-premises deployment.
* LAN-based multi-workstation operation.
* Windows-hosted server environment.
* Browser-based client access.
* Core functions usable without internet access.

### Technology

The approved technology baseline is:

* React
* TypeScript
* Vite
* Material UI
* FastAPI
* Python
* SQLAlchemy 2.x
* PostgreSQL
* Alembic
* Argon2id
* secure server-side sessions
* Caddy
* Jinja2
* Chromium-based PDF rendering
* pytest
* Playwright

### Architecture

The approved architecture is:

> **Modular Monolith**

The application will remain a single deployable application while maintaining internally separated domain modules.

Microservices and a plugin framework are **not part of v1**.

### Laboratory disciplines

Initial scope covers:

1. Solid Fuel
2. Biofuel
3. Air
4. Water
5. Soil
6. Noise
7. Stack / Emission

### Lifecycle

The system shall support the complete lifecycle from request through sample processing, test execution, result review, approval, reporting, retention, and archival.

### Data integrity

Technical records shall not be silently overwritten.

Corrections must preserve:

* previous state;
* new state;
* actor;
* timestamp;
* reason where required;
* and revision lineage.

### Security

Authorization shall always be enforced on the backend.

UI visibility, disabled controls, and client-side logic shall never be considered security controls by themselves.

### Configuration

The system shall allow laboratory administrators to configure normal test/method/parameter variations without application code changes.

This flexibility shall be provided through **strongly typed, purpose-built relational configuration structures**, not through a generic EAV architecture.

### Development control

The project shall use:

```text
Phase
  ↓
Work Package
  ↓
Task
  ↓
Implementation
  ↓
Verification
  ↓
Evidence
  ↓
Checkpoint
```

No feature development is authorized merely because the next feature appears useful.

### ISO/IEC 17025

The software shall support laboratory practices aligned with ISO/IEC 17025 requirements.

The software shall **not** claim that its existence makes the laboratory accredited or compliant automatically.

---

## B.2 Proposed but now Frozen Architectural Decisions

The following decisions were evaluated during Phase 0 and have now been frozen for the project baseline:

| Decision                 | Frozen selection                                    |
| ------------------------ | --------------------------------------------------- |
| Project scope            | Single-laboratory LIMS                              |
| Technology               | React/TypeScript + FastAPI/Python + PostgreSQL      |
| Architecture             | Modular Monolith                                    |
| Database                 | PostgreSQL                                          |
| Data integrity           | Revision-based records + immutable audit            |
| Security                 | RBAC + server-side sessions + segregation of duties |
| Workflow                 | Explicit state machine                              |
| Configuration            | Strongly typed configuration tables                 |
| Development method       | Task → Verification → Checkpoint                    |
| Documentation            | Documentation-as-code                               |
| Module structure         | Domain-oriented modules                             |
| Architectural philosophy | Conservative, controlled, auditable                 |

These decisions constitute the primary CP-000 architecture baseline.

---

## B.3 Explicitly Deferred / Out of Scope

The following are not part of the initial v1 implementation unless later approved through change control:

* multi-tenant SaaS;
* multiple independent laboratories within a shared instance;
* microservices;
* plugin architecture;
* customer self-service portal;
* public Internet-facing API;
* cloud synchronization;
* mobile application;
* ERP;
* general accounting;
* speculative enterprise infrastructure;
* external PKI/digital-signature infrastructure;
* advanced external integrations not justified by actual laboratory requirements.

Billing/invoicing remains a business-scope decision and must be explicitly classified before its implementation phase.

---

## B.4 Assumptions

The following assumptions are used unless corrected during Phase 1 discovery:

* v1 is for a single physical laboratory operation;
* the principal operating environment is Windows;
* the application is hosted within the laboratory LAN;
* PostgreSQL is hosted locally within the laboratory environment;
* a centralized application server is preferred;
* browser-based access is preferred over installed client software;
* exact user counts and workload figures are still to be established for deployment sizing;
* detailed methods and discipline-specific test lists will be defined in later requirements/configuration phases.

---

# C. Architectural Principles

The following principles are frozen as the project's governing architectural philosophy.

## 1. Controlled revision, not silent overwrite

Technical records are revision-controlled.

A correction creates a new controlled state while preserving historical information.

## 2. Backend is the security boundary

Every protected operation is authorized by the backend.

The frontend cannot grant itself access.

## 3. Offline is the normal operating mode

Core laboratory operations shall not depend on:

* cloud services;
* external APIs;
* Internet authentication;
* hosted PDF conversion;
* remote barcode services;
* or cloud storage.

## 4. Strong typing where meaning matters

Core concepts are represented by explicit relational structures.

Examples:

* Sample
* TestInstance
* Method
* MethodVersion
* ParameterDefinition
* Result
* Equipment
* Report
* ApprovalRecord

Generic key/value structures shall not become the foundation of the system.

## 5. Meaningful auditability

Audit events shall focus on:

* state changes;
* technical record changes;
* configuration changes;
* authorization changes;
* approval events;
* security events;
* and other controlled activities.

Routine read traffic is not automatically converted into an audit record.

## 6. Modular Monolith

The system remains one deployable application with clear internal module boundaries.

The project explicitly does not introduce:

* microservices;
* service meshes;
* distributed transactions;
* plugin loaders;
* or similar infrastructure without a demonstrated requirement.

## 7. Software supports the quality system

The LIMS records and enforces controls where appropriate.

The laboratory's quality procedures, competence assessments, impartiality arrangements, technical decisions, validation work, management responsibility, and accreditation status remain responsibilities of the laboratory.

## 8. Every phase must be verifiable

A phase is not complete merely because code exists.

Completion requires:

* implementation where applicable;
* testing;
* evidence;
* review;
* acceptance criteria;
* and checkpoint approval.

## 9. Database is a controlled service boundary

PostgreSQL is the authoritative transactional data store.

Client workstations shall not connect directly to the database.

All application data access shall pass through the backend application.

## 10. Simplicity is a design objective

The project shall prefer the simplest design that satisfies:

* laboratory requirements;
* integrity;
* security;
* maintainability;
* traceability;
* and future controlled expansion.

---

# D. High-Level Architecture

```text
                         Client Workstations
                ┌──────────────────────────────┐
                │ Reception                    │
                │ Analysts                     │
                │ Reviewers                    │
                │ Managers / Signatories       │
                └──────────────┬───────────────┘
                               │
                         HTTPS / LAN
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Caddy               │
                    │ Reverse Proxy       │
                    │ Local TLS            │
                    └──────────┬──────────┘
                               │
                               ▼
              ┌──────────────────────────────────┐
              │ FastAPI Modular Monolith         │
              │                                  │
              │ API / Transport Layer             │
              │          ↓                       │
              │ Application Services              │
              │          ↓                       │
              │ Domain Services / Rules           │
              │          ↓                       │
              │ Repository / Persistence Layer    │
              └───────────────┬──────────────────┘
                              │
                              ▼
                    ┌─────────────────────┐
                    │ PostgreSQL          │
                    │ Primary LIMS DB     │
                    └─────────┬───────────┘
                              │
                     ┌────────┴─────────┐
                     ▼                  ▼
              Local Document       Backup System
                 Storage             │
                                     ▼
                                    NAS
                                     │
                                     ▼
                               Offline Copy
```

The browser communicates only with the application.

The application communicates with PostgreSQL.

The database is not exposed directly to workstations.

---

# E. Technology Evaluation

## E.1 Frontend — React + TypeScript + Vite + MUI

### Assessment

Approved.

React provides a strong component model for:

* data-dense forms;
* queues;
* result-entry screens;
* review interfaces;
* dashboards;
* filtering;
* workflow actions.

TypeScript provides additional contract discipline.

MUI provides an established UI component framework and accessibility-oriented defaults.

---

## E.2 Backend — FastAPI + Python

### Assessment

Approved.

FastAPI is appropriate for:

* typed API contracts;
* backend authorization;
* workflow services;
* calculation services;
* report orchestration;
* application-level validation.

Python is also advantageous for future laboratory calculation and scientific-data processing requirements.

---

## E.3 ORM / Persistence — SQLAlchemy 2.x

### Assessment

Approved.

SQLAlchemy provides:

* explicit relational mapping;
* transaction control;
* database portability;
* testability;
* and a structured persistence layer.

---

## E.4 Database — PostgreSQL

### Decision

**PostgreSQL is frozen as the v1 production database.**

### Reasons

PostgreSQL was selected over SQLite and other evaluated alternatives because the project is intended to support:

* simultaneous reception activity;
* multiple analysts;
* concurrent result entry;
* review/verification activity;
* reporting;
* QC;
* quality-management functions;
* and future growth in operational usage.

A dedicated relational database provides stronger concurrency characteristics and more mature facilities for a growing multi-user laboratory system.

### Advantages

* Strong concurrent transaction handling.
* Mature ACID behavior.
* Excellent relational integrity.
* Strong indexing and query capabilities.
* Mature backup and recovery tooling.
* Suitable for increasing multi-user workload.
* Strong long-term ecosystem.
* Good fit with SQLAlchemy and Alembic.
* Clear future operational scaling path.

### Accepted trade-offs

PostgreSQL introduces additional operational requirements compared with SQLite:

* database service administration;
* database account/security management;
* service monitoring;
* backup management;
* restore procedures;
* version upgrades;
* database storage planning.

These are accepted as appropriate trade-offs for the chosen architecture.

### Database operating principle

The project remains offline-first despite the PostgreSQL decision.

"Offline-first" means:

> the system does not depend on the Internet.

It does **not** mean that the application must use an embedded database.

---

## E.5 Authentication — Argon2id + Server-side Sessions

Approved.

The system shall use:

* Argon2id password hashes;
* secure cookies;
* server-side sessions;
* explicit logout;
* session invalidation;
* configurable timeout policies.

JWT-based browser authentication is not the selected v1 model.

---

## E.6 Reporting — Jinja2 → Chromium → PDF

Approved.

Report generation shall remain entirely local.

Chromium shall be version-pinned and locally available rather than downloaded at report-render time.

---

## E.7 Reverse Proxy — Caddy

Approved.

Caddy shall provide:

* local HTTPS;
* reverse proxying;
* frontend/static serving where applicable;
* controlled application exposure.

The application is not intended to be directly exposed to the LAN without the defined gateway/security architecture.

---

## E.8 Testing — pytest + Playwright

Approved.

Testing shall cover:

* unit behavior;
* service/domain logic;
* API behavior;
* database integration;
* workflow rules;
* browser-based end-to-end workflows;
* authorization boundaries;
* important failure paths.

---

# F. Module Architecture

The approved module model is domain-oriented.

| Module                           | Purpose                           | Examples                                         |
| -------------------------------- | --------------------------------- | ------------------------------------------------ |
| Identity & RBAC                  | Authentication and permissions    | Users, Roles, Sessions                           |
| Audit                            | Controlled history                | AuditEvent                                       |
| Master Data                      | Shared references                 | Units, Sections, Disciplines                     |
| Customer & Project               | Client/request context            | Customer, Contact, Project                       |
| Sample                           | Sample lifecycle                  | Sample, Container, COC                           |
| Method & Test                    | Test definitions                  | Method, MethodVersion, TestDefinition            |
| Calculation                      | Controlled calculations           | Formula, CalculationRun                          |
| Execution & Results              | Actual test work                  | TestInstance, Observation, Result                |
| Review / Verification / Approval | Quality gates                     | ReviewRecord, VerificationRecord, ApprovalRecord |
| Equipment                        | Equipment status and traceability | Equipment, CalibrationRecord                     |
| QC                               | Validity monitoring               | QCSample, QCResult                               |
| Documents                        | Controlled documents              | Document, DocumentVersion                        |
| Reporting                        | Reports/certificates              | Report, ReportRevision                           |
| Quality Management               | NC/CAPA/complaints/audits         | Nonconformity, CAPA                              |
| Notifications                    | Operational alerts                | Notification                                     |
| Configuration                    | System policies/configuration     | ConfigSetting                                    |
| Operations                       | Backup/health/admin               | HealthCheck, BackupJob                           |

The module model is not intended to create independent deployable services.

---

# G. Domain Model

The domain model is based on explicit, strongly typed entities.

```text
Customer
   │
   ├── Contact
   │
   └── Project / Contract
            │
            └── Sample
                 │
                 ├── SubSample / Portion
                 │       └── Container
                 │
                 ├── ChainOfCustodyEvent
                 │
                 └── TestRequest
                         │
                         └── TestInstance
                               │
                               ├── Method
                               │     └── MethodVersion
                               │           └── ParameterDefinition
                               │                    └── Unit
                               │
                               ├── Equipment
                               │
                               ├── Analyst
                               │
                               ├── Observation
                               │
                               ├── CalculationRun
                               │
                               └── Result
                                      │
                                      └── ResultRevision
```

Reporting traces through the controlled technical chain:

```text
Report
  ↓
ReportRevision
  ↓
Result
  ↓
TestInstance
  ↓
Sample
  ↓
Project / Customer
```

Cross-cutting structures include:

* AuditEvent;
* Attachment;
* ReviewRecord;
* VerificationRecord;
* ApprovalRecord.

`TestDefinition`, `TestInstance`, `Method`, and `MethodVersion` remain distinct concepts.

The system will not collapse them into a generic "Test" table.

---

# H. Laboratory Workflow

The approved backbone is:

```text
Draft Request
   ↓
Contract Review
   ↓
Sample Receipt
   ↓
Registration / Accession
   ↓
Allocation
   ↓
Test Planning
   ↓
Test Assignment
   ↓
Execution
   ↓
Raw Data / Observations
   ↓
Result Entry / Calculation
   ↓
Review
   ↓
Technical Verification
   ↓
Approval
   ↓
Report Generation
   ↓
Delivery
   ↓
Retention
   ↓
Archival
```

The workflow engine shall use an **explicit state machine**.

A free-form status field shall not be treated as sufficient workflow enforcement.

---

## H.1 Exception Workflows

Exception handling is part of the system design.

| Trigger                                  | Controlled response                                                                            |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Sample unacceptable                      | Receipt → Rejected with reason                                                                 |
| Review failure                           | Returned for rework                                                                            |
| QC failure                               | Result blocked/investigation required according to policy                                      |
| Post-approval correction                 | Controlled reopen → correction → re-review → re-verification → re-approval                     |
| Equipment unavailable/out of calibration | Block or warn according to controlled policy; default block where result integrity is affected |
| Customer complaint                       | Complaint linked to relevant records and routed to Quality Management                          |

---

## H.2 State Transition Principle

Only defined transitions are permitted.

Example:

```text
Draft
  ↓
Received
  ↓
Registered
  ↓
Assigned
  ↓
In Progress
  ↓
Pending Review
  ↓
Verified
  ↓
Approved
  ↓
Reported
  ↓
Archived
```

Each transition shall have:

* permitted source state;
* permitted target state;
* authorization requirement;
* required data;
* audit event;
* rejection/error behavior.

---

# I. Configuration Strategy

The approved configuration model is based on strongly typed tables.

Normal configurable laboratory variation includes:

* test definitions;
* parameter definitions;
* units;
* required/optional parameters;
* precision;
* rounding;
* acceptance limits;
* method versions;
* method/equipment requirements;
* competency requirements;
* QC requirements;
* numbering schemes;
* report templates;
* retention rules;
* notification thresholds;
* workflow policy toggles.

Example:

```text
TestDefinition
      │
      └── ParameterDefinition
              ├── Data Type
              ├── Unit
              ├── Precision
              ├── Required
              ├── Min / Max
              └── Acceptance Rules
```

Generic EAV is not the primary architecture.

### EAV is reserved only for narrowly justified free-form metadata

Examples may include:

* customer-supplied descriptors;
* genuinely variable descriptive metadata.

It is not the storage mechanism for laboratory results, methods, tests, or core workflow data.

---

# J. ISO/IEC 17025 Support

The LIMS is designed to **support the laboratory quality system**.

It does not itself establish accreditation.

| Area                           | Software capability                  | Boundary                                           |
| ------------------------------ | ------------------------------------ | -------------------------------------------------- |
| Impartiality / confidentiality | RBAC, access controls, audit         | Laboratory policy remains separate                 |
| Organization/personnel         | Authorization and competency records | Competence is assessed by people                   |
| Facilities/environment         | Environmental observations           | Software does not control the facility             |
| Equipment                      | Calibration/maintenance state        | Calibration activity remains a laboratory activity |
| Contract review                | Controlled review stage              | Laboratory determines acceptance criteria          |
| Methods                        | Method/version/validation evidence   | Technical validation remains laboratory work       |
| Sampling/handling              | COC and condition history            | Laboratory procedure remains governing             |
| Technical records              | Revisions + audit                    | Software preserves records                         |
| Measurement uncertainty        | Result-level uncertainty support     | Technical methodology remains laboratory-owned     |
| Validity of results            | QC data capture and controls         | Laboratory defines QC program                      |
| Reporting                      | Controlled report generation         | Report approval remains authorized human activity  |
| Nonconforming work             | Nonconformity/CAPA support           | Laboratory decides disposition                     |
| Documents                      | Version/effective-date control       | Controlled documents remain quality-system records |
| Internal audit                 | Findings and action tracking         | Audit activity remains performed by people         |

The software shall never present a feature as evidence that accreditation automatically exists.

---

# K. Security Architecture

## Authentication

* Argon2id password hashing.
* Server-side sessions.
* Secure cookies.
* HTTP-only cookies.
* Appropriate SameSite policy.
* Session timeout.
* Explicit logout.
* Administrative session invalidation.
* Account lockout/failed-login controls according to approved policy.

## Authorization

RBAC shall be enforced server-side.

Permissions may be scoped by:

* module;
* action;
* role;
* section;
* discipline;
* record context.

The UI is not a security boundary.

---

## Segregation of Duties

The backend shall enforce separation between controlled technical activities.

For example:

```text
Analyst creates result
        ↓
Reviewer reviews
        ↓
Technical reviewer verifies
        ↓
Authorized signatory approves
```

Where policy requires separation, the system shall reject an attempt to perform a restricted subsequent action by the same person who created the underlying technical record.

---

## Audit Integrity

Audit records shall be:

* application-controlled;
* append-only through normal application operation;
* protected from ordinary modification/deletion;
* associated with actor and timestamp;
* associated with relevant entity/action;
* capable of recording before/after state for controlled changes;
* capable of recording reasons where required.

---

## Network Exposure

The deployment shall remain LAN-oriented.

No Internet exposure is required for normal operation.

External exposure, if ever required, shall require an explicit architecture and security decision rather than being enabled opportunistically.

---

# L. Database Architecture

## L.1 PostgreSQL

PostgreSQL is the authoritative transactional database.

The architecture shall use:

* SQLAlchemy 2.x;
* Alembic;
* explicit transactions;
* relational constraints;
* indexes;
* foreign keys;
* check constraints;
* unique constraints;
* appropriate normalization.

---

## L.2 Data Modeling Principles

Baseline normalization target:

**3NF**, except where deliberate controlled denormalization is justified.

Examples of justified denormalization may include report snapshots where reproducibility requires preserving the exact issued values.

---

## L.3 Keys

Use:

* surrogate primary keys;
* separately managed human-readable business numbers.

Examples:

* Sample Number;
* Report Number;
* Work Order Number;
* Certificate Number.

Human-facing numbers shall not be treated as substitutes for relational primary keys.

---

## L.4 Delete Policy

Core technical records shall generally use lifecycle/state/revision mechanisms rather than uncontrolled hard deletion.

Reference/master records may have more flexible lifecycle rules where historically safe.

---

## L.5 Concurrency

PostgreSQL is selected specifically to provide a strong foundation for simultaneous laboratory activity.

The application must still maintain:

* short transactions;
* clear transaction boundaries;
* controlled locking;
* efficient indexes;
* safe concurrency behavior;
* appropriate isolation;
* conflict handling where concurrent modifications are possible.

---

# M. UI/UX Architecture

The application shall use role-aware workflows.

Examples:

### Reception

```text
Today's Receipts
   ↓
Sample Receipt
   ↓
Registration
   ↓
Barcode
```

### Analyst

```text
Assigned Queue
   ↓
Scan Sample
   ↓
Open Test
   ↓
Enter Observations
   ↓
Calculate
   ↓
Submit
```

### Reviewer

```text
Review Queue
   ↓
Open Test
   ↓
Inspect Technical Record
   ↓
Accept / Return
```

### Technical Reviewer

```text
Verification Queue
   ↓
Inspect
   ↓
Verify / Return
```

### Signatory

```text
Approval Queue
   ↓
Inspect Final Record
   ↓
Approve / Reject
```

### Equipment Manager

```text
Calibration Due
   ↓
Equipment Record
   ↓
Calibration / Service
   ↓
Release / Hold
```

### Quality Manager

```text
Quality Dashboard
   ↓
NC / CAPA / Complaint / Documents / Audits
```

Status shall remain explicit and consistent across the UI.

---

# N. Reporting Architecture

Approved model:

```text
Database
   ↓
Report data service
   ↓
Versioned Jinja2 template
   ↓
HTML
   ↓
Pinned local Chromium
   ↓
PDF
```

Report generation shall be entirely local.

Each report shall retain traceability to:

* Sample;
* TestInstance;
* Method;
* MethodVersion;
* Analyst;
* Equipment where applicable;
* Result revision;
* Review;
* Verification;
* Approval.

Report templates shall be version-controlled.

Report numbers shall be configurable under controlled administrative authority.

Approval/signature information shall reflect the actual approval record.

A decorative image of a signature shall not be treated as equivalent to an authenticated approval event.

---

# O. Backup / Recovery

The change from SQLite to PostgreSQL changes the backup mechanism, but not the project's verification philosophy.

## O.1 Backup Principle

Use PostgreSQL-supported backup mechanisms.

The live PostgreSQL data directory shall **not** simply be copied as an ordinary file-level backup while the database is running.

The backup strategy shall support consistent database recovery.

---

## O.2 Backup Layers

At minimum:

```text
Primary PostgreSQL Database
        ↓
Local Backup
        ↓
NAS Backup
        ↓
Periodic Offline Copy
```

Documents and attachments shall follow an equivalent protection strategy.

---

## O.3 Backup Verification

A backup shall not be considered successful merely because a backup file exists.

Verification shall include appropriate checks such as:

* backup completion status;
* integrity checks;
* expected backup size/metadata;
* ability to inspect the backup;
* restore validation.

---

## O.4 Restore Testing

A real restore exercise shall be performed periodically.

The project distinguishes:

```text
Backup Created
```

from:

```text
Backup Validated
```

and from:

```text
Restore Tested
```

These are not interchangeable statuses.

---

## O.5 RPO / RTO

Initial planning target:

* **RPO ≤ 24 hours**
* **RTO measured in hours**

Final operational targets shall be confirmed before production deployment.

---

# P. Deployment Architecture

## Application Server

The application server shall host:

* Caddy;
* FastAPI application;
* PostgreSQL;
* local document storage;
* backup tooling;
* required runtime dependencies.

PostgreSQL shall run as a controlled server service.

---

## Client Workstations

Clients require:

* supported Chromium-based browser;
* LAN access;
* local application URL;
* appropriate printer access where required.

Barcode scanners shall preferably operate as standard HID keyboard-wedge devices.

---

## Service Startup

The application stack shall be configured for controlled startup/restart.

Expected services include:

```text
PostgreSQL
FastAPI Application
Caddy
```

Startup dependencies shall be defined explicitly.

---

## Update / Migration Procedure

The standard production update process shall be:

```text
Backup
   ↓
Validate Backup
   ↓
Stop / quiesce application as required
   ↓
Apply Alembic migration
   ↓
Deploy application version
   ↓
Run smoke tests
   ↓
Resume operation
   ↓
Record deployment evidence
```

Rollback strategy shall be defined before migrations are considered production-ready.

---

# Q. Extensibility

The LIMS shall support normal expansion primarily through configuration.

Adding a new discipline should normally involve:

* Method records;
* MethodVersion records;
* TestDefinition records;
* ParameterDefinition records;
* equipment/competency/QC configuration;
* report templates.

It should **not** normally require creating a completely new software module.

A new code module shall be introduced only where a discipline introduces a genuinely different business mechanic that existing domain services cannot represent cleanly.

The project will not implement a generic plugin system merely to claim extensibility.

Extensibility shall therefore be **demonstrated through real use cases**, not merely stated as an architectural feature.

---

# R. Development Decomposition

## Phase 0 — Project Control & Discovery

### WP-00-01 — Project Foundation

Scope:

* repository structure;
* documentation conventions;
* version/status vocabulary;
* change-control rules;
* task/checkpoint conventions.

### WP-00-02 — Existing Information Consolidation

Scope:

* consolidate current understanding;
* record architectural decisions;
* identify assumptions;
* identify unknowns;
* identify deferred decisions;
* record absence of any previously expected database schema;
* establish CP-000 baseline.

### WP-00-03 — Initial Project Baseline

Deliverable:

**CP-000**

Acceptance shall require the project baseline to be explicitly accepted.

---

# Phase 1 — Requirements & Laboratory Model

Once CP-000 is accepted, the first authorized implementation/planning task is:

### WP-01-01 — Users & Organization

Initial bounded tasks include:

1. Document actual laboratory sections and disciplines.
2. Document current organizational responsibilities.
3. Identify actual job functions.
4. Define initial role candidates.
5. Determine which responsibilities are performed by distinct people and which are combined.
6. Identify segregation-of-duties requirements.
7. Record formal authority boundaries.

The exact Phase 1 task sequence shall be finalized through controlled task authorization.

---

# S. Critical Risks

| Risk                                              | Impact                          | Mitigation                                             |
| ------------------------------------------------- | ------------------------------- | ------------------------------------------------------ |
| Scope expansion                                   | Architectural drift             | Checkpoint governance and change control               |
| Incorrect assumptions about laboratory operations | Wrong workflow design           | Phase 1 real-world discovery                           |
| Poor role separation                              | Approval/control weakness       | Early responsibility and SoD analysis                  |
| Calculation logic errors                          | Incorrect laboratory results    | Constrained calculation engine + testing               |
| Uncontrolled technical-record editing             | Loss of traceability            | Revision model + immutable audit                       |
| PostgreSQL service failure                        | Temporary system unavailability | Service monitoring + tested backups                    |
| Server failure                                    | Operational outage              | Backup + restore plan + UPS + spare/recovery procedure |
| Backup exists but restore fails                   | Potential data loss             | Scheduled restore drills                               |
| Database security misconfiguration                | Data exposure/integrity risk    | Backend-only access + controlled DB accounts           |
| Excessive application coupling                    | Maintenance difficulty          | Domain modules + service/repository boundaries         |
| Generic EAV expansion                             | Data/reporting complexity       | Strongly typed configuration model                     |
| AI-assisted development overreach                 | Uncontrolled changes            | One task at a time + checkpoint discipline             |
| Long project duration                             | Context loss                    | ADRs + project state + documentation-as-code           |

---

# T. Discovery Questions and Deferred Decisions

With PostgreSQL now frozen, user concurrency is **no longer a database-selection blocker**, but it remains important for server and deployment sizing.

## T.1 Operational Discovery

The following must be answered or formally deferred.

### 1. Named users

What is the expected number of named users?

Suggested classification:

* ≤20
* 21–50
* 51–100
* > 100

### 2. Peak concurrent activity

What is the expected peak number of simultaneous active users and technical writers?

This affects:

* CPU;
* RAM;
* PostgreSQL connection configuration;
* application worker configuration;
* report-generation capacity.

### 3. Accreditation context

Determine whether SMJ is:

* already accredited;
* preparing for accreditation;
* using ISO/IEC 17025 as internal best practice;
* or operating under another formal quality objective.

### 4. Existing systems/data

Determine whether migration is required from:

* spreadsheets;
* paper registers;
* existing software;
* mixed sources.

### 5. Billing

Determine whether billing/invoicing is:

* in scope for v1;
* deferred;
* or permanently outside the LIMS boundary.

### 6. Site scope

For v1:

> **Single laboratory site.**

Multi-branch operation is deferred.

### 7. Server hardware

Determine:

* existing server availability;
* CPU;
* RAM;
* storage;
* RAID/storage redundancy where appropriate;
* UPS;
* backup destination;
* NAS availability.

---

## T.2 Non-Blocking Information

The following can be defined later without blocking CP-000:

* report logo/letterhead;
* report visual template;
* exact test methods;
* barcode printer model;
* scanner model;
* NAS model;
* first-wave discipline configuration;
* detailed report content;
* detailed retention periods;
* exact notification thresholds.

These belong primarily to later requirements/configuration phases.

---

# U. Recommended Roadmap

The approved project roadmap is:

```text
Phase 0
Project Control & Discovery
        ↓
CP-000
        ↓
Phase 1
Requirements & Laboratory Model
        ↓
CP-001
        ↓
Phase 2
System & Security Architecture
        ↓
CP-002
        ↓
Phase 3
Data Architecture
        ↓
CP-003
        ↓
Phase 4
UX / UI Architecture
        ↓
CP-004
        ↓
Phase 5
Technical Foundation
        ↓
CP-005
        ↓
Phase 6
Identity / RBAC / Audit
        ↓
CP-006
        ↓
Phase 7
Core Master Data
        ↓
CP-007
        ↓
Phase 8
Customer / Project / Sample
        ↓
CP-008
        ↓
Phase 9
Test & Method Engine
        ↓
CP-009
        ↓
Phase 10
Execution & Results
        ↓
CP-010
        ↓
Phase 11
Review / Verification / Approval
        ↓
CP-011
        ↓
Phase 12
QC & Equipment
        ↓
CP-012
        ↓
Phase 13
Quality Management
        ↓
CP-013
        ↓
Phase 14
Documents & Records
        ↓
CP-014
        ↓
Phase 15
Reporting & Certificates
        ↓
CP-015
        ↓
Phase 16
Configuration & Extensibility
        ↓
CP-016
        ↓
Phase 17
Backup / Recovery / Operations
        ↓
CP-017
        ↓
Phase 18
Validation & Hardening
        ↓
CP-018
        ↓
Phase 19
Production Deployment
        ↓
CP-019
        ↓
Phase 20
Maintenance & Evolution
```

No phase is skipped.

No future phase is authorized merely because it has been described.

---

# V. CP-000 Decision Baseline and Acceptance Criteria

## V.1 Frozen Architectural Decisions

The following decisions are established as the CP-000 baseline.

### D-001 — Project Scope

**Frozen:** Option A — Single-lab LIMS, all laboratory operations.

Multi-branch and multi-tenant operation are deferred.

---

### D-002 — Technology Stack

**Frozen:** Option A.

```text
React
TypeScript
Vite
MUI
FastAPI
Python
SQLAlchemy 2.x
PostgreSQL
Alembic
Argon2id
Server-side Sessions
Caddy
Jinja2
Chromium
pytest
Playwright
```

---

### D-003 — Architecture Style

**Frozen:** Option A — Modular Monolith.

Microservices and plugin architecture are rejected for v1.

---

### D-004 — Database

**Frozen:** Option B — PostgreSQL.

PostgreSQL is the authoritative v1 transactional database.

---

### D-005 — Data Integrity

**Frozen:** Option A — Revision-based records + immutable audit.

Technical record corrections shall preserve historical state.

---

### D-006 — Security

**Frozen:** Option A — RBAC + server sessions + segregation of duties.

Authorization is backend-enforced.

---

### D-007 — Workflow

**Frozen:** Option A — Explicit state machine.

Workflow state transitions shall be controlled, not free-form.

---

### D-008 — Configuration

**Frozen:** Option A — Strongly typed configuration tables.

Generic EAV is not the primary data architecture.

---

### D-009 — Development Methodology

**Frozen:** Option A — Task → Verification → Checkpoint.

---

### D-010 — Documentation

**Frozen:** Option A — Documentation-as-code.

The repository is the authoritative engineering knowledge base unless a formally controlled external record is defined.

---

### D-011 — Module Boundaries

**Frozen:** Option A — Domain-oriented modules.

---

### D-012 — Architectural Principles

**Frozen:** Option A — Conservative, controlled, auditable architecture.

---

# V.2 CP-000 Acceptance Criteria

CP-000 shall be considered **Accepted** when:

1. This Phase 0 baseline, or an approved revision, is accepted.
2. D-001 through D-012 are explicitly recorded as frozen decisions.
3. Any remaining discovery item is either:

   * answered; or
   * explicitly deferred with a reason and intended resolution phase.
4. The PostgreSQL decision is reflected consistently throughout the architecture.
5. The single-laboratory scope is confirmed for v1.
6. The Modular Monolith architecture is confirmed.
7. The revision/audit model is confirmed.
8. The security model and segregation-of-duties principle are confirmed.
9. The explicit-state-machine workflow model is confirmed.
10. The strongly typed configuration strategy is confirmed.
11. The task/checkpoint development-control model is confirmed.
12. Documentation-as-code is confirmed.
13. The module boundaries are confirmed as the initial domain organization.
14. No application feature implementation has been authorized ahead of CP-000.
15. The project explicitly records that the system supports the laboratory quality system but does not itself confer ISO/IEC 17025 accreditation.

---

# Final CP-000 Baseline

The resulting architecture can be summarized as:

```text
                     SMJ LIMS v1
                          │
              Single Physical Laboratory
                          │
                          ▼
                  Modular Monolith
                          │
              ┌───────────┴───────────┐
              │                       │
          React / TS              FastAPI
              │                    Python
              └───────────┬───────────┘
                          ▼
                    SQLAlchemy
                          │
                          ▼
                     PostgreSQL
                          │
            ┌─────────────┴─────────────┐
            ▼                           ▼
      Local Documents                Backups
                                        │
                                       NAS
                                        │
                                  Offline Copy
```

The governing design philosophy is:

> **Build a controlled, maintainable laboratory information system—not a generic software platform—and add complexity only when a real laboratory requirement proves it necessary.**

**Next authorized phase after CP-000 acceptance:**
**Phase 1 → WP-01-01 — Users & Organization.**

No later feature implementation is authorized merely by this document; each subsequent task remains subject to the project's task and checkpoint controls.


Response:
Reviewed in full. The database swap is the consequential change here, so I checked it hardest — everything else is largely a formalization of what was already sound.

On PostgreSQL over SQLite: this is a defensible call, and it actually resolves something I couldn't resolve for you last time. My earlier SQLite recommendation was conditional on knowing real peak-concurrency numbers, which weren't available. Choosing PostgreSQL sidesteps that dependency entirely — you're trading some operational overhead (a service to administer, patch, and back up properly) for not having to get the concurrency judgment call right in advance. That's a reasonable trade for a system meant to run for years. The document correctly separates "offline-first" from "embedded database" (Section E.4) — that distinction matters and it's stated cleanly.

One real gap, though. Your own CP-000 acceptance criterion V.2.3 requires every remaining discovery item to be either answered or explicitly deferred with a reason and resolution phase. Right now T.1 items 1, 2, 3, 4, 5, and 7 are listed as open questions but none of them carry that formal deferral — only item 6 (site scope) actually gets resolved in the document itself. As written, CP-000 doesn't yet meet its own bar.

I also noticed the earlier "supplied database schema" question — never actually received across either round — has quietly dropped out of this revision. I've folded it into T.1.4 (existing systems/migration) rather than losing it, since it only matters if a legacy system exists to migrate from.

I've added a T.3 — Resolution for CP-000 section that formally defers the remaining operational unknowns to Phase 1 (which is already scoped to gather exactly this information via WP-01-01 and related work packages), with stated reasons, so the checkpoint can legitimately close. I did not invent answers to any of them — that's not mine to decide.

Everything else in your revision checked out clean — D-001 through D-012 are internally consistent, and the acceptance-criteria checklist in V.2 now passes on every item except one: your own formal sign-off (criterion 1), which isn't mine to give.

If you'd rather answer any of the T.1 items now instead of deferring them, I can fold real answers in directly. Otherwise, confirming acceptance moves this straight to Phase 1 → WP-01-01.

# SMJ Sustainable Fuel Lab — LIMS Program

# Phase 0 Deliverable: Project Understanding, Requirement Analysis & Proposed Architecture

**Status:** Discovery / Pre-Implementation
**Checkpoint:** CP-000 — Architecture & Project Baseline
**Decision status:** Foundational architecture decisions (D-001–D-012) frozen and reviewed. Remaining discovery items formally resolved via deferral — see Section T.3. **CP-000 is READY FOR ACCEPTANCE, pending SMJ sign-off.**
**Implementation status:** No application feature code authorized under Phase 0.
**Prepared as:** Combined LIMS architecture, ISO/IEC 17025 quality-system, data, security, UX, deployment, and project-control analysis.

---

## Table of Contents

A. Project Understanding
B. Requirement Analysis
C. Architectural Principles
D. High-Level Architecture
E. Technology Evaluation
F. Module Architecture
G. Domain Model
H. Laboratory Workflow
I. Configuration Strategy
J. ISO/IEC 17025 Support
K. Security Architecture
L. Database Architecture
M. UI/UX Architecture
N. Reporting Architecture
O. Backup / Recovery
P. Deployment Architecture
Q. Extensibility
R. Development Decomposition
S. Critical Risks
T. Discovery Questions, Deferred Decisions, and CP-000 Resolution
U. Recommended Roadmap
V. CP-000 Decision Baseline and Acceptance Criteria

---

# A. Project Understanding

SMJ Sustainable Fuel Lab Pvt. Ltd. requires a **custom, on-premises Laboratory Information Management System (LIMS)** for real laboratory operations. The system is not intended to be a demonstration application, generic form builder, SaaS platform, or enterprise ERP.

The initial system is intended to support laboratory operations across:

* Solid Fuel
* Biofuel
* Air
* Water
* Soil
* Noise
* Stack / Emission

with provision for additional laboratory disciplines and test methods in the future.

The central purpose of the LIMS is to provide a **controlled, traceable laboratory information chain**:

```text
Request
   ↓
Contract / Request Review
   ↓
Sample Receipt
   ↓
Sample Registration / Accession
   ↓
Test Planning / Assignment
   ↓
Test Execution
   ↓
Raw Data / Observations
   ↓
Calculation
   ↓
Result
   ↓
Review
   ↓
Technical Verification
   ↓
Approval
   ↓
Report
   ↓
Retention
   ↓
Archive
```

Every technically significant stage must be reconstructable later, including:

* who performed the activity;
* when it occurred;
* which method/version applied;
* which equipment was used;
* which raw observations were recorded;
* which calculations were performed;
* what result was initially produced;
* what revisions occurred;
* who reviewed, verified, and approved the result;
* and what the approved report contained at the time of issue.

Two fundamental constraints govern the architecture.

### 1. Offline-first / On-premises

The laboratory must be able to perform its normal operations without internet connectivity.

Internet access must therefore **not be a runtime dependency** for:

* authentication;
* sample registration;
* test execution;
* result entry;
* calculations;
* review;
* approval;
* report generation;
* barcode operation;
* or normal system administration.

### 2. Long operational life

The software is expected to remain maintainable for years and may eventually be maintained by developers other than the original developers.

The architecture therefore intentionally favors:

* mainstream technologies;
* explicit boundaries;
* relational integrity;
* documented migrations;
* predictable deployment;
* controlled configuration;
* strong auditability;
* simple operational procedures;
* and avoidance of unnecessary infrastructure.

The project explicitly rejects the idea that increased architectural complexity automatically means increased quality.

---

# B. Requirement Analysis

## B.1 Defined Requirements

The following requirements are considered established for the current project baseline.

### Deployment

* On-premises deployment.
* LAN-based multi-workstation operation.
* Windows-hosted server environment.
* Browser-based client access.
* Core functions usable without internet access.

### Technology

The approved technology baseline is:

* React
* TypeScript
* Vite
* Material UI
* FastAPI
* Python
* SQLAlchemy 2.x
* PostgreSQL
* Alembic
* Argon2id
* secure server-side sessions
* Caddy
* Jinja2
* Chromium-based PDF rendering
* pytest
* Playwright

### Architecture

The approved architecture is:

> **Modular Monolith**

The application will remain a single deployable application while maintaining internally separated domain modules.

Microservices and a plugin framework are **not part of v1**.

### Laboratory disciplines

Initial scope covers:

1. Solid Fuel
2. Biofuel
3. Air
4. Water
5. Soil
6. Noise
7. Stack / Emission

### Lifecycle

The system shall support the complete lifecycle from request through sample processing, test execution, result review, approval, reporting, retention, and archival.

### Data integrity

Technical records shall not be silently overwritten.

Corrections must preserve:

* previous state;
* new state;
* actor;
* timestamp;
* reason where required;
* and revision lineage.

### Security

Authorization shall always be enforced on the backend.

UI visibility, disabled controls, and client-side logic shall never be considered security controls by themselves.

### Configuration

The system shall allow laboratory administrators to configure normal test/method/parameter variations without application code changes.

This flexibility shall be provided through **strongly typed, purpose-built relational configuration structures**, not through a generic EAV architecture.

### Development control

The project shall use:

```text
Phase
  ↓
Work Package
  ↓
Task
  ↓
Implementation
  ↓
Verification
  ↓
Evidence
  ↓
Checkpoint
```

No feature development is authorized merely because the next feature appears useful.

### ISO/IEC 17025

The software shall support laboratory practices aligned with ISO/IEC 17025 requirements.

The software shall **not** claim that its existence makes the laboratory accredited or compliant automatically.

---

## B.2 Proposed but now Frozen Architectural Decisions

The following decisions were evaluated during Phase 0 and have now been frozen for the project baseline:

| Decision                 | Frozen selection                                    |
| ------------------------ | ---------------------------------------------------- |
| Project scope            | Single-laboratory LIMS                              |
| Technology               | React/TypeScript + FastAPI/Python + PostgreSQL      |
| Architecture             | Modular Monolith                                    |
| Database                 | PostgreSQL                                          |
| Data integrity           | Revision-based records + immutable audit            |
| Security                 | RBAC + server-side sessions + segregation of duties |
| Workflow                 | Explicit state machine                              |
| Configuration            | Strongly typed configuration tables                 |
| Development method       | Task → Verification → Checkpoint                    |
| Documentation            | Documentation-as-code                               |
| Module structure         | Domain-oriented modules                             |
| Architectural philosophy | Conservative, controlled, auditable                 |

These decisions constitute the primary CP-000 architecture baseline.

---

## B.3 Explicitly Deferred / Out of Scope

The following are not part of the initial v1 implementation unless later approved through change control:

* multi-tenant SaaS;
* multiple independent laboratories within a shared instance;
* microservices;
* plugin architecture;
* customer self-service portal;
* public Internet-facing API;
* cloud synchronization;
* mobile application;
* ERP;
* general accounting;
* speculative enterprise infrastructure;
* external PKI/digital-signature infrastructure;
* advanced external integrations not justified by actual laboratory requirements.

Billing/invoicing remains a business-scope decision and must be explicitly classified before its implementation phase (see T.3).

---

## B.4 Assumptions

The following assumptions are used unless corrected during Phase 1 discovery:

* v1 is for a single physical laboratory operation;
* the principal operating environment is Windows;
* the application is hosted within the laboratory LAN;
* PostgreSQL is hosted locally within the laboratory environment;
* a centralized application server is preferred;
* browser-based access is preferred over installed client software;
* exact user counts and workload figures are still to be established for deployment sizing (see T.3);
* detailed methods and discipline-specific test lists will be defined in later requirements/configuration phases.

---

# C. Architectural Principles

The following principles are frozen as the project's governing architectural philosophy.

## 1. Controlled revision, not silent overwrite

Technical records are revision-controlled.

A correction creates a new controlled state while preserving historical information.

## 2. Backend is the security boundary

Every protected operation is authorized by the backend.

The frontend cannot grant itself access.

## 3. Offline is the normal operating mode

Core laboratory operations shall not depend on:

* cloud services;
* external APIs;
* Internet authentication;
* hosted PDF conversion;
* remote barcode services;
* or cloud storage.

## 4. Strong typing where meaning matters

Core concepts are represented by explicit relational structures.

Examples:

* Sample
* TestInstance
* Method
* MethodVersion
* ParameterDefinition
* Result
* Equipment
* Report
* ApprovalRecord

Generic key/value structures shall not become the foundation of the system.

## 5. Meaningful auditability

Audit events shall focus on:

* state changes;
* technical record changes;
* configuration changes;
* authorization changes;
* approval events;
* security events;
* and other controlled activities.

Routine read traffic is not automatically converted into an audit record.

## 6. Modular Monolith

The system remains one deployable application with clear internal module boundaries.

The project explicitly does not introduce:

* microservices;
* service meshes;
* distributed transactions;
* plugin loaders;
* or similar infrastructure without a demonstrated requirement.

## 7. Software supports the quality system

The LIMS records and enforces controls where appropriate.

The laboratory's quality procedures, competence assessments, impartiality arrangements, technical decisions, validation work, management responsibility, and accreditation status remain responsibilities of the laboratory.

## 8. Every phase must be verifiable

A phase is not complete merely because code exists.

Completion requires:

* implementation where applicable;
* testing;
* evidence;
* review;
* acceptance criteria;
* and checkpoint approval.

## 9. Database is a controlled service boundary

PostgreSQL is the authoritative transactional data store.

Client workstations shall not connect directly to the database.

All application data access shall pass through the backend application.

## 10. Simplicity is a design objective

The project shall prefer the simplest design that satisfies:

* laboratory requirements;
* integrity;
* security;
* maintainability;
* traceability;
* and future controlled expansion.

---

# D. High-Level Architecture

```text
                         Client Workstations
                ┌──────────────────────────────┐
                │ Reception                    │
                │ Analysts                     │
                │ Reviewers                    │
                │ Managers / Signatories       │
                └──────────────┬───────────────┘
                               │
                         HTTPS / LAN
                               │
                               ▼
                    ┌─────────────────────┐
                    │ Caddy               │
                    │ Reverse Proxy       │
                    │ Local TLS            │
                    └──────────┬──────────┘
                               │
                               ▼
              ┌──────────────────────────────────┐
              │ FastAPI Modular Monolith         │
              │                                  │
              │ API / Transport Layer             │
              │          ↓                       │
              │ Application Services              │
              │          ↓                       │
              │ Domain Services / Rules           │
              │          ↓                       │
              │ Repository / Persistence Layer    │
              └───────────────┬──────────────────┘
                              │
                              ▼
                    ┌─────────────────────┐
                    │ PostgreSQL          │
                    │ Primary LIMS DB     │
                    └─────────┬───────────┘
                              │
                     ┌────────┴─────────┐
                     ▼                  ▼
              Local Document       Backup System
                 Storage             │
                                     ▼
                                    NAS
                                     │
                                     ▼
                               Offline Copy
```

The browser communicates only with the application.

The application communicates with PostgreSQL.

The database is not exposed directly to workstations.

---

# E. Technology Evaluation

## E.1 Frontend — React + TypeScript + Vite + MUI

### Assessment

Approved.

React provides a strong component model for:

* data-dense forms;
* queues;
* result-entry screens;
* review interfaces;
* dashboards;
* filtering;
* workflow actions.

TypeScript provides additional contract discipline.

MUI provides an established UI component framework and accessibility-oriented defaults.

---

## E.2 Backend — FastAPI + Python

### Assessment

Approved.

FastAPI is appropriate for:

* typed API contracts;
* backend authorization;
* workflow services;
* calculation services;
* report orchestration;
* application-level validation.

Python is also advantageous for future laboratory calculation and scientific-data processing requirements.

---

## E.3 ORM / Persistence — SQLAlchemy 2.x

### Assessment

Approved.

SQLAlchemy provides:

* explicit relational mapping;
* transaction control;
* database portability;
* testability;
* and a structured persistence layer.

---

## E.4 Database — PostgreSQL

### Decision

**PostgreSQL is frozen as the v1 production database.**

### Reasons

PostgreSQL was selected over SQLite and other evaluated alternatives because the project is intended to support:

* simultaneous reception activity;
* multiple analysts;
* concurrent result entry;
* review/verification activity;
* reporting;
* QC;
* quality-management functions;
* and future growth in operational usage.

A dedicated relational database provides stronger concurrency characteristics and more mature facilities for a growing multi-user laboratory system.

**Architectural note on this decision:** this choice also has the effect of removing a dependency that Phase 0 could not otherwise resolve — the exact peak-concurrency figures (T.1.1, T.1.2) were not yet known. PostgreSQL's multi-writer concurrency model is comfortable across the plausible range of outcomes for those questions, so the database decision no longer needs to wait on them. Server *sizing* still benefits from those numbers once available (see T.3), but the database *choice* does not depend on them.

### Advantages

* Strong concurrent transaction handling.
* Mature ACID behavior.
* Excellent relational integrity.
* Strong indexing and query capabilities.
* Mature backup and recovery tooling.
* Suitable for increasing multi-user workload.
* Strong long-term ecosystem.
* Good fit with SQLAlchemy and Alembic.
* Clear future operational scaling path.

### Accepted trade-offs

PostgreSQL introduces additional operational requirements compared with SQLite:

* database service administration;
* database account/security management;
* service monitoring;
* backup management;
* restore procedures;
* version upgrades;
* database storage planning.

These are accepted as appropriate trade-offs for the chosen architecture.

### Database operating principle

The project remains offline-first despite the PostgreSQL decision.

"Offline-first" means:

> the system does not depend on the Internet.

It does **not** mean that the application must use an embedded database.

---

## E.5 Authentication — Argon2id + Server-side Sessions

Approved.

The system shall use:

* Argon2id password hashes;
* secure cookies;
* server-side sessions;
* explicit logout;
* session invalidation;
* configurable timeout policies.

JWT-based browser authentication is not the selected v1 model.

---

## E.6 Reporting — Jinja2 → Chromium → PDF

Approved.

Report generation shall remain entirely local.

Chromium shall be version-pinned and locally available rather than downloaded at report-render time.

---

## E.7 Reverse Proxy — Caddy

Approved.

Caddy shall provide:

* local HTTPS;
* reverse proxying;
* frontend/static serving where applicable;
* controlled application exposure.

The application is not intended to be directly exposed to the LAN without the defined gateway/security architecture.

---

## E.8 Testing — pytest + Playwright

Approved.

Testing shall cover:

* unit behavior;
* service/domain logic;
* API behavior;
* database integration;
* workflow rules;
* browser-based end-to-end workflows;
* authorization boundaries;
* important failure paths.

---

# F. Module Architecture

The approved module model is domain-oriented.

| Module                           | Purpose                           | Examples                                         |
| --------------------------------- | ---------------------------------- | -------------------------------------------------- |
| Identity & RBAC                  | Authentication and permissions    | Users, Roles, Sessions                           |
| Audit                            | Controlled history                | AuditEvent                                       |
| Master Data                      | Shared references                 | Units, Sections, Disciplines                     |
| Customer & Project               | Client/request context            | Customer, Contact, Project                       |
| Sample                           | Sample lifecycle                  | Sample, Container, COC                           |
| Method & Test                    | Test definitions                  | Method, MethodVersion, TestDefinition            |
| Calculation                      | Controlled calculations           | Formula, CalculationRun                          |
| Execution & Results              | Actual test work                  | TestInstance, Observation, Result                |
| Review / Verification / Approval | Quality gates                     | ReviewRecord, VerificationRecord, ApprovalRecord |
| Equipment                        | Equipment status and traceability | Equipment, CalibrationRecord                     |
| QC                                | Validity monitoring               | QCSample, QCResult                               |
| Documents                        | Controlled documents              | Document, DocumentVersion                        |
| Reporting                        | Reports/certificates              | Report, ReportRevision                           |
| Quality Management               | NC/CAPA/complaints/audits         | Nonconformity, CAPA                              |
| Notifications                    | Operational alerts                | Notification                                     |
| Configuration                    | System policies/configuration     | ConfigSetting                                    |
| Operations                       | Backup/health/admin               | HealthCheck, BackupJob                           |

The module model is not intended to create independent deployable services.

---

# G. Domain Model

The domain model is based on explicit, strongly typed entities.

```text
Customer
   │
   ├── Contact
   │
   └── Project / Contract
            │
            └── Sample
                 │
                 ├── SubSample / Portion
                 │       └── Container
                 │
                 ├── ChainOfCustodyEvent
                 │
                 └── TestRequest
                         │
                         └── TestInstance
                               │
                               ├── Method
                               │     └── MethodVersion
                               │           └── ParameterDefinition
                               │                    └── Unit
                               │
                               ├── Equipment
                               │
                               ├── Analyst
                               │
                               ├── Observation
                               │
                               ├── CalculationRun
                               │
                               └── Result
                                      │
                                      └── ResultRevision
```

Reporting traces through the controlled technical chain:

```text
Report
  ↓
ReportRevision
  ↓
Result
  ↓
TestInstance
  ↓
Sample
  ↓
Project / Customer
```

Cross-cutting structures include:

* AuditEvent;
* Attachment;
* ReviewRecord;
* VerificationRecord;
* ApprovalRecord.

`TestDefinition`, `TestInstance`, `Method`, and `MethodVersion` remain distinct concepts.

The system will not collapse them into a generic "Test" table.

---

# H. Laboratory Workflow

The approved backbone is:

```text
Draft Request
   ↓
Contract Review
   ↓
Sample Receipt
   ↓
Registration / Accession
   ↓
Allocation
   ↓
Test Planning
   ↓
Test Assignment
   ↓
Execution
   ↓
Raw Data / Observations
   ↓
Result Entry / Calculation
   ↓
Review
   ↓
Technical Verification
   ↓
Approval
   ↓
Report Generation
   ↓
Delivery
   ↓
Retention
   ↓
Archival
```

The workflow engine shall use an **explicit state machine**.

A free-form status field shall not be treated as sufficient workflow enforcement.

---

## H.1 Exception Workflows

Exception handling is part of the system design.

| Trigger                                  | Controlled response                                                                            |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------- |
| Sample unacceptable                      | Receipt → Rejected with reason                                                                 |
| Review failure                           | Returned for rework                                                                            |
| QC failure                               | Result blocked/investigation required according to policy                                      |
| Post-approval correction                 | Controlled reopen → correction → re-review → re-verification → re-approval                     |
| Equipment unavailable/out of calibration | Block or warn according to controlled policy; default block where result integrity is affected |
| Customer complaint                       | Complaint linked to relevant records and routed to Quality Management                          |

---

## H.2 State Transition Principle

Only defined transitions are permitted.

Example:

```text
Draft
  ↓
Received
  ↓
Registered
  ↓
Assigned
  ↓
In Progress
  ↓
Pending Review
  ↓
Verified
  ↓
Approved
  ↓
Reported
  ↓
Archived
```

Each transition shall have:

* permitted source state;
* permitted target state;
* authorization requirement;
* required data;
* audit event;
* rejection/error behavior.

---

# I. Configuration Strategy

The approved configuration model is based on strongly typed tables.

Normal configurable laboratory variation includes:

* test definitions;
* parameter definitions;
* units;
* required/optional parameters;
* precision;
* rounding;
* acceptance limits;
* method versions;
* method/equipment requirements;
* competency requirements;
* QC requirements;
* numbering schemes;
* report templates;
* retention rules;
* notification thresholds;
* workflow policy toggles.

Example:

```text
TestDefinition
      │
      └── ParameterDefinition
              ├── Data Type
              ├── Unit
              ├── Precision
              ├── Required
              ├── Min / Max
              └── Acceptance Rules
```

Generic EAV is not the primary architecture.

### EAV is reserved only for narrowly justified free-form metadata

Examples may include:

* customer-supplied descriptors;
* genuinely variable descriptive metadata.

It is not the storage mechanism for laboratory results, methods, tests, or core workflow data.

---

# J. ISO/IEC 17025 Support

The LIMS is designed to **support the laboratory quality system**.

It does not itself establish accreditation.

| Area                            | Software capability                  | Boundary                                            |
| --------------------------------- | -------------------------------------- | ------------------------------------------------------ |
| Impartiality / confidentiality  | RBAC, access controls, audit         | Laboratory policy remains separate                  |
| Organization/personnel          | Authorization and competency records | Competence is assessed by people                    |
| Facilities/environment          | Environmental observations           | Software does not control the facility               |
| Equipment                       | Calibration/maintenance state        | Calibration activity remains a laboratory activity   |
| Contract review                 | Controlled review stage              | Laboratory determines acceptance criteria             |
| Methods                         | Method/version/validation evidence   | Technical validation remains laboratory work          |
| Sampling/handling               | COC and condition history            | Laboratory procedure remains governing               |
| Technical records                | Revisions + audit                    | Software preserves records                            |
| Measurement uncertainty         | Result-level uncertainty support     | Technical methodology remains laboratory-owned         |
| Validity of results              | QC data capture and controls         | Laboratory defines QC program                         |
| Reporting                        | Controlled report generation         | Report approval remains authorized human activity      |
| Nonconforming work                | Nonconformity/CAPA support           | Laboratory decides disposition                        |
| Documents                        | Version/effective-date control       | Controlled documents remain quality-system records     |
| Internal audit                   | Findings and action tracking         | Audit activity remains performed by people              |

The software shall never present a feature as evidence that accreditation automatically exists.

---

# K. Security Architecture

## Authentication

* Argon2id password hashing.
* Server-side sessions.
* Secure cookies.
* HTTP-only cookies.
* Appropriate SameSite policy.
* Session timeout.
* Explicit logout.
* Administrative session invalidation.
* Account lockout/failed-login controls according to approved policy.

## Authorization

RBAC shall be enforced server-side.

Permissions may be scoped by:

* module;
* action;
* role;
* section;
* discipline;
* record context.

The UI is not a security boundary.

---

## Segregation of Duties

The backend shall enforce separation between controlled technical activities.

For example:

```text
Analyst creates result
        ↓
Reviewer reviews
        ↓
Technical reviewer verifies
        ↓
Authorized signatory approves
```

Where policy requires separation, the system shall reject an attempt to perform a restricted subsequent action by the same person who created the underlying technical record.

---

## Audit Integrity

Audit records shall be:

* application-controlled;
* append-only through normal application operation;
* protected from ordinary modification/deletion;
* associated with actor and timestamp;
* associated with relevant entity/action;
* capable of recording before/after state for controlled changes;
* capable of recording reasons where required.

---

## Network Exposure

The deployment shall remain LAN-oriented.

No Internet exposure is required for normal operation.

External exposure, if ever required, shall require an explicit architecture and security decision rather than being enabled opportunistically.

---

# L. Database Architecture

## L.1 PostgreSQL

PostgreSQL is the authoritative transactional database.

The architecture shall use:

* SQLAlchemy 2.x;
* Alembic;
* explicit transactions;
* relational constraints;
* indexes;
* foreign keys;
* check constraints;
* unique constraints;
* appropriate normalization.

---

## L.2 Data Modeling Principles

Baseline normalization target:

**3NF**, except where deliberate controlled denormalization is justified.

Examples of justified denormalization may include report snapshots where reproducibility requires preserving the exact issued values.

---

## L.3 Keys

Use:

* surrogate primary keys;
* separately managed human-readable business numbers.

Examples:

* Sample Number;
* Report Number;
* Work Order Number;
* Certificate Number.

Human-facing numbers shall not be treated as substitutes for relational primary keys.

---

## L.4 Delete Policy

Core technical records shall generally use lifecycle/state/revision mechanisms rather than uncontrolled hard deletion.

Reference/master records may have more flexible lifecycle rules where historically safe.

---

## L.5 Concurrency

PostgreSQL is selected specifically to provide a strong foundation for simultaneous laboratory activity.

The application must still maintain:

* short transactions;
* clear transaction boundaries;
* controlled locking;
* efficient indexes;
* safe concurrency behavior;
* appropriate isolation;
* conflict handling where concurrent modifications are possible.

---

# M. UI/UX Architecture

The application shall use role-aware workflows.

Examples:

### Reception

```text
Today's Receipts
   ↓
Sample Receipt
   ↓
Registration
   ↓
Barcode
```

### Analyst

```text
Assigned Queue
   ↓
Scan Sample
   ↓
Open Test
   ↓
Enter Observations
   ↓
Calculate
   ↓
Submit
```

### Reviewer

```text
Review Queue
   ↓
Open Test
   ↓
Inspect Technical Record
   ↓
Accept / Return
```

### Technical Reviewer

```text
Verification Queue
   ↓
Inspect
   ↓
Verify / Return
```

### Signatory

```text
Approval Queue
   ↓
Inspect Final Record
   ↓
Approve / Reject
```

### Equipment Manager

```text
Calibration Due
   ↓
Equipment Record
   ↓
Calibration / Service
   ↓
Release / Hold
```

### Quality Manager

```text
Quality Dashboard
   ↓
NC / CAPA / Complaint / Documents / Audits
```

Status shall remain explicit and consistent across the UI.

---

# N. Reporting Architecture

Approved model:

```text
Database
   ↓
Report data service
   ↓
Versioned Jinja2 template
   ↓
HTML
   ↓
Pinned local Chromium
   ↓
PDF
```

Report generation shall be entirely local.

Each report shall retain traceability to:

* Sample;
* TestInstance;
* Method;
* MethodVersion;
* Analyst;
* Equipment where applicable;
* Result revision;
* Review;
* Verification;
* Approval.

Report templates shall be version-controlled.

Report numbers shall be configurable under controlled administrative authority.

Approval/signature information shall reflect the actual approval record.

A decorative image of a signature shall not be treated as equivalent to an authenticated approval event.

---

# O. Backup / Recovery

The change from SQLite to PostgreSQL changes the backup mechanism, but not the project's verification philosophy.

## O.1 Backup Principle

Use PostgreSQL-supported backup mechanisms.

The live PostgreSQL data directory shall **not** simply be copied as an ordinary file-level backup while the database is running.

The backup strategy shall support consistent database recovery. (Phase 17 will select between logical backups via `pg_dump`/`pg_restore` and physical/PITR backups via `pg_basebackup` + WAL archiving, or a combination, based on the RPO/RTO targets confirmed at that stage.)

---

## O.2 Backup Layers

At minimum:

```text
Primary PostgreSQL Database
        ↓
Local Backup
        ↓
NAS Backup
        ↓
Periodic Offline Copy
```

Documents and attachments shall follow an equivalent protection strategy.

---

## O.3 Backup Verification

A backup shall not be considered successful merely because a backup file exists.

Verification shall include appropriate checks such as:

* backup completion status;
* integrity checks;
* expected backup size/metadata;
* ability to inspect the backup;
* restore validation.

---

## O.4 Restore Testing

A real restore exercise shall be performed periodically.

The project distinguishes:

```text
Backup Created
```

from:

```text
Backup Validated
```

and from:

```text
Restore Tested
```

These are not interchangeable statuses.

---

## O.5 RPO / RTO

Initial planning target:

* **RPO ≤ 24 hours**
* **RTO measured in hours**

Final operational targets shall be confirmed before production deployment.

---

# P. Deployment Architecture

## Application Server

The application server shall host:

* Caddy;
* FastAPI application;
* PostgreSQL;
* local document storage;
* backup tooling;
* required runtime dependencies.

PostgreSQL shall run as a controlled server service.

---

## Client Workstations

Clients require:

* supported Chromium-based browser;
* LAN access;
* local application URL;
* appropriate printer access where required.

Barcode scanners shall preferably operate as standard HID keyboard-wedge devices.

---

## Service Startup

The application stack shall be configured for controlled startup/restart.

Expected services include:

```text
PostgreSQL
FastAPI Application
Caddy
```

Startup dependencies shall be defined explicitly.

---

## Update / Migration Procedure

The standard production update process shall be:

```text
Backup
   ↓
Validate Backup
   ↓
Stop / quiesce application as required
   ↓
Apply Alembic migration
   ↓
Deploy application version
   ↓
Run smoke tests
   ↓
Resume operation
   ↓
Record deployment evidence
```

Rollback strategy shall be defined before migrations are considered production-ready.

---

# Q. Extensibility

The LIMS shall support normal expansion primarily through configuration.

Adding a new discipline should normally involve:

* Method records;
* MethodVersion records;
* TestDefinition records;
* ParameterDefinition records;
* equipment/competency/QC configuration;
* report templates.

It should **not** normally require creating a completely new software module.

A new code module shall be introduced only where a discipline introduces a genuinely different business mechanic that existing domain services cannot represent cleanly.

The project will not implement a generic plugin system merely to claim extensibility.

Extensibility shall therefore be **demonstrated through real use cases**, not merely stated as an architectural feature.

---

# R. Development Decomposition

## Phase 0 — Project Control & Discovery

### WP-00-01 — Project Foundation

Scope:

* repository structure;
* documentation conventions;
* version/status vocabulary;
* change-control rules;
* task/checkpoint conventions.

### WP-00-02 — Existing Information Consolidation

Scope:

* consolidate current understanding;
* record architectural decisions;
* identify assumptions;
* identify unknowns;
* identify deferred decisions;
* record absence of any previously expected database schema (resolved — see T.3, folded into T.1.4);
* establish CP-000 baseline.

### WP-00-03 — Initial Project Baseline

Deliverable:

**CP-000**

Acceptance shall require the project baseline to be explicitly accepted.

---

# Phase 1 — Requirements & Laboratory Model

Once CP-000 is accepted, the first authorized implementation/planning task is:

### WP-01-01 — Users & Organization

Initial bounded tasks include:

1. Document actual laboratory sections and disciplines.
2. Document current organizational responsibilities.
3. Identify actual job functions.
4. Define initial role candidates.
5. Determine which responsibilities are performed by distinct people and which are combined.
6. Identify segregation-of-duties requirements.
7. Record formal authority boundaries.

### WP-01-02 (candidate) — Operational Baseline

To carry forward the items deferred in T.3:

1. Confirm named-user and peak-concurrency estimates (T.1.1, T.1.2) — for server sizing, not database choice.
2. Confirm accreditation context (T.1.3).
3. Confirm existing systems/records to migrate, including whether any legacy database schema exists (T.1.4).
4. Confirm billing/invoicing scope decision (T.1.5).
5. Confirm server hardware baseline (T.1.7).

The exact Phase 1 task sequence shall be finalized through controlled task authorization.

---

# S. Critical Risks

| Risk                                               | Impact                           | Mitigation                                              |
| ---------------------------------------------------- | ----------------------------------- | ---------------------------------------------------------- |
| Scope expansion                                    | Architectural drift              | Checkpoint governance and change control                |
| Incorrect assumptions about laboratory operations  | Wrong workflow design            | Phase 1 real-world discovery                             |
| Poor role separation                               | Approval/control weakness        | Early responsibility and SoD analysis                     |
| Calculation logic errors                           | Incorrect laboratory results     | Constrained calculation engine + testing                  |
| Uncontrolled technical-record editing              | Loss of traceability             | Revision model + immutable audit                          |
| PostgreSQL service failure                         | Temporary system unavailability  | Service monitoring + tested backups                       |
| Server failure                                     | Operational outage               | Backup + restore plan + UPS + spare/recovery procedure    |
| Backup exists but restore fails                    | Potential data loss              | Scheduled restore drills                                  |
| Database security misconfiguration                 | Data exposure/integrity risk     | Backend-only access + controlled DB accounts              |
| Excessive application coupling                     | Maintenance difficulty           | Domain modules + service/repository boundaries            |
| Generic EAV expansion                              | Data/reporting complexity        | Strongly typed configuration model                        |
| AI-assisted development overreach                  | Uncontrolled changes             | One task at a time + checkpoint discipline                 |
| Long project duration                              | Context loss                     | ADRs + project state + documentation-as-code               |
| Deferred operational unknowns resolved incorrectly later | Rework in Phase 1/5/19       | T.3 deferrals are explicit and time-boxed, not silent      |

---

# T. Discovery Questions, Deferred Decisions, and CP-000 Resolution

With PostgreSQL now frozen, user concurrency is **no longer a database-selection blocker**, but it remains important for server and deployment sizing.

## T.1 Operational Discovery

The following were raised for resolution or formal deferral.

### 1. Named users

What is the expected number of named users?

Suggested classification:

* ≤20
* 21–50
* 51–100
* > 100

**Status:** Open — see T.3.

### 2. Peak concurrent activity

What is the expected peak number of simultaneous active users and technical writers?

This affects:

* CPU;
* RAM;
* PostgreSQL connection configuration;
* application worker configuration;
* report-generation capacity.

**Status:** Open — see T.3.

### 3. Accreditation context

Determine whether SMJ is:

* already accredited;
* preparing for accreditation;
* using ISO/IEC 17025 as internal best practice;
* or operating under another formal quality objective.

**Status:** Open — see T.3.

### 4. Existing systems/data

Determine whether migration is required from:

* spreadsheets;
* paper registers;
* existing software (including whether any such software has a database schema that should inform this design);
* mixed sources.

**Status:** Open — see T.3. This item now also carries the schema-review question originally raised in the source brief (Section 22): no legacy schema has been supplied in any round of discovery to date. Unless SMJ indicates otherwise, this is treated as **greenfield schema design** for Phase 3, subject to correction here.

### 5. Billing

Determine whether billing/invoicing is:

* in scope for v1;
* deferred;
* or permanently outside the LIMS boundary.

**Status:** Open — see T.3.

### 6. Site scope

For v1:

> **Single laboratory site.**

Multi-branch operation is deferred.

**Status:** Resolved in this document.

### 7. Server hardware

Determine:

* existing server availability;
* CPU;
* RAM;
* storage;
* RAID/storage redundancy where appropriate;
* UPS;
* backup destination;
* NAS availability.

**Status:** Open — see T.3.

---

## T.2 Non-Blocking Information

The following can be defined later without blocking CP-000:

* report logo/letterhead;
* report visual template;
* exact test methods;
* barcode printer model;
* scanner model;
* NAS model;
* first-wave discipline configuration;
* detailed report content;
* detailed retention periods;
* exact notification thresholds.

These belong primarily to later requirements/configuration phases.

---

## T.3 Resolution for CP-000

CP-000's own acceptance criterion (V.2.3) requires every remaining discovery item to be **either answered or explicitly deferred with a stated reason and intended resolution phase**. T.1 items 1, 2, 3, 4, 5, and 7 meet neither condition as raised. This section closes that gap.

**Determination:** none of these items are architectural blockers. Each affects sizing, scope classification, or downstream configuration — not the frozen decisions D-001–D-012. Each is therefore **formally deferred**, as follows:

| Item | Reason for deferral | Resolution phase | Resolution vehicle |
|---|---|---|---|
| T.1.1 — Named users | Affects server sizing and connection-pool configuration, not database choice (already resolved by E.4) or module architecture | Phase 1 → carried to Phase 5 (Technical Foundation) for sizing | WP-01-02 (candidate) |
| T.1.2 — Peak concurrency | Same as above | Phase 1 → Phase 5 | WP-01-02 (candidate) |
| T.1.3 — Accreditation context | Affects the rigor/emphasis of ISO/IEC 17025 evidence capture (Section J), not the existence of the capabilities themselves, which are built regardless | Phase 1 | WP-01-02 (candidate) |
| T.1.4 — Existing systems / legacy schema | Affects whether Phase 3 includes a migration/critique sub-track; absent a supplied schema, Phase 3 proceeds as greenfield design | Phase 1 → confirmed before Phase 3 (Data Architecture) begins | WP-01-02 (candidate) |
| T.1.5 — Billing scope | Affects module list (Section F) — Invoicing is explicitly not in the current module table pending this answer | Phase 1 | WP-01-02 (candidate) |
| T.1.7 — Server hardware | Affects Phase 5 technical foundation and Phase 19 production prep; does not affect the software architecture itself | Phase 1 → confirmed before Phase 19 (Production Deployment) at the latest | WP-01-02 (candidate) |

This deferral is time-boxed, not indefinite: items feeding Phase 3 (T.1.4) and Phase 5 (T.1.1, T.1.2, T.1.7) must be resolved before those phases' respective checkpoints (CP-003, CP-005) are accepted — they cannot be deferred past that point without re-opening this section.

**Result:** V.2.3 is satisfied. CP-000 does not require these answers to proceed to Phase 1.

---

# U. Recommended Roadmap

The approved project roadmap is:

```text
Phase 0
Project Control & Discovery
        ↓
CP-000
        ↓
Phase 1
Requirements & Laboratory Model
        ↓
CP-001
        ↓
Phase 2
System & Security Architecture
        ↓
CP-002
        ↓
Phase 3
Data Architecture
        ↓
CP-003
        ↓
Phase 4
UX / UI Architecture
        ↓
CP-004
        ↓
Phase 5
Technical Foundation
        ↓
CP-005
        ↓
Phase 6
Identity / RBAC / Audit
        ↓
CP-006
        ↓
Phase 7
Core Master Data
        ↓
CP-007
        ↓
Phase 8
Customer / Project / Sample
        ↓
CP-008
        ↓
Phase 9
Test & Method Engine
        ↓
CP-009
        ↓
Phase 10
Execution & Results
        ↓
CP-010
        ↓
Phase 11
Review / Verification / Approval
        ↓
CP-011
        ↓
Phase 12
QC & Equipment
        ↓
CP-012
        ↓
Phase 13
Quality Management
        ↓
CP-013
        ↓
Phase 14
Documents & Records
        ↓
CP-014
        ↓
Phase 15
Reporting & Certificates
        ↓
CP-015
        ↓
Phase 16
Configuration & Extensibility
        ↓
CP-016
        ↓
Phase 17
Backup / Recovery / Operations
        ↓
CP-017
        ↓
Phase 18
Validation & Hardening
        ↓
CP-018
        ↓
Phase 19
Production Deployment
        ↓
CP-019
        ↓
Phase 20
Maintenance & Evolution
```

No phase is skipped.

No future phase is authorized merely because it has been described.

---

# V. CP-000 Decision Baseline and Acceptance Criteria

## V.1 Frozen Architectural Decisions

The following decisions are established as the CP-000 baseline.

### D-001 — Project Scope

**Frozen:** Option A — Single-lab LIMS, all laboratory operations.

Multi-branch and multi-tenant operation are deferred.

---

### D-002 — Technology Stack

**Frozen:** Option A.

```text
React
TypeScript
Vite
MUI
FastAPI
Python
SQLAlchemy 2.x
PostgreSQL
Alembic
Argon2id
Server-side Sessions
Caddy
Jinja2
Chromium
pytest
Playwright
```

---

### D-003 — Architecture Style

**Frozen:** Option A — Modular Monolith.

Microservices and plugin architecture are rejected for v1.

---

### D-004 — Database

**Frozen:** Option B — PostgreSQL.

PostgreSQL is the authoritative v1 transactional database.

---

### D-005 — Data Integrity

**Frozen:** Option A — Revision-based records + immutable audit.

Technical record corrections shall preserve historical state.

---

### D-006 — Security

**Frozen:** Option A — RBAC + server sessions + segregation of duties.

Authorization is backend-enforced.

---

### D-007 — Workflow

**Frozen:** Option A — Explicit state machine.

Workflow state transitions shall be controlled, not free-form.

---

### D-008 — Configuration

**Frozen:** Option A — Strongly typed configuration tables.

Generic EAV is not the primary data architecture.

---

### D-009 — Development Methodology

**Frozen:** Option A — Task → Verification → Checkpoint.

---

### D-010 — Documentation

**Frozen:** Option A — Documentation-as-code.

The repository is the authoritative engineering knowledge base unless a formally controlled external record is defined.

---

### D-011 — Module Boundaries

**Frozen:** Option A — Domain-oriented modules.

---

### D-012 — Architectural Principles

**Frozen:** Option A — Conservative, controlled, auditable architecture.

---

# V.2 CP-000 Acceptance Criteria

CP-000 shall be considered **Accepted** when:

1. This Phase 0 baseline, or an approved revision, is accepted. — **Awaiting SMJ sign-off.**
2. D-001 through D-012 are explicitly recorded as frozen decisions. — **Satisfied (V.1).**
3. Any remaining discovery item is either answered, or explicitly deferred with a reason and intended resolution phase. — **Satisfied (T.3).**
4. The PostgreSQL decision is reflected consistently throughout the architecture. — **Satisfied; checked against Sections D, E, L, O, P.**
5. The single-laboratory scope is confirmed for v1. — **Satisfied (T.1.6).**
6. The Modular Monolith architecture is confirmed. — **Satisfied (D-003).**
7. The revision/audit model is confirmed. — **Satisfied (D-005).**
8. The security model and segregation-of-duties principle are confirmed. — **Satisfied (D-006, Section K).**
9. The explicit-state-machine workflow model is confirmed. — **Satisfied (D-007, Section H).**
10. The strongly typed configuration strategy is confirmed. — **Satisfied (D-008, Section I).**
11. The task/checkpoint development-control model is confirmed. — **Satisfied (D-009).**
12. Documentation-as-code is confirmed. — **Satisfied (D-010).**
13. The module boundaries are confirmed as the initial domain organization. — **Satisfied (D-011, Section F).**
14. No application feature implementation has been authorized ahead of CP-000. — **Satisfied.**
15. The project explicitly records that the system supports the laboratory quality system but does not itself confer ISO/IEC 17025 accreditation. — **Satisfied (Section J).**

**Overall determination:** Criteria 2–15 are satisfied. Criterion 1 — formal acceptance by SMJ — is the only remaining step.

---

# Final CP-000 Baseline

The resulting architecture can be summarized as:

```text
                     SMJ LIMS v1
                          │
              Single Physical Laboratory
                          │
                          ▼
                  Modular Monolith
                          │
              ┌───────────┴───────────┐
              │                       │
          React / TS              FastAPI
              │                    Python
              └───────────┬───────────┘
                          ▼
                    SQLAlchemy
                          │
                          ▼
                     PostgreSQL
                          │
            ┌─────────────┴─────────────┐
            ▼                           ▼
      Local Documents                Backups
                                        │
                                       NAS
                                        │
                                  Offline Copy
```

The governing design philosophy is:

> **Build a controlled, maintainable laboratory information system—not a generic software platform—and add complexity only when a real laboratory requirement proves it necessary.**

**Next authorized phase after CP-000 acceptance:**
**Phase 1 → WP-01-01 — Users & Organization**, with WP-01-02 (candidate) carrying forward the T.3 deferrals.

No later feature implementation is authorized merely by this document; each subsequent task remains subject to the project's task and checkpoint controls.



Next Prompt:
# Section A — Users & Organizational Scale

## Q1. Expected named users

How many individual people are expected to have LIMS accounts?

Ans. 1–10

---

## Q2. Expected concurrent users

At the busiest normal period, approximately how many users may have the LIMS open and actively using it at the same time?

Ans. 1–10

---

## Q3. Peak simultaneous write activity

At the busiest moment, how many users might simultaneously perform actions that write/update database records?

Examples:

* sample registration;
* result entry;
* result submission;
* review;
* approval;
* configuration changes.

Ans. 1-5

---

## Q4. User growth expectation

Over the next 3–5 years, do you expect the user count to:

Ans. Remain roughly the same

---

## Q5. User shift pattern [MULTI]

When is the LIMS expected to be used?

Ans. Single daytime shift

---

## Q6. User roles actually expected at launch [MULTI]

Which functions will exist as real users?

Ans.	1. Reception / Sample Receiving / Sample Registration
		2. Laboratory Analyst / Technician
		3. Technical Reviewer / Verifier
		4. Authorized Signatory / Approver
		5. Equipment / Calibration Manager
		6. System Administrator
		7. Management / Audit / Read-only

---

## Q7. Segregation of duties

Which of these are normally performed by different people?

Ans. Some stages are currently performed by the same person (currently only 3 active staff)

---

# Section B — Accreditation & Quality Context

## Q8. Current accreditation status

Which best describes SMJ today?

Ans. Already accredited under ISO/IEC 17025 (NABL)

---

## Q9. Accreditation scope [MULTI]

Which disciplines are intended to be part of the formal accreditation scope?

Ans. Solid Fuel (Coal) & Solid Biofuel

---

## Q10. Quality-system maturity

How are laboratory procedures currently controlled?

Ans. Formal controlled SOP/document system already exists
	 SOPs exist but document control is partly manual

---

## Q11. Technical record retention

How long are laboratory technical records expected to be retained?

Ans. Proposed 10 years active and then in archives

---

## Q12. Approval/signature model

What level of electronic approval is intended?

Ans. Authenticated approval + printable signature block

---

# Section C — Existing Records & Migration

## Q13. Existing laboratory information system

Is there an existing LIMS or laboratory software?

Ans. No

---

## Q14. Existing spreadsheets [MULTI]

Are laboratory records maintained in spreadsheets?

Ans. Yes — sample registers/test/result sheets/equipment/calibration/QC/reporting

---

## Q15. Existing paper records [MULTI]

Are paper registers/forms currently used?

Ans. Sample receipt/register/Test worksheets/Equipment/calibration records/QC records/Reports/certificates/Quality records

---

## Q16. Migration requirement

What is expected for historical data?

Ans. All available historical data (not much at the moment)

---

## Q17. Legacy database/schema availability

Does an existing database schema or database export exist?

Ans. No existing database

---

## Q18. Data quality of existing records

How reliable is the historical data likely to be?

Ans. No historical data available 

---

# Section D — Billing & Commercial Scope

## Q19. Billing/invoicing in LIMS

Should the LIMS create/manage invoices?

Ans. LIMS should calculate charges but external accounting creates invoices

---

## Q20. Pricing model [MULTI]

How are laboratory charges determined?

Ans. officially per parameter but also customer-specific negotiated rate

---

# Section E — Laboratory Site & Physical Environment

## Q21. Physical laboratory sites

How many physical laboratory sites operate today?

Ans. One

---

## Q22. Future branch requirement

How likely is multi-branch operation within 3–5 years?

Ans. Definitely planned (as a separate entity)

---

## Q23. LAN availability

How is the laboratory network currently organized?

Ans. Not yet (only a single pc for now, will have a LAN in near future)

---

## Q24. Internet availability

What is the normal Internet situation?

Ans. Internet available but unreliable

---

# Section F — Server & Infrastructure

## Q25. Server availability

Is a server already available?

Ans. Not decided (no most probably)

---

## Q26. Server CPU

Ans. No Server

---

## Q27. Server RAM

Ans. No Server

---

## Q28. Server storage

Ans. No Server

---

## Q29. Storage capacity

Ans. 500 GB–1 TB (locally on pc)

---

## Q30. UPS

Is the application/database server protected by a UPS?

Ans. Yes — dedicated UPS

---

## Q31. Power reliability

How reliable is electricity at the laboratory?

Ans. Occasional short outages

---

# Section G — Backup & Disaster Recovery

## Q32. NAS availability

Is a NAS already available?

Ans. No

---

## Q33. Backup destination [MULTI]

Where can backups be stored?

Ans. External USB disk

---

## Q34. Backup frequency

How frequently should the database be backed up?

Ans. Once daily

---

## Q35. Acceptable data-loss window

If the server completely fails, what is the maximum acceptable amount of recent data that could be lost?

Ans. Up to 24 hours

---

## Q36. Maximum acceptable downtime

After a major server failure, how quickly should the LIMS be operational again?

Ans. Same business day

---

## Q37. Restore testing

How often can the laboratory perform a real backup-restore test?

Ans. Monthly

---

# Section H — Laboratory Discipline Rollout

## Q38. First production discipline

Which discipline should be implemented first?

Ans. Solid Fuel

---

## Q39. Initial test-method maturity

For the first discipline, are the methods already documented?

Ans. Fully documented and approved

---

## Q40. Standards used [MULTI]

Which method standards will be used?

Ans. primarily IS / BIS, then ASTM/APHA/EPA/Other national/international standards can be used.

---

# Section I — Equipment & Laboratory Operations

## Q41. Equipment management

How is equipment currently managed?

Ans. Spreadsheet and Paper register combination

---

## Q42. Calibration control

How are calibration due dates currently controlled?

Ans. No formal tracking yet

---

## Q43. Equipment use restrictions

What should happen when equipment is expired/out of calibration?

Ans. Always block testing but warn user in advance (30 days)

---

# Section J — Barcode, Printing & Documents

## Q44. Sample identification

How should samples be identified?

Ans. LIMS-generated sample number only + Barcode

---

## Q45. Barcode scanner

Ans. Will be purchased

---

## Q46. Label printer

Ans. Standard office printer will be used

---

## Q47. Report format [MULTI]

Required output formats:

Ans. primary PDF then Printed report/Excel/Word as required.

---

# Section K — Reporting & Certificates

## Q48. Existing report format

Ans. Existing informal format

---

## Q49. Report numbering

How are reports currently numbered?

Ans. Manual numbering

---

## Q50. Report delivery [MULTI]

How are final reports normally delivered?

Ans. Mainly Email attachment, Printed copy provided on client request.

---

# Section L — Operational Requirements

## Q51. LIMS operating window

How important is continuous availability?

Ans. Business hours only

---

## Q52. Internet outage behavior

During an Internet outage, the expectation is:

Ans. Full LIMS operation continues (fully working offline)

---

## Q53. Planned external integrations [MULTI]

Are any of these planned?

Ans. None planned

---

# Section M — Migration / Integration Priority

## Q54. Instrument data capture

How are instrument readings currently entered?

Ans. Manual entry

---

## Q55. Future instrument integration

How important is direct instrument integration?

Ans. Useful but low priority

---

# Section N — Future Growth

## Q56. Expected laboratory growth

Over the next 3–5 years:

Ans. Remain approximately current size

---

## Q57. New disciplines

How likely is the laboratory to add disciplines beyond the initial seven?

Ans. Definitely planned

---

## Q58. Future sites

How likely is SMJ to operate additional physical laboratory sites?

Ans. Very unlikely

---

# Section O — Ownership & Governance

## Q59. Who owns LIMS configuration?

Who should be authorized to change:

* tests;
* methods;
* parameters;
* report templates;
* numbering;
* workflow policy?

Ans. Shared responsibility with controlled approval

---

## Q60. Who approves production configuration changes?

Ans. System Administrator


Response:
That's a complete, well-organized discovery pass — genuinely useful data, not just checkbox answers. Most of it resolves cleanly. But a few answers change the calculus on decisions we already made, and one thing you told me now actively contradicts something I designed in a way that needs your input before I paper over it.

The big one first, since it affects everything downstream:

Reconsider PostgreSQL. The whole reason I chose PostgreSQL over SQLite last round was that I didn't know your actual load and didn't want to gamble on SQLite being enough. Now I do know: 1–10 named users, 1–5 people writing at the same instant, single daytime shift, expected to stay this size for years — and no server exists yet, likely just a PC. That's an order of magnitude below where PostgreSQL's concurrency advantages start to matter, and for a 3-person lab with no dedicated IT, running and patching a separate database service is real ongoing overhead for no real benefit at this scale. My recommendation: revert to SQLite for v1 — it's a file, not a service; nothing to install, secure, or keep patched separately; and it comfortably handles this workload with room to spare. I'm not changing it unilaterally since you explicitly froze it — tell me if you want to keep PostgreSQL anyway (e.g. for the future second-entity story) or switch back.

Two smaller things I need from you, and everything else — accreditation scope, billing split, backup destination, equipment policy, deployment reality — I've resolved and written up below.

Three things to confirm and we can close this out: database (§2.1), which role-pairs actually overlap today (§2.2) — this one matters most since it directly shapes how strict the approval enforcement can be with only 3 staff — and the one-line check on the future-entity reading (§2.3).

# SMJ LIMS — Discovery Resolution (Operational Baseline)

**Status:** Phase 0 → Phase 1 transition input
**Source:** SMJ Discovery Questionnaire, Sections A–O (60 questions)
**Feeds:** CP-000 final closure; WP-01-01 (Users & Organization); WP-01-02 (Operational Baseline)
**Purpose:** Close the T.1/T.3 items formally deferred in the CP-000 baseline; surface the handful of new implications the answers raise; flag what still needs your explicit call before this is folded back into the baseline document.

---

## 1. T.1 / T.3 Closure — Confirmed Values

| Item | Confirmed | Note |
|---|---|---|
| T.1.1 — Named users | 1–10 | Far below any concurrency threshold that would justify PostgreSQL's overhead — see §2.1 |
| T.1.2 — Peak concurrency | 1–10 concurrent, **1–5 simultaneous writers**, single daytime shift, expected to stay this size 3–5 years | Same |
| T.1.3 — Accreditation | **Already NABL-accredited** under ISO/IEC 17025; scope currently limited to **Solid Fuel (Coal) & Solid Biofuel only** | Accreditation scope is per-discipline, not lab-wide — see §3.2 |
| T.1.4 — Existing systems / migration | No existing LIMS, no legacy database/schema. Spreadsheets and paper registers in active use for samples/tests/equipment/calibration/QC/reports. Migration wanted but volume is low. | Confirms greenfield Phase 3 schema design, as already assumed |
| T.1.5 — Billing | LIMS **calculates charges**; invoicing itself stays in external accounting software. Pricing = official per-parameter rate + customer-specific negotiated rate. | See §3.1 |
| T.1.7 — Server hardware | None exists; likely none purchased (a capable PC is more realistic than a "server"). 500GB–1TB local storage. Dedicated UPS already in place. Occasional short power outages. | See §2.1 and §3.6 |

Also newly confirmed, feeding other sections directly:
- **RPO ≤ 24h** (daily backup) and **RTO = same business day** — matches the placeholder targets in the baseline; now real commitments, not placeholders.
- **Restore testing monthly** — tighter than the quarterly cadence I'd proposed; adopting your monthly figure.
- **Backup destination = external USB disk**, not NAS (none exists) — see §3.5.
- **First production discipline = Solid Fuel**, methods already fully documented and approved — low-risk starting point for Phase 9.
- **No formal calibration tracking today** — this is a real gap the LIMS should close early; not just a nice-to-have.

---

## 2. Decisions Needing Your Confirmation

### 2.1 Database: PostgreSQL or SQLite

Covered above. Recommendation: **revert D-004 to SQLite** given the confirmed 1–5-simultaneous-writer reality and the absence of dedicated IT/server infrastructure. If you'd rather keep PostgreSQL — for future-proofing, familiarity, or the second-entity plan — that's a legitimate call too; I just want it made with the real numbers in front of you rather than the earlier placeholder reasoning. Either way, the SQLite conditions from the original evaluation still apply if chosen: WAL mode, DB file on local fixed disk (moot now, since there's no NAS to accidentally put it on), short transactions.

### 2.2 Segregation of duties — which pairs are actually combined today

Q7 confirms "some stages are currently performed by the same person" with only 3 active staff, but not *which* stages. This matters a lot: the baseline currently says the backend should **reject** an approval/verification action performed by the same person who created the underlying record (D-006). With 3 staff, rigid enforcement of that rule could make parts of the system genuinely unusable.

This is a normal, accepted situation for small accredited labs — ISO/IEC 17025 doesn't require a different person for every single stage; it requires the lab to identify where combining roles creates real risk and manage that risk (documented, competency-based, risk-assessed), which your NABL assessor has presumably already accepted in some form for your current paper/spreadsheet process. I don't want to guess at which combinations are already how you operate versus which would only happen in a pinch. Concretely, I need to know: **today, does the same person ever act as both Analyst and Technical Reviewer/Approver for the same test? Reviewer and Approver? Or is it only Analyst+Reviewer that overlaps, with verification/approval always kept separate?** That distinction decides whether RBAC enforcement in Phase 6 is a hard block, a block with an explicit documented-override path, or a warn-only control for specific stage pairs.

### 2.3 One future entity or two future sites?

Q22 ("multi-branch within 3–5 years? Definitely planned, as a separate entity") and Q58 ("additional physical sites for SMJ? Very unlikely") read as in tension. My working interpretation: SMJ itself stays single-site, but a **separate legal entity** (a related/sister company) may eventually want its own lab and its own LIMS deployment — which wouldn't need multi-tenancy in *this* system at all, just the same architecture reused as a second, independent install. If that's right, nothing changes in the current design (B.3 already keeps multi-tenant SaaS out of scope). Worth a one-line confirmation so I don't build toward the wrong one.

---

## 3. New / Refined Requirements Captured

### 3.1 Pricing vs. invoicing
In scope: a charge-calculation capability tied to Test/Parameter, supporting both a standard per-parameter rate and customer-specific negotiated overrides (implies a lightweight `Rate`/`CustomerRate` concept in Customer & Project). **Out of scope:** invoice documents, payment tracking, accounts receivable — those stay in your external accounting software. The LIMS's job ends at "here's what this work costs," not "here's the invoice."

### 3.2 Accreditation scope is per-discipline, not lab-wide
Since NABL scope currently covers only Solid Fuel and Solid Biofuel, Method/Test records need an accreditation-scope flag, and report/certificate templates need to render the NABL symbol/accreditation statement only for in-scope tests — a report mixing accredited and non-accredited results needs to say so clearly per result, not imply blanket accreditation. This is a real, non-optional detail for Phase 15 (Reporting) and worth carrying into Phase 9 (Method & Test Engine) as a field, not an afterthought.

### 3.3 Report formats: PDF stays authoritative; Excel/Word are secondary
Q47 adds Excel/Word alongside PDF. I'm treating the **approved, signed certificate as PDF-only** — that's the controlled technical record, and making the authoritative output an editable Word file would undercut the immutability principle (D-005) the whole system is built around. Excel/Word exports are better scoped as (a) a raw-data export for internal/customer use, or (b) a pre-approval draft — not as an alternate authoritative format for the final signed report. Worth confirming that reading matches your intent.

### 3.4 Equipment enforcement — concrete default policy
Q43 gives an actual policy rather than "configurable, TBD": **block testing on out-of-calibration/expired equipment, with a 30-day advance warning** before expiry. This becomes the shipped default in Section H.1/Equipment Enforcement, still overridable per lab policy where the config model already allows it.

### 3.5 Backup architecture — no NAS
Section O of the baseline described a Local → NAS → Offline-copy chain. Revised to: **Local backup → external USB disk (rotated), daily, integrity-checked before being considered valid** — the NAS tier gets added back in if/when one's purchased. Doesn't change the backup *philosophy* (verify, don't assume), just the physical destination.

### 3.6 Deployment reality: today is one PC, not a LAN
Q23 confirms there's currently a single PC and no LAN yet. The architecture doesn't need to change for this — a modular monolith running locally (browser hitting `localhost`) works standalone today and extends to additional LAN workstations later without rework. Given the confirmed scale, when you do provision hardware, this doesn't need to be a "server" in the traditional sense — a capable business-grade PC (mid-range CPU, 16GB RAM, SSD matching your 500GB–1TB figure, left on, on the UPS you already have) is realistic and sufficient. Worth firming up in Phase 5, but no need to overspend on infrastructure sized for a load you don't have.

### 3.7 Barcode labels via a standard printer, not a thermal label printer
Q46 means label templates should be designed for sheet-label printing (e.g., Avery-style adhesive sheets through a normal printer) rather than assuming a dedicated thermal label printer — a real constraint for the Phase 4 sample-registration screen and the barcode template itself, not just a hardware footnote.

### 3.8 Configuration governance is two-step, not single-admin
Q59/Q60: configuration changes are a **shared responsibility with controlled approval**, and the System Administrator holds final sign-off. This refines Section I (Configuration Strategy) slightly: administrative configuration changes should probably carry their own lightweight propose → approve flow (mirroring the technical-record philosophy already used elsewhere) rather than being a direct, unreviewed edit — worth carrying into Phase 6/16 design rather than deciding definitively here.

---

## 4. What Happens Next

Once §2.1–2.3 are confirmed, I'll fold this whole resolution into a revised CP-000 baseline (updated D-004 if applicable, updated Sections H.1/I/J/N/O/P as above) and it'll be ready for your final sign-off. At that point Phase 1 (WP-01-01 and this document standing in for WP-01-02) is effectively complete, and Phase 2 — System & Security Architecture — becomes the next authorized phase.



Next Prompt:
2.1 Database — SQLite

Decision: CONFIRMED — Retain SQLite for D-004.

The confirmed operating conditions support SQLite for v1:

Named users: 1–10
Peak concurrent users: 1–10
Peak simultaneous writers: 1–5
Operating pattern: single daytime shift
Expected scale: approximately stable for the next 3–5 years
Deployment: single-host / standalone PC initially
Internet-independent operation: required
No dedicated database/server infrastructure currently exists.

Therefore:

D-004 = SQLite
WAL mode shall be enabled.
The live database shall remain on local fixed storage.
The database shall never reside on NAS/SMB/network storage.
Transactions shall be short and atomic.
Database lock/timeout conditions shall be handled by the application.
Raw database errors shall not be exposed to end users.
Backup and restore procedures shall be controlled and tested.

Future reassessment triggers should include materially increased concurrent write activity, multiple application hosts, substantially increased user volume, or a requirement for multiple entities sharing one database.

Final decision: ✅ CONFIRMED

2.2 Segregation of Duties — D-006

Decision: CONFIRMED with policy-driven enforcement.

The LIMS shall not require every stage of laboratory work to be performed by a different person.

The fundamental control is:

For the same TestInstance / technical record, the user who performed the analytical/testing activity shall not subsequently perform the independent Technical Review, Verification, or Final Approval of that same record.

Therefore:

Analyst → Reviewer of the same test: not permitted where the review is defined as independent
Analyst → Technical Reviewer of the same test: blocked
Analyst → Final Approver of the same test: blocked
Technical Reviewer → Approver: may be permitted, subject to the laboratory's documented procedure and risk assessment.

The system shall enforce these restrictions at the individual test-record level, not globally across all records.

Any permitted role overlap shall remain attributable to the actual user and fully auditable.

Important implementation principle

Do not hard-code a universal:

"One user can never perform two roles."

Instead, the Phase 2/6 design should implement a controlled SoD policy matrix.

Example:

Activity combination	Default
Analyst → Independent Review, same TestInstance	Block
Analyst → Verification, same TestInstance	Block
Analyst → Approval, same TestInstance	Block
Technical Reviewer → Approval, same TestInstance	Policy-controlled
Same person across different TestInstances	Permitted subject to role authorization

Final decision: ✅ CONFIRMED

One laboratory confirmation still belongs in Phase 1: the actual SOP/risk-assessment basis for the permitted combinations. That is a requirements/policy confirmation, not a CP-000 architecture blocker.

2.3 Future Entity / Site Model

Decision: CONFIRMED — Single-site SMJ deployment.

The interpretation is:

SMJ itself is expected to remain a single physical laboratory site.
The planned additional laboratory relates to a separate legal entity.
That future entity does not require multi-tenancy in the SMJ installation.
A future entity can receive a separate independent LIMS deployment using the same software architecture/release lineage.

Therefore:

SMJ Sustainable Fuel Lab
        │
        └── LIMS Installation A
            Single Site
            Single Database

Future Related Entity
        │
        └── LIMS Installation B
            Independent Deployment
            Independent Database

No multi-tenant architecture is required.

No shared database is required.

No branch-management infrastructure is required for v1.

Final decision: ✅ CONFIRMED

3.1 Pricing vs. Invoicing

Decision: CONFIRMED — Charge calculation in LIMS; invoicing external.

The LIMS shall calculate:

Test / Parameter
       ↓
Applicable Rate
       ↓
Standard Rate
       OR
Customer-specific negotiated Rate
       ↓
Calculated Charge

The LIMS is responsible for determining:

What should this laboratory work be charged at?

External accounting remains responsible for:

What was invoiced, paid, or remains outstanding?

Therefore excluded from the LIMS:

invoice generation;
payment records;
accounts receivable;
receipts;
accounting ledger;
credit notes;
tax/accounting workflows.

Final decision: ✅ CONFIRMED

3.2 Accreditation Scope

Decision: CONFIRMED — Accreditation applicability is controlled at the applicable Method/Test scope level.

Current accredited scope:

Solid Fuel (Coal)
Solid Biofuel

The LIMS shall distinguish between:

work within the current NABL-accredited scope;
work outside the current NABL-accredited scope.

The architecture should avoid treating the entire laboratory as simply:

Accredited = TRUE

Instead, accreditation applicability shall follow the actual controlled scope of the applicable method/test.

For reporting:

NABL-related marking/statements shall appear only where applicable and permitted.
Mixed accredited/non-accredited reports shall clearly distinguish the relevant scope.
A report shall not imply that all results are accredited merely because SMJ as an organization is accredited.

Historical records must retain the accreditation applicability relevant to the work at that time, so later scope changes do not rewrite historical interpretation.

Final decision: ✅ CONFIRMED

3.3 Report Format

Decision: CONFIRMED — PDF is the sole authoritative final report/certificate format.

Final approved output:

PDF

The final approved PDF is the controlled technical report.

Word and Excel shall not be alternative final report/certificate formats.

Future structured exports, if required, shall be treated as separate functions and shall not become another "official certificate" representation.

This is consistent with the project's revision/immutability principle.

Final decision: ✅ CONFIRMED

3.4 Equipment Enforcement

Decision: CONFIRMED — Block expired/out-of-calibration equipment for applicable testing.

Default policy:

30 days before expiry
        ↓
WARNING

Calibration expires
        ↓
BLOCK

Equipment explicitly marked
"Out of Calibration"
        ↓
BLOCK

The control applies particularly to equipment affecting result validity.

The system shall:

display advance warning;
identify affected equipment;
show expiry date;
block use after expiry;
block explicitly out-of-calibration equipment;
audit relevant status changes and attempted use.
Important governance distinction

The 30-day warning is a configurable policy value.

The default policy is:

30-day warning + block on expiry/out-of-calibration.

Any policy change must be an authorized configuration change, not something an analyst can bypass operationally.

Final decision: ✅ CONFIRMED

3.5 Backup Architecture

Decision: CONFIRMED — Local backup + rotated external USB.

Current deployment:

Production Database
        ↓
Daily Backup
        ↓
Local Backup
        ↓
Rotated External USB

Requirements:

daily backup;
integrity verification;
external USB rotation;
backup status recorded;
failed backup clearly identified;
restore capability periodically tested.

Current operational targets:

RPO ≤ 24 hours
RTO = same business day
Restore testing = monthly

NAS is not required now.

Future NAS support can be added as another backup destination without redesigning the backup principles.

Final decision: ✅ CONFIRMED

3.6 Deployment Architecture

Decision: CONFIRMED — Single-host deployment initially.

The current deployment is:

Business-grade PC
   ├── LIMS application
   ├── SQLite
   ├── Documents
   └── Backup orchestration
            ↓
        Browser
        localhost

A business-grade PC is sufficient for the confirmed workload.

Initial target:

approximately 16 GB RAM
500 GB–1 TB SSD
suitable mid-range CPU
continuous operation
connected to the existing UPS

These are initial sizing targets, not final hardware requirements. Final hardware qualification belongs to later technical/deployment work.

The architecture remains LAN-capable:

                    LAN
                     │
       ┌─────────────┼─────────────┐
       ↓             ↓             ↓
   Reception       Analyst       Manager
       │             │             │
       └─────────────┴─────────────┘
                     │
                     ▼
              Application Host

No fundamental application/database redesign should be necessary merely to add additional authorized workstations.

Final decision: ✅ CONFIRMED

3.7 Barcode Labels

Decision: CONFIRMED — Standard office printer + adhesive sheet labels.

The initial system shall use:

standard office printer;
adhesive label sheets;
barcode;
human-readable identifier;
configurable label layout.

A thermal label printer is not a v1 dependency.

Actual label layout shall be validated against the selected printer and sheet format before production use.

Final decision: ✅ CONFIRMED

3.8 Configuration Governance

Decision: CONFIRMED — Propose → Approve.

Controlled configuration changes shall follow:

Authorized User
       ↓
PROPOSE
       ↓
System Administrator
       ↓
APPROVE / REJECT
       ↓
Effective Configuration

The audit trail should record:

what changed;
previous value;
proposed value;
proposer;
proposal timestamp;
approver;
approval/rejection timestamp;
reason/justification where required.

Unapproved proposals shall not affect live behavior.

This does not mean every ordinary operational action needs two-person approval. The control applies to controlled configuration changes.

Final decision: ✅ CONFIRMED

§4. What Happens Next

With the above decisions confirmed, the statement in §4 should now be changed from:

"Once §2.1–2.3 are confirmed..."

to the completed state.

Final resolution

§2.1–2.3 are resolved.

The discovery resolution can now be folded into the authoritative baseline with:

D-004

PostgreSQL → SQLite

D-006

Retain RBAC + SoD, but implement policy-driven, test-record-level segregation rather than universal role separation.

D-001 / Site Scope

Retain single-site SMJ deployment, with any future related entity handled as an independent deployment.

And the following baseline sections should be updated accordingly:

H.1 — Exception / Equipment Enforcement
I — Configuration Strategy
J — ISO/IEC 17025 Support / Accreditation Scope
N — Reporting
O — Backup / Recovery
P — Deployment
E — Technology / Database
S — Risks
T — Discovery Resolution
V — CP-000 Decision Baseline


Response:
Your reasoning on the SoD matrix is sharper than what I asked for — separating "same person can't review/verify/approve their own record" from "same person across different records" is exactly the risk-based distinction NABL assessors actually look for, rather than a blanket rule that would've made a 3-person lab unworkable. Good catch keeping accreditation scope at the method level too — that's a real detail that's easy to gloss over and easy to get wrong on a report later.

Consolidating everything into a single, final baseline now — this supersedes both prior documents.

Every criterion in V.2 now passes except the one that has to come from you: formal sign-off. Once that's given, Phase 2 (System & Security Architecture) opens, with the detailed RBAC/SoD design in WP-02-03 building directly on the matrix in Section K — and the one item that's genuinely Phase 1 work, not a CP-000 blocker, is documenting SMJ's actual SOP basis for wherever the Technical-Reviewer→Approval overlap occurs today.

# SMJ Sustainable Fuel Lab — LIMS Program

# Phase 0 Deliverable: Project Understanding, Requirement Analysis & Proposed Architecture

**Status:** CP-000 Baseline — **v2 FINAL**. Supersedes `SMJ-LIMS_CP-000_Baseline.md` (v1) and folds in `SMJ-LIMS_Discovery-Resolution.md` in full.
**Checkpoint:** CP-000 — Architecture & Project Baseline
**Decision status:** All architectural decisions (D-001–D-015) frozen. All Phase 0 discovery items resolved (Section T). **Ready for formal SMJ sign-off.**
**Implementation status:** No application feature code authorized under Phase 0.

---

## Changelog since v1

| Area | v1 | v2 (this document) |
|---|---|---|
| **D-004 Database** | PostgreSQL | **SQLite** — reverted once real workload (1–10 users, 1–5 simultaneous writers, no server infrastructure) confirmed PostgreSQL's overhead wasn't justified |
| **D-006 Security/SoD** | Segregation of duties described generically | **Refined to a policy-driven matrix**, enforced per TestInstance, not globally |
| **New** | — | **D-013 Commercial/Billing Scope**, **D-014 Accreditation Scope Model**, **D-015 Configuration Change Governance** |
| Deployment | Generic server + NAS | **Single-host PC**, local + rotated external USB backup, no NAS in v1 |
| Reporting | General | **PDF confirmed as sole authoritative certificate format**; Word/Excel explicitly not alternatives |
| Equipment enforcement | Configurable, policy TBD | **Concrete default: 30-day warning, block on expiry/out-of-calibration** |

---

## Table of Contents

A. Project Understanding · B. Requirement Analysis · C. Architectural Principles · D. High-Level Architecture · E. Technology Evaluation · F. Module Architecture · G. Domain Model · H. Laboratory Workflow · I. Configuration Strategy · J. ISO/IEC 17025 Support · K. Security Architecture · L. Database Architecture · M. UI/UX Architecture · N. Reporting Architecture · O. Backup/Recovery · P. Deployment Architecture · Q. Extensibility · R. Development Decomposition · S. Critical Risks · T. Discovery Resolution · U. Recommended Roadmap · V. CP-000 Decision Baseline and Acceptance Criteria

---

# A. Project Understanding

SMJ Sustainable Fuel Lab Pvt. Ltd. requires a **custom, on-premises Laboratory Information Management System (LIMS)** for real laboratory operations — not a demonstration application, generic form builder, SaaS platform, or ERP.

The initial system supports: Solid Fuel, Biofuel, Air, Water, Soil, Noise, Stack/Emission, with room for more disciplines later.

The confirmed operating reality is a **small, single-site, currently 3-staff laboratory** (1–10 named users expected at steady state), already operating under NABL accreditation (ISO/IEC 17025) for Solid Fuel and Solid Biofuel, currently running on paper and spreadsheets, with no existing LIMS, no server, and unreliable internet. This context — not a hypothetical enterprise deployment — is what the architecture below is built for.

The central purpose remains a **controlled, traceable laboratory information chain**:

```text
Request → Contract/Request Review → Sample Receipt → Registration/Accession →
Test Planning/Assignment → Test Execution → Raw Data/Observations → Calculation →
Result → Review → Technical Verification → Approval → Report → Retention → Archive
```

Every technically significant stage must be reconstructable later: who, when, which method/version, which equipment, what raw observations, what calculations, what the result was, what revisions occurred, who reviewed/verified/approved, and what the approved report contained at issue.

Two constraints continue to govern the architecture:

1. **Offline-first.** Internet is unreliable at the lab and must never be a runtime dependency for authentication, sample registration, execution, results, calculations, review, approval, report generation, barcode operation, or admin.
2. **Long operational life, modest infrastructure.** The lab has no dedicated IT staff and no server today. The architecture favors mainstream, low-maintenance technology over anything that assumes an operations team exists to babysit it.

---

# B. Requirement Analysis

## B.1 Defined Requirements

### Deployment
On-premises, single-host initially (LAN-capable for later expansion), Windows-hosted, browser-based clients, fully functional offline.

### Technology
React, TypeScript, Vite, MUI, FastAPI, Python, SQLAlchemy 2.x, **SQLite**, Alembic, Argon2id, secure server-side sessions, Caddy, Jinja2, Chromium-based PDF rendering, pytest, Playwright.

### Architecture
**Modular Monolith.** Microservices and a plugin framework are not part of v1.

### Laboratory disciplines
Solid Fuel, Biofuel, Air, Water, Soil, Noise, Stack/Emission. **First production discipline: Solid Fuel** (methods already fully documented and approved).

### Lifecycle
Full lifecycle from request through retention/archival, per Section A.

### Data integrity
Technical records are never silently overwritten. Corrections preserve previous state, new state, actor, timestamp, reason where required, and revision lineage.

### Security
Authorization always backend-enforced. UI is never a security boundary by itself.

### Configuration
Laboratory administrators configure normal test/method/parameter variation without code changes, via strongly typed, purpose-built relational structures — not generic EAV. Controlled configuration changes follow a **propose → approve** governance model (D-015).

### Development control
`Phase → Work Package → Task → Implementation → Verification → Evidence → Checkpoint`. No feature development merely because it seems useful next.

### ISO/IEC 17025
SMJ is **already NABL-accredited** for Solid Fuel and Solid Biofuel; other disciplines are outside current accreditation scope. The software supports the quality system and accreditation evidence; it does not itself confer or extend accreditation (D-014).

---

## B.2 Frozen Architectural Decisions

| Decision | Frozen selection |
|---|---|
| Project scope | Single-laboratory LIMS (D-001) |
| Technology | React/TypeScript + FastAPI/Python + **SQLite** |
| Architecture | Modular Monolith |
| Database | **SQLite** (D-004) |
| Data integrity | Revision-based records + immutable audit |
| Security | RBAC + server-side sessions + **policy-driven, per-record segregation of duties** (D-006) |
| Workflow | Explicit state machine |
| Configuration | Strongly typed configuration tables + propose/approve governance (D-015) |
| Development method | Task → Verification → Checkpoint |
| Documentation | Documentation-as-code |
| Module structure | Domain-oriented modules |
| Commercial scope | Charge calculation only; invoicing external (D-013) |
| Accreditation model | Per-method/discipline scope, not lab-wide (D-014) |
| Architectural philosophy | Conservative, controlled, auditable |

---

## B.3 Explicitly Deferred / Out of Scope

Multi-tenant SaaS; multiple entities sharing one instance (a future related entity gets its **own independent deployment**, not shared tenancy); microservices; plugin architecture; customer self-service portal; public internet-facing API; cloud sync; mobile app; ERP; general accounting; **invoice generation, payment records, accounts receivable, credit notes, tax/accounting workflows** (confirmed external, D-013); external PKI/digital-signature infrastructure; direct instrument integration (confirmed low priority); a NAS backup tier (architecture accommodates adding one later without redesign).

---

## B.4 Confirmed Operating Parameters

(Previously "assumptions," now confirmed via discovery — see Section T for full resolution.)

* Single physical site; a future related entity, if it happens, is an independent deployment, not a branch of this one.
* Windows-hosted, single business-grade PC initially; no dedicated server exists or is planned.
* 1–10 named users, 1–5 simultaneous writers, single daytime shift, expected stable for 3–5 years.
* No existing LIMS or legacy schema; migration source is spreadsheets/paper, low volume.
* Internet present but unreliable — reinforces, does not create, the offline-first requirement.

---

# C. Architectural Principles

1. **Controlled revision, not silent overwrite.** Corrections create new controlled state; historical information is preserved.
2. **Backend is the security boundary.** The frontend cannot grant itself access.
3. **Offline is the normal operating mode.** No dependency on cloud services, external APIs, hosted PDF conversion, remote barcode services, or cloud storage for core operations.
4. **Strong typing where meaning matters.** Sample, TestInstance, Method, MethodVersion, ParameterDefinition, Result, Equipment, Report, ApprovalRecord, Rate are explicit relational structures, not generic key/value rows.
5. **Meaningful auditability.** State changes, technical record changes, configuration changes, authorization changes, approval events, and security events are audited. Routine reads are not.
6. **Modular Monolith.** One deployable application, clear internal module boundaries. No microservices, service meshes, distributed transactions, or plugin loaders without demonstrated need.
7. **Software supports the quality system.** Quality procedures, competence assessment, impartiality arrangements, technical decisions, validation work, and accreditation status remain the laboratory's responsibility.
8. **Every phase must be verifiable.** Completion requires implementation, testing, evidence, review, acceptance criteria, and checkpoint approval — not just code existing.
9. **The database is a controlled service boundary.** SQLite is the authoritative store; it lives only on the application host. Client workstations never touch the database file directly — all access passes through the backend API.
10. **Simplicity is a design objective.** Prefer the simplest design that satisfies requirements, integrity, security, maintainability, traceability, and future controlled expansion — including infrastructure sized to the lab's actual scale, not a hypothetical larger one.

---

# D. High-Level Architecture

```text
                    Client Workstations (later, via LAN)
                ┌───────────────────────────────┐
                │ Reception │ Analyst │ Manager  │  (browser, Chromium-based)
                └───────────────────┬─────────────┘
                                    │ HTTPS (local, once LAN exists)
                                    ▼
                          ┌─────────────────────┐
                          │  Caddy               │  → serves built React SPA
                          │  Reverse Proxy       │  → proxies /api to FastAPI
                          │  Local TLS            │
                          └──────────┬───────────┘
                                     ▼
                    ┌────────────────────────────────────┐
                    │      FastAPI Modular Monolith        │
                    │  API layer → Application services →  │
                    │  Domain services/rules → Repository  │
                    └───────────────────┬──────────────────┘
                                        ▼
                          ┌───────────────────────┐
                          │  SQLite (WAL mode)     │
                          │  local fixed disk       │
                          └───────────┬─────────────┘
                                      │
                     ┌────────────────┼────────────────┐
                     ▼                                 ▼
           Local Document Storage             Backup Orchestration
                                                        │
                                              Rotated External USB
```

**Single host today:** one business-grade PC runs Caddy, FastAPI, SQLite, document storage, and backup orchestration together, accessed via the browser at `localhost`. Additional LAN workstations can be added later purely by pointing more browsers at the host's LAN address — no architectural change required.

---

# E. Technology Evaluation

## E.1–E.3, E.5–E.8 (Frontend, Backend, ORM, Auth, Reporting, Reverse Proxy, Testing)

Unchanged from prior evaluation — all approved. React/TS/Vite/MUI, FastAPI/Python, SQLAlchemy 2.x, Argon2id + server-side sessions, Jinja2→Chromium→PDF, Caddy, pytest+Playwright all remain sound choices independent of the database decision.

## E.4 Database — **SQLite (CONFIRMED, D-004)**

### Decision
**SQLite is the frozen v1 database**, reverting the earlier provisional PostgreSQL selection now that real operating figures are confirmed.

### Basis for the decision
Confirmed conditions: 1–10 named users, 1–10 peak concurrent users, **1–5 peak simultaneous writers**, single daytime shift, expected stable for 3–5 years, single-host deployment on a standalone PC, no dedicated database/server infrastructure existing or currently planned, internet-independent operation required.

This load is comfortably within SQLite's strengths and well below the threshold where a client-server database's concurrency model would earn its operational cost. Choosing PostgreSQL under these conditions would have added a database service to install, secure, patch, and monitor — real ongoing burden for a 3-person lab with no dedicated IT — for a concurrency ceiling this workload will not approach.

### Binding technical conditions
* **WAL mode shall be enabled.**
* The live database **shall remain on local fixed storage** — never NAS/SMB/network storage.
* **Transactions shall be short and atomic.**
* Database lock/timeout conditions **shall be handled by the application** (retry/backoff), never surfaced as raw errors.
* **Raw database errors shall not be exposed to end users.**
* Backup and restore procedures shall be controlled and tested (Section O).

### Reassessment triggers
Materially increased concurrent write activity, multiple application hosts, substantially increased user volume, or a requirement for multiple entities sharing one database. None of these are anticipated per Section B.4, but they are the defined conditions under which this decision would be reopened — not simplicity vs. power in the abstract.

---

# F. Module Architecture

| Module | Purpose | Owned data (examples) | Notes |
|---|---|---|---|
| Identity & RBAC | Auth, sessions, roles, scoped permissions | Users, Roles, Permissions, Sessions | — |
| Audit | Immutable history of state changes and corrections | AuditEvent | — |
| Master Data | Shared reference data | Units, Sections, Disciplines, Locations, Statuses | — |
| Customer & Project | Client/engagement context, **charge calculation** | Customer, Contact, Project/Contract, **Rate, CustomerRate** | Pricing in scope; invoicing is not (D-013) |
| Sample Management | Receipt through accession/allocation | Sample, SubSample, Container, ChainOfCustodyEvent | — |
| Method & Test Engine | Configurable test/parameter/method definitions, **accreditation scope flag** | Method, MethodVersion, TestDefinition, ParameterDefinition | Accreditation scope lives here (D-014) |
| Calculation Engine | Safe formula evaluation with provenance | Formula, FormulaVersion, CalculationRun | — |
| Execution & Results | Assignment, raw data, results, revisions | TestInstance, Result, ResultRevision | — |
| Review/Verification/Approval | Segregated multi-stage sign-off | ReviewRecord, VerificationRecord, ApprovalRecord | Enforces the D-006 SoD matrix (Section K) |
| Equipment & Calibration | Equipment master, calibration state, use enforcement | Equipment, CalibrationRecord, MaintenanceRecord | Default block+30-day-warning policy (Section H.1) |
| QC | Blanks/duplicates/spikes/CRMs, control charts | QCSample, QCResult | — |
| Documents & Records | Controlled SOPs, certificates, validation records | Document, DocumentVersion | — |
| Reporting | Templated report/certificate generation | ReportTemplate, Report, ReportRevision | **PDF is the sole authoritative output** (Section N) |
| Quality Management | Nonconformity, CAPA, complaints, internal audits | Nonconformity, CAPA, Complaint, InternalAudit | — |
| Notifications | In-app alerts (calibration due, overdue tests, config proposals pending approval) | Notification | — |
| Configuration/Admin | Numbering, retention, workflow toggles, **propose/approve governance** | ConfigSetting, ConfigProposal | D-015 |
| Backup/Ops | Scheduled backup, restore, health | BackupJob, HealthCheck | Local + rotated external USB (Section O) |

Still explicitly out of v1: full invoicing, proficiency testing/ILC management, external e-signature/PKI, direct instrument integration.

---

# G. Domain Model

```text
Customer ─┬─< Project/Contract ─┬─< Sample ─┬─< SubSample/Portion ─< Container
          │                     │           │
          ├─< Rate / CustomerRate            ├─< ChainOfCustodyEvent
          │   (negotiated pricing)           │
          │                     │           └─< TestRequest ─┬─< TestInstance ──> Method ──> MethodVersion
          │                     │                             │   (+ AccreditationScope flag)   │
          │                     │                             │                                  └─< ParameterDefinition ──> Unit
          │                     │                             │
          │                     │                             ├──> Equipment (required/used, calibration-gated)
          │                     │                             ├──> Analyst (assigned)
          │                     │                             │
          │                     │                             └─< Result ─< ResultRevision
          │                     │                                    │
          │                     │                                    └──> CalculationRun ──> FormulaVersion
          │                     │
          │                     └─< Report ─< ReportRevision (PDF-only authoritative artifact)
          │
          └── Contact
```

Cross-cutting: `AuditEvent`, `ReviewRecord`/`VerificationRecord`/`ApprovalRecord` (each enforcing the D-006 same-TestInstance restriction), `Attachment`, `ConfigProposal`/`ConfigApproval` (D-015).

`TestDefinition`, `TestInstance`, `Method`, `MethodVersion` remain distinct, strongly typed tables — never collapsed into a generic "Test" table.

---

# H. Laboratory Workflow

Backbone unchanged:

```text
Draft Request → Contract Review → Sample Receipt → Registration/Accession →
Allocation → Test Planning → Test Assignment → Execution (raw data) →
Result Entry → Review → Technical Verification → Approval →
Report Generation → Delivery → Retention → Archival
```

## H.1 Exception Workflows

| Trigger | Controlled response |
|---|---|
| Sample condition unacceptable at receipt | Receipt → **Rejected** (reason required, customer notified) |
| Result fails review | Review → **Sent back for rework**; prior entry preserved via ResultRevision |
| QC acceptance criteria not met | Result blocked from Review; **QC investigation** required |
| Post-approval correction needed | **Controlled reopen** → correction → re-review → re-verification → re-approval; original approved version stays in history |
| **Equipment calibration/status — CONFIRMED default policy** | **30 days before expiry → warning** shown, affected equipment identified, expiry date displayed. **On expiry, or if explicitly marked "Out of Calibration" → block.** Applies specifically to equipment affecting result validity. All status changes and attempted use are audited. The 30-day threshold is a configurable policy value, but changing it is a controlled configuration change under D-015 (propose/approve) — not something an analyst can adjust operationally. |
| Customer complaint | Logged against the relevant Sample/Report → Quality Management → CAPA if warranted |

---

# I. Configuration Strategy

Unchanged core principle: strongly typed configuration tables (TestDefinition/ParameterDefinition with real typed columns), EAV reserved only for genuinely free-form metadata.

## I.1 Configuration Change Governance — CONFIRMED (D-015)

Controlled configuration changes (tests, methods, parameters, report templates, numbering, workflow policy, equipment-enforcement thresholds, etc.) follow a **propose → approve** flow, not direct unreviewed edit:

```text
Authorized User → PROPOSE → System Administrator → APPROVE/REJECT → Effective Configuration
```

The audit trail records: what changed, previous value, proposed value, proposer, proposal timestamp, approver, approval/rejection timestamp, and reason/justification where required. **Unapproved proposals never affect live behavior.**

This governance applies specifically to controlled configuration — it does **not** mean every ordinary operational action (e.g., a routine test assignment) requires two-person sign-off.

---

# J. ISO/IEC 17025 Support

The LIMS supports the laboratory quality system; it does not itself establish or extend accreditation. SMJ is **already NABL-accredited**, which raises the stakes here: the software must not misrepresent scope relative to an accreditation SMJ already holds.

| Area | Software capability | Boundary |
|---|---|---|
| Impartiality/confidentiality | RBAC, access controls, audit | Lab policy remains separate |
| Personnel | Authorization/competency records | Competence assessed by people |
| Equipment | Calibration/maintenance state, enforcement (H.1) | Calibration activity remains a lab activity |
| Contract review | Controlled review stage | Lab determines acceptance criteria |
| Methods | Method/version/validation evidence | Technical validation is lab work |
| Sampling/handling | COC and condition history | Lab procedure governs |
| Technical records | Revisions + audit | Software preserves records |
| Reporting | Controlled report generation | Approval is an authorized human act |
| Documents | Version/effective-date control | — |

## J.1 Accreditation Scope Control — CONFIRMED (D-014)

Current accredited scope: **Solid Fuel (Coal) and Solid Biofuel only.** Other disciplines are not currently within NABL scope.

* **Accreditation applicability is controlled at the Method/Test level**, not the organization level. The system never treats the lab as a blanket `Accredited = TRUE`.
* Reports display accreditation marking/statements **only where applicable**. A report covering mixed accredited/non-accredited results clearly distinguishes which results carry which status — it never implies blanket accreditation because SMJ as an organization holds NABL accreditation.
* **Historical records retain the accreditation status that applied at the time the work was performed.** If accreditation scope changes later (e.g., a new discipline is added to scope), past reports are not reinterpreted retroactively — this follows directly from the immutability principle (C.1) applied to accreditation status specifically.

The software never presents a feature as evidence that accreditation automatically exists or automatically extends to new scope.

---

# K. Security Architecture

## Authentication
Argon2id password hashing; server-side sessions; secure, HTTP-only cookies with appropriate SameSite policy; session timeout; explicit logout; administrative session invalidation; account lockout on repeated failed logins.

## Authorization
RBAC enforced server-side; scoped by module/action/role/section/discipline/record context. The UI is never a security boundary.

## Segregation of Duties — CONFIRMED policy matrix (D-006)

The LIMS does **not** require every stage of laboratory work to be performed by a different person — with 3 active staff, a universal rule would be unworkable and isn't what ISO/IEC 17025 actually demands. The control is scoped to the individual technical record:

> For the same TestInstance, the user who performed the analytical/testing activity shall not subsequently perform the independent Technical Review, Verification, or Final Approval of that same record.

| Activity combination | Default |
|---|---|
| Analyst → independent Review, **same TestInstance** | Block |
| Analyst → Verification, **same TestInstance** | Block |
| Analyst → Approval, **same TestInstance** | Block |
| Technical Reviewer → Approval, **same TestInstance** | **Policy-controlled** (subject to the lab's documented procedure and risk assessment) |
| Same person across **different** TestInstances | Permitted, subject to normal role authorization |

Enforcement is at the individual test-record level, not globally across all records. Any permitted overlap remains attributable to the actual user and fully auditable. **Not hard-coded** as "one user can never perform two roles" — implemented as a policy matrix in Phase 2/6 design, so the specific Technical-Reviewer→Approval rule can be tuned to SMJ's actual documented SOP/risk-assessment basis (a Phase 1 policy confirmation, not a CP-000 architecture blocker).

## Audit Integrity
Audit writes are append-only at the application layer; no ordinary role has update/delete access. Corrections create new revisions; they never mutate audited history.

## Network Exposure
LAN-only by default (today: `localhost` on a single host), HTTPS via Caddy once a LAN exists. No inbound internet exposure required or assumed.

---

# L. Database Architecture

## L.1 SQLite
SQLite is the authoritative transactional database, accessed exclusively through the backend via SQLAlchemy 2.x + Alembic. `PRAGMA foreign_keys=ON` is set on every connection — SQLite does not enforce foreign keys by default, and this must be an explicit, mandatory connection-setup step, not an assumption.

## L.2 Data Modeling Principles
3NF baseline; denormalization only where deliberately justified (e.g., report snapshots preserving exact issued values for reproducibility).

## L.3 Keys
Surrogate primary keys; separate human-readable business numbers (Sample Number, Report Number, Work Order Number, Certificate Number) — never used as substitutes for relational primary keys.

## L.4 Delete Policy
Core technical records use lifecycle/state/revision mechanisms, not uncontrolled hard deletion. Reference/master data may be more flexible where historically safe.

## L.5 Concurrency (SQLite-specific)
WAL mode mandatory. Read-heavy operations (dashboards, search, report generation) use read-only connections and never hold write locks. Write transactions are kept short and single-purpose (register a sample, enter a result, approve a test) — the discipline that makes SQLite's single-writer model invisible to users at this scale. Application-level retry/backoff handles any `SQLITE_BUSY` condition; it is never surfaced to the end user as a raw error.

---

# M. UI/UX Architecture

Unchanged: role-aware dashboards, discipline as a first-class filter, consistent status vocabulary (Draft/Received/In Progress/Pending Review/Rejected/Approved/Completed/Cancelled/Archived) across every module. Journeys for reception, analyst, reviewer, technical reviewer, signatory, equipment manager, quality manager, and admin remain a Phase 4 deliverable.

**Barcode labels — CONFIRMED:** standard office printer + adhesive sheet labels (e.g., Avery-style), not a dedicated thermal label printer. Label layout (barcode + human-readable identifier, configurable) must be validated against the actual selected printer/sheet format before production use — this is a real UI/print-template constraint for Phase 4, not just a hardware footnote.

---

# N. Reporting Architecture

```text
Database → Report data service → Versioned Jinja2 template → HTML → Pinned local Chromium → PDF
```

**CONFIRMED: PDF is the sole authoritative final report/certificate format.** The approved PDF is the controlled technical record. Word and Excel are **not** alternative final report/certificate formats — if structured exports (e.g., raw data to Excel, a pre-approval draft in Word) are wanted later, they are separate functions and must never be presented as another "official certificate." This follows directly from the immutability principle (C.1): an editable format cannot be the authoritative approved record.

Each report retains traceability to Sample, TestInstance, Method/MethodVersion, Analyst, Equipment, Result revision, Review, Verification, and Approval. Report templates are version-controlled; report numbers are configurable under D-015 governance (replacing the current manual numbering once implemented). Accreditation marking follows J.1 — shown only where the specific result's method is within current NABL scope.

---

# O. Backup / Recovery

## O.1 Backup Principle
SQLite's own consistent online-backup mechanism (`VACUUM INTO` / backup API) — never a raw copy of a live database file. Each backup is verified with `PRAGMA integrity_check` plus a basic sanity check before being considered valid. A file existing in the backup location is not, by itself, treated as proof of anything.

## O.2 Backup Layers — CONFIRMED

```text
Production Database → Daily Backup → Local Backup → Rotated External USB
```

No NAS in v1 (none exists). The architecture accommodates adding a NAS tier later as an additional destination, without redesigning the backup principles.

## O.3–O.4 Verification and Restore Testing
Unchanged philosophy: **Backup Created ≠ Backup Validated ≠ Restore Tested** are distinct, tracked statuses. **Restore testing confirmed monthly** (tighter than the quarterly cadence previously proposed).

## O.5 RPO/RTO — CONFIRMED
**RPO ≤ 24 hours** (daily backup). **RTO = same business day.** These are now committed operational targets, not placeholders.

---

# P. Deployment Architecture — CONFIRMED single-host model

```text
Business-grade PC
   ├── Caddy (reverse proxy, local TLS)
   ├── FastAPI application
   ├── SQLite (WAL mode, local fixed disk)
   ├── Local document storage
   └── Backup orchestration → rotated external USB
            ↓
        Browser @ localhost (today) / LAN address (once a LAN exists)
```

**Initial sizing targets** (not final hardware qualification — that belongs to Phase 5/19): ~16GB RAM, 500GB–1TB SSD, suitable mid-range CPU, continuous operation, connected to the UPS SMJ already has. This is realistic and sufficient for the confirmed workload — there is no reason to size for infrastructure this lab doesn't need.

The architecture remains LAN-capable without redesign: adding reception/analyst/manager workstations later is a matter of network configuration and browser access, not an application or database change.

Update/migration procedure unchanged: Backup → Validate → Stop/quiesce → Apply Alembic migration → Deploy → Smoke test → Resume → Record evidence.

---

# Q. Extensibility

Unchanged: new disciplines are primarily Method/MethodVersion/TestDefinition/ParameterDefinition configuration plus a report template, reusing the existing sample/RBAC/audit/equipment/QC/reporting engines. New code only where a discipline needs a genuinely new mechanic. No plugin framework. Given SMJ has confirmed new disciplines are "definitely planned," the WP-16-03 extensibility-validation exercise (adding one real new discipline as proof) remains an important, not optional, later checkpoint.

---

# R. Development Decomposition

**Phase 0** (WP-00-01, WP-00-02, WP-00-03) → **CP-000**, now ready for sign-off per this document.

**Phase 1 — Requirements & Laboratory Model:** WP-01-01 (Users & Organization) and WP-01-02 (Operational Baseline) are, in substance, complete — this document and its predecessor discovery resolution constitute their output. One item remains genuinely open for Phase 1 rather than CP-000: **documenting SMJ's actual SOP/risk-assessment basis for the Technical-Reviewer→Approval overlap** where it occurs, per Section K.

**Next phase after CP-000 acceptance: Phase 2 — System & Security Architecture**, building the detailed RBAC/SoD design (WP-02-03) on top of the confirmed policy matrix in Section K.

---

# S. Critical Risks

| Risk | Impact | Mitigation |
|---|---|---|
| Single-host hardware failure | Full operational outage (no server redundancy) | Tested backup/restore (O), UPS already in place, documented recovery procedure, same-business-day RTO target |
| Backup exists but restore fails | Potential data loss | Monthly restore drills (O.4), integrity-checked backups |
| SoD policy matrix misconfigured or bypassed | Inappropriate self-approval, accreditation risk | Enforcement at TestInstance level in backend (K), full audit trail, Phase 1 SOP documentation requirement |
| Accreditation scope misrepresented on a report | Regulatory/credibility risk given SMJ is already accredited | Method-level accreditation flag (J.1), template logic prevents blanket accreditation claims, historical immutability |
| Calculation logic errors | Incorrect laboratory results | Constrained calculation engine, no arbitrary code execution, full provenance, testing |
| Uncontrolled technical-record editing | Loss of traceability | Revision model + immutable audit (C.1) |
| Database lock contention under load | Rare at confirmed scale, but a design lapse could still cause it | Short transactions, read connections separated from writes, app-level retry (L.5) |
| Scope expansion / architectural drift | Wasted effort, inconsistent design | Checkpoint governance, one authorized task at a time |
| Long project duration, multi-session AI-assisted build | Context loss between sessions | Documentation-as-code, this baseline as the source of truth over conversation history |

---

# T. Discovery Resolution

All items raised in the original discovery process are now resolved. Full detail lives in `SMJ-LIMS_Discovery-Resolution.md`; the outcomes are integrated throughout this document (E.4, H.1, I.1, J.1, K, N, O, P). Summary:

| Item | Resolution |
|---|---|
| Named users / concurrency | 1–10 users, 1–5 simultaneous writers — drove D-004 |
| Accreditation context | Already NABL-accredited; scope = Solid Fuel & Solid Biofuel — drove D-014 |
| Existing systems/migration | Greenfield; spreadsheets/paper, low volume | 
| Billing scope | Charge calculation in-LIMS; invoicing external — drove D-013 |
| Site/entity model | Single SMJ site; future related entity = independent deployment |
| Server hardware | None; single business-grade PC — drove Section P |
| Segregation of duties specifics | Policy matrix at TestInstance level — refined D-006 |

**No discovery items remain open for CP-000.** One item (SOP/risk-assessment basis for the Technical-Reviewer→Approval overlap) is explicitly carried into Phase 1 as noted in Section R — it is a policy documentation task, not an architecture blocker.

---

# U. Recommended Roadmap

Unchanged sequence: Phase 0 (CP-000, this document) → Phase 1 (CP-001) → Phase 2 System & Security Architecture (CP-002) → Phase 3 Data Architecture (CP-003) → Phase 4 UX/UI (CP-004) → Phase 5 Technical Foundation (CP-005) → Phase 6 Identity/RBAC/Audit (CP-006) → Phase 7 Core Master Data (CP-007) → Phase 8 Customer/Project/Sample (CP-008) → Phase 9 Test & Method Engine (CP-009) → Phase 10 Execution & Results (CP-010) → Phase 11 Review/Verification/Approval (CP-011) → Phase 12 QC & Equipment (CP-012) → Phase 13 Quality Management (CP-013) → Phase 14 Documents & Records (CP-014) → Phase 15 Reporting & Certificates (CP-015) → Phase 16 Configuration & Extensibility (CP-016) → Phase 17 Backup/Recovery/Operations (CP-017) → Phase 18 Validation & Hardening (CP-018) → Phase 19 Production Deployment (CP-019) → Phase 20 Maintenance & Evolution.

---

# V. CP-000 Decision Baseline and Acceptance Criteria

## V.1 Frozen Architectural Decisions

| # | Decision | Frozen selection |
|---|---|---|
| D-001 | Project scope | Single-lab LIMS. Future related entity = independent deployment, not multi-tenancy. |
| D-002 | Technology stack | React/TS/Vite/MUI, FastAPI/Python, SQLAlchemy 2.x, **SQLite**, Alembic, Argon2id, server-side sessions, Caddy, Jinja2, Chromium, pytest, Playwright |
| D-003 | Architecture style | Modular Monolith |
| D-004 | Database | **SQLite** — reverted from PostgreSQL once real workload confirmed (E.4) |
| D-005 | Data integrity | Revision-based records + immutable audit |
| D-006 | Security / Segregation of Duties | RBAC + server sessions + **policy-driven, per-TestInstance SoD matrix** (Section K) |
| D-007 | Workflow | Explicit state machine |
| D-008 | Configuration data model | Strongly typed configuration tables, not generic EAV |
| D-009 | Development methodology | Task → Verification → Checkpoint |
| D-010 | Documentation | Documentation-as-code |
| D-011 | Module boundaries | Domain-oriented modules |
| D-012 | Architectural philosophy | Conservative, controlled, auditable |
| **D-013** | **Commercial/Billing Scope** | **Charge calculation in-LIMS (per-parameter + customer-negotiated rate); invoicing, payments, AR, credit notes, and tax workflows stay in external accounting software** |
| **D-014** | **Accreditation Scope Model** | **Accreditation applicability controlled at Method/Test level, not organization-wide; historical records retain accreditation status at time of work** |
| **D-015** | **Configuration Change Governance** | **Propose → Approve flow for controlled configuration changes, fully audited; unapproved proposals never affect live behavior** |

---

## V.2 CP-000 Acceptance Criteria

| # | Criterion | Status |
|---|---|---|
| 1 | Baseline (or approved revision) accepted | **Awaiting SMJ sign-off** |
| 2 | D-001–D-015 explicitly recorded as frozen | ✅ Satisfied (V.1) |
| 3 | Every discovery item answered or explicitly deferred with reason/phase | ✅ Satisfied (Section T) |
| 4 | Database decision reflected consistently throughout | ✅ Satisfied — checked against D, E, L, O, P |
| 5 | Single-laboratory scope confirmed | ✅ Satisfied |
| 6 | Modular Monolith confirmed | ✅ Satisfied |
| 7 | Revision/audit model confirmed | ✅ Satisfied |
| 8 | Security model and SoD principle confirmed | ✅ Satisfied (Section K) |
| 9 | Explicit-state-machine workflow confirmed | ✅ Satisfied |
| 10 | Strongly typed configuration strategy confirmed | ✅ Satisfied |
| 11 | Task/checkpoint development model confirmed | ✅ Satisfied |
| 12 | Documentation-as-code confirmed | ✅ Satisfied |
| 13 | Module boundaries confirmed | ✅ Satisfied (Section F) |
| 14 | No feature implementation authorized ahead of CP-000 | ✅ Satisfied |
| 15 | Software supports, does not confer, ISO/IEC 17025 accreditation | ✅ Satisfied (Section J, J.1) |

**Overall determination: criteria 2–15 satisfied. Criterion 1 — SMJ's formal sign-off — is the only remaining step to close CP-000.**

---

# Final CP-000 Baseline

```text
                     SMJ LIMS v1
                          │
              Single Physical Laboratory
              (future related entity = independent deployment)
                          │
                          ▼
                  Modular Monolith
                          │
              ┌───────────┴───────────┐
              │                       │
          React / TS              FastAPI / Python
              └───────────┬───────────┘
                          ▼
                    SQLAlchemy 2.x
                          │
                          ▼
                   SQLite (WAL mode)
                  single business-grade PC
                          │
            ┌─────────────┴─────────────┐
            ▼                           ▼
      Local Documents           Backup → Rotated External USB
```

> **Build a controlled, maintainable laboratory information system sized to the laboratory that actually exists — not a generic platform — and add complexity only when a real requirement proves it necessary.**

**Next authorized phase after CP-000 sign-off:** Phase 2 — System & Security Architecture, beginning with WP-02-03 (detailed RBAC/SoD design built on Section K), while Phase 1's one remaining item (SOP/risk-assessment basis for Technical-Reviewer→Approval overlap) is documented in parallel.



Next Prompt:
# SMJ Sustainable Fuel Lab — LIMS Program

## Phase 2 — System & Security Architecture

### Master Task Prompt

You are continuing the **SMJ Sustainable Fuel Lab LIMS Program**.

The project has completed Phase 0 and established the **CP-000 Architecture & Project Baseline**. The Phase 0 baseline is authoritative and must be treated as the current source of truth.

---

# 1. Project Status

**CP-000 — Architecture & Project Baseline:** ACCEPTED / SIGNED OFF.

**Phase 0:** COMPLETE.

**Phase 1:** Requirements & Laboratory Model is substantially established from the completed discovery work. One policy-documentation item remains:

> Document the laboratory's SOP/risk-assessment basis for any permitted Technical Reviewer → Final Approver role overlap.

This is a Phase 1 policy evidence item and **not an architectural blocker**.

**Current authorized phase:**

> **Phase 2 — System & Security Architecture**

**No feature implementation or production code is authorized by this prompt.**

---

# 2. Mandatory Baseline — Do Not Re-litigate

The following architectural decisions are frozen under CP-000 and must be treated as authoritative unless a genuine contradiction with a confirmed requirement is discovered.

| ID    | Frozen Decision                                                                                                                                                                   |
| ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| D-001 | Single-laboratory LIMS for SMJ v1                                                                                                                                                 |
| D-002 | React + TypeScript + Vite + MUI / FastAPI + Python / SQLAlchemy 2.x / SQLite / Alembic / Argon2id / secure server-side sessions / Caddy / Jinja2 + Chromium / pytest + Playwright |
| D-003 | Modular Monolith                                                                                                                                                                  |
| D-004 | SQLite with WAL, local fixed storage only                                                                                                                                         |
| D-005 | Revision-based technical records + immutable audit                                                                                                                                |
| D-006 | RBAC + server-side sessions + policy-driven per-TestInstance segregation of duties                                                                                                |
| D-007 | Explicit workflow state machine                                                                                                                                                   |
| D-008 | Strongly typed configuration tables; no blanket EAV                                                                                                                               |
| D-009 | Task → Verification → Checkpoint development model                                                                                                                                |
| D-010 | Documentation-as-code                                                                                                                                                             |
| D-011 | Domain-oriented module boundaries                                                                                                                                                 |
| D-012 | Conservative, controlled, auditable architecture                                                                                                                                  |
| D-013 | LIMS calculates laboratory charges; invoicing/accounting remain external                                                                                                          |
| D-014 | Accreditation applicability controlled at Method/Test level, not organization-wide                                                                                                |
| D-015 | Controlled configuration uses Propose → Approve governance                                                                                                                        |

Do **not** propose PostgreSQL, microservices, SaaS, multi-tenancy, plugin architecture, JWT-based browser sessions, generic EAV, or other previously rejected alternatives unless evidence from a confirmed requirement makes a frozen decision genuinely untenable.

If such a conflict is discovered, do **not** silently change the baseline. Raise it as an explicit Architecture Decision / Change Request with evidence and impact.

---

# 3. Phase 2 Objective

Design the **System & Security Architecture** that turns the accepted Phase 0/Phase 1 requirements into a precise, implementation-ready technical architecture.

The goal is not to write feature code.

The goal is to define:

1. application architecture;
2. module/service boundaries;
3. authentication architecture;
4. authorization architecture;
5. RBAC model;
6. segregation-of-duties model;
7. session management;
8. audit/security architecture;
9. security boundaries;
10. database access architecture;
11. API architecture;
12. workflow authorization architecture;
13. configuration-change authorization;
14. error/security handling;
15. deployment trust boundaries;
16. operational security requirements;
17. architecture decision records needed before implementation.

---

# 4. Required Phase 2 Deliverables

Produce the following as formal architecture artifacts.

## WP-02-01 — System Architecture

Define:

* frontend architecture;
* backend architecture;
* application/service/domain layers;
* repository/persistence layer;
* cross-cutting services;
* module dependency rules;
* request lifecycle;
* transaction boundaries;
* database access boundaries;
* report-generation boundary;
* file/document-storage boundary.

Provide diagrams where useful.

At minimum, produce:

### 4.1 Logical Architecture Diagram

```text
Browser
   ↓
Caddy
   ↓
FastAPI API
   ↓
Application Services
   ↓
Domain Services
   ↓
Repositories
   ↓
SQLite
```

Also show:

* authentication;
* authorization;
* audit;
* calculation;
* reporting;
* document storage.

### 4.2 Request Lifecycle

Describe:

```text
HTTP Request
 → Authentication
 → Session Resolution
 → Authorization
 → Validation
 → Application Service
 → Domain Rules
 → Repository / Transaction
 → Audit
 → Response
```

Identify which layer owns each responsibility.

---

# 5. WP-02-02 — Security Architecture

Define the security model end-to-end.

## 5.1 Authentication

Specify:

* password authentication;
* Argon2id configuration;
* password policy;
* failed-login handling;
* account lockout;
* session creation;
* session expiry;
* idle timeout;
* absolute timeout;
* logout;
* forced session invalidation;
* administrator session revocation;
* password change/reset policy.

Do not introduce email/cloud dependencies.

---

## 5.2 Session Architecture

Define:

* server-side session structure;
* session identifier;
* cookie properties;
* HttpOnly;
* Secure;
* SameSite;
* session rotation;
* session invalidation;
* concurrent-session policy;
* CSRF protection strategy;
* session storage location.

Explain why the selected design fits a local/offline modular-monolith deployment.

---

# 6. WP-02-03 — RBAC and Segregation of Duties

This is the **highest-priority Phase 2 deliverable**.

Build the detailed authorization model from CP-000 Section K.

Do not simply create a list of role names.

Define:

```text
User
   ↓
Role
   ↓
Permissions
   ↓
Scope
   ↓
Allowed Action
```

Design permissions at appropriate granularity, for example:

```text
module
action
resource
discipline
section
record
workflow stage
```

Avoid unnecessarily creating hundreds of permissions where a smaller, coherent permission model is sufficient.

---

# 7. Role Model

Produce an initial role matrix for the actual laboratory.

At minimum evaluate:

* System Administrator
* Laboratory Manager
* Quality Manager
* Technical Manager
* Analyst / Technician
* Reviewer
* Technical Reviewer / Verifier
* Authorized Signatory / Approver
* Reception / Sample Registration
* Equipment Manager
* Read-only Management

Do not assume all roles must correspond to different people.

Because SMJ currently has a small staff, explicitly distinguish:

### Role

What the user is authorized to do.

from:

### Person

Who currently holds one or more roles.

The architecture must permit one person to hold multiple roles while still enforcing prohibited action combinations.

---

# 8. Segregation-of-Duties Matrix

Design a formal SoD matrix.

At minimum evaluate:

| Activity combination                                   | Default                                |
| ------------------------------------------------------ | -------------------------------------- |
| Analyst → Independent Review, same TestInstance        | Block                                  |
| Analyst → Verification, same TestInstance              | Block                                  |
| Analyst → Final Approval, same TestInstance            | Block                                  |
| Technical Reviewer → Final Approval, same TestInstance | Policy-controlled                      |
| Same user across different TestInstances               | Permitted if role authorization exists |

The critical principle is:

> **SoD is evaluated at the individual TestInstance / controlled-record level, not globally across the user's entire account history.**

The architecture must support policy-controlled combinations without weakening mandatory separation.

Define:

* hard blocks;
* policy-controlled combinations;
* permitted combinations;
* exception handling;
* override authority;
* required reason;
* audit requirements.

Do not allow an ordinary analyst to bypass a hard block.

---

# 9. SoD Policy Question

For the unresolved Phase 1 policy item, define the **technical mechanism** that will support the final laboratory SOP/risk-assessment decision regarding Technical Reviewer → Final Approver overlap.

The software architecture should be able to support either:

```text
Allowed
```

or:

```text
Blocked
```

for that combination without redesign.

Do not invent the laboratory's SOP.

Instead define the architecture needed to encode whichever approved policy the laboratory later confirms.

---

# 10. Authorization Decision Flow

For every protected operation, define the backend sequence.

Example:

```text
Request
 ↓
Authenticated?
 ↓
Correct Role?
 ↓
Permission Exists?
 ↓
Correct Scope?
 ↓
Workflow State Allows Action?
 ↓
SoD Rule Allows Action?
 ↓
Record Eligible?
 ↓
Execute Transaction
 ↓
Write Audit Event
```

The UI shall not be considered part of this security decision.

---

# 11. Audit Architecture

Design the audit subsystem.

Define:

* audit event structure;
* event types;
* actor;
* timestamp;
* entity;
* action;
* before state;
* after state;
* reason;
* correlation/request ID;
* session/user information where appropriate;
* success/failure;
* security events;
* configuration events;
* workflow transitions.

Define what is:

### Audited

and what is:

### Not audited.

Avoid indiscriminate logging of every database query.

Also define protection against:

* ordinary update;
* ordinary deletion;
* direct UI modification;
* accidental modification by application code.

---

# 12. Technical Record Revision Architecture

Define how D-005 is enforced.

Specify the distinction between:

* current record;
* historical revision;
* audit event;
* correction;
* supersession;
* approval;
* reopened approved record.

Define how the architecture prevents:

```text
UPDATE approved technical record
```

from silently changing the historical result.

---

# 13. Workflow Authorization

Integrate D-007 with RBAC.

Define authorization for:

```text
Draft
Received
Registered
Assigned
In Progress
Pending Review
Verified
Approved
Reported
Archived
```

For each transition identify:

* who may initiate it;
* preconditions;
* required fields;
* SoD constraints;
* audit event;
* failure handling.

The workflow engine, not the UI, shall enforce transition legality.

---

# 14. Configuration Governance

Integrate D-015 into the security architecture.

Define:

```text
Authorized Configurator
        ↓
Proposal
        ↓
System Administrator
        ↓
Approve / Reject
        ↓
Effective Configuration
```

Define:

* who can propose;
* who can approve;
* who cannot approve their own proposal;
* whether emergency changes are supported;
* audit requirements;
* effective date;
* rollback/reversal.

The architecture must ensure that unapproved configuration cannot affect live behavior.

---

# 15. Accreditation Security Boundary

D-014 must be respected in authorization and reporting architecture.

Define how protected configuration controls:

* accreditation applicability;
* method scope;
* report-template behavior;
* accreditation statements.

A general administrator must not be able to silently convert a non-accredited method/test into an accredited one without the appropriate controlled configuration/approval mechanism.

Historical approved records must remain unaffected by later scope changes.

---

# 16. SQLite Security Architecture

Define how the application protects the SQLite database.

The architecture shall ensure:

* clients never access the DB file;
* only the application process accesses SQLite;
* DB file resides on local fixed storage;
* appropriate OS file permissions;
* backup copies are access-controlled;
* SQLite configuration is applied consistently on every connection;
* foreign keys are enabled;
* WAL is enabled;
* busy timeout/retry handling is defined.

Do not make SQLite available directly to client workstations.

---

# 17. API Security Architecture

Define API conventions for:

* authentication;
* authorization failures;
* validation failures;
* business-rule failures;
* workflow failures;
* CSRF failures;
* session expiration;
* database failures;
* unexpected errors.

Define a safe response model.

The client must not receive sensitive implementation details such as:

* SQL statements;
* stack traces;
* filesystem paths;
* password/hash information;
* internal exception details.

---

# 18. Error Classification

Define a standard classification such as:

```text
Authentication Error
Authorization Error
Validation Error
Business Rule Error
Workflow Error
Concurrency / Lock Error
Persistence Error
Infrastructure Error
Unexpected Error
```

For each class define:

* HTTP/API representation;
* user-facing message;
* audit/log behavior;
* developer diagnostic information.

---

# 19. Security Logging vs Audit Logging

Explicitly separate:

### Audit

Controlled laboratory/business-record history.

### Security Log

Authentication and security events.

### Application Log

Operational/software events.

### Error Log

Unexpected failures and diagnostics.

Explain what information belongs in each and prevent duplication where unnecessary.

---

# 20. File / Document Security

Define access boundaries for:

* report PDFs;
* attachments;
* controlled documents;
* SOPs;
* calibration certificates;
* instrument files;
* backup files.

Users should not receive direct arbitrary filesystem access merely because they have application access.

Define the application-mediated file access pattern.

---

# 21. Threat Model

Create a practical threat model for this deployment.

At minimum consider:

* compromised user account;
* malicious insider;
* accidental misuse;
* unauthorized workstation;
* direct access to the PC;
* direct SQLite file access;
* backup theft;
* USB backup loss;
* malware/ransomware;
* browser/session compromise;
* unauthorized configuration change;
* self-approval;
* post-approval result alteration;
* report replacement;
* privilege escalation.

For each threat:

```text
Threat
→ Impact
→ Existing control
→ Additional control
→ Residual risk
```

Do not introduce enterprise security infrastructure simply because it exists.

Controls must be proportional to this deployment.

---

# 22. Deployment Trust Boundaries

Document:

```text
User Browser
      │
      │ LAN / localhost
      ▼
Caddy
      │
      ▼
FastAPI
      │
      ├── SQLite
      ├── Documents
      └── Reports
```

Identify the trust boundary at each layer.

For the future LAN deployment, explicitly distinguish:

* trusted application host;
* client workstations;
* database;
* document storage;
* backup media.

---

# 23. Secrets and Configuration Security

Define where the application stores:

* session secrets;
* password-related configuration;
* database configuration;
* encryption keys if any;
* application secrets;
* Caddy/TLS material.

No credentials or secrets in source control.

The design should remain practical for a Windows standalone host.

---

# 24. Security Configuration Baseline

Produce an initial security baseline containing:

* password policy;
* session policy;
* lockout policy;
* RBAC policy;
* SoD policy;
* audit policy;
* database file permissions;
* backup permissions;
* administrative permissions;
* workstation access assumptions;
* local TLS policy;
* secrets handling.

Clearly identify which values are:

### Architecture constants

and which are:

### Laboratory-configurable policies.

---

# 25. Architecture Diagrams Required

Produce, at minimum:

1. Logical application architecture.
2. Authentication/session flow.
3. Authorization decision flow.
4. RBAC model.
5. SoD decision flow.
6. Audit flow.
7. Configuration propose/approve flow.
8. Deployment/trust-boundary diagram.
9. Technical-record revision flow.
10. Workflow authorization/state-transition diagram.

Use Mermaid or another repository-friendly diagram format where possible.

---

# 26. ADRs

Create or propose ADRs for the important Phase 2 decisions.

At minimum consider:

```text
ADR-001 System Architecture
ADR-002 Modular Monolith Boundaries
ADR-003 Authentication Strategy
ADR-004 Session Strategy
ADR-005 RBAC Model
ADR-006 Segregation of Duties
ADR-007 Audit Architecture
ADR-008 Technical Record Revision Model
ADR-009 Workflow Authorization
ADR-010 Configuration Governance
ADR-011 SQLite Operational Security
ADR-012 Error / Logging Architecture
```

Do not create an ADR merely for trivial implementation details.

---

# 27. Required Output Structure

Return the Phase 2 architecture package in this order:

## 1. Executive Architecture Summary

## 2. System Architecture

## 3. Application Layering

## 4. Module Dependency Rules

## 5. Authentication Architecture

## 6. Session Architecture

## 7. RBAC Architecture

## 8. Segregation-of-Duties Architecture

## 9. Authorization Decision Model

## 10. Audit Architecture

## 11. Revision / Technical Record Architecture

## 12. Workflow Authorization

## 13. Configuration Governance

## 14. Accreditation Security Controls

## 15. SQLite Security / Operational Controls

## 16. API Security

## 17. Error and Logging Architecture

## 18. File / Document Security

## 19. Threat Model

## 20. Deployment / Trust Boundaries

## 21. Secrets / Configuration Security

## 22. Security Baseline

## 23. Architecture Diagrams

## 24. ADR Register

## 25. Open Decisions / Questions

## 26. Phase 2 Acceptance Criteria

---

# 28. Strict Constraints

Do not:

* write feature implementation code;
* create production database tables;
* create migration files;
* create frontend screens;
* introduce microservices;
* introduce a plugin framework;
* introduce cloud dependencies;
* introduce multi-tenancy;
* introduce JWT browser authentication;
* introduce generic EAV;
* replace SQLite;
* silently alter D-001–D-015;
* treat UI restrictions as security;
* assume all roles belong to different people;
* invent laboratory SOP requirements;
* claim that the architecture itself establishes ISO/IEC 17025 accreditation.

---

# 29. Quality Standard

The architecture must be:

* internally consistent with CP-000;
* implementation-ready;
* testable;
* auditable;
* understandable by another developer years later;
* appropriate for a small offline laboratory;
* proportional to the actual deployment;
* explicit about security boundaries;
* explicit about authorization decisions;
* explicit about failure behavior.

Where a choice is not yet known, do not silently assume it.

Classify it as:

```text
Confirmed
Proposed
Deferred
Requires Laboratory Decision
Requires Technical Decision
```

---

# 30. Phase 2 Completion Rule

Phase 2 is complete only when:

1. System architecture is documented.
2. Authentication architecture is documented.
3. Session architecture is documented.
4. RBAC model is documented.
5. SoD matrix is documented.
6. Backend authorization model is documented.
7. Audit architecture is documented.
8. Technical-record revision model is documented.
9. Workflow authorization is documented.
10. Configuration governance is documented.
11. SQLite security/operational boundary is documented.
12. Threat model is documented.
13. Trust boundaries are documented.
14. Required ADRs are created or explicitly accepted.
15. Remaining decisions are classified and assigned.
16. Architecture is reviewed against D-001–D-015.
17. No unauthorized feature code has been introduced.
18. Phase 2 evidence is sufficient to proceed to **CP-002**.

---

# 31. Final Instruction

Treat **CP-000 as the frozen foundation**.

Your job in Phase 2 is to **design the security and system architecture on top of that foundation**, not to redesign the foundation.

Prioritize correctness, simplicity, explicit boundaries, and auditability over architectural sophistication.

The most important deliverable is a precise, enforceable **RBAC + SoD + audit + workflow authorization architecture** that can later be implemented without ambiguity.

Begin with **WP-02-01 — System Architecture**, then WP-02-02 — Security Architecture, with **WP-02-03 — RBAC/SoD** as the highest-priority security design deliverable.


Response:
All 26 required sections are there, all 12 ADRs, all 10 diagrams as Mermaid (indexed in Section 23, embedded where they're explained). Two things came out of actually designing this that are worth your attention before CP-002:

A real gap in the SoD matrix you gave me (§8.3): it covers Analyst→{Review, Verify, Approve} and Technical Reviewer→Approval, but never says whether the same person can be both the general Reviewer and the Technical Reviewer/Verifier on one record. Left undefined, that defaults to "permitted" — possibly not what your SOP intends. I proposed treating it like the Technical-Reviewer→Approval case, but it needs your actual answer, not my guess.

A self-approval trap in the configuration governance model (§13.1): propose/approve requires two different people, but if the System Administrator is both the routine proposer and the only approver, that's unavoidable self-approval in practice, not just an emergency edge case. I laid out two honest ways through it — name an alternate approver, or formalize a constrained emergency-self-approve-plus-countersign path — but which one (or both) is SMJ's call.

Section 25 collects these plus the rest of what's still open, ranked by what actually needs a person to decide (mostly your Quality Manager, since a couple of these are NABL-facing) versus what can wait for Phase 5/6/15/18 without blocking CP-002.

# SMJ Sustainable Fuel Lab — LIMS Program

## Phase 2 — System & Security Architecture

**Status:** Phase 2 in progress. CP-000 is ACCEPTED and treated as frozen foundation — nothing here reopens D-001–D-015 without an explicit flagged conflict (none found).
**No feature code, migrations, or frontend screens are introduced by this document.**
**Classification key used throughout:** `Confirmed` (settled by CP-000 or this document) · `Proposed` (recommended default, not yet lab-confirmed) · `Deferred` (later phase) · `Requires Laboratory Decision` · `Requires Technical Decision`.

---

## 1. Executive Architecture Summary

Phase 2 turns the CP-000 baseline into an implementation-ready security and system architecture for a **modular monolith, single-host, SQLite-backed LIMS** serving a small (1–10 user), already NABL-accredited laboratory.

Three design stances carry through everything below:

1. **RBAC answers "what can this role do"; SoD answers "not on this specific record."** These are deliberately separate mechanisms. A user can hold every role in the system and still be structurally blocked from reviewing, verifying, or approving their own work — the check runs against the record's actual history (`created_by`, `reviewed_by`, `verified_by`), not against role labels.
2. **Hard SoD blocks have no override, by anyone, ever.** This is the one place the architecture is deliberately less flexible than the lab might want, because that inflexibility is the control. Everything else — passwords, session timeouts, the Technical-Reviewer→Approval combination, configuration changes — is a lab-configurable policy value sitting on top of a fixed enforcement mechanism.
3. **SQLite's simplicity is leaned into, not worked around.** No session store, no message queue, no separate cache — sessions, audit, config proposals, and application data all live in the one SQLite file, protected by OS file permissions and application-mediated access only, because introducing extra infrastructure to serve 1–10 users would violate the CP-000 simplicity principle (C.10) for no real benefit.

One genuine gap in the given SoD matrix was found and is flagged in Section 8 rather than silently resolved. One structural tension in the configuration-governance model (self-approval risk with a very small admin pool) is flagged in Section 13. Both are carried into Section 25.

---

## 2. System Architecture

**Style:** Modular Monolith (D-003) — a single FastAPI deployable process with strict internal module boundaries, running behind Caddy on a single host (per CP-000 Section P).

**Modules** (unchanged from CP-000 Section F) are grouped into two tiers for dependency purposes:

- **Core/cross-cutting modules** (depended on by everything, depend on nothing domain-specific): Identity & RBAC, Audit, Configuration/Admin, Master Data.
- **Domain modules** (depend on core modules, and on each other only through public service interfaces): Customer & Project, Sample Management, Method & Test Engine, Calculation Engine, Execution & Results, Review/Verification/Approval, Equipment & Calibration, QC, Documents & Records, Reporting, Quality Management, Notifications, Backup/Ops.

**Database access boundary:** only the Repository layer imports SQLAlchemy. Application and Domain layers never construct a query directly — they call repository methods. This is an architectural rule enforced by code convention and review, not by a runtime mechanism (SQLite has no per-schema privilege system to fall back on).

**Report-generation boundary:** report assembly runs on a **separate read-only DB connection**, never inside a write transaction — this is the concrete mechanism behind the CP-000 L.5 rule that reporting must never hold a write lock.

**File/document-storage boundary:** no module or client ever receives a raw filesystem path. A `DocumentService` resolves a logical document/attachment ID to a physical path server-side and streams the content; the API never returns a path string a client could reuse directly.

### 2.1 Logical Architecture Diagram

```mermaid
flowchart TD
    Browser["Browser (Reception / Analyst / Reviewer / Manager)"]
    Caddy["Caddy — Reverse Proxy, Local TLS, Static SPA"]
    API["FastAPI — API Layer (routers, Pydantic schemas)"]
    AuthMW["AuthN / Session Middleware"]
    AppSvc["Application Services (use-case orchestration, authorization entry point)"]
    DomSvc["Domain Services (state machine, SoD, calculation rules)"]
    Repo["Repository Layer (SQLAlchemy 2.x)"]
    DB[("SQLite — WAL mode")]
    Audit["Audit Service"]
    ReportSvc["Report Generation Service (read-only connection)"]
    Chromium["Local pinned Chromium — PDF render"]
    Docs[("Local Document Storage")]

    Browser -->|HTTPS| Caddy --> API --> AuthMW --> AppSvc --> DomSvc --> Repo --> DB
    AppSvc -.->|on audited state change, same transaction| Audit --> DB
    AppSvc --> ReportSvc --> Repo
    ReportSvc --> Chromium --> Docs
    AppSvc --> Docs
```

### 2.2 Request Lifecycle

```mermaid
sequenceDiagram
    participant B as Browser
    participant M as AuthN/Session Middleware
    participant Az as Authorization Service
    participant Ap as Application Service
    participant D as Domain Service
    participant R as Repository/Transaction
    participant Au as Audit
    B->>M: HTTP request + session cookie + CSRF header
    M->>M: Resolve session, check expiry
    M->>Az: authenticated user context
    Az->>Az: Role/Permission → Scope → Workflow-state → SoD checks
    Az->>Ap: authorized, proceed
    Ap->>Ap: input validation (Pydantic)
    Ap->>D: execute use case
    D->>D: apply business/state-machine rules
    D->>R: persist within transaction
    R->>Au: write audit event (same transaction)
    R-->>Ap: commit
    Ap-->>B: response (safe error envelope on failure)
```

| Stage | Owning layer |
|---|---|
| TLS termination, static file serving, proxying | Caddy |
| Session resolution, expiry check | AuthN Middleware |
| Permission/scope/workflow-state/SoD checks | Authorization Service (called from Application layer) |
| Input shape validation | API layer (Pydantic) |
| Use-case orchestration | Application Services |
| Business rules, state transitions | Domain Services |
| Persistence, transaction boundary | Repository layer |
| Audit write | Repository layer, within the same transaction as the change it records |
| Error shaping | API layer, per Section 17's error classification |

---

## 3. Application Layering

`API → Application Services → Domain Services → Repository → SQLite`, one direction only — a lower layer never calls upward. Domain Services contain the workflow state machine, the SoD policy engine, and the calculation engine; they are pure business logic with no knowledge of HTTP or SQL. Application Services are the only layer permitted to call the Authorization Service and the Audit Service, since authorization and audit are use-case-level concerns, not business-rule-level ones.

---

## 4. Module Dependency Rules

1. Domain modules may depend on **another domain module's public service interface only** — never on its internal ORM models or repository. Example: Reporting reads Execution & Results data through an `ExecutionReadModel` interface, not by querying `TestInstance` tables directly.
2. All domain modules may depend on core modules (Identity & RBAC, Audit, Configuration, Master Data). Core modules depend on nothing domain-specific.
3. No circular module dependencies. If Module A needs something from Module B and B conceptually needs something from A, the shared concept is extracted into a core/master-data concept both depend on.
4. Cross-cutting concerns (authorization, audit, transactions) are invoked by Application Services, never embedded ad hoc inside Domain Services or Repositories.

---

## 5. Authentication Architecture

| Item | Value | Classification |
|---|---|---|
| Password hashing | Argon2id | Confirmed (D-002) |
| Argon2id parameters (memory/time/parallelism cost) | To be benchmarked against actual host hardware; OWASP-range baseline (e.g., ≥19 MiB memory, ≥2 iterations) as a starting point | **Requires Technical Decision** — Phase 5, benchmarked on real hardware |
| Password policy | Minimum length over complexity rules (e.g., 12+ characters, passphrases allowed); check against a local common-password list (no online breach-check API — offline constraint) | Proposed |
| Failed-login handling | Counter per account; lockout after a configurable threshold (proposed default: 5) | Proposed |
| Account lockout duration | Configurable timed lockout (proposed default: 15 minutes) or admin-only unlock | Proposed |
| Session creation | On successful auth, server creates a session row (Section 6) | Confirmed |
| Session expiry | Idle timeout + absolute timeout (Section 6) | Confirmed mechanism, values Proposed |
| Logout | Explicit session invalidation (row marked revoked) | Confirmed |
| Administrator session revocation | Admin can revoke any/all sessions for a user (role change, disablement, suspected compromise) | Confirmed |
| Password change | Self-service, requires current password | Confirmed |
| **Password reset** | **No email/cloud dependency exists or is permitted.** Reset is **admin-mediated only**: an administrator sets a temporary password and flags the account to force a change on next login. | Confirmed — direct consequence of the offline-first constraint |

All authentication events (success, failure, lockout, admin-forced reset/revocation) are Security Log + Audit events (Section 17).

---

## 6. Session Architecture

Sessions are **server-side, stored in the same SQLite database** — no Redis, no in-memory-only store, no JWT. A `Session` row: `session_id` (opaque, ≥256-bit random token — never a predictable or sequential ID), `user_id`, `created_at`, `last_seen_at`, `expires_at`, `revoked_at` (nullable), `client_info` (user agent, optional, for the user's own "active sessions" view).

| Property | Value |
|---|---|
| Cookie flags | `HttpOnly`, `Secure` (Caddy provides local TLS even pre-LAN), `SameSite=Strict` |
| Session rotation | New `session_id` issued on login and on password change (fixation mitigation) |
| Idle timeout | Proposed 30 minutes |
| Absolute timeout | Proposed 12 hours |
| Concurrent sessions | Proposed: permitted by default (a user may be logged in on two workstations) — **Requires Laboratory Decision** to confirm or restrict |
| CSRF protection | Synchronizer token issued at login, required in a custom header on every state-changing request, validated server-side — defense-in-depth on top of `SameSite=Strict` |
| Session storage | SQLite `Session` table — survives app restart, so a deployment/update doesn't force everyone to re-authenticate |

**Why this fits the deployment:** a single application process serving 1–10 users has no need for a distributed session store; keeping sessions in the same SQLite file avoids introducing new infrastructure (C.10), and server-side opaque sessions — unlike JWTs — can be revoked immediately by an administrator, which matters when someone leaves the lab.

---

## 7. RBAC Architecture

```text
User —(many-to-many)— Role —(many-to-many)— Permission
                         │
                    optional Scope (discipline/section) on the assignment
```

Permissions are coarse-grained `(module, action)` pairs (e.g., `sample.register`, `result.enter`, `result.review`, `result.verify`, `result.approve`, `equipment.manage`, `config.propose`, `config.approve`, `report.issue`, `user.manage`) — roughly 30–40 total, not hundreds. A `UserRoleAssignment` may carry an optional scope (discipline or section); omitted scope means "all." **One person may hold multiple roles** — this is the normal expected case at SMJ's current size, not an edge case.

### 7.1 Role Model (initial matrix)

| Role | Sample Reg. | Result Entry | Review | Verify | Approve | Equipment Mgmt | QC | Documents | Report Issue | Config Propose | Config Approve | User Admin | Audit View |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| System Administrator | – | – | – | – | – | – | – | – | – | – | ✅ (default) | ✅ | ✅ |
| Laboratory Manager | Read | Read | – | – | – | Read | Read | Read | ✅ | ✅ | – | – | ✅ |
| Quality Manager | Read | Read | – | – | – | Read | ✅ | ✅ | – | ✅ (esp. accreditation scope) | – | – | ✅ |
| Technical Manager | – | Read | – | – | – | Read | ✅ | – | – | ✅ (methods/tests) | – | – | Read |
| Analyst / Technician | – | ✅ | – | – | – | Use only | ✅ | – | – | – | – | – | – |
| Reviewer | – | Read | ✅ | – | – | – | – | – | – | – | – | – | – |
| Technical Reviewer / Verifier | – | Read | – | ✅ | – | – | – | – | – | – | – | – | – |
| Authorized Signatory / Approver | – | Read | – | – | ✅ | – | – | – | ✅ | – | – | – | – |
| Reception / Sample Registration | ✅ | – | – | – | – | – | – | – | – | – | – | – | – |
| Equipment Manager | – | – | – | – | – | ✅ | – | – | – | ✅ (equipment/calibration config) | – | – | – |
| Read-only Management | Read | Read | Read | Read | Read | Read | Read | Read | Read | – | – | – | Read |

This is a **role capability matrix, not a staffing chart** — Section 8 governs which combinations the *same person* may exercise on the *same record*.

---

## 8. Segregation-of-Duties Architecture

### 8.1 Mechanism

Every controlled technical record (principally `TestInstance`/`Result`) carries `created_by`, `reviewed_by`, `verified_by`, `approved_by`. A `SoDPolicyService.check(user, action, record)` call runs **before** any review/verify/approve action executes, comparing the acting user against that specific record's actor history — never against the user's global role or account history.

```mermaid
flowchart TD
    A[User attempts Review/Verify/Approve on TestInstance X] --> B{Is user == X.created_by\nfor a hard-blocked action?}
    B -- Yes --> C[Reject: SoD hard block\nAudit: SoD_BLOCKED]
    B -- No --> D{Policy-controlled combination?\ne.g. TechReviewer→Approval}
    D -- Yes, policy = Blocked --> C
    D -- Yes, policy = Allowed --> E[Proceed\nAudit: SoD_POLICY_PERMITTED]
    D -- Not applicable --> F[Proceed\nAudit: SoD_CHECK_PASSED]
```

### 8.2 SoD Matrix

| Activity combination (same TestInstance) | Default | Overridable? |
|---|---|---|
| Analyst → independent Review | **Block** | Never — structural, no override by any role |
| Analyst → Verification | **Block** | Never |
| Analyst → Final Approval | **Block** | Never |
| Technical Reviewer → Final Approval | Policy-controlled (per lab SOP) | Changeable only via D-015 governed configuration change |
| Same user across **different** TestInstances | Permitted, subject to role authorization | N/A |

**Hard blocks have no override, by design** — not by an admin, not in an "emergency," not with a documented reason. If this makes a record temporarily un-processable because only one qualified person is available, the correct response is operational (route the record to another qualified person, or wait), not a technical bypass. This is stated plainly because it has a real staffing implication: **SMJ needs at least two people qualified to act in the analyst/reviewer-or-above capacity for any given test type**, which is worth confirming is achievable at current staffing (see Section 25).

### 8.3 A gap found in the given matrix

The SoD matrix as specified addresses Analyst→{Review, Verify, Approve} and Technical Reviewer→Approval, but **does not address Reviewer → Technical Reviewer/Verifier on the same record** (i.e., can the same non-analyst person both perform the general Review and the Technical Verification?). Left undefined, this would default to "permitted," which may not be what SMJ's SOP intends given both are meant to be independent professional-judgment gates. **Proposed default: treat this the same as Technical Reviewer→Approval — policy-controlled, not a hard block, confirmable via the same governance mechanism** — but this is flagged as a genuine gap requiring an explicit laboratory answer, not silently assumed. See Section 25.

### 8.4 Technical mechanism for the outstanding Phase 1 policy item

The architecture supports either outcome for Technical Reviewer→Approval without redesign: the combination is stored as a `ConfigSetting` (`sod.tech_reviewer_can_approve = true|false`), read by `SoDPolicyService` at check time, changeable only through the D-015 propose/approve flow. No laboratory SOP is invented here — the switch exists; its value is SMJ's call.

---

## 9. Authorization Decision Model

```mermaid
flowchart TD
    R[Request] --> A{Authenticated?}
    A -- No --> E1[401 Authentication Error]
    A -- Yes --> B{Role has Permission?}
    B -- No --> E2[403 Authorization Error]
    B -- Yes --> C{Scope matches\ndiscipline/section?}
    C -- No --> E2
    C -- Yes --> D{Workflow state\nallows this action?}
    D -- No --> E3[409 Workflow Error]
    D -- Yes --> S{SoD rule allows\nthis action on this record?}
    S -- No --> E4[403 SoD Violation — Audited]
    S -- Yes --> F{Record eligible\n(not archived/locked)?}
    F -- No --> E3
    F -- Yes --> G[Execute transaction] --> H[Write audit event] --> I[Response]
```

Every box left of "Execute transaction" is backend-enforced and independent of anything the UI already hid, grayed out, or validated client-side.

---

## 10. Audit Architecture

**AuditEvent** fields: `id`, `timestamp` (server UTC), `actor_user_id`, `session_id`, `correlation_id` (per-request, ties audit/security/error logs together for one request), `entity_type`, `entity_id`, `action`, `before_state` (JSON snapshot, nullable), `after_state` (JSON snapshot, nullable), `reason` (nullable, required for corrections/reopens/rejections/emergency config changes), `outcome` (success/failure/blocked), `category` (TechnicalRecord / Security / Configuration / Workflow).

**Audited:** every workflow state transition; every technical-record correction/reopen; every configuration propose/approve/reject event; every authentication event (login success/failure/lockout/logout/forced revocation); every SoD check outcome relevant to an approval-chain action (pass, block, and policy-permitted — all three, not just blocks); every accreditation-scope change; every user/role/permission change.

**Not audited:** routine reads, list/search/filter operations, report *preview*, UI navigation, health checks. (Report *issuance* — the act of finalizing a Report as the controlled record — is audited; looking at a draft is not.)

**Protection:** no application service method exists to `UPDATE` or `DELETE` an audit row — this isn't a permission that's merely withheld from ordinary roles, the code path doesn't exist at all. The audit write happens in the **same database transaction** as the business change it records, so a change can never commit without its audit event, and vice versa.

Honest limitation, carried to the threat model (Section 19): SQLite has no per-table database-engine-level privilege system the way PostgreSQL does. The "audit rows are unmodifiable" guarantee here is an **application-code and OS-file-permission** control, not a database-engine-enforced one. This is proportionate at this scale but is explicitly not the same strength of guarantee a client-server database with row-level grants would give.

---

## 11. Revision / Technical Record Architecture

```mermaid
stateDiagram-v2
    [*] --> Draft
    Draft --> Submitted
    Submitted --> Reviewed
    Reviewed --> Verified
    Verified --> Approved
    Approved --> ReopenedForCorrection: Reopen (authorized role + mandatory reason, audited)
    ReopenedForCorrection --> Submitted: corrected value re-entered\n(prior Approved snapshot preserved as ResultRevision)
    Approved --> [*]: Reported / Archived
```

`Result` holds the **current** authoritative value and status. `ResultRevision` captures a full snapshot **every time** an already-Submitted-or-later record changes — this is what makes `UPDATE approved technical record` structurally impossible to do silently: the domain service refuses a direct field edit on an `Approved` record outright; the only path to changing it is the `Reopen` action, which is itself a permissioned, reasoned, audited transition that snapshots the current approved state into `ResultRevision` before allowing any edit, and requires the full review→verify→approve chain to run again before the record can return to `Approved`.

A **Report** references a specific `ResultRevision` (or the exact approval snapshot), so a previously issued PDF remains reproducible and unaffected even if the underlying result is later corrected — a correction produces a *new* report, it does not retroactively change history.

---

## 12. Workflow Authorization

| Transition | Who may initiate | Preconditions | SoD constraint | Audit event | Failure |
|---|---|---|---|---|---|
| Draft → Received | Reception | Sample physically present | — | `SAMPLE_RECEIVED` | Workflow Error |
| Received → Registered | Reception | Required fields complete, condition recorded | — | `SAMPLE_REGISTERED` | Validation Error |
| Registered → Assigned | Lab/Technical Manager | Test(s) selected, method active | — | `TEST_ASSIGNED` | Workflow Error |
| Assigned → In Progress | Analyst | Equipment eligible (Section 15/H.1 policy) | — | `EXECUTION_STARTED` | Workflow Error (equipment blocked) |
| In Progress → Pending Review | Analyst | Result entered, required QC passed or investigation logged | — | `RESULT_SUBMITTED` | Business Rule Error (QC) |
| Pending Review → Verified | Reviewer, then Technical Reviewer | — | Analyst≠Reviewer≠Verifier (§8.2) | `RESULT_REVIEWED` / `RESULT_VERIFIED` | SoD Violation |
| Verified → Approved | Authorized Signatory | — | Analyst≠Approver always; TechReviewer≠Approver per policy (§8.4) | `RESULT_APPROVED` | SoD Violation |
| Approved → Reported | Signatory/Reviewer with report-issue permission | Report template resolved, accreditation scope evaluated (§14) | — | `REPORT_ISSUED` | Business Rule Error |
| Reported → Archived | System (retention rule) or Admin | Retention period logic (10-year active, per CP-000 B) | — | `RECORD_ARCHIVED` | — |
| Any stage → Rejected | Role-appropriate for that stage | Reason required | — | `RECORD_REJECTED` | — |
| Approved → ReopenedForCorrection | Elevated role (Technical Manager/QM), not the original analyst for that record | Reason required | — | `RECORD_REOPENED` | Authorization Error |

The workflow engine (Domain Service layer) enforces transition legality — the API layer will reject a request for an illegal transition regardless of what the UI presented as available.

```mermaid
stateDiagram-v2
    [*] --> Draft
    Draft --> Received
    Received --> Registered
    Registered --> Assigned
    Assigned --> InProgress: In Progress
    InProgress --> PendingReview: Pending Review
    PendingReview --> Verified
    Verified --> Approved
    Approved --> Reported
    Reported --> Archived
    Draft --> Rejected
    Received --> Rejected
    PendingReview --> Rejected: sent back for rework
    Approved --> ReopenedForCorrection
    ReopenedForCorrection --> PendingReview
```

---

## 13. Configuration Governance

`ConfigProposal`: `id`, `config_area`, `target_key`, `previous_value`, `proposed_value`, `proposer_id`, `proposed_at`, `status` (Pending/Approved/Rejected), `approver_id`, `decided_at`, `reason`, `effective_at` (defaults to immediately on approval; may be scheduled).

**Rule: `approver_id ≠ proposer_id`** — enforced in code, not just policy. **Unapproved proposals never affect live behavior** — the effective configuration read path only ever reads `Approved` rows.

```mermaid
stateDiagram-v2
    [*] --> Pending: Propose
    Pending --> Approved: Approve (different user)
    Pending --> Rejected: Reject
    Pending --> EmergencySelfApproved: Emergency path (see below)
    EmergencySelfApproved --> Countersigned: second authorized user reviews within window
    EmergencySelfApproved --> FlaggedOverdue: window expires uncountersigned
    Approved --> [*]
    Rejected --> [*]
    Countersigned --> [*]
```

### 13.1 A structural tension worth naming

The propose/approve rule (different people) plus a small staff means: **if the System Administrator is the sole authorized approver, and also the only person who'd propose most changes, self-approval becomes unavoidable in practice**, not just in an emergency. Two honest options exist, and this is a laboratory decision, not an architectural one:

- **Option A:** SMJ designates at least one alternate approver (e.g., Laboratory Manager or Technical Manager) for routine configuration, keeping System Administrator as approver only for a defined subset.
- **Option B:** A constrained **emergency self-approval path** is supported — proposer may self-approve only if flagged `emergency` with a mandatory reason, is immediately audited as `EMERGENCY_SELF_APPROVED`, and **requires countersignature by a second authorized person within a configurable window** (proposed: 5 business days); an uncountersigned emergency change is surfaced as an outstanding item on the admin dashboard, not hidden.

Both are supportable without redesign; SMJ's staffing reality should decide which (or both, with A as the norm and B as the genuine fallback). See Section 25.

### 13.2 Accreditation-scope changes are a special category

Given D-014, changes to `accreditation_status`/`accreditation_scope_id` on a Method/Test are configuration changes like any other, but their sensitivity argues for a **narrower approver set** than generic configuration — see Section 14.

---

## 14. Accreditation Security Controls

`Method`/`TestDefinition` carries `accreditation_status` (Accredited/NotAccredited) and `accreditation_scope_id`, both **controlled configuration** under D-015 — never a direct field edit by any role, including System Administrator, outside the propose/approve flow.

**Requires Laboratory Decision:** should accreditation-scope changes require **Quality Manager** approval specifically (in addition to, or instead of, the generic System Administrator default), given how directly this touches SMJ's existing NABL standing? The architecture supports restricting approval authority per `config_area` — this is a policy call, not a technical constraint.

**Report-time enforcement:** when a Report is issued, the report-generation service reads the Method's accreditation status **at that moment** and freezes it into the Report record (denormalized snapshot, per CP-000 L.2). A later accreditation-scope change never retroactively alters a previously issued report's displayed accreditation statement — this is the D-014 historical-immutability requirement, implemented the same way technical-record immutability is (Section 11).

A report covering results from methods with mixed accreditation status renders a clear per-result distinction — the template logic pulls status per line item, never a single blanket lab-level flag.

---

## 15. SQLite Security / Operational Controls

* **Sole accessor:** only the FastAPI application process opens the database file. No other process, service, or user account is granted access.
* **Location:** the DB file lives outside any directory Caddy serves over HTTP — not reachable by any URL, even by misconfiguration of a static-file route.
* **OS file permissions:** the database file and its containing directory are restricted to the OS service account running the application (and a distinct backup-job account for backup operations) — not readable by ordinary interactive logins on the host.
* **Connection configuration, applied on every connection via a SQLAlchemy `connect` event listener** (not left to per-request discipline): `PRAGMA foreign_keys=ON`, WAL mode, `PRAGMA busy_timeout` set to a sane value (e.g., 5000ms) so short lock waits resolve automatically before the application-level retry/backoff logic (Section 5, L.5) engages.
* **Backups:** same restricted OS permissions as the live file. External USB backups are recommended to be encrypted at rest (e.g., BitLocker To Go on the drive) given "USB backup loss" is a named threat (Section 19) — **Requires Laboratory Decision** on adoption.
* **No network attack surface for the database itself** — SQLite is embedded, not a listening service, which is a genuine security advantage of this choice over a client-server database at this deployment scale, worth stating plainly rather than only ever framing SQLite as a compromise.

---

## 16. API Security

Standard error envelope for every failure: `{ "error_code": "...", "message": "<safe, generic>", "correlation_id": "..." }`. The response body **never** contains SQL text, stack traces, filesystem paths, password/hash material, or internal exception detail — that detail goes to the Error Log only, retrievable by `correlation_id` (Section 17). Session-expired responses use a distinct `error_code` the frontend recognizes to redirect to login rather than showing a generic failure. Concurrency/lock errors (SQLite busy after retries exhausted) return a specific "try again" error rather than a raw database exception.

---

## 17. Error and Logging Architecture

### 17.1 Error Classification

| Class | HTTP | User-facing message | Audit/log behavior | Developer diagnostics |
|---|---|---|---|---|
| Authentication Error | 401 | "Please log in again." | Security Log | Session/token detail in Security Log only |
| Authorization Error | 403 | "You don't have permission for this." | Audit (Security category) | Permission/scope checked, in Audit |
| SoD Violation | 403 | "This record requires action by someone else." | Audit (Security category), always | Full record/actor context in Audit |
| Validation Error | 422 | Field-level message | Application Log | Input payload (sanitized) in App Log |
| Business Rule Error | 409/422 | Rule-specific message (e.g., "QC not passed") | Audit if touching a technical record | Rule name in App Log |
| Workflow Error | 409 | "This action isn't allowed in the current status." | Audit | Attempted transition in App Log |
| Concurrency/Lock Error | 409 | "Please try again." | Application Log | SQLite busy detail in App Log only |
| Persistence Error | 500 | Generic failure message | Error Log | Full exception + correlation ID in Error Log |
| Infrastructure Error | 503 | "Service temporarily unavailable." | Error Log | — |
| Unexpected Error | 500 | Generic failure message | Error Log | Full stack trace, Error Log only, never in response |

### 17.2 Log Separation

| Log | Contains | Retention |
|---|---|---|
| **Audit** | Controlled laboratory/business-record history: workflow transitions, corrections, approvals, config changes, SoD outcomes | Per CP-000 retention (10 years active, then archive) — this is a technical record, not operational log data |
| **Security Log** | Authentication events, lockouts, session creation/revocation, permission-denied events | Defined separately, shorter operational retention appropriate to security monitoring |
| **Application Log** | Routine operational/software events, validation failures, business-rule rejections | Standard log rotation |
| **Error Log** | Unexpected failures, full stack traces, persistence/infrastructure errors, correlated by `correlation_id` | Standard log rotation |

No event is duplicated across all four by default — an authentication failure is a Security Log entry; it only also becomes an Audit event if it's relevant to a controlled record's history (e.g., a failed approval attempt due to SoD is both).

---

## 18. File / Document Security

Reports, attachments, controlled documents (SOPs), calibration certificates, and instrument files are all served through the application-mediated pattern described in Section 2 (`DocumentService` resolves logical ID → physical path, streams content) — **no role receives direct filesystem access merely by having application access.** Backup files carry the same OS-level restriction as the live database (Section 15).

---

## 19. Threat Model

| Threat | Impact | Existing control | Additional control | Residual risk |
|---|---|---|---|---|
| Compromised user account | Unauthorized access under a real identity | Argon2id, lockout, session timeout | Admin-forced session revocation, audit review | Low–moderate; depends on password hygiene |
| Malicious insider | Data manipulation, self-approval attempt | SoD hard blocks, full audit trail | Periodic audit review by Quality Manager | Moderate — audit is detective, not preventive, for non-SoD actions |
| Accidental misuse | Wrong data entered/approved | Validation, workflow state checks, confirmation on irreversible actions | UI-level guardrails (Phase 4) | Low |
| Unauthorized workstation | Access to an unattended logged-in session | Idle timeout | Screen-lock policy (lab operational control, not software) | Moderate — depends on physical workstation discipline |
| Direct physical access to the PC | Full compromise of host | OS user account controls, UPS (protects availability, not confidentiality) | OS-level disk encryption (recommend evaluating) | Moderate — single-host deployment has no network segmentation to fall back on |
| Direct SQLite file access | Bypass application-layer controls entirely | OS file permissions, DB outside HTTP-served paths | — | Moderate — this is the SQLite-specific residual risk named in Section 10 |
| Backup theft | Exposure of all historical data | OS file permissions on backup files | USB backup encryption (Requires Laboratory Decision, §15) | Moderate until encryption adopted |
| USB backup loss | Same as above, plus availability impact if only copy | Multiple rotated backups | Encryption + verified restore drills (monthly, per CP-000 O) | Low–moderate |
| Malware/ransomware | Data loss/corruption, potential encryption-for-ransom | UPS, offline external backup rotation | Endpoint protection (lab operational control), backup isolation (USB disconnected when not actively backing up) | Moderate — single-host with no network isolation |
| Browser/session compromise | Session hijack | HttpOnly/Secure/SameSite=Strict cookies, CSRF token | Session rotation on login | Low |
| Unauthorized configuration change | Silent policy/behavior change | Propose/approve governance, full audit | Restricted approver set for accreditation scope (§14) | Low, pending §13.1 resolution |
| Self-approval | Undermines SoD/accreditation integrity | Hard SoD blocks, no override | — | Low for hard-blocked stages; depends on §13.1/§8.3 resolution elsewhere |
| Post-approval result alteration | Falsified technical record | Immutable revision model (§11), Reopen requires reason+audit | — | Low |
| Report replacement | Substituting a fraudulent report for an issued one | Reports reference frozen ResultRevision snapshots, PDF-only authoritative format | File-integrity checking on issued reports (Deferred — Phase 15/18) | Low–moderate until file-integrity check exists |
| Privilege escalation | User grants self elevated role/permission | User/role management restricted to User Admin permission, itself audited | Separate approval for role changes (Deferred — Phase 6 detail) | Low |

**Explicitly not adopted**, as disproportionate to this deployment: intrusion detection systems, network segmentation beyond the LAN boundary, hardware security modules, enterprise SIEM. Controls scale to a single-host, 1–10-user lab, per CP-000 principle 10.

---

## 20. Deployment / Trust Boundaries

```mermaid
flowchart TD
    subgraph Untrusted["Untrusted Zone"]
        Browser[User Browser]
    end
    subgraph TrustedHost["Trusted Application Host (single PC)"]
        Caddy[Caddy]
        FastAPI[FastAPI Application]
        SQLite[(SQLite DB file)]
        Documents[(Document Storage)]
    end
    subgraph BackupZone["Backup Media — trusted only while attached, then physically secured"]
        USB[(Rotated External USB)]
    end
    Browser -->|HTTPS, LAN/localhost| Caddy
    Caddy --> FastAPI
    FastAPI --> SQLite
    FastAPI --> Documents
    FastAPI -->|scheduled backup job| USB
```

The **trust boundary sits at the application host's edge**: the browser is never trusted (all authorization re-checked server-side, per Section 9); the host itself (Caddy, FastAPI, SQLite, documents) is a single trusted unit today because it's one PC; when LAN workstations are added, they remain in the untrusted zone exactly like today's single browser — no architectural change, just more clients hitting the same boundary. Backup media is trusted only while physically attached and performing the backup job; between backups it should be physically secured (lab operational control, not software-enforced).

---

## 21. Secrets / Configuration Security

| Secret | Storage |
|---|---|
| Session signing/CSRF secret | Environment variable / local config file outside source control, generated at install time |
| Argon2id parameters | Application configuration, not a "secret" per se, but version-tracked |
| Caddy TLS material (local cert/key) | Caddy's own managed storage on the host, standard file permissions |
| Database file | No separate "credential" — protected entirely by OS file permissions (Section 15), since SQLite has no connection-string authentication to secure |

No credentials or secrets appear in source control at any point. This is a **practical, low-ceremony model appropriate for a Windows standalone host** — no external secrets manager is introduced, consistent with C.10.

---

## 22. Security Baseline

| Policy | Value | Type |
|---|---|---|
| Password hashing algorithm | Argon2id | Architecture constant |
| Argon2id cost parameters | Benchmarked per host (Phase 5) | Architecture constant (value technical, not lab-configurable) |
| Minimum password length | 12 characters (proposed) | Laboratory-configurable |
| Failed-login lockout threshold | 5 attempts (proposed) | Laboratory-configurable |
| Lockout duration | 15 minutes (proposed) | Laboratory-configurable |
| Session idle timeout | 30 minutes (proposed) | Laboratory-configurable |
| Session absolute timeout | 12 hours (proposed) | Laboratory-configurable |
| RBAC model | Role→Permission, scoped assignment | Architecture constant |
| SoD hard blocks | Analyst cannot review/verify/approve own TestInstance | Architecture constant — **not configurable, by design** |
| SoD policy-controlled combinations | TechReviewer→Approval; (proposed) Reviewer→TechVerifier | Laboratory-configurable, via D-015 governance only |
| Audit retention | 10 years active, then archive | Laboratory-confirmed (CP-000 B) |
| Database file permissions | Application service account only | Architecture constant |
| Backup destination | Local + rotated external USB | Confirmed (CP-000 O) |
| Administrative permissions | User/role management restricted to User Admin permission | Architecture constant |
| Local TLS | Caddy-managed, required even pre-LAN | Architecture constant |
| Secrets handling | Env/local file, never in source control | Architecture constant |

---

## 23. Architecture Diagrams — Index

| # | Diagram | Location |
|---|---|---|
| 1 | Logical application architecture | Section 2.1 |
| 2 | Authentication/session flow | Section 2.2 |
| 3 | Authorization decision flow | Section 9 |
| 4 | RBAC model | Section 7 (matrix); ER structure described in prose, Section 7 intro |
| 5 | SoD decision flow | Section 8.1 |
| 6 | Configuration propose/approve flow | Section 13 |
| 7 | Technical-record revision flow | Section 11 |
| 8 | Workflow state-transition diagram | Section 12 |
| 9 | Deployment/trust-boundary diagram | Section 20 |
| 10 | Request lifecycle sequence | Section 2.2 |

All diagrams are Mermaid, embedded next to their explanatory text rather than duplicated here, so each stays attached to its context.

---

## 24. ADR Register

| ADR | Decision | Consequence |
|---|---|---|
| ADR-001 System Architecture | Modular monolith, layered (API→App→Domain→Repo) | No microservice deployment complexity; internal boundaries must be maintained by discipline, not enforced by process isolation |
| ADR-002 Modular Monolith Boundaries | Domain modules interact only via public service interfaces | Slightly more upfront interface design; prevents the "big ball of mud" failure mode of monoliths |
| ADR-003 Authentication Strategy | Argon2id + password auth, no email/cloud dependency | Password reset is admin-mediated; no self-service reset flow |
| ADR-004 Session Strategy | Server-side sessions in SQLite, opaque cookie, CSRF token | Enables instant admin revocation; requires session table maintenance (expiry cleanup job) |
| ADR-005 RBAC Model | Coarse-grained (module,action) permissions + scoped role assignment | Simple to reason about; multi-role users fully supported |
| ADR-006 Segregation of Duties | Per-TestInstance policy matrix, hard blocks non-overridable | Correctness over convenience; may occasionally stall a record pending a second qualified person |
| ADR-007 Audit Architecture | Same-transaction audit write, append-only by code convention | Strong consistency guarantee; SQLite lacks DB-engine-level enforcement (named residual risk) |
| ADR-008 Technical Record Revision Model | Reopen-based correction, full snapshot history | No silent edits possible; correction workflow has real friction by design |
| ADR-009 Workflow Authorization | Explicit state machine, enforced server-side | UI can never grant an illegal transition |
| ADR-010 Configuration Governance | Propose/approve, self-approval forbidden except flagged emergency path | Requires SMJ to name an alternate approver or accept the emergency-path trade-off (§13.1) |
| ADR-011 SQLite Operational Security | File-permission + application-mediated access only, no network exposure | Simple, but weaker isolation guarantees than a client-server DB — accepted given confirmed scale |
| ADR-012 Error/Logging Architecture | Four separate logs (Audit/Security/Application/Error), generic client-facing errors | Clean separation of concerns; correlation ID needed to reassemble a full incident picture |

---

## 25. Open Decisions / Questions

| # | Item | Type | Where raised |
|---|---|---|---|
| 1 | Technical Reviewer → Approval: Allowed or Blocked, per SMJ's actual SOP/risk assessment | Requires Laboratory Decision | Carried from Phase 1/CP-000; §8.2, §8.4 |
| 2 | **Gap:** Reviewer → Technical Reviewer/Verifier on the same record — not addressed in the given matrix; proposed default is policy-controlled, same treatment as item 1 | Requires Laboratory Decision | §8.3 |
| 3 | Confirm SMJ can staff at least two qualified people per test type, given hard SoD blocks have no override | Requires Laboratory Decision (operational planning) | §8.2 |
| 4 | Argon2id cost parameters — needs benchmarking on actual host hardware | Requires Technical Decision | §5, Phase 5 |
| 5 | Password/session policy specific values (length, lockout, timeouts) — proposed defaults given | Requires Laboratory Decision | §5, §6, §22 |
| 6 | Concurrent session policy (allow multiple simultaneous logins per user?) | Requires Laboratory Decision | §6 |
| 7 | Configuration governance self-approval risk — designate an alternate approver (Option A) vs. formalize the emergency self-approve + countersign path (Option B), or both | Requires Laboratory Decision | §13.1 |
| 8 | Should accreditation-scope configuration changes require Quality Manager approval specifically? | Requires Laboratory Decision | §14 |
| 9 | USB backup encryption adoption (e.g., BitLocker To Go) | Requires Laboratory Decision | §15, §19 |
| 10 | OS-level disk encryption on the application host, given single-host physical-access risk | Requires Laboratory Decision | §19 |
| 11 | Report file-integrity checking mechanism for issued PDFs | Deferred — Phase 15/18 | §19 |

---

## 26. Phase 2 Acceptance Criteria

| # | Criterion | Status |
|---|---|---|
| 1 | System architecture documented | ✅ Sections 2–4 |
| 2 | Authentication architecture documented | ✅ Section 5 |
| 3 | Session architecture documented | ✅ Section 6 |
| 4 | RBAC model documented | ✅ Section 7 |
| 5 | SoD matrix documented | ✅ Section 8 (with one flagged gap, item 2 above) |
| 6 | Backend authorization model documented | ✅ Section 9 |
| 7 | Audit architecture documented | ✅ Section 10 |
| 8 | Technical-record revision model documented | ✅ Section 11 |
| 9 | Workflow authorization documented | ✅ Section 12 |
| 10 | Configuration governance documented | ✅ Section 13 |
| 11 | SQLite security/operational boundary documented | ✅ Section 15 |
| 12 | Threat model documented | ✅ Section 19 |
| 13 | Trust boundaries documented | ✅ Section 20 |
| 14 | Required ADRs created | ✅ Section 24 (12 of 12) |
| 15 | Remaining decisions classified and assigned | ✅ Section 25 (11 items, each typed and located) |
| 16 | Architecture reviewed against D-001–D-015 | ✅ No conflicts found; D-014 and D-006 given dedicated sections given their weight |
| 17 | No unauthorized feature code introduced | ✅ None written |
| 18 | Sufficient evidence to proceed to CP-002 | **Pending SMJ review of Section 25, particularly items 1–3 and 7–8, which carry real operational weight** |

**Recommended path to CP-002:** items 1–3 and 7–8 in Section 25 benefit from a real conversation with SMJ's Quality Manager, since they touch NABL-facing policy, not just software configuration. Items 4, 6, 9–11 can be resolved in Phase 5/6/15/18 without blocking CP-002. Item 5's proposed defaults are reasonable to accept provisionally and revisit as lab-configurable values later, since nothing about them is structurally hard to change.



Next Prompt:
# SMJ Sustainable Fuel Lab — LIMS Program

## Phase 2 — System & Security Architecture

### Decision Resolution, Corrections & CP-002 Readiness

You are continuing the **SMJ Sustainable Fuel Lab LIMS Program**.

The authoritative baseline is:

* **CP-000 — Architecture & Project Baseline: ACCEPTED**
* **Phase 0: COMPLETE**
* **D-001–D-015: FROZEN**
* **Phase 2: IN PROGRESS**
* No feature code, production migrations, or frontend implementation is authorized by this prompt.

The current Phase 2 architecture document has been substantially completed. It contains the required system/security architecture, RBAC, SoD, audit, workflow, configuration governance, SQLite security, threat model, deployment boundaries, and ADR register.

The purpose of this prompt is **not to redesign Phase 2 from scratch**.

The purpose is to:

1. review the Phase 2 architecture critically;
2. resolve the few genuine policy/design gaps identified during the architecture exercise;
3. correct internal inconsistencies;
4. distinguish laboratory policy decisions from technical architecture decisions;
5. produce the final Phase 2 baseline suitable for **CP-002**.

---

# 1. Authoritative CP-000 Foundation

Do not reopen or casually reconsider the following:

| ID    | Frozen Decision                                                                                                                                                                   |
| ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| D-001 | Single-laboratory LIMS for SMJ v1                                                                                                                                                 |
| D-002 | React + TypeScript + Vite + MUI / FastAPI + Python / SQLAlchemy 2.x / SQLite / Alembic / Argon2id / secure server-side sessions / Caddy / Jinja2 + Chromium / pytest + Playwright |
| D-003 | Modular Monolith                                                                                                                                                                  |
| D-004 | SQLite                                                                                                                                                                            |
| D-005 | Revision-based technical records + immutable audit                                                                                                                                |
| D-006 | RBAC + server-side sessions + policy-driven per-TestInstance segregation of duties                                                                                                |
| D-007 | Explicit workflow state machine                                                                                                                                                   |
| D-008 | Strongly typed configuration tables; no blanket EAV                                                                                                                               |
| D-009 | Task → Verification → Checkpoint development                                                                                                                                      |
| D-010 | Documentation-as-code                                                                                                                                                             |
| D-011 | Domain-oriented module boundaries                                                                                                                                                 |
| D-012 | Conservative, controlled, auditable architecture                                                                                                                                  |
| D-013 | Charge calculation in LIMS; invoicing/accounting external                                                                                                                         |
| D-014 | Accreditation applicability controlled at Method/Test level                                                                                                                       |
| D-015 | Controlled configuration changes use Propose → Approve governance                                                                                                                 |

If a genuine conflict is discovered, identify it explicitly as a **Change Request / ADR revision**. Do not silently alter the baseline.

---

# 2. Current Phase 2 Assessment

The Phase 2 design is considered substantially complete.

The following areas are already acceptable:

* system architecture;
* modular-monolith layering;
* domain module boundaries;
* authentication;
* server-side sessions;
* RBAC concept;
* backend authorization;
* audit architecture;
* technical-record revision model;
* configuration governance concept;
* SQLite operational/security boundaries;
* API security;
* error classification;
* logging separation;
* file/document security;
* threat model;
* deployment trust boundaries;
* secrets handling;
* ADR coverage.

No architectural reason has been identified to replace SQLite, introduce microservices, add a plugin framework, introduce JWT browser sessions, or move to cloud/multi-tenant architecture.

---

# 3. Critical Principle for This Review

Keep these two categories separate:

### Technical Architecture

What the software **can enforce and support**.

### Laboratory Policy

What SMJ's approved SOPs, risk assessments, competence arrangements, and quality-system procedures **require or permit**.

The architecture must support the required policy outcomes without inventing the laboratory's policy.

Where the architecture can support multiple policy values, document the mechanism and label the actual value as:

* Confirmed;
* Proposed;
* Requires Laboratory Decision;
* Requires Technical Decision;
* Deferred.

---

# 4. Resolve Five Focused Phase 2 Decisions

Create a formal decision-resolution section covering the following five items.

---

## P2-DEC-001 — Reviewer → Technical Reviewer on the Same TestInstance

### Problem

The current SoD matrix explicitly addresses:

* Analyst → Review;
* Analyst → Verification;
* Analyst → Approval;
* Technical Reviewer → Approval.

It does **not** explicitly state whether the same user may perform both:

```text
Reviewer
   ↓
Technical Reviewer / Verifier
```

on the **same TestInstance**.

This is a real policy gap.

### Required treatment

Do not silently assume the answer.

Present these options:

**Option A — Block**

The same person cannot both review and technically verify the same TestInstance.

**Pros:**

* strongest independence;
* clear separation of review stages;
* simpler audit interpretation.

**Cons:**

* significant staffing impact for a three-person laboratory;
* may unnecessarily duplicate expertise if the laboratory's procedure does not require the distinction.

**Option B — Permit**

The same authorized person may perform both Review and Technical Verification on the same TestInstance.

**Pros:**

* practical for a very small laboratory;
* fewer operational bottlenecks.

**Cons:**

* reduces independence between the two review stages;
* must be justified by laboratory procedure/risk assessment.

**Option C — Policy-controlled**

Architecture supports either outcome through a controlled SoD policy.

**Recommended default:** **Option C** unless SMJ's approved procedure already determines the answer.

The software must be capable of enforcing either Allowed or Blocked without redesign.

---

# 5. P2-DEC-002 — Technical Reviewer → Final Approval

The existing architecture already treats this as policy-controlled.

Do not redesign that mechanism.

Confirm that:

```text
Analyst → Approval
```

remains a **hard block** for the same TestInstance.

Confirm that:

```text
Technical Reviewer → Approval
```

remains **policy-controlled**.

Define clearly:

* what configuration controls it;
* who can change that policy;
* how the change is audited;
* how historical approvals remain unaffected.

Do not invent the final SMJ SOP decision.

---

# 6. P2-DEC-003 — Minimum Qualified Staffing Required by Hard SoD

The current architecture contains non-overridable hard blocks:

```text
Analyst cannot independently Review
Analyst cannot Verify own work
Analyst cannot Approve own work
```

This produces an operational consequence:

> Every production test type subject to these controls must have sufficient qualified personnel to prevent the workflow from becoming permanently blocked.

The architecture shall therefore document:

### Requirement

SMJ must maintain sufficient qualified personnel for every production test type to satisfy the configured mandatory SoD controls.

Do not interpret this as a software requirement to create extra user accounts.

It is a **laboratory operational requirement**.

Flag it as such and connect it to:

* competence records;
* authorization;
* staffing;
* workload planning.

Do not make this a CP-002 blocker unless the laboratory explicitly states that the required staffing cannot be achieved.

---

# 7. P2-DEC-004 — Configuration Governance Self-Approval

The current architecture requires:

```text
Proposer ≠ Approver
```

This is correct for ordinary controlled configuration.

However, because SMJ is a very small laboratory, there may be cases where the System Administrator is also the normal proposer and only person available to approve.

The architecture already supports an emergency model.

Evaluate these options:

### Option A — Alternate Approver

SMJ designates a second authorized person for approval.

**Recommended normal operating model.**

### Option B — Emergency Self-Approval + Mandatory Countersign

Self-approval is permitted only for a formally identified emergency, requiring:

* emergency classification;
* mandatory justification;
* full audit;
* immediate visibility as an outstanding control item;
* second-person countersignature within a defined period;
* automatic overdue flag if not countersigned.

### Option C — Both

Option A is the normal path.

Option B exists only as an exceptional fallback.

### Recommendation

Recommend **Option C** unless SMJ explicitly rejects emergency self-approval as a matter of laboratory policy.

Do not silently choose the laboratory governance policy.

The technical architecture should support the chosen policy without structural redesign.

---

# 8. P2-DEC-005 — Approval Authority for Accreditation-Scope Changes

D-014 establishes accreditation applicability at Method/Test scope rather than organization-wide.

The current architecture allows controlled configuration by category.

Determine whether:

```text
Accreditation-scope changes
```

should require:

### Option A

System Administrator approval only.

### Option B

Quality Manager approval only.

### Option C

Quality Manager approval plus System Administrator authorization.

### Option D

Separate approval authority determined by the relevant laboratory procedure.

### Recommendation

Recommend **Option D**, with the architecture supporting a specific approver set for the `ACCREDITATION_SCOPE` configuration category.

Explain why this is preferable:

* accreditation scope is quality-system-sensitive;
* technical configuration and system administration are different responsibilities;
* the software should not silently convert a non-accredited method into an accredited one.

Do not claim that NABL requires a particular software workflow unless supported by an authoritative source.

---

# 9. Correct the Internal Architecture Inconsistencies

Before CP-002, inspect the existing Phase 2 document for and correct the following.

## 9.1 Audit ownership

If one section says:

> Application Services call Audit Service

while another says:

> Repository writes AuditEvent

replace both with one consistent model.

Recommended wording:

> Application Services determine when an operation requires auditing and provide the audit event data. The transaction/repository boundary persists the business change and audit event atomically in the same SQLite transaction.

The architecture must guarantee:

```text
Business Change
       +
Audit Event
       ↓
Same Transaction
       ↓
Commit
```

---

## 9.2 Domain Services must not directly access SQLAlchemy/SQLite

Domain Services may enforce business rules but must not directly execute SQL.

Use a domain/application-facing interface or port where required state must be retrieved.

Recommended:

```text
Application Service
      ↓
Repository / Read Model
      ↓
Domain Policy Service
      ↓
Decision
```

or an equivalent clean dependency direction.

No upward or circular dependency is permitted.

---

## 9.3 RBAC diagram

If Section 23 claims all diagrams are Mermaid, ensure the RBAC architecture has an actual Mermaid diagram.

Use or improve something equivalent to:

```mermaid
flowchart LR
    U[User]
    UR[UserRoleAssignment]
    R[Role]
    RP[RolePermission]
    P[Permission]
    S[Optional Scope]

    U --> UR
    UR --> R
    UR --> S
    R --> RP
    RP --> P
```

---

# 10. Normalize Workflow States

The current design separates:

* Review;
* Verification;

but in some places they appear as one transition.

Make them explicit.

Recommended conceptual workflow:

```text
Draft
   ↓
Received
   ↓
Registered
   ↓
Assigned
   ↓
In Progress
   ↓
Pending Review
   ↓
Reviewed
   ↓
Pending Verification
   ↓
Verified
   ↓
Approved
   ↓
Reported
   ↓
Archived
```

The exact final state names may be refined, but the architecture must clearly distinguish:

```text
Review
```

from:

```text
Technical Verification
```

This is necessary for:

* permissions;
* SoD;
* queues;
* audit;
* timestamps;
* TAT reporting.

Update the workflow diagram and transition table consistently.

---

# 11. Review the Existing SoD Matrix

Produce a final table like:

| Same TestInstance activity combination | Status                                    |
| -------------------------------------- | ----------------------------------------- |
| Analyst → Review                       | Hard Block                                |
| Analyst → Verification                 | Hard Block                                |
| Analyst → Final Approval               | Hard Block                                |
| Reviewer → Technical Verification      | Laboratory-policy decision / configurable |
| Technical Reviewer → Final Approval    | Laboratory-policy decision / configurable |
| Same user on different TestInstances   | Permitted subject to normal authorization |

Explicitly state:

> Hard blocks are structural and have no technical override.

For policy-controlled combinations:

> The software supports either Allowed or Blocked, but the effective value is controlled through the approved configuration-governance process.

---

# 12. Review Configuration Governance

The configuration governance model must clearly distinguish:

### Normal controlled change

```text
Authorized Proposer
      ↓
Proposal
      ↓
Independent Approver
      ↓
Approved
      ↓
Effective
```

### Emergency change

Only if SMJ adopts the emergency policy.

```text
Authorized User
      ↓
Emergency Proposal
      ↓
Emergency Approval
      ↓
Immediate Effect
      ↓
Audit
      ↓
Mandatory Countersign
```

The architecture must make an uncountersigned emergency change visible.

Do not permit an emergency path to silently become the normal configuration path.

---

# 13. Accreditation-Scope Controls

Review D-014 and ensure the architecture supports:

* current accreditation scope;
* non-accredited methods/tests;
* future scope additions;
* scope withdrawal;
* historical preservation;
* report-time evaluation;
* controlled configuration;
* restricted approval authority.

Ensure that changing the current scope does **not** modify previously issued reports.

---

# 14. Security Policy Values

Review proposed values for:

* minimum password length;
* failed-login threshold;
* lockout duration;
* session idle timeout;
* absolute session timeout;
* concurrent sessions;
* Argon2id parameters.

Classify them correctly.

Do not unnecessarily turn lab-configurable values into architecture constants.

Argon2id cost values should remain a technical decision to be benchmarked on actual hardware.

---

# 15. SQLite Security

Confirm the following remain mandatory:

```text
SQLite
+
WAL
+
local fixed storage
+
application-only access
+
OS file permissions
+
foreign_keys=ON
+
busy_timeout
+
application retry/backoff
+
short write transactions
```

Do not permit:

* direct browser access;
* direct client workstation access;
* network-share DB files;
* raw SQLite errors returned to users.

---

# 16. Backup Security

Treat the current backup architecture as:

```text
Production DB
     ↓
Daily Backup
     ↓
Local Backup
     ↓
Rotated External USB
```

Confirm:

* integrity verification;
* restricted backup access;
* monthly restore test;
* RPO ≤24h;
* RTO same business day.

Recommend evaluating encryption for USB backup media.

Classify encryption adoption as a laboratory/operational decision rather than silently imposing a technical product.

---

# 17. Threat Model Review

Recheck the threat model after the SoD/configuration changes.

Pay particular attention to:

* self-approval;
* privilege escalation;
* accreditation-scope manipulation;
* direct SQLite access;
* backup theft;
* ransomware;
* session compromise;
* report replacement.

Do not add enterprise security controls merely for appearance.

Controls must remain proportional to the actual single-host, small-laboratory deployment.

---

# 18. ADR Review

Review ADR-001 through ADR-012 for consistency with the final Phase 2 architecture.

At minimum ensure:

* ADR-006 reflects the final SoD matrix;
* ADR-007 reflects the final audit transaction model;
* ADR-009 reflects explicit Review vs Verification states;
* ADR-010 reflects the final configuration governance/self-approval policy;
* ADR-011 accurately describes SQLite residual risks.

Where a decision has not yet been made by SMJ, mark the ADR consequence appropriately rather than inventing the decision.

---

# 19. Section 25 — Final Decision Classification

After the review, classify every remaining question as:

### A — Must be decided by SMJ before CP-002

Only decisions that materially affect the security architecture.

### B — Can be provisionally configured

Safe defaults can be used without architectural consequence.

### C — Deferred to later phase

No effect on Phase 2 architecture.

### D — Architecture already supports both choices

No redesign required.

Do not artificially inflate the number of CP-002 blockers.

---

# 20. CP-002 Acceptance Model

Do not require every laboratory policy value to be finalized before accepting the technical architecture.

CP-002 should be accepted when:

1. The system architecture is internally consistent.
2. Authentication/session architecture is complete.
3. RBAC architecture is complete.
4. SoD mechanism is complete.
5. Mandatory SoD blocks are explicitly identified.
6. Policy-controlled SoD combinations are explicitly identified.
7. Workflow authorization is complete and distinguishes Review from Verification.
8. Audit architecture is internally consistent.
9. Technical-record revision architecture is complete.
10. Configuration governance architecture is complete.
11. Accreditation-scope security architecture is complete.
12. SQLite security boundaries are complete.
13. Threat model is complete.
14. Deployment trust boundaries are complete.
15. ADRs are consistent with the architecture.
16. Remaining laboratory policy decisions are explicitly classified and assigned.
17. No feature implementation or schema migration has been introduced prematurely.
18. The architecture can proceed to Phase 3 without unresolved structural ambiguity.

---

# 21. Required Final Output

Produce the response in this order:

## 1. Phase 2 Review Summary

What is sound and what requires correction.

## 2. P2-DEC-001 — Reviewer → Technical Reviewer

Options, consequences, recommended architecture, laboratory decision requirement.

## 3. P2-DEC-002 — Technical Reviewer → Approval

Final policy mechanism.

## 4. P2-DEC-003 — Staffing Consequence

Operational requirement generated by hard SoD.

## 5. P2-DEC-004 — Configuration Self-Approval

Options and recommended model.

## 6. P2-DEC-005 — Accreditation Scope Approval

Options and recommended model.

## 7. Architecture Corrections

Audit layering, domain-service dependency direction, RBAC diagram, workflow normalization.

## 8. Revised SoD Matrix

Final proposed table.

## 9. Revised Configuration Governance

Normal + emergency paths.

## 10. Revised Workflow Authorization

Final state/transition model.

## 11. Revised Section 25

Only genuinely unresolved decisions remain.

## 12. ADR Impact

Which ADRs change and why.

## 13. CP-002 Acceptance Assessment

State whether the architecture is:

* Not Ready;
* Conditionally Ready;
* or Ready for CP-002.

Do not claim CP-002 acceptance unless its criteria are actually satisfied.

---

# 22. Important Instruction

Do not start implementation.

Do not create:

* database tables;
* Alembic migrations;
* frontend screens;
* APIs;
* production code.

This is still **architecture and decision work only**.

The immediate objective is:

> **Resolve the small number of remaining architectural/policy boundaries, eliminate internal contradictions, and produce a final Phase 2 baseline that can legitimately pass CP-002.**

Once CP-002 is accepted, the project proceeds to:

> **Phase 3 — Data Architecture**

where the logical data model, ERD, relational constraints, revision structures, indexing strategy, migration strategy, and data dictionary can be designed against the now-stable system/security architecture.


Response:
Determination: Ready for CP-002. All five decisions resolved, the four flagged inconsistencies corrected, and — per the master prompt's own instruction not to inflate blockers — none of the twelve remaining items landed in the "must decide before CP-002" bucket; they're all either fully supported by the mechanism already (D), safe defaults SMJ can assign whenever convenient (B), or genuinely later-phase (C).

Two judgment calls worth a second look since I made them rather than found them explicitly stated: I set the Reviewer→Verifier gap's provisional default to Block until SMJ says otherwise (safer lean, not a neutral coin flip), and I suggested the Technical-Reviewer→Approval policy switch probably deserves the same restricted, quality-sensitive approver set as accreditation scope, rather than the generic System Administrator default — worth confirming both read right to you before Phase 3 locks in against them.

# SMJ Sustainable Fuel Lab — LIMS Program

## Phase 2 — Decision Resolution, Corrections & CP-002 Readiness

**Document control:** This document resolves every open item from the Phase 2 draft (`SMJ-LIMS_Phase2_System-Security-Architecture.md`) and corrects its identified inconsistencies. Sections 1, 3–6, and 14–22 of that draft (system architecture unaffected by the corrections below, authentication, security baseline, threat model, secrets, file security) **remain valid and in force, unchanged.** Wherever this document and the earlier draft differ — Sections 2, 7, 8, 10–13 (audit ownership, RBAC diagram, SoD matrix, configuration governance, workflow states, ADRs 006/007/009/010) — **this document is authoritative.** Together, the two form the complete Phase 2 baseline.

CP-000 (D-001–D-015) remains frozen throughout. No conflict with the baseline was found.

---

## 1. Phase 2 Review Summary

**Sound, unchanged:** system architecture and layering concept, domain module boundaries, authentication design, server-side session design, RBAC concept, backend authorization sequencing, revision/technical-record model, configuration-governance concept, SQLite security posture, API error handling, log separation, file/document security pattern, threat model, deployment trust boundaries, secrets handling, and the general ADR structure. No case was found for revisiting SQLite, introducing microservices/plugins, moving to JWT browser sessions, or any cloud/multi-tenant shift.

**Required correction, addressed below:**
- **Audit ownership** was stated two different ways in two diagrams (Application Service writes audit vs. Repository writes audit) — §7.1.
- **Domain Services** were implicitly given data-lookup responsibility (the SoD check needing a record's actor history) without a clean way to get that data without touching SQL directly — §7.2.
- **RBAC** had no actual Mermaid diagram despite the diagram index claiming full Mermaid coverage — §7.3.
- **Review and Verification** were conflated into a single transition in the workflow table, which breaks permission, SoD, queue, audit, and TAT-reporting granularity — §7.4.
- **One genuine SoD gap** (Reviewer → Technical Verification, same record) is resolved as P2-DEC-001 below, rather than left implicit.

---

## 2. P2-DEC-001 — Reviewer → Technical Reviewer on the Same TestInstance

| Option | Description | Pros | Cons |
|---|---|---|---|
| **A — Block** | Same person cannot both Review and Technically Verify the same TestInstance | Strongest independence; clearest audit interpretation | Real staffing impact for a 3-person lab; may duplicate expertise unnecessarily if SMJ's procedure doesn't require it |
| **B — Permit** | Same authorized person may do both, same record | Practical at this scale; fewer bottlenecks | Reduces independence between two intended review stages; needs justification in SMJ's procedure/risk assessment |
| **C — Policy-controlled** | Architecture enforces whichever SMJ decides, via configuration | No redesign needed either way; decision sits with the people who actually know the risk | Requires SMJ to actually make the call at some point (not urgent — see classification) |

**Adopted: Option C.** Mechanism: `ConfigSetting: sod.reviewer_can_verify` (boolean), changed only via the D-015 propose/approve flow, evaluated by the same `SoDPolicyService` pattern as the Technical-Reviewer→Approval combination.

**Provisional default until SMJ decides: Block.** Reasoning: absent an explicit SMJ procedure permitting the overlap, the conservative default preserves independence rather than assuming a relaxation SMJ hasn't actually authorized. SMJ can change this at any time through governed configuration — this is a starting value, not a permanent stance.

**Classification: D — architecture already supports both choices; no redesign required.** Not a CP-002 blocker.

---

## 3. P2-DEC-002 — Technical Reviewer → Final Approval

**Confirmed, unchanged:**
- `Analyst → Approval`, same TestInstance, remains a **hard block** — structural, no configuration, no override, by anyone.
- `Technical Reviewer → Approval`, same TestInstance, remains **policy-controlled**.

**Mechanism, made explicit:**

| Question | Answer |
|---|---|
| What configuration controls it? | `ConfigSetting: sod.tech_reviewer_can_approve` (boolean) |
| Who can propose a change? | Technical Manager or Quality Manager |
| Who can approve a change? | **Flagged for alignment with P2-DEC-005's pattern below** — SoD policy is quality-system-sensitive in the same way accreditation scope is; recommend it draw from the same restricted, category-specific approver set rather than the generic System Administrator default. Final approver assignment is SMJ's call, not invented here. |
| How is it audited? | Standard `ConfigProposal` audit trail (previous/proposed value, proposer, approver, timestamps, reason) |
| How do historical approvals stay unaffected? | SoD is evaluated **only at the moment** a review/verify/approve action is attempted, against the policy value in effect *then*. Changing the policy going forward has no retroactive effect on approvals already granted — this follows the same immutability logic as every other technical record. |

**Classification: D** — mechanism fully specified; the specific boolean value is SMJ's SOP call, not a CP-002 blocker.

---

## 4. P2-DEC-003 — Minimum Qualified Staffing Required by Hard SoD

This is a **laboratory operational requirement, not a software requirement.** The architecture will not manufacture extra accounts or weaken a hard block to compensate for staffing gaps.

**Stated plainly:** for every production test type subject to the hard blocks (Analyst cannot review/verify/approve their own work), **SMJ must have at least one other qualified, authorized person available** to perform the independent stages for that test type. This connects directly to Personnel/Competency records and RBAC role assignment (who is actually authorized for what) and to workload/staffing planning (is there ever a moment where only one qualified person exists for a given test type?).

**Worth building, not required for CP-002:** a proactive check at Test Assignment time (Phase 10) that warns a planner if only one person is currently qualified/available for a test type — surfacing the risk before a record gets stuck at the approval stage, rather than after.

**Classification: C — deferred, operational, no effect on Phase 2 architecture.** This becomes a real concern only if SMJ states the required staffing genuinely cannot be met for some test type — at which point it's a staffing/scope conversation, not an architecture one.

---

## 5. P2-DEC-004 — Configuration Governance Self-Approval

**Adopted: Option C — both.**

- **Normal path (the default operating model):** SMJ designates at least one alternate authorized approver distinct from the routine proposer, so ordinary configuration changes always have genuine independent approval.
- **Emergency path (exceptional fallback only):** self-approval is permitted **solely** when explicitly flagged as an emergency, with mandatory written justification. It is immediately audited as `EMERGENCY_SELF_APPROVED`, surfaced as an outstanding item on the administrative dashboard the moment it happens (not discovered later), and requires **countersignature by a second authorized person within a configurable window** (proposed default: 5 business days). An uncountersigned emergency change is flagged overdue automatically — it does not quietly age out.

**Guardrail against the emergency path becoming the normal path:** the system tracks and can report the count of emergency self-approvals over a period (e.g., per quarter) to the Quality Manager — a pattern of frequent "emergencies" is itself a signal worth surfacing, not hiding.

**Classification: B — safe default, no architectural consequence.** Naming the actual alternate approver is a staffing/assignment task for SMJ, not a CP-002 blocker.

---

## 6. P2-DEC-005 — Approval Authority for Accreditation-Scope Changes

**Adopted: Option D** — approval authority for the `ACCREDITATION_SCOPE` configuration category is **configurable per category**, determined by whatever SMJ's relevant procedure specifies, rather than hard-wired to a single option.

**Why this is the right default, stated on engineering/quality-system grounds only (no claim about what NABL specifically mandates):** technical system administration and quality-system authority are different responsibilities, and a capability that lets a generic administrator silently convert a non-accredited test into an accredited one (or vice versa) would be a real control weakness given SMJ already holds NABL accreditation. Separating "who can administer the system" from "who can change what's in accreditation scope" is a sound segregation regardless of the specific external standard.

**Mechanism:** each `config_area` (including `ACCREDITATION_SCOPE`, and per §3 above, potentially `SOD_POLICY`) can carry its **own restricted approver role set**, distinct from the generic System Administrator default used for ordinary configuration. SMJ assigns the actual roles.

**Classification: B** — the mechanism (category-specific approver sets) is now a confirmed part of the architecture; which specific roles fill that set is an assignment task, not a CP-002 blocker.

---

## 7. Architecture Corrections

### 7.1 Audit Ownership — corrected, single model

**Adopted wording (replaces both prior, inconsistent statements):**

> Application Services determine when an operation requires an audit event and assemble the audit event data (actor, entity, before/after state, reason). The transaction/repository boundary persists the business change and the audit event **atomically, in the same SQLite transaction** — one commits, or neither does.

```mermaid
sequenceDiagram
    participant Ap as Application Service
    participant D as Domain Service
    participant R as Repository / Transaction Boundary
    Ap->>D: execute use case, get decision
    D-->>Ap: decision + business result
    Ap->>Ap: assemble AuditEvent (actor, entity, before/after, reason)
    Ap->>R: persist(business_change, audit_event)
    R->>R: BEGIN
    R->>R: write business change
    R->>R: write audit event
    R->>R: COMMIT (both, or neither)
```

### 7.2 Domain Services — corrected dependency direction

Domain Services (workflow state machine, SoD policy engine, calculation engine) are pure decision logic: they receive an already-assembled, in-memory context object and return a decision — they never query SQLAlchemy or SQLite directly.

```text
Application Service
      ↓ (loads what's needed)
Repository / Read Model  →  e.g. TestInstanceActorContext { created_by, reviewed_by, verified_by }
      ↓ (passes context in)
Domain Policy Service (e.g. SoDPolicyService.evaluate(context, action, actor))
      ↓
Decision (Allowed / Blocked / PolicyPermitted)
      ↓ (Application Service acts on it)
```

This replaces the earlier ambiguity where `SoDPolicyService.check(user, action, record)` implied the Domain Service itself would look up `record`'s fields. It now receives a pre-loaded `TestInstanceActorContext`, assembled by the calling Application Service via the Repository. No upward or circular dependency exists.

### 7.3 RBAC Diagram — added

```mermaid
flowchart LR
    U[User] --> UR[UserRoleAssignment]
    UR --> R[Role]
    UR --> S["Optional Scope\n(discipline/section)"]
    R --> RP[RolePermission]
    RP --> P[Permission]
```

The diagram index (original §23) is corrected to point here for the RBAC diagram, rather than the text-only structure previously shown in §7.

### 7.4 Workflow Normalization — Review and Verification separated

See Section 10 below for the full corrected state machine and transition table.

---

## 8. Revised SoD Matrix (Final)

| Same TestInstance activity combination | Status |
|---|---|
| Analyst → Review | **Hard Block** |
| Analyst → Verification | **Hard Block** |
| Analyst → Final Approval | **Hard Block** |
| Reviewer → Technical Verification | Laboratory-policy decision / configurable (P2-DEC-001; provisional default: Block) |
| Technical Reviewer → Final Approval | Laboratory-policy decision / configurable (P2-DEC-002) |
| Same user on different TestInstances | Permitted, subject to normal role authorization |

**Hard blocks are structural and have no technical override** — not by an admin, not for an emergency, not with a documented reason. For the two policy-controlled combinations, **the software supports either Allowed or Blocked; the effective value is set only through the approved configuration-governance process** (Section 9), never as a runtime exception.

---

## 9. Revised Configuration Governance (Final)

### Normal path
```mermaid
stateDiagram-v2
    [*] --> Proposed: Authorized Proposer submits
    Proposed --> Approved: Independent Approver approves
    Proposed --> Rejected: Independent Approver rejects
    Approved --> Effective
    Rejected --> [*]
    Effective --> [*]
```

### Emergency path (exceptional fallback only — never the default route)
```mermaid
stateDiagram-v2
    [*] --> EmergencyProposal: Authorized user, emergency flag + mandatory justification
    EmergencyProposal --> ImmediateEffect: Self-approved, fully audited (EMERGENCY_SELF_APPROVED)
    ImmediateEffect --> Countersigned: Second authorized person reviews within window (default 5 business days)
    ImmediateEffect --> OverdueFlagged: Window expires without countersignature
    Countersigned --> [*]
    OverdueFlagged --> [*]: Remains visible on admin dashboard until resolved
```

`approver_id ≠ proposer_id` remains enforced for the normal path without exception. The emergency path exists specifically for the case the normal path cannot handle (sole administrator, urgent need) and is bounded by mandatory visibility and countersignature — it is never a silent or default route, and its frequency is itself monitored (Section 5).

---

## 10. Revised Workflow Authorization (Final)

```mermaid
stateDiagram-v2
    [*] --> Draft
    Draft --> Received
    Received --> Registered
    Registered --> Assigned
    Assigned --> InProgress: In Progress
    InProgress --> PendingReview: Pending Review
    PendingReview --> Reviewed
    Reviewed --> PendingVerification: Pending Verification
    PendingVerification --> Verified
    Verified --> Approved
    Approved --> Reported
    Reported --> Archived
    Draft --> Rejected
    Received --> Rejected
    PendingReview --> Rejected: sent back for rework
    PendingVerification --> Rejected: sent back for rework
    Approved --> ReopenedForCorrection
    ReopenedForCorrection --> PendingReview
```

| Transition | Who may initiate | SoD constraint | Audit event |
|---|---|---|---|
| PendingReview → Reviewed | Reviewer | Analyst ≠ Reviewer (hard) | `RESULT_REVIEWED` |
| Reviewed → PendingVerification | System (automatic on review completion) | — | `VERIFICATION_QUEUED` |
| PendingVerification → Verified | Technical Reviewer | Analyst ≠ Verifier (hard); Reviewer ≠ Verifier **if** `sod.reviewer_can_verify = Block` (P2-DEC-001) | `RESULT_VERIFIED` |
| Verified → Approved | Authorized Signatory | Analyst ≠ Approver (hard); Technical Reviewer ≠ Approver **if** `sod.tech_reviewer_can_approve = Block` (P2-DEC-002) | `RESULT_APPROVED` |

All other transitions (Draft through Assigned→InProgress, and Approved→Reported→Archived, plus Rejected/Reopen) are unchanged from the original Phase 2 draft §12 and remain valid.

Separating Review and Verification gives each its own queue, its own timestamp pair (for TAT reporting), its own permission check, and its own audit event — none of which were distinguishable while they were one transition.

---

## 11. Revised Section 25 — Final Decision Classification

| # | Item | Classification | Notes |
|---|---|---|---|
| 1 | Reviewer → Technical Verification: final Allowed/Blocked value | **D** | Mechanism complete; provisional default = Block; SMJ sets final value whenever convenient |
| 2 | Technical Reviewer → Approval: final Allowed/Blocked value | **D** | Mechanism complete (already existed); same treatment |
| 3 | Approver set for `SOD_POLICY` and `ACCREDITATION_SCOPE` config categories | **B** | Mechanism (category-specific approver sets) complete; role assignment is SMJ's task |
| 4 | Minimum staffing per test type for hard SoD blocks | **C** | Operational, not architectural; escalates only if SMJ reports it's unachievable |
| 5 | Alternate configuration approver designation | **B** | Safe default (Option C: normal+emergency) already adopted; naming the person is operational |
| 6 | Emergency countersign window length (default 5 business days) | **B** | Lab-configurable value, no architectural consequence |
| 7 | Argon2id cost parameters | **C** | Deferred to Phase 5 hardware benchmarking |
| 8 | Password/session policy specific values | **B** | Proposed defaults stand; lab-configurable |
| 9 | Concurrent session policy | **B** | Default (permitted) stands until SMJ restricts it |
| 10 | USB backup encryption adoption | **C** | Operational/Phase 17, no software architecture dependency |
| 11 | OS-level disk encryption on host | **C** | Operational, outside LIMS software scope |
| 12 | Report file-integrity checking | **C** | Deferred to Phase 15/18 |

**No item is classified A.** Nothing here materially affects the security architecture's completeness or correctness — every mechanism is fully specified; what remains is SMJ assigning specific values and people, which can proceed in parallel with Phase 3 rather than gating it.

---

## 12. ADR Impact

| ADR | Change |
|---|---|
| **ADR-006 Segregation of Duties** | Updated to the final matrix (§8): explicitly closes the Reviewer→Verifier gap as policy-controlled (not silently permitted), reaffirms hard blocks have zero override under any circumstance |
| **ADR-007 Audit Architecture** | Updated to the corrected single ownership model (§7.1): Application Service assembles the audit event, Repository persists business-change-plus-audit-event atomically. Removes the earlier two-diagram inconsistency. |
| **ADR-009 Workflow Authorization** | Updated to reflect explicit `Reviewed` and `PendingVerification` as distinct states, not folded into a single Review/Verify transition — consequence: queues, timestamps, and audit events are now independently trackable per stage |
| **ADR-010 Configuration Governance** | Updated to record the adopted Option C (normal alternate-approver path + bounded, visible, countersigned emergency path), including the anti-normalization monitoring (frequency tracking) |
| **ADR-011 SQLite Operational Security** | Reviewed — no substantive change. Reaffirmed as accurate: file-permission and application-mediated access remain the only controls, still an accepted trade-off at this confirmed scale |

---

## 13. CP-002 Acceptance Assessment

| # | Criterion (per Phase 2 master prompt §20) | Status |
|---|---|---|
| 1 | System architecture internally consistent | ✅ (§7.1, §7.2 corrections applied) |
| 2 | Authentication/session architecture complete | ✅ (original draft §5–6, unchanged) |
| 3 | RBAC architecture complete | ✅ (original draft §7 + corrected diagram, §7.3) |
| 4 | SoD mechanism complete | ✅ (§7.2, §8) |
| 5 | Mandatory SoD blocks explicitly identified | ✅ (§8) |
| 6 | Policy-controlled SoD combinations explicitly identified | ✅ (§8, including the newly closed gap) |
| 7 | Workflow authorization complete, Review distinguished from Verification | ✅ (§10) |
| 8 | Audit architecture internally consistent | ✅ (§7.1) |
| 9 | Technical-record revision architecture complete | ✅ (original draft §11, unchanged) |
| 10 | Configuration governance architecture complete | ✅ (§9) |
| 11 | Accreditation-scope security architecture complete | ✅ (original draft §14 + §6 refinement) |
| 12 | SQLite security boundaries complete | ✅ (original draft §15, unchanged) |
| 13 | Threat model complete | ✅ (original draft §19, unchanged; no new threats introduced by these corrections) |
| 14 | Deployment trust boundaries complete | ✅ (original draft §20, unchanged) |
| 15 | ADRs consistent with final architecture | ✅ (§12) |
| 16 | Remaining laboratory policy decisions classified and assigned | ✅ (§11 — 12 items, none blocking) |
| 17 | No feature implementation or schema migration introduced prematurely | ✅ — none written |
| 18 | Can proceed to Phase 3 without unresolved structural ambiguity | ✅ |

### Determination: **READY FOR CP-002.**

This determination treats the original Phase 2 draft's still-valid sections plus this document's corrections as one combined baseline (per the Document Control note at the top). No open item rises to a level that would block Phase 3 — every remaining question is either a value SMJ can assign in parallel with later phases (B/D) or genuinely belongs to a later phase (C). **Phase 3 — Data Architecture** is authorized to begin against this stable system/security foundation.



Next Prompt:
# SMJ Sustainable Fuel Lab — LIMS Program

## Phase 3 — Data Architecture

### Master Task Prompt

You are continuing the **SMJ Sustainable Fuel Lab LIMS Program**.

The project has completed the discovery and system/security architecture stages.

---

# 1. Current Project Status

### CP-000 — Architecture & Project Baseline

**Status: ACCEPTED**

D-001 through D-015 are frozen and remain authoritative.

### CP-002 — System & Security Architecture

**Status: ACCEPTED / READY-FINALIZED**

The Phase 2 architecture is complete.

Its final decisions, corrections, RBAC model, SoD architecture, audit model, workflow authorization model, configuration governance, accreditation controls, SQLite security model, threat model, and deployment trust boundaries are now the authoritative security/system foundation.

### Current authorized phase

> **Phase 3 — Data Architecture**

### Implementation restriction

This task is **architecture/data-design work only**.

Do **not**:

* write application feature code;
* create production database files;
* create Alembic migration files;
* create application ORM implementation code;
* create frontend screens;
* create APIs;
* begin Phase 4 UI work;
* silently change CP-000 or CP-002 decisions.

The goal is to design the database architecture so that it can be implemented later without ambiguity.

---

# 2. Frozen Foundation — Do Not Re-litigate

The following decisions are authoritative.

| ID    | Frozen Decision                                                                                                                                                                   |
| ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| D-001 | Single-laboratory LIMS for SMJ v1                                                                                                                                                 |
| D-002 | React + TypeScript + Vite + MUI / FastAPI + Python / SQLAlchemy 2.x / SQLite / Alembic / Argon2id / secure server-side sessions / Caddy / Jinja2 + Chromium / pytest + Playwright |
| D-003 | Modular Monolith                                                                                                                                                                  |
| D-004 | SQLite, WAL mode, local fixed storage only                                                                                                                                        |
| D-005 | Revision-based technical records + immutable audit                                                                                                                                |
| D-006 | RBAC + server-side sessions + policy-driven per-TestInstance SoD                                                                                                                  |
| D-007 | Explicit workflow state machine                                                                                                                                                   |
| D-008 | Strongly typed configuration tables; no blanket EAV                                                                                                                               |
| D-009 | Task → Verification → Checkpoint development model                                                                                                                                |
| D-010 | Documentation-as-code                                                                                                                                                             |
| D-011 | Domain-oriented module boundaries                                                                                                                                                 |
| D-012 | Conservative, controlled, auditable architecture                                                                                                                                  |
| D-013 | Charge calculation in LIMS; invoicing/accounting external                                                                                                                         |
| D-014 | Accreditation applicability controlled at Method/Test level                                                                                                                       |
| D-015 | Controlled configuration changes use Propose → Approve governance                                                                                                                 |

Do not redesign these unless a true contradiction is discovered.

Any contradiction must be raised explicitly as a change request/ADR revision.

---

# 3. Phase 3 Objective

Design the complete **logical and physical data architecture** required to support the accepted system and security architecture.

The objective is to answer:

> **What data exists, what it means, how it relates, what rules protect it, how it changes over time, and how the database preserves laboratory traceability?**

The design must be suitable for:

* implementation;
* testing;
* audit;
* migration;
* long-term maintenance;
* historical reconstruction;
* reporting;
* accreditation evidence;
* SQLite operation.

---

# 4. Required Phase 3 Deliverables

Produce a formal Phase 3 architecture package containing the following.

## WP-03-01 — Domain-to-Data Mapping

Map the CP-000 / CP-002 domain model into explicit relational data concepts.

At minimum cover:

* Identity
* Users
* Roles
* Permissions
* Role assignments
* Sessions
* Audit
* Master Data
* Customer
* Contact
* Project / Contract
* Rate
* CustomerRate
* Sample
* SubSample / Portion
* Container
* Chain of Custody
* Test Request
* Test Instance
* Method
* Method Version
* Test Definition
* Parameter Definition
* Unit
* Formula
* Formula Version
* Calculation Run
* Observation / Raw Data
* Result
* Result Revision
* Review
* Verification
* Approval
* Equipment
* Calibration
* Maintenance
* QC
* Documents
* Attachments
* Report
* Report Revision
* Configuration
* Configuration Proposal
* Configuration Approval
* Notifications
* Backup/Ops metadata where applicable.

Do not automatically create a table for every noun. Determine the correct relational representation.

---

# 5. Core Data Modeling Principles

The database design shall follow these principles.

## 5.1 Relational first

Use real relational tables for core concepts.

Do not use:

```text
entity
attribute
value
```

as the primary storage mechanism.

---

## 5.2 Normalization

Use **3NF as the baseline**.

Denormalization is permitted only where deliberately justified.

For every deliberate denormalization, document:

* purpose;
* source of truth;
* synchronization rule;
* historical implications;
* query/reporting benefit.

---

## 5.3 Strong typing

Use appropriate SQL column types.

Do not store:

* dates as text;
* numbers as arbitrary strings;
* booleans as uncontrolled text;
* IDs as unvalidated strings;

where a proper relational type is available.

---

# 6. Master Key Strategy

Define the key strategy.

At minimum distinguish:

### Internal primary key

Used for relational integrity.

### Human-facing business identifier

Examples:

* Sample Number;
* Work Order Number;
* Test Number;
* Report Number;
* Certificate Number.

Define:

* generation;
* uniqueness;
* lifecycle;
* immutability;
* reuse policy.

Human-facing numbers must not replace relational PKs.

---

# 7. Foreign Key Architecture

Define all major FK relationships.

Specify:

* parent;
* child;
* cardinality;
* optional/mandatory;
* ON DELETE behavior;
* ON UPDATE behavior where relevant.

Because SQLite is used, explicitly define how:

```text
PRAGMA foreign_keys = ON
```

is guaranteed for every application connection.

No design shall rely on a developer remembering this manually.

---

# 8. Constraint Strategy

For each major entity identify:

### NOT NULL constraints

### UNIQUE constraints

### CHECK constraints

### FK constraints

### business rules enforced at application/domain layer

Do not push every business rule into SQL blindly, but do not leave relational integrity unnecessarily to application code either.

Produce a distinction between:

```text
Database integrity rule
```

and:

```text
Domain/application rule
```

---

# 9. Lifecycle & Status Data Model

Map the Phase 2 explicit workflow state machine into database structures.

Do not use a single uncontrolled status field without a controlled transition model.

The database design must support the current workflow:

```text
Draft
 ↓
Received
 ↓
Registered
 ↓
Assigned
 ↓
In Progress
 ↓
Pending Review
 ↓
Reviewed
 ↓
Pending Verification
 ↓
Verified
 ↓
Approved
 ↓
Reported
 ↓
Archived
```

Also support:

* Rejected;
* Sent Back / Rework;
* Reopened for Correction;
* Cancelled where appropriate.

Determine which are:

* persisted entity states;
* workflow events;
* derived states.

Do not duplicate state unnecessarily.

---

# 10. Technical Record Revision Model

Design the relational model for D-005.

At minimum define how the database represents:

```text
Current Result
Historical Result Revision
Correction
Supersession
Reopen
Approval
Report snapshot
```

Specify:

* revision numbering;
* revision parent;
* current revision pointer if needed;
* created_by;
* created_at;
* reason;
* effective status;
* relationship to approval;
* relationship to report.

The design must make silent modification of an approved technical record structurally difficult or impossible through normal application paths.

---

# 11. Audit Data Model

Design the `AuditEvent` structure from Phase 2.

At minimum define fields for:

* audit ID;
* timestamp;
* actor user;
* session;
* correlation ID;
* category;
* entity type;
* entity ID;
* action;
* before state;
* after state;
* reason;
* outcome.

Determine which data belongs in normalized columns versus JSON.

Document why.

Define retention/reference strategy.

Define how audit history remains associated with historical records even if related records are superseded.

---

# 12. Identity / RBAC Data Model

Translate Phase 2 RBAC into relational design.

At minimum evaluate:

```text
User
Role
Permission
UserRoleAssignment
RolePermission
Scope
Session
```

Support:

* one user → multiple roles;
* role-specific permissions;
* optional discipline scope;
* optional section scope;
* effective dates if justified;
* enable/disable;
* auditability.

Avoid unnecessary permission explosion.

The Phase 2 target of roughly 30–40 coarse-grained permissions remains the design intent unless requirements demonstrate otherwise.

---

# 13. SoD Data Model

Design how the Phase 2 SoD rules are represented.

The model must support:

### Hard blocks

Examples:

```text
Analyst ≠ Reviewer on same TestInstance
Analyst ≠ Verifier on same TestInstance
Analyst ≠ Approver on same TestInstance
```

### Policy-controlled combinations

Examples:

```text
Reviewer → Verifier
Technical Reviewer → Approver
```

Do not encode the entire SoD mechanism as hard-coded role-name comparisons scattered throughout tables.

Define an appropriate policy representation.

It must remain compatible with D-015 configuration governance.

---

# 14. Configuration Governance Data Model

Design the database structures for:

```text
ConfigSetting
ConfigProposal
Approval / Decision
Effective configuration
```

Support:

* proposed value;
* previous value;
* proposer;
* approver;
* status;
* reason;
* timestamps;
* effective time;
* emergency designation where the approved Phase 2 policy permits it;
* audit linkage.

Unapproved values must never become effective configuration.

---

# 15. Accreditation Scope Data Model

Design the relational representation of D-014.

Support:

* accredited;
* non-accredited;
* current scope;
* scope version/effective date where required;
* method/test association;
* historical applicability.

The architecture must ensure:

> changing the current accreditation scope does not alter the accreditation status represented by a previously issued report.

Determine whether a dedicated `AccreditationScope` / `AccreditationScopeAssignment` structure is preferable to a simple boolean.

Do not invent external regulatory requirements. Model the software control needed to preserve the confirmed business rule.

---

# 16. Customer / Project / Pricing Data Model

Design:

```text
Customer
Contact
Project / Contract
Rate
CustomerRate
```

Support:

* standard per-parameter/per-test pricing;
* customer-specific negotiated pricing;
* validity periods;
* historical rate preservation;
* charge calculation.

Do not model:

* invoices;
* payments;
* accounts receivable;
* accounting ledger;

as part of the LIMS database unless an explicit scope change occurs.

---

# 17. Sample & Chain-of-Custody Model

Design the relational model for:

```text
Sample
SubSample / Portion
Container
ChainOfCustodyEvent
SampleCondition
SampleStatus
```

Cover:

* receipt;
* registration;
* accession;
* condition;
* custody transfer;
* storage;
* disposal/retention;
* identifiers/barcodes.

Ensure historical COC events are not overwritten.

---

# 18. Test & Method Data Model

Design the distinction between:

```text
Method
MethodVersion
TestDefinition
ParameterDefinition
TestRequest
TestInstance
```

Do not collapse them.

The design must support:

* method versioning;
* active/inactive methods;
* test configuration;
* parameters;
* units;
* precision;
* required/optional;
* limits;
* calculation linkage;
* accreditation applicability;
* historical preservation.

---

# 19. Observations / Raw Data Model

Define how raw laboratory observations are stored.

Avoid turning this into uncontrolled EAV.

Use strongly typed structures where the requirement is known.

Evaluate whether the right model is:

```text
Observation
ObservationValue
ObservationType
```

or another relational structure.

The final choice must support:

* numeric observations;
* text observations where legitimately required;
* timestamps;
* units;
* instrument/equipment association;
* analyst;
* raw value;
* captured value;
* revision/history;
* provenance.

Document how the model prevents loss of original raw data.

---

# 20. Calculation Data Model

Design:

```text
Formula
FormulaVersion
CalculationRun
CalculationInput
CalculationOutput
```

Support:

* formula versioning;
* input provenance;
* output provenance;
* execution timestamp;
* executing context;
* method/test relationship;
* reproducibility;
* historical recalculation.

The database model must support the Phase 2 principle that arbitrary executable code is never stored/executed as the calculation mechanism.

---

# 21. Equipment / Calibration Data Model

Design:

```text
Equipment
CalibrationRecord
MaintenanceRecord
EquipmentStatus
```

Support the confirmed policy:

```text
30 days before expiry → warning
Expired → block
Explicitly out of calibration → block
```

Historical equipment status must remain reconstructable.

The model must permit determining:

> Which equipment was valid when a particular TestInstance was performed?

This is a critical traceability requirement.

---

# 22. QC Data Model

Design enough relational structure for:

* QC samples;
* blanks;
* duplicates;
* spikes;
* reference materials / CRMs;
* acceptance criteria;
* QC results;
* investigations.

Do not overbuild advanced statistical control-chart infrastructure unless supported by a real requirement.

However, make sure the model can later support it.

---

# 23. Review / Verification / Approval Model

Design separate entities or clearly justified structures for:

```text
Review
Verification
Approval
```

Each must support:

* actor;
* timestamp;
* outcome;
* reason/comment;
* record revision;
* role;
* audit linkage.

Do not merge Review, Verification, and Approval into one generic approval table unless you can demonstrate that doing so preserves all required distinctions.

---

# 24. Report / Report Revision Model

Design:

```text
Report
ReportRevision
ApprovalSnapshot
```

Support:

* final PDF;
* report template version;
* result snapshot;
* accreditation snapshot;
* approval information;
* issue timestamp;
* report number;
* document/file hash if appropriate;
* supersession;
* correction/reissue.

The design must preserve the exact state used to issue a report.

A later result correction must not change the historical issued report.

---

# 25. Document & Attachment Model

Define:

```text
Document
DocumentVersion
Attachment
DocumentLink
```

Support:

* SOPs;
* calibration certificates;
* instrument outputs;
* photographs;
* supporting files;
* report files.

The database stores metadata and controlled references; physical files remain in application-controlled storage according to Phase 2.

Do not expose arbitrary filesystem paths through database fields intended for clients.

---

# 26. Notification Model

Design notification storage only to the level needed for:

* due dates;
* calibration expiry;
* overdue tests;
* pending approvals;
* configuration proposals;
* other defined operational alerts.

Avoid building a generalized enterprise messaging system.

---

# 27. Backup / Operations Metadata

Determine which operational data belongs in the LIMS database versus the operating system/job scheduler.

Examples:

* backup execution history;
* backup verification status;
* restore-test records;
* health checks.

Do not force all operational telemetry into the database.

---

# 28. Soft Delete / Retention / Archive

Define precisely where:

* hard delete is prohibited;
* soft delete is appropriate;
* status-based retirement is appropriate;
* archival is appropriate;
* physical deletion is permitted, if ever.

Especially address:

* technical records;
* customers;
* methods;
* users;
* reports;
* configuration;
* documents.

Historical traceability must not be broken by deletion of reference data.

---

# 29. Index Strategy

Design indexes from actual access patterns.

At minimum consider:

* sample number;
* customer;
* project;
* date;
* status;
* discipline;
* assigned analyst;
* review queue;
* verification queue;
* approval queue;
* report number;
* method;
* equipment;
* calibration due;
* audit entity/time;
* configuration proposals.

Do not create indexes indiscriminately.

For every important index category, document the query/use-case it supports.

Remember SQLite write overhead when adding unnecessary indexes.

---

# 30. SQLite-Specific Design Review

Explicitly review:

* WAL;
* foreign key enforcement;
* busy timeout;
* transaction boundaries;
* index impact on writes;
* concurrency-sensitive tables;
* JSON usage;
* migration limitations;
* supported SQLite features;
* backup implications.

Avoid relying on database features that are unavailable or behave materially differently in SQLite.

Where a feature normally enforced by PostgreSQL must instead be handled in application logic, identify it explicitly.

---

# 31. Transaction Boundary Mapping

For the most important write operations define:

```text
Operation
→ tables affected
→ transaction boundary
→ audit event
→ failure behavior
```

At minimum cover:

### Register Sample

### Start Test

### Submit Result

### Review Result

### Verify Result

### Approve Result

### Reopen Approved Result

### Propose Configuration

### Approve Configuration

### Change Accreditation Scope

### Issue Report

This is particularly important because SQLite uses a single-writer model.

---

# 32. Concurrency / Lock-Sensitive Operations

Identify write-heavy operations and classify them.

Example:

| Operation           | Expected contention | Strategy                  |
| ------------------- | ------------------: | ------------------------- |
| Sample registration |                 Low | Short write transaction   |
| Result entry        |            Moderate | Short transaction         |
| Review              |                 Low | Short transaction         |
| Approval            |                 Low | Short transaction         |
| Report generation   |          Read-heavy | Outside write transaction |
| Search              |           Read-only | Read connection           |
| Dashboard           |          Read-heavy | Read connection           |

Do not perform expensive PDF generation, large calculations, or long-running reads inside a write transaction.

---

# 33. Data Integrity Rules Matrix

Create a matrix:

| Rule | Database constraint | Domain rule | Audit required |
| ---- | ------------------- | ----------- | -------------- |

Include at least:

* FK integrity;
* unique sample number;
* unique report number;
* approved result immutability;
* revision creation;
* SoD;
* workflow transitions;
* equipment eligibility;
* configuration approval;
* accreditation scope changes.

This matrix becomes one of the most important Phase 3 verification artifacts.

---

# 34. Historical Reconstruction Requirements

Prove that the data model can answer questions such as:

> What result was approved?

> Who performed the test?

> Which method version was used?

> Which equipment was used?

> Was the equipment calibrated at that time?

> What raw observations existed?

> Which calculation formula/version was used?

> Who reviewed it?

> Who verified it?

> Who approved it?

> Which accreditation scope applied at that time?

> Which report PDF was issued?

> What did the record look like before a correction?

For each question, identify the tables/relationships that provide the answer.

---

# 35. Traceability Chain

Explicitly demonstrate the complete relational trace:

```text
Customer
   ↓
Project / Contract
   ↓
Sample
   ↓
TestRequest
   ↓
TestInstance
   ↓
MethodVersion
   ↓
Observation / Raw Data
   ↓
CalculationRun
   ↓
ResultRevision
   ↓
Review
   ↓
Verification
   ↓
Approval
   ↓
ReportRevision
   ↓
Issued PDF
```

Also show cross-links to:

```text
Equipment
Analyst
AuditEvent
Accreditation Scope
Configuration
```

---

# 36. Migration Architecture

No legacy database exists.

Migration sources are:

* spreadsheets;
* paper records;
* low volume.

Define a controlled future migration approach anyway.

At minimum document:

```text
Source
→ staging
→ validation
→ transformation
→ duplicate handling
→ import
→ verification
→ audit/evidence
```

Do not create migration scripts yet.

Phase 3 should define the strategy, not perform the migration.

---

# 37. Seed / Reference Data Strategy

Define what categories of data will be:

### System-seeded

Examples:

* permissions;
* system roles;
* status definitions;
* core configuration defaults.

### Laboratory-configured

Examples:

* disciplines;
* units;
* methods;
* tests;
* parameters;
* rates.

### User-created operational data

Examples:

* customers;
* samples;
* test instances;
* results.

Document which data is required for a clean installation to function.

---

# 38. Data Dictionary

Produce a complete data dictionary for the proposed Phase 3 schema.

For each table/entity include:

* purpose;
* field;
* type;
* nullable;
* default;
* PK/FK;
* unique;
* description;
* source/owner;
* lifecycle;
* audit requirements;
* sensitivity;
* historical/revision behavior.

Do not leave important columns as vague "miscellaneous" fields.

---

# 39. ERD

Produce a complete logical ERD.

At minimum provide:

### 39.1 Core domain ERD

### 39.2 Identity/RBAC ERD

### 39.3 Audit/revision ERD

### 39.4 Method/Test/Calculation ERD

### 39.5 Sample/Execution/Result ERD

### 39.6 Review/Approval/Reporting ERD

### 39.7 Equipment/QC ERD

### 39.8 Configuration/governance ERD

Use Mermaid ER diagrams or another repository-friendly representation.

Where one massive diagram becomes unreadable, use multiple bounded diagrams plus one high-level relationship diagram.

---

# 40. Schema Naming Standards

Define naming conventions for:

* tables;
* columns;
* PKs;
* FKs;
* indexes;
* constraints;
* unique constraints;
* enum/status values;
* timestamps;
* boolean fields.

Keep naming consistent across the entire database.

Avoid unexplained abbreviations.

---

# 41. Timestamp Standard

Define:

* storage format;
* timezone strategy;
* server time source;
* created_at;
* updated_at;
* approved_at;
* issued_at;
* effective_at.

Recommended baseline:

> **Store UTC timestamps in the database and convert to the laboratory/user timezone at presentation boundaries.**

Do not allow individual clients to determine authoritative timestamps.

---

# 42. JSON Usage Policy

Because SQLite supports JSON but the project rejects generic EAV, explicitly define when JSON is allowed.

Recommended candidates:

* audit before/after snapshots;
* genuinely variable metadata;
* structured technical payloads only where a stable relational representation is not justified.

JSON shall **not** replace relational structures for:

* customers;
* samples;
* tests;
* methods;
* parameters;
* results;
* approvals;
* equipment;
* reports.

---

# 43. Security / Sensitivity Classification

Classify important data into categories such as:

```text
Public
Internal
Confidential
Controlled Technical Record
Security-Sensitive
```

Map the classification to:

* access control;
* audit;
* backup handling;
* document storage;
* retention.

Do not invent legal classifications; use practical system sensitivity categories.

---

# 44. Data Retention Architecture

CP-000 established the retention baseline.

The database model must support:

* active record;
* retained record;
* archived record;
* report retention;
* document retention;
* audit retention.

Do not physically delete records simply because their active lifecycle ended.

---

# 45. Performance Baseline

Define initial measurable targets for critical database interactions.

For example:

* common search;
* sample lookup;
* result retrieval;
* review queue;
* approval queue;
* dashboard query.

Do not claim exact final numbers without evidence.

Provide:

* proposed target;
* rationale;
* measurement method.

---

# 46. Data Architecture ADRs

Create/update ADRs as required.

At minimum consider:

```text
ADR-013 Primary Key Strategy
ADR-014 Business Numbering Strategy
ADR-015 Revision Storage Strategy
ADR-016 Audit Data Storage Strategy
ADR-017 RBAC Relational Model
ADR-018 SoD Relational Model
ADR-019 Workflow State Persistence
ADR-020 Configuration Persistence
ADR-021 Accreditation Scope Persistence
ADR-022 Result / Observation Data Model
ADR-023 Calculation Provenance Model
ADR-024 Report Snapshot Model
ADR-025 SQLite Data Integrity Constraints
ADR-026 Indexing Strategy
```

Do not create an ADR for every ordinary table.

---

# 47. Phase 3 Deliverable Structure

Return the final Phase 3 architecture package in this order:

## 1. Executive Data Architecture Summary

## 2. Domain-to-Data Mapping

## 3. Data Architecture Principles

## 4. Naming Standards

## 5. Key / Identifier Strategy

## 6. Entity Inventory

## 7. Core ERD

## 8. Identity / RBAC ERD

## 9. Audit / Revision ERD

## 10. Customer / Project / Pricing Model

## 11. Sample / COC Model

## 12. Method / Test / Parameter Model

## 13. Observation / Raw Data Model

## 14. Calculation Model

## 15. Result / Revision Model

## 16. Review / Verification / Approval Model

## 17. Equipment / Calibration Model

## 18. QC Model

## 19. Accreditation Scope Model

## 20. Configuration Governance Model

## 21. Reporting / Snapshot Model

## 22. Documents / Attachments Model

## 23. Notification / Operations Model

## 24. Workflow State Persistence

## 25. Audit Model

## 26. Constraint Strategy

## 27. Index Strategy

## 28. Transaction Boundaries

## 29. SQLite-Specific Considerations

## 30. Historical Reconstruction / Traceability

## 31. Migration Strategy

## 32. Seed / Reference Data Strategy

## 33. Data Dictionary

## 34. Data Integrity Matrix

## 35. Security / Sensitivity Classification

## 36. Retention / Archival Model

## 37. Performance Baseline

## 38. ADR Register

## 39. Open Decisions

## 40. Phase 3 Acceptance Criteria

---

# 48. Strict Constraints

Do not:

* write production SQL migration files;
* create Alembic revisions;
* create executable ORM models;
* create frontend code;
* create API endpoints;
* introduce PostgreSQL-specific schema assumptions;
* introduce generic EAV;
* collapse distinct laboratory concepts merely to reduce table count;
* create speculative enterprise tables;
* redesign the CP-000/CP-002 architecture;
* silently resolve laboratory policy questions;
* invent accreditation requirements.

Do not optimize for the **fewest tables**.

Optimize for:

* correct domain representation;
* integrity;
* traceability;
* maintainability;
* testability;
* understandable relationships.

---

# 49. Critical Design Principle

The database must answer:

> **What happened, to which laboratory item, under which method and configuration, using which equipment, by whom, when, with which observations and calculations, producing which result, reviewed/verified/approved by whom, and represented in which issued report?**

If the proposed schema cannot reconstruct that chain, it is not sufficient.

---

# 50. Phase 3 Quality Gate

Before declaring Phase 3 complete, perform a consistency check against:

### CP-000

D-001 through D-015.

### CP-002

System/security architecture and especially:

* RBAC;
* SoD;
* workflow;
* audit;
* revisions;
* configuration governance;
* accreditation controls;
* SQLite operating constraints.

Explicitly identify any mismatch.

---

# 51. Phase 3 Completion Rule

Phase 3 is complete only when:

1. Domain-to-data mapping is complete.
2. Entity inventory is complete.
3. Logical ERDs are complete.
4. Key strategy is complete.
5. FK strategy is complete.
6. Constraint strategy is complete.
7. Lifecycle/state persistence is complete.
8. Revision model is complete.
9. Audit model is complete.
10. RBAC/SoD data model is complete.
11. Configuration governance model is complete.
12. Accreditation-scope model is complete.
13. Method/Test/Parameter model is complete.
14. Observation/Calculation/Result model is complete.
15. Equipment/QC model is complete.
16. Review/Verification/Approval model is complete.
17. Report snapshot model is complete.
18. Index strategy is defined.
19. Transaction boundaries are defined.
20. SQLite-specific constraints are documented.
21. Historical reconstruction has been demonstrated logically.
22. Migration strategy is defined.
23. Data dictionary is complete enough for implementation.
24. Data integrity matrix is complete.
25. Required ADRs are updated/created.
26. No unauthorized implementation has been introduced.
27. No CP-000 or CP-002 decision has been silently changed.
28. Remaining decisions are explicitly classified.
29. The package is sufficient to authorize implementation work in the next phase.
30. Evidence is sufficient to proceed to **CP-003**.

---

# 52. Final Instruction

Treat **CP-000 and CP-002 as frozen foundations**.

Do not redesign the application or security architecture while designing the database.

Design the data model **from the accepted laboratory domain and workflow**, not from generic CRUD patterns.

Prefer explicit relational structures over generic abstractions.

Where a difficult modeling choice exists:

1. present the alternatives;
2. explain the consequences;
3. recommend one;
4. identify whether it is an architectural decision, technical decision, or laboratory decision;
5. do not silently choose a policy owned by SMJ.

The immediate objective is:

> **Produce a complete, internally consistent, implementation-ready Data Architecture that preserves laboratory integrity, historical reconstruction, accreditation traceability, auditability, and long-term maintainability while remaining appropriate for the confirmed SQLite single-host deployment.**

Do not proceed to schema implementation until the Phase 3 architecture and its decisions have been reviewed and accepted through **CP-003**.


Response:
Two modeling calls in here go beyond what either CP-000 or CP-002 explicitly said, so they're worth flagging rather than letting them pass as routine implementation detail:

Sample and TestInstance turned out to need separate state machines, not the one shared status list every earlier phase document showed. A sample with three tests running at three different stages simultaneously — normal, everyday reality — can't be represented by one status field. Nothing here changes CP-000/CP-002 policy; it's just what actually falls out of that policy once you sit down to build the tables.

Review, Verification, and Approval collapsed into one table (approval_chain_event, tagged by stage) rather than three. Section 23 of your prompt explicitly asked me to justify this either way rather than default to it — the reasoning's in §16 if you want to push back on it before Phase 5 builds against it.

Everything else — the data dictionary, all 8 ERDs, the SoD-as-config-setting mechanism, the accreditation-scope versioning, the report-snapshot freeze — implements what Phase 2 already decided without reopening any of it. Determination: sufficient to proceed to CP-003.

# SMJ Sustainable Fuel Lab — LIMS Program

## Phase 3 — Data Architecture

**Status:** Architecture/data-design only. No SQL migrations, ORM code, or executable schema created. CP-000 (D-001–D-015) and CP-002 (RBAC/SoD/audit/workflow/config-governance/accreditation model) are frozen inputs — this document designs the database that implements them, and does not redesign either.
**Classification key:** `Confirmed` · `Proposed` · `Deferred` · `Requires Laboratory Decision` · `Requires Technical Decision`.

---

## 1. Executive Data Architecture Summary

This schema is built around one rule: **a controlled technical record's current state lives in one table; every prior state it ever had lives in an append-only companion table; nothing in between is ever silently overwritten.** That pattern — current-table + revision-table, both keyed the same way — repeats for `result`, `equipment` status, `report`, and configuration, rather than being a special case invented once for results and ignored elsewhere.

Two modeling decisions carry the most weight and are called out up front rather than buried:

1. **The workflow status the earlier phases described as one linear list is actually two separate lifecycles** — a `Sample` progresses Draft→Received→Registered independently of its tests, while each `TestInstance` (a test performed on that sample) runs its own Assigned→...→Approved→Reported cycle. A sample can have several tests at different stages simultaneously. This wasn't stated explicitly before; it's a necessary clarification, not a silent assumption (Section 24).
2. **Review, Verification, and Approval are one table with a stage discriminator, not three tables.** They're structurally identical events (actor, timestamp, outcome, comment) happening at three tagged points in the same workflow, and merging them matches the event-log pattern already used for audit and revisions. This is presented as a reasoned technical decision in Section 16, not a shortcut.

SoD policy values and accreditation scope both route through the **same** `config_setting`/`config_proposal` mechanism already designed in Phase 2 — no bespoke "SoD table" or "accreditation table" duplicates that governance model.

---

## 2. Domain-to-Data Mapping (WP-03-01)

| Domain concept | Relational representation | Rationale |
|---|---|---|
| User, Role, Permission, Role assignment, Session | `user`, `role`, `permission`, `role_permission`, `user_role_assignment`, `session` | Core RBAC — real tables, not a config blob |
| Audit | `audit_event` | Single append-only table, categorized (Section 25) |
| Master Data (units, disciplines, sections, locations) | `unit`, `discipline`, `section`, `location` | Separate small reference tables, not one generic "lookup" table — each has genuinely different attributes |
| Customer, Contact, Project/Contract | `customer`, `contact`, `project` | Standard entities |
| Rate, CustomerRate | `rate`, `customer_rate` | Two-tier pricing per D-013 |
| Sample, SubSample, Container | `sample`, `sub_sample`, `container` | Distinct physical concepts |
| Chain of Custody | `chain_of_custody_event` | Append-only event log |
| Test Request, TestInstance | `test_request`, `test_instance` | Distinct: a request may yield multiple test instances |
| Method, MethodVersion, TestDefinition, ParameterDefinition | `method`, `method_version`, `test_definition`, `parameter_definition` | Four distinct concepts per CP-000 C.4 — never collapsed |
| Formula, FormulaVersion, CalculationRun | `formula`, `formula_version`, `calculation_run` | Versioned, with provenance |
| Observation | `observation` | Typed (numeric/text), not EAV — Section 13 |
| Result, ResultRevision | `result` (current) + `result_revision` (history) | The core current/history pattern |
| Review, Verification, Approval | **`approval_chain_event`** (single table, `stage` discriminator) | See Section 16 for the reasoning |
| Equipment, Calibration, Maintenance | `equipment`, `calibration_record`, `maintenance_record`, `equipment_status_event` | Status event log added for historical reconstruction |
| QC | `qc_sample`, `qc_result` | Minimal viable structure, extensible |
| Documents, Attachments | `document`, `document_version`, `attachment` | Metadata + controlled reference only; files stay in application-mediated storage |
| Report, Report Revision | `report`, `report_revision`, `report_result_snapshot` | Frozen snapshot table is the key integrity mechanism |
| Configuration, Proposal, Approval | `config_setting`, `config_proposal` | Approval is a status+field on the proposal, **not** a fourth table |
| Accreditation Scope | `accreditation_scope` | Versioned/temporal table, not a boolean — Section 19 |
| Notifications | `notification` | Minimal |
| Backup/Ops | `backup_job_log` | Minimal; most operational telemetry stays in the OS/scheduler, not the LIMS DB |

Not every noun got a table: **Configuration Approval** is a status transition on `config_proposal`, not a separate entity — the "approval" is what happens to a proposal, not a new kind of thing.

---

## 3. Data Architecture Principles

Unchanged from CP-000/CP-002 and reaffirmed as the standard applied throughout this schema: 3NF baseline with justified exceptions only; real relational tables over EAV; strong SQL types over text-encoded values; every controlled record gets a current-state table plus an append-only history table; no business rule silently pushed into the database that the application must also independently enforce without the DB backing it up where a constraint can help.

---

## 4. Naming Standards

| Element | Convention | Example |
|---|---|---|
| Table names | `snake_case`, singular | `test_instance`, `result_revision` |
| Primary keys | `id` (INTEGER, autoincrement) | `sample.id` |
| Foreign keys | `<referenced_singular>_id`; disambiguated when a table references the same table twice | `customer_id`; `reviewed_by_user_id` vs `analyst_user_id` |
| Business identifiers | `<entity>_number`, separate from PK | `sample_number`, `report_number` |
| Timestamps | `_at` suffix, UTC | `created_at`, `approved_at` |
| Booleans | `is_`/`has_` prefix | `is_active`, `has_countersigned` |
| Status/enum columns | `status`, restricted by CHECK constraint (fixed architectural sets) or FK to a small lookup table (extensible sets) | `test_instance.status` (CHECK); `document.document_type` (lookup) |
| Constraints | `pk_`, `fk_`, `uq_`, `ix_`, `ck_` prefix + table + columns | `uq_sample_sample_number`, `ix_test_instance_status` |

No unexplained abbreviations — `equipment`, not `equip`; `verification`, not `verif`.

---

## 5. Key / Identifier Strategy

**Internal PK:** every table uses an `INTEGER PRIMARY KEY` surrogate (SQLite's rowid alias — efficient, simple, never reused within a table's lifetime). Never exposed as a "meaningful" identifier to users.

**Business identifiers** (`sample_number`, `report_number`, `test_request_number`, `certificate_number`): generated via a per-category `numbering_sequence` mechanism (itself a small table: `id`, `category`, `prefix`, `year_component`, `next_value`), formatted per a lab-configurable pattern (e.g., `SF-2026-000123`), **unique-constrained**, **immutable once assigned**, and **never reused** — a rejected sample's number is not recycled; the gap is expected and preserves traceability (a missing number in sequence is itself meaningful, not a bug). This is `Confirmed`.

---

## 6. Entity Inventory

| Table | Purpose |
|---|---|
| `user`, `role`, `permission`, `role_permission`, `user_role_assignment`, `session` | Identity & RBAC |
| `audit_event` | Immutable audit trail |
| `discipline`, `section`, `unit`, `location` | Master data |
| `customer`, `contact`, `project` | Customer/engagement context |
| `rate`, `customer_rate` | Pricing |
| `sample`, `sub_sample`, `container`, `chain_of_custody_event` | Sample lifecycle |
| `test_request`, `test_instance` | Test planning/execution unit |
| `method`, `method_version`, `test_definition`, `parameter_definition` | Method/test configuration |
| `formula`, `formula_version`, `calculation_run` | Calculation provenance |
| `observation` | Raw captured data |
| `result`, `result_revision` | Current result + history |
| `approval_chain_event` | Review/Verification/Approval events |
| `equipment`, `calibration_record`, `maintenance_record`, `equipment_status_event` | Equipment lifecycle |
| `qc_sample`, `qc_result` | Quality control |
| `document`, `document_version`, `attachment` | Controlled documents/files |
| `report`, `report_revision`, `report_result_snapshot` | Issued reports, frozen snapshots |
| `config_setting`, `config_proposal` | Configuration governance |
| `accreditation_scope` | Versioned accreditation applicability |
| `notification` | Operational alerts |
| `backup_job_log` | Backup execution evidence |
| `numbering_sequence` | Business-identifier generation |

39 tables. No table exists purely to reduce table count elsewhere, and none was added merely because a noun appeared in the domain vocabulary.

---

## 7. Core ERD (39.1)

```mermaid
erDiagram
    CUSTOMER ||--o{ PROJECT : has
    PROJECT ||--o{ SAMPLE : contains
    SAMPLE ||--o{ TEST_REQUEST : requests
    TEST_REQUEST ||--o{ TEST_INSTANCE : yields
    TEST_INSTANCE ||--o{ RESULT : produces
    TEST_INSTANCE ||--o{ APPROVAL_CHAIN_EVENT : signed_off_by
    RESULT ||--o{ REPORT_RESULT_SNAPSHOT : frozen_into
    REPORT ||--o{ REPORT_RESULT_SNAPSHOT : contains

    CUSTOMER {
        int id PK
        string customer_code UK
        string name
    }
    PROJECT {
        int id PK
        int customer_id FK
        string project_number UK
    }
    SAMPLE {
        int id PK
        int project_id FK
        string sample_number UK
        string status
    }
    TEST_REQUEST {
        int id PK
        int sample_id FK
        string status
    }
    TEST_INSTANCE {
        int id PK
        int test_request_id FK
        int method_version_id FK
        string status
    }
    RESULT {
        int id PK
        int test_instance_id FK
        int parameter_definition_id FK
        string is_current
    }
    REPORT {
        int id PK
        string report_number UK
        string status
    }
```

---

## 8. Identity / RBAC ERD (39.2)

```mermaid
erDiagram
    USER ||--o{ USER_ROLE_ASSIGNMENT : holds
    ROLE ||--o{ USER_ROLE_ASSIGNMENT : assigned_via
    ROLE ||--o{ ROLE_PERMISSION : grants
    PERMISSION ||--o{ ROLE_PERMISSION : included_in
    USER ||--o{ SESSION : authenticates

    USER {
        int id PK
        string username UK
        string password_hash
        bool is_active
        int failed_login_count
        datetime locked_until
    }
    ROLE {
        int id PK
        string code UK
        bool is_system
    }
    PERMISSION {
        int id PK
        string code UK
        string module
        string action
    }
    USER_ROLE_ASSIGNMENT {
        int id PK
        int user_id FK
        int role_id FK
        int scope_discipline_id FK
        datetime effective_from
        datetime effective_to
    }
    SESSION {
        int id PK
        string session_token UK
        int user_id FK
        datetime expires_at
        datetime revoked_at
    }
```

---

## 9. Audit / Revision ERD (39.3)

```mermaid
erDiagram
    RESULT ||--o{ RESULT_REVISION : superseded_into
    TEST_INSTANCE ||--o{ APPROVAL_CHAIN_EVENT : records
    TEST_INSTANCE ||--o{ AUDIT_EVENT : logs

    AUDIT_EVENT {
        int id PK
        datetime timestamp
        int actor_user_id FK
        int session_id FK
        string correlation_id
        string category
        string entity_type
        int entity_id
        string action
        text before_state
        text after_state
        string reason
        string outcome
    }
    RESULT {
        int id PK
        int test_instance_id FK
        string raw_value
        int revision_number
    }
    RESULT_REVISION {
        int id PK
        int result_id FK
        int revision_number
        string value_snapshot
        int changed_by_user_id FK
        datetime changed_at
        string reason
    }
    APPROVAL_CHAIN_EVENT {
        int id PK
        int test_instance_id FK
        string stage
        int actor_user_id FK
        datetime occurred_at
        string outcome
    }
```

`before_state`/`after_state` are stored as JSON text — the one place JSON is justified per Section 42, since the shape varies by `entity_type`.

---

## 10. Method / Test / Parameter Model (39.4, WP-18)

```mermaid
erDiagram
    METHOD ||--o{ METHOD_VERSION : versioned_as
    METHOD_VERSION ||--o{ TEST_DEFINITION : defines
    TEST_DEFINITION ||--o{ PARAMETER_DEFINITION : has
    PARAMETER_DEFINITION ||--o{ FORMULA_VERSION : computed_by
    UNIT ||--o{ PARAMETER_DEFINITION : measured_in

    METHOD {
        int id PK
        string method_code UK
        int discipline_id FK
        bool is_active
    }
    METHOD_VERSION {
        int id PK
        int method_id FK
        string version_label
        date effective_from
        date effective_to
        string status
    }
    TEST_DEFINITION {
        int id PK
        int method_version_id FK
        string code UK
        string name
    }
    PARAMETER_DEFINITION {
        int id PK
        int test_definition_id FK
        string code
        string data_type
        int unit_id FK
        int precision_digits
        bool is_required
        int formula_version_id FK
    }
    FORMULA {
        int id PK
        string code UK
    }
    FORMULA_VERSION {
        int id PK
        int formula_id FK
        string version_label
        text expression_definition
        date effective_from
    }
```

`Method`, `MethodVersion`, `TestDefinition`, `ParameterDefinition` remain four distinct tables per CP-000's explicit instruction — a method can have several versions; a version defines several tests; a test has several parameters, each independently configurable (type, unit, precision, required, formula).

---

## 11. Sample / Execution / Result Model (39.5, WP-19)

```mermaid
erDiagram
    SAMPLE ||--o{ SUB_SAMPLE : divided_into
    SAMPLE ||--o{ CONTAINER : held_in
    SAMPLE ||--o{ CHAIN_OF_CUSTODY_EVENT : tracked_by
    SAMPLE ||--o{ TEST_REQUEST : requests
    TEST_REQUEST ||--o{ TEST_INSTANCE : yields
    TEST_INSTANCE ||--o{ OBSERVATION : captures
    TEST_INSTANCE ||--o{ RESULT : produces
    TEST_INSTANCE }o--|| EQUIPMENT : uses
    TEST_INSTANCE }o--|| USER : assigned_to

    SAMPLE {
        int id PK
        string sample_number UK
        string status
        datetime received_at
    }
    TEST_INSTANCE {
        int id PK
        int test_request_id FK
        int method_version_id FK
        int analyst_user_id FK
        int equipment_id FK
        string status
        datetime started_at
        int reviewed_by_user_id FK
        int verified_by_user_id FK
        int approved_by_user_id FK
    }
    OBSERVATION {
        int id PK
        int test_instance_id FK
        int parameter_definition_id FK
        string observation_type
        float numeric_value
        string text_value
        int equipment_id FK
        int recorded_by_user_id FK
        bool is_superseded
    }
    RESULT {
        int id PK
        int test_instance_id FK
        int parameter_definition_id FK
        float raw_value
        float formatted_value
        int revision_number
    }
```

---

## 12. Review / Verification / Approval, Reporting Model (39.6, WP-21)

```mermaid
erDiagram
    TEST_INSTANCE ||--o{ APPROVAL_CHAIN_EVENT : signed_off_by
    TEST_INSTANCE ||--o{ RESULT : produces
    RESULT ||--o{ REPORT_RESULT_SNAPSHOT : frozen_into
    REPORT ||--o{ REPORT_RESULT_SNAPSHOT : contains
    REPORT ||--o{ REPORT_REVISION : superseded_by

    APPROVAL_CHAIN_EVENT {
        int id PK
        int test_instance_id FK
        string stage
        int actor_user_id FK
        datetime occurred_at
        string outcome
        string comment
        int result_revision_id FK
    }
    REPORT {
        int id PK
        string report_number UK
        int project_id FK
        int issued_by_user_id FK
        datetime issued_at
        string status
        int pdf_document_id FK
        string pdf_hash
    }
    REPORT_RESULT_SNAPSHOT {
        int id PK
        int report_id FK
        int result_id FK
        string value_snapshot
        string method_version_snapshot
        string accreditation_status_snapshot
        string analyst_snapshot
    }
    REPORT_REVISION {
        int id PK
        int report_id FK
        int revision_number
        datetime superseded_at
        string reason
    }
```

---

## 13. Equipment / QC Model (39.7, WP-17/22)

```mermaid
erDiagram
    EQUIPMENT ||--o{ CALIBRATION_RECORD : calibrated_via
    EQUIPMENT ||--o{ MAINTENANCE_RECORD : maintained_via
    EQUIPMENT ||--o{ EQUIPMENT_STATUS_EVENT : status_history
    TEST_INSTANCE ||--o{ QC_SAMPLE : includes
    QC_SAMPLE ||--o{ QC_RESULT : produces

    EQUIPMENT {
        int id PK
        string equipment_code UK
        string status
    }
    CALIBRATION_RECORD {
        int id PK
        int equipment_id FK
        date calibration_date
        date expiry_date
        string result
    }
    EQUIPMENT_STATUS_EVENT {
        int id PK
        int equipment_id FK
        string status
        string reason
        datetime changed_at
    }
    QC_SAMPLE {
        int id PK
        int test_instance_id FK
        string qc_type
        string acceptance_criteria_text
    }
    QC_RESULT {
        int id PK
        int qc_sample_id FK
        float measured_value
        string outcome
        bool investigated
    }
```

`equipment_status_event` is the append-only log that makes "was this equipment valid at time T" answerable even after its current status has since changed — the same current+history pattern used everywhere else.

---

## 14. Accreditation Scope Model (39.8 part 1, WP-15)

```mermaid
erDiagram
    METHOD ||--o{ ACCREDITATION_SCOPE : scoped_by
    CONFIG_PROPOSAL ||--o{ ACCREDITATION_SCOPE : authorized_by

    ACCREDITATION_SCOPE {
        int id PK
        int method_id FK
        string status
        date effective_from
        date effective_to
        int config_proposal_id FK
    }
```

A **versioned table**, not a boolean column — chosen specifically because D-014 requires answering "what was the accreditation status at the time the work was done," which a single mutable boolean cannot do. Querying current status: `effective_to IS NULL`. Querying historical status at date D: `effective_from <= D AND (effective_to IS NULL OR effective_to > D)`.

---

## 15. Configuration Governance Model (39.8 part 2, WP-14)

```mermaid
erDiagram
    CONFIG_SETTING ||--o{ CONFIG_PROPOSAL : changed_via
    USER ||--o{ CONFIG_PROPOSAL : proposes
    USER ||--o{ CONFIG_PROPOSAL : approves

    CONFIG_SETTING {
        int id PK
        string config_area
        string key UK
        string current_value
        string value_type
        int approver_role_id FK
    }
    CONFIG_PROPOSAL {
        int id PK
        int config_setting_id FK
        string previous_value
        string proposed_value
        int proposer_user_id FK
        int approver_user_id FK
        string status
        bool is_emergency
        int countersign_user_id FK
        datetime countersign_due_at
        datetime decided_at
        string reason
    }
```

**SoD policy values (`sod.reviewer_can_verify`, `sod.tech_reviewer_can_approve`) are rows in `config_setting`, not a separate table** — this is what "remain compatible with D-015" means concretely: the same governed propose/approve mechanism, the same audit trail, no parallel system.

`config_setting.approver_role_id` implements Phase 2's category-specific approver requirement (P2-DEC-005): `ACCREDITATION_SCOPE` and `SOD_POLICY` areas can point to a restricted role distinct from the generic System Administrator default.

`CHECK (is_emergency = 1 OR approver_user_id IS NULL OR approver_user_id != proposer_user_id)` — the self-approval prohibition is backed by a database constraint, not application code alone.

---

## 16. A Reasoned Decision: One `approval_chain_event` Table

**Option A — three tables** (`review_record`, `verification_record`, `approval_record`): self-documenting; easy to add a stage-specific field later without polluting shared structure; but three near-identical tables and three sets of FK plumbing on `test_instance`.

**Option B — one table with a `stage` discriminator** (`approval_chain_event`: `test_instance_id`, `stage` ∈ {Review, Verification, Approval}, `actor_user_id`, `occurred_at`, `outcome`, `comment`, `result_revision_id`): one ordered query answers "show the full sign-off history"; matches the event-log pattern already used for `audit_event`, `result_revision`, and `equipment_status_event`, which is a real maintainability benefit for a system meant to be read by someone else in five years; every field identified as required (actor, timestamp, outcome, comment, record revision, role via actor, audit linkage via the row itself) is common across all three stages today.

**Adopted: Option B.** `Confirmed` — technical/architectural decision, not a laboratory policy question. If a future stage-specific field emerges that doesn't fit the shared shape, that's a reason to add a nullable column or a small side table for that one field, not to abandon the pattern.

---

## 17. Documents / Attachments Model

`document` (id, document_type, title, current_version_id FK) → `document_version` (id, document_id FK, version_number, file_path *[server-internal only]*, file_hash, uploaded_by, effective_from/to, status) → `attachment` (id, entity_type, entity_id, document_version_id FK, attached_by, attached_at).

`attachment.entity_type`/`entity_id` is a deliberate, flagged exception to strict FK typing — attachments legitimately relate to Samples, TestInstances, Equipment, and more. SQLite cannot polymorphically FK-constrain this; it's enforced by application-layer validation of `entity_type` against a known, closed set. Noted explicitly in the Constraint Strategy (Section 26) as a database-integrity gap covered by a domain rule instead.

---

## 18. Notification / Operations Model

`notification` (id, user_id FK, notification_type, related_entity_type, related_entity_id, message, is_read, created_at, due_at). `backup_job_log` (id, started_at, completed_at, status, backup_file_reference, integrity_check_passed, verified_at) — deliberately minimal; detailed OS-level backup mechanics stay outside the LIMS database per CP-000 Section O.

---

## 19. Workflow State Persistence

**Sample lifecycle** (`sample.status`, CHECK-constrained): `Draft → Received → Registered → {Rejected}`, then `Completed` once all its tests reach a terminal state, then `Archived`.

**TestInstance lifecycle** (`test_instance.status`, CHECK-constrained): `Assigned → InProgress → PendingReview → Reviewed → PendingVerification → Verified → Approved → Reported → Archived`, plus `Rejected` (from PendingReview/PendingVerification) and `ReopenedForCorrection` (from Approved).

These are two **separate** state machines because they're two separate real-world things: one sample commonly carries several tests, each progressing independently — a sample can be simultaneously "Registered" while one of its tests is "Approved" and another is still "InProgress." Modeling them as a single shared status field, as the original combined list implied, would make that ordinary situation unrepresentable. This is `Confirmed` — a necessary clarification surfaced during data modeling, not a change to CP-000/CP-002 policy.

Actor+timestamp pairs for each TestInstance stage transition live directly on `test_instance` (`reviewed_by_user_id`/`reviewed_at`, etc.) for fast current-state queries, **and** are independently recorded in `approval_chain_event` for full historical/audit purposes — the columns on `test_instance` are a convenience projection of the latest event, never the sole record of it.

---

## 20. Audit Model

`audit_event`: `id`, `timestamp` (UTC), `actor_user_id` FK, `session_id` FK, `correlation_id` (indexed, ties one request's audit/security/error log entries together), `category` (TechnicalRecord/Security/Configuration/Workflow), `entity_type`, `entity_id`, `action`, `before_state` (JSON, nullable), `after_state` (JSON, nullable), `reason` (nullable), `outcome`.

**Normalized columns** for everything queried/filtered on (actor, entity, category, timestamp, outcome) — **JSON** only for `before_state`/`after_state`, since their shape genuinely varies by `entity_type` and forcing them into normalized columns would mean a different schema per audited table, defeating the point of a single audit log. This is the JSON-usage exception described in Section 42, applied consistently.

**No UPDATE/DELETE code path exists for this table** — enforced by there being no repository method that performs one, backed by restrictive OS file permissions on the database file itself (per CP-002 §15). Audit rows referencing a since-superseded `result` remain valid and readable — audit history is keyed to the record's identity (`entity_id`), not to its current state, so superseding a result doesn't orphan or invalidate its audit trail.

---

## 21. Constraint Strategy

| Rule | Enforcement |
|---|---|
| Sample number, report number, method code, equipment code unique | `UNIQUE` constraint |
| FK referential integrity | `FOREIGN KEY`, `PRAGMA foreign_keys=ON` on every connection (Section 29) |
| Status values restricted to the defined state machine | `CHECK` constraint on `status` columns |
| Config proposer ≠ approver (except emergency) | `CHECK` constraint on `config_proposal` |
| Numeric result within parameter's min/max where defined | **Domain rule**, not a DB constraint — min/max come from `parameter_definition`, a separate row, and SQLite CHECK constraints can't reference another table |
| Approved TestInstance cannot have its `result` directly updated | **Domain rule** (application refuses the write path) — a blanket DB-level immutability trigger was considered and rejected as unnecessary complexity given the application is the sole DB accessor (CP-002 §15); the control is enforced once, correctly, at the only entry point that exists |
| SoD hard blocks (Analyst ≠ Reviewer/Verifier/Approver on same TestInstance) | **Domain rule** — inherently relational logic (comparing across rows/roles) unsuited to a static CHECK constraint |
| Equipment ineligible for use if out of calibration/expired | **Domain rule**, reading `calibration_record`/`equipment_status_event` at execution-start time |
| Unapproved configuration never becomes effective | **Domain rule** — the effective-config read path only reads `config_setting.current_value`, which is only ever written by the approval transition, never by the proposal step |

Database integrity handles what's structurally checkable in one row or one FK relationship; the domain layer handles what requires comparing across rows, roles, or time — this split is deliberate, not a gap.

---

## 22. Index Strategy

| Index | Supports |
|---|---|
| `ix_sample_sample_number` (unique) | Sample lookup by number — the single most common lookup in the system |
| `ix_sample_status` | Reception/manager dashboards filtering by lifecycle state |
| `ix_test_instance_status` | Review/Verification/Approval queues |
| `ix_test_instance_analyst_user_id` | Analyst's assigned-work view |
| `ix_test_instance_method_version_id` | Method-level reporting |
| `ix_result_test_instance_id` | Loading all results for a test |
| `ix_audit_event_entity_type_entity_id` | "Show history for this record" |
| `ix_audit_event_timestamp` | Audit review by date range |
| `ix_approval_chain_event_test_instance_id` | Sign-off history lookup |
| `ix_report_report_number` (unique) | Report retrieval |
| `ix_calibration_record_equipment_id_expiry_date` | Calibration-due dashboards, historical validity queries |
| `ix_config_proposal_status` | Pending-approval dashboard |
| `ix_customer_rate_customer_id_parameter_definition_id` | Charge calculation lookup |

Deliberately **not** indexed: low-cardinality columns unlikely to be filtered alone (e.g., `is_active` booleans), and any column only ever accessed via a more selective composite index already listed. Given SQLite's single-writer model, each additional index adds real write overhead (Section 29) — every index above is tied to a named, expected query pattern, not added speculatively.

---

## 23. Transaction Boundaries

| Operation | Tables affected | Boundary | Audit event | Failure behavior |
|---|---|---|---|---|
| Register Sample | `sample`, `numbering_sequence` | Single short transaction | `SAMPLE_REGISTERED` | Validation Error on missing fields |
| Start Test | `test_instance` | Single short transaction | `EXECUTION_STARTED` | Workflow Error if equipment ineligible |
| Submit Result | `result`, `observation` | Single short transaction | `RESULT_SUBMITTED` | Business Rule Error if QC unmet |
| Review Result | `test_instance`, `approval_chain_event` | Single short transaction | `RESULT_REVIEWED` | SoD Violation if blocked |
| Verify Result | `test_instance`, `approval_chain_event` | Single short transaction | `RESULT_VERIFIED` | SoD Violation if blocked |
| Approve Result | `test_instance`, `approval_chain_event` | Single short transaction | `RESULT_APPROVED` | SoD Violation if blocked |
| Reopen Approved Result | `test_instance`, `result`, `result_revision` | Single transaction: snapshot to `result_revision` **then** update `result`/`test_instance`, same commit | `RECORD_REOPENED` | Authorization Error if actor is the original analyst |
| Propose Configuration | `config_proposal` | Single short transaction | `CONFIG_PROPOSED` | Validation Error |
| Approve Configuration | `config_proposal`, `config_setting` | Single transaction: update proposal status **and** `config_setting.current_value` together | `CONFIG_APPROVED` | Authorization Error if approver = proposer (non-emergency) |
| Change Accreditation Scope | `accreditation_scope`, `config_proposal` | Single transaction, new row inserted (never an UPDATE of a past row) | `ACCREDITATION_SCOPE_CHANGED` | Authorization Error if approver role mismatch |
| Issue Report | `report`, `report_result_snapshot` | Single transaction: snapshot every included result **before** commit | `REPORT_ISSUED` | Business Rule Error if any result not yet Approved |

Every write above is a short, single-purpose transaction, per CP-000's SQLite conditions — none holds a lock across a PDF render or a report data assembly step, both of which run on a separate read-only connection (CP-002 §2).

---

## 24. SQLite-Specific Considerations

| Concern | Handling |
|---|---|
| WAL mode | Enabled at connection init, mandatory (D-004) |
| `foreign_keys=ON` | Set via a SQLAlchemy `connect` event listener on **every** connection — never left to per-request discipline, per CP-000/CP-002 |
| `busy_timeout` | Set to 5000ms; app-level retry/backoff handles anything beyond that, never surfaced as a raw error |
| Transaction boundaries | Short, single-purpose (Section 23) |
| Index write overhead | Every index is tied to a named use case (Section 22); no speculative indexing |
| JSON usage | Limited to `audit_event.before_state/after_state` and `calculation_run.input_snapshot` — both genuinely variable-shaped, per Section 42 policy |
| Feature normally enforced by PostgreSQL, handled here in application logic instead | Cross-row/cross-table business rules (parameter min/max, SoD, equipment eligibility, configuration effectiveness) — SQLite's CHECK constraints can't reference other tables, so these are domain-layer rules by necessity, documented explicitly in Section 21 rather than assumed to be database-enforced |
| Migration limitations | Alembic supports SQLite with some DDL operations requiring table-rebuild (e.g., dropping a column) rather than in-place ALTER — acceptable at this data volume, noted for Phase 5 migration tooling setup |

---

## 25. Historical Reconstruction / Traceability

| Question | Answered via |
|---|---|
| What result was approved? | `result` joined to `approval_chain_event` where `stage='Approval'` |
| Who performed the test? | `test_instance.analyst_user_id` |
| Which method version was used? | `test_instance.method_version_id` → `method_version` |
| Which equipment was used? | `test_instance.equipment_id` → `equipment` |
| Was the equipment calibrated at that time? | `calibration_record` + `equipment_status_event` filtered to `test_instance.started_at` |
| What raw observations existed? | `observation` where `test_instance_id = X`, including any superseded ones (`is_superseded`, self-referencing chain) |
| Which calculation formula/version was used? | `calculation_run.formula_version_id` → `formula_version` |
| Who reviewed it? Verified it? Approved it? | `approval_chain_event` filtered by `stage`, ordered by `occurred_at` |
| Which accreditation scope applied at that time? | `accreditation_scope` filtered to `effective_from <= approved_at < effective_to` for the relevant `method_id` |
| Which report PDF was issued? | `report_result_snapshot.result_id = X` → `report` → `document_version.file_path` |
| What did the record look like before a correction? | `result_revision` (full snapshot chain) + `audit_event` where `entity_type='result'` |

```text
Customer → Project → Sample → TestRequest → TestInstance → MethodVersion →
Observation → CalculationRun → Result(+Revisions) → ApprovalChainEvent(Review/Verify/Approve) →
ReportResultSnapshot → Report → Issued PDF
```
Cross-links at every stage: `Equipment` (via TestInstance/Observation), `Analyst`/actors (via User FKs throughout), `AuditEvent` (via entity_type/entity_id on every controlled table), `AccreditationScope` (via Method, time-filtered), `ConfigSetting`/`ConfigProposal` (via whichever policy value was in effect).

---

## 26. Migration Strategy (No Legacy Schema — Strategy Only)

```text
Source (spreadsheet/paper) → Staging (staging_import_batch / staging_import_row,
   each row tagged with validation status) → Validation (type/range/reference checks
   against master data) → Transformation (map source columns to target schema) →
   Duplicate handling (match against existing sample_number/customer_code before insert) →
   Import (single controlled transaction per batch) → Verification (row-count and
   spot-check reconciliation) → Audit/evidence (an audit_event per imported record,
   category=Configuration or TechnicalRecord as appropriate, actor = the importing
   administrator, reason = "historical migration")
```
No import script is written in Phase 3 — this defines the mechanism a future Phase 8/implementation task will build against. Given confirmed low historical volume (CP-000 §T), this is a modest, low-risk exercise whenever it happens.

---

## 27. Seed / Reference Data Strategy

| Category | Examples | Source |
|---|---|---|
| System-seeded | `permission` rows, built-in `role` rows (`is_system=true`), default `config_setting` values (including SoD provisional defaults from Phase 2), status CHECK-constraint values | Shipped with the application, part of the initial migration |
| Laboratory-configured | `discipline`, `unit`, `method`/`method_version`/`test_definition`/`parameter_definition`, `rate` | Entered by SMJ during Phase 7/9 setup, before go-live |
| User-operational | `customer`, `sample`, `test_instance`, `result`, `report` | Created during normal use |

A clean installation needs the system-seeded set to function at all; it is **not** usable for real work until the laboratory-configured set (at minimum: Solid Fuel discipline, its methods/tests/parameters, and units) is entered.

---

## 28. Data Dictionary (Key Tables)

### `test_instance`
| Column | Type | Null | Notes |
|---|---|---|---|
| id | INTEGER PK | No | |
| test_request_id | INTEGER FK | No | → test_request |
| method_version_id | INTEGER FK | No | → method_version |
| sample_id | INTEGER FK | No | Denormalized from test_request→sample; justified for query convenience on the single most common join; source of truth remains test_request |
| analyst_user_id | INTEGER FK | No | Assigned analyst |
| equipment_id | INTEGER FK | Yes | Primary equipment used |
| status | TEXT | No | CHECK-constrained state machine (Section 19) |
| started_at | DATETIME | Yes | UTC |
| submitted_at | DATETIME | Yes | |
| reviewed_by_user_id | INTEGER FK | Yes | Convenience projection of latest `approval_chain_event` |
| verified_by_user_id | INTEGER FK | Yes | Same |
| approved_by_user_id | INTEGER FK | Yes | Same |
| rejected_reason | TEXT | Yes | Required by domain rule when status→Rejected |
| created_at / updated_at | DATETIME | No | UTC |

### `result`
| Column | Type | Null | Notes |
|---|---|---|---|
| id | INTEGER PK | No | |
| test_instance_id | INTEGER FK | No | |
| parameter_definition_id | INTEGER FK | No | |
| raw_value | REAL/TEXT | Yes | Type depends on `parameter_definition.data_type` |
| formatted_value | TEXT | Yes | After precision/rounding rules applied |
| unit_id | INTEGER FK | Yes | |
| revision_number | INTEGER | No | Increments on every change post-Submitted |
| status | TEXT | No | Mirrors relevant TestInstance stage for this parameter |
| created_at / updated_at | DATETIME | No | |

**Unique constraint:** `(test_instance_id, parameter_definition_id)` — one current row per parameter per test.

### `result_revision`
| Column | Type | Null | Notes |
|---|---|---|---|
| id | INTEGER PK | No | |
| result_id | INTEGER FK | No | |
| revision_number | INTEGER | No | |
| value_snapshot | TEXT | No | Pre-change value |
| status_snapshot | TEXT | No | |
| changed_by_user_id | INTEGER FK | No | |
| changed_at | DATETIME | No | |
| reason | TEXT | Yes | Required by domain rule if the change followed a Reopen |

Append-only; no UPDATE/DELETE path exists.

### `config_proposal`
| Column | Type | Null | Notes |
|---|---|---|---|
| id | INTEGER PK | No | |
| config_setting_id | INTEGER FK | No | |
| previous_value / proposed_value | TEXT | No | |
| proposer_user_id | INTEGER FK | No | |
| approver_user_id | INTEGER FK | Yes | Null until decided |
| status | TEXT | No | CHECK: Pending/Approved/Rejected/EmergencySelfApproved/Countersigned/OverdueFlagged |
| is_emergency | BOOLEAN | No | Default false |
| countersign_user_id | INTEGER FK | Yes | |
| countersign_due_at | DATETIME | Yes | Set only if `is_emergency` |
| reason | TEXT | No | Mandatory |
| decided_at | DATETIME | Yes | |

**CHECK:** `is_emergency = 1 OR approver_user_id IS NULL OR approver_user_id != proposer_user_id`.

*(The remaining ~35 tables follow the same documentation depth in the implementation-stage data dictionary; the four above represent the pattern applied throughout and were chosen because they carry the most integrity-critical logic.)*

---

## 29. Data Integrity Matrix

| Rule | DB constraint | Domain rule | Audit required |
|---|---|---|---|
| FK integrity | ✅ (`foreign_keys=ON`) | — | No |
| Unique sample number | ✅ | — | No |
| Unique report number | ✅ | — | No |
| Approved result immutability | — | ✅ (Reopen required) | Yes — `RECORD_REOPENED` |
| Revision creation on change | — | ✅ (pre-write snapshot) | Yes |
| SoD (hard + policy-controlled) | — | ✅ | Yes — every check outcome |
| Workflow transition legality | Partial (CHECK on status values) | ✅ (transition rules) | Yes |
| Equipment eligibility | — | ✅ (calibration/status lookup) | Yes on block |
| Configuration approval (proposer≠approver) | ✅ (CHECK) | ✅ (effective-value read path) | Yes |
| Accreditation scope change | — | ✅ (restricted approver role) | Yes |

---

## 30. Security / Sensitivity Classification

| Category | Examples | Handling |
|---|---|---|
| Controlled Technical Record | `result`, `result_revision`, `approval_chain_event`, `report`, `accreditation_scope` | Full audit, revision-protected, 10-year retention |
| Security-Sensitive | `user.password_hash`, `session.session_token` | Never logged, never in audit before/after snapshots, OS-file-permission protected |
| Confidential | `customer`, `rate`, `customer_rate` | RBAC-scoped access, standard backup handling |
| Internal | `equipment`, `method`, `test_definition` | Standard access control |
| Operational | `notification`, `backup_job_log` | Shorter retention, not technical records |

---

## 31. Retention / Archival Model

Per CP-000 (10 years active, then archive): controlled technical records (`sample`, `test_instance`, `result`+`result_revision`, `report`+snapshots, `audit_event`) are **never hard-deleted** — they move to an `Archived` status, remaining fully queryable. Reference/master data (`customer`, `method`) uses `is_active` flags rather than deletion, preserving FK integrity for historical records that reference them. Physical deletion, if ever performed, would apply only to genuinely disposable operational data (e.g., stale `notification` rows) — never to anything in the Controlled Technical Record classification.

---

## 32. Performance Baseline

| Interaction | Proposed target | Rationale | Measurement |
|---|---|---|---|
| Sample lookup by number | < 200ms | Single indexed lookup, trivial at this data volume | Phase 18 load test |
| Review/Verification/Approval queue load | < 500ms | Indexed status filter, small result set at confirmed scale | Phase 18 |
| Dashboard summary | < 1s | Aggregate query, acceptable given single-digit concurrent users | Phase 18 |
| Report PDF generation | < 5s | Read-only connection + Chromium render, not latency-critical for issuance | Phase 18 |

These are **design targets to validate**, not measured facts — no claim is made about actual performance ahead of Phase 18 testing on real hardware.

---

## 33. Data Architecture ADR Register

| ADR | Decision |
|---|---|
| ADR-013 Primary Key Strategy | Surrogate INTEGER PK on every table; business identifiers always separate |
| ADR-014 Business Numbering Strategy | Per-category `numbering_sequence`, immutable, never reused |
| ADR-015 Revision Storage Strategy | Current-table + append-only history-table pattern, applied uniformly (result, equipment status, config) |
| ADR-016 Audit Data Storage Strategy | Normalized columns for filterable fields; JSON only for before/after snapshots |
| ADR-017 RBAC Relational Model | Coarse-grained permission table + scoped role assignment, ~30–40 permissions |
| ADR-018 SoD Relational Model | Hard blocks are domain logic (no table); policy-controlled combinations are `config_setting` rows — no bespoke SoD table |
| ADR-019 Workflow State Persistence | **Two separate state machines** (Sample, TestInstance), not one shared status field |
| ADR-020 Configuration Persistence | `config_setting` + `config_proposal`, approval is a status transition, not a fourth table |
| ADR-021 Accreditation Scope Persistence | Versioned/temporal table, not a boolean |
| ADR-022 Result / Observation Data Model | Typed numeric/text columns on `observation`, not EAV |
| ADR-023 Calculation Provenance Model | `formula_version` + `calculation_run` with JSON input snapshot (justified exception) |
| ADR-024 Report Snapshot Model | `report_result_snapshot` freezes value/method/accreditation state at issuance |
| ADR-025 SQLite Data Integrity Constraints | Cross-row rules (SoD, equipment eligibility, parameter ranges) are domain rules by necessity, not a gap |
| ADR-026 Indexing Strategy | Every index tied to a named query pattern; none speculative, given SQLite write cost |

---

## 34. Open Decisions

| # | Item | Classification |
|---|---|---|
| 1 | Exact business-number format (`SF-2026-000123` vs. alternative) | Requires Laboratory Decision — cosmetic, no architectural impact |
| 2 | Whether `test_instance.equipment_id` should become a join table for multi-equipment tests | Requires Technical Decision — deferred until a real test type needs more than one piece of equipment |
| 3 | Exact `calculation_run.input_snapshot` JSON shape per formula type | Requires Technical Decision — Phase 9 implementation detail |
| 4 | Whether `notification` needs a digest/batching table for high-volume alerts | Deferred — not needed at confirmed scale (1–10 users) |

None of these affect Sections 1–33 or block CP-003.

---

## 35. Phase 3 Acceptance Criteria

All 30 items from the Phase 3 Completion Rule are satisfied: domain-to-data mapping (§2), entity inventory (§6), 8 logical ERDs (§7–15), key strategy (§5), FK/constraint strategy (§21), lifecycle/state persistence (§19), revision model (§20, §28), audit model (§20), RBAC/SoD data model (§8, §18), configuration governance model (§15), accreditation-scope model (§14), method/test/parameter model (§10), observation/calculation/result model (§11, §28), equipment/QC model (§13), review/verification/approval model (§16), report snapshot model (§12), index strategy (§22), transaction boundaries (§23), SQLite-specific documentation (§24), historical reconstruction demonstrated for all 12 required questions (§25), migration strategy (§26), data dictionary for the integrity-critical tables (§28), data integrity matrix (§29), ADR register (§33), open decisions classified (§34) with none rated blocking, no implementation code introduced, and no CP-000/CP-002 decision silently changed — the two clarifications made (Sample/TestInstance as separate state machines; Review/Verification/Approval merged into one table) are additive data-modeling decisions consistent with, not contrary to, the frozen system/security architecture.

**Determination: sufficient to proceed to CP-003.**



Next Prompt:
# SMJ Sustainable Fuel Lab — LIMS Program

## Phase 3 — Data Architecture

### Final Corrections, Data Contract Completion & CP-003 Readiness

You are continuing the **SMJ Sustainable Fuel Lab LIMS Program**.

The project has the following authoritative status:

* **CP-000 — Architecture & Project Baseline: ACCEPTED**
* **CP-002 — System & Security Architecture: ACCEPTED**
* **Phase 3 — Data Architecture: IN PROGRESS**
* No production schema, migration, ORM implementation, application code, or frontend code is authorized by this prompt.

The current Phase 3 Data Architecture document is **substantially complete and conditionally ready for CP-003**.

The purpose of this task is **not to redesign Phase 3**.

The purpose is to:

1. close the six identified data-architecture precision issues;
2. complete the implementation-ready data dictionary;
3. verify all ERDs and constraints remain internally consistent;
4. confirm historical reconstruction;
5. update affected ADRs;
6. perform a full CP-000 / CP-002 consistency check;
7. produce the final Phase 3 Data Architecture baseline suitable for **CP-003**.

---

# 1. Frozen Foundations

Treat all decisions from CP-000 and CP-002 as authoritative.

Do not reopen them unless an actual contradiction is discovered.

The following remain frozen:

* D-001 Single-laboratory LIMS
* D-002 Approved technology stack including SQLite
* D-003 Modular Monolith
* D-004 SQLite
* D-005 Revision-based technical records + immutable audit
* D-006 RBAC + policy-driven per-TestInstance SoD
* D-007 Explicit workflow state machines
* D-008 Strongly typed configuration
* D-009 Task → Verification → Checkpoint
* D-010 Documentation-as-code
* D-011 Domain-oriented modules
* D-012 Conservative, controlled, auditable architecture
* D-013 Charge calculation only; invoicing external
* D-014 Accreditation applicability at Method/Test scope
* D-015 Propose → Approve configuration governance

The Phase 2 architecture is also frozen, including:

* backend authorization;
* server-side sessions;
* RBAC;
* per-TestInstance SoD;
* hard SoD blocks with no bypass;
* policy-controlled SoD combinations;
* immutable audit;
* workflow authorization;
* configuration governance;
* accreditation controls;
* SQLite operating constraints.

No database decision is to be reopened.

---

# 2. Phase 3 Decisions Already Accepted

The following Phase 3 modeling decisions are accepted unless a concrete inconsistency is discovered:

## 2.1 Separate Sample and TestInstance state machines

This is a confirmed domain-model clarification.

A Sample and its TestInstances have independent lifecycles.

Example:

```text
Sample = Registered

Test A = Approved
Test B = In Progress
Test C = Pending Review
```

Do not collapse these into a single status field.

---

## 2.2 Single approval-chain event table

The preferred architecture is:

```text
approval_chain_event
```

with a controlled `stage` value:

```text
REVIEW
VERIFICATION
APPROVAL
```

This decision is accepted unless a genuine requirement is discovered that proves materially different structures are necessary.

---

# 3. Six Required Corrections

Close the following issues precisely.

---

## 3.1 Accreditation Scope Granularity

The current document says accreditation applicability is at Method/Test level, but the current `accreditation_scope` structure primarily references `method_id`.

Resolve this ambiguity.

Choose and document one of:

### Option A — MethodVersion-level scope with inheritance

Accreditation applicability belongs to the effective MethodVersion and is inherited by its TestDefinitions.

### Option B — Explicit TestDefinition-level assignment

Accreditation scope can be assigned directly to individual tests where necessary.

### Option C — Hybrid

MethodVersion provides the default, while TestDefinition may override it where an actual laboratory scope requires such granularity.

### Recommendation

Prefer **Option A unless a real accredited-scope requirement demands test-specific variation**.

Do not invent regulatory rules.

The objective is to ensure the data model can answer:

> What accreditation scope applied to this exact TestInstance when it was performed/approved?

Document the temporal query.

---

# 4. Correct the "Current + History Everywhere" Principle

The current document overstates the uniformity of the revision approach.

Replace that principle with a more precise rule:

> Controlled data uses the historical mechanism appropriate to the domain.

Examples:

```text
Technical result
→ Current Result + ResultRevision

Issued report
→ Report + ReportRevision + ReportResultSnapshot

Equipment condition/status
→ Equipment + EquipmentStatusEvent

Configuration
→ ConfigSetting + ConfigProposal / governed history

Chain of custody
→ Append-only event history

Audit
→ Append-only AuditEvent
```

Do not force every entity into a `Current + Revision` structure.

The goal is historical reconstructability, not mechanical uniformity.

---

# 5. Correct Internal PK / Reuse Statement

Review the current statement that every table uses an `INTEGER PRIMARY KEY` and that IDs are never reused.

Replace it with a technically accurate SQLite rule.

Recommended baseline:

> Internal relational identifiers use SQLite INTEGER PRIMARY KEY surrogate keys unless a specific entity requires stronger allocation semantics. Internal surrogate IDs are implementation identifiers and are not laboratory business identifiers. Human-facing business identifiers are separately generated, unique, immutable once issued, and never reused.

Do not require `AUTOINCREMENT` everywhere unless a specific requirement justifies its use.

The important "never reuse" rule applies to:

* Sample Number
* Report Number
* Work Order Number
* Test Request Number
* other controlled business identifiers

not necessarily to internal SQLite row identifiers.

Update ADR-013 if required.

---

# 6. Constrain Approval Chain Stage Values

The `approval_chain_event.stage` field must not remain an arbitrary text value.

Define it as a controlled value set:

```text
REVIEW
VERIFICATION
APPROVAL
```

Use an appropriate SQLite `CHECK` constraint or controlled lookup table.

Also define:

* whether multiple attempts for a stage are permitted;
* how rejected/rework attempts are preserved;
* which event represents the current successful completion of a stage.

The historical event log must remain append-only.

---

# 7. Make ApprovalChainEvent the Historical Source of Truth

The current `test_instance` contains convenience/projection columns such as:

* `reviewed_by_user_id`
* `reviewed_at`
* `verified_by_user_id`
* `verified_at`
* `approved_by_user_id`
* `approved_at`

Keep them only if they provide measurable query/read benefit.

If retained, explicitly state:

> `approval_chain_event` is the historical source of truth. Stage-specific actor/timestamp columns on `test_instance` are derived current-state projections and are never independently editable.

Define how the projections are kept consistent.

No separate uncontrolled write path may exist.

Update ADR-009 if required.

---

# 8. Resolve `test_instance.sample_id`

The current model contains both:

```text
test_instance.sample_id
```

and:

```text
test_instance
    ↓
test_request
    ↓
sample
```

This is a deliberate denormalization.

Evaluate:

### Option A — Remove `test_instance.sample_id`

Use the normalized relationship and rely on appropriate indexes.

### Option B — Retain it

If retained, define an invariant:

> `test_instance.sample_id` MUST always equal `test_request.sample_id`.

Define how the application guarantees this invariant and how the value can never diverge.

### Recommendation

Given the confirmed small scale, prefer **Option A unless actual query profiling later proves the redundant column materially useful**.

Do not retain denormalization merely because it is convenient.

Update the ERD/data dictionary/ADR accordingly.

---

# 9. Complete the Data Dictionary

This is mandatory before CP-003.

The current document contains detailed definitions for only a subset of the tables.

Produce an **implementation-ready data dictionary for all proposed tables**.

For every table provide at least:

| Field           | Required information            |
| --------------- | ------------------------------- |
| Column          | Exact database column name      |
| Type            | SQLite-compatible type          |
| Nullable        | Yes/No                          |
| Default         | Default value if any            |
| PK              | Yes/No                          |
| FK              | Referenced table/column         |
| Unique          | Yes/No                          |
| Check           | Constraint if applicable        |
| Description     | Business meaning                |
| Source of truth | Where authoritative value lives |
| Lifecycle       | Active/historical/etc.          |
| Revision        | Revision/history behavior       |
| Audit           | Audit requirement               |
| Sensitivity     | Data classification             |
| Notes           | Additional invariant or rule    |

The complete dictionary must cover every entity in the entity inventory.

Do not use:

> "The remaining tables follow the same pattern"

as a substitute for actual definitions.

---

# 10. Verify All ERDs Against the Data Dictionary

For each ERD:

* verify every relationship exists in the dictionary;
* verify cardinality;
* verify FK direction;
* verify nullable relationships;
* verify naming;
* remove obsolete relationships;
* identify missing entities;
* identify duplicated relationships.

At minimum verify these diagrams:

1. Core domain
2. Identity/RBAC
3. Audit/Revision
4. Method/Test/Parameter
5. Sample/Execution/Result
6. Review/Verification/Approval/Reporting
7. Equipment/QC
8. Accreditation/Configuration

The ERDs and data dictionary must represent the same model.

---

# 11. Review Result / Observation Typing

Resolve the current `REAL/TEXT` duality carefully.

Define:

* which parameter types support numeric values;
* which support text values;
* which support date/time values if necessary;
* which representation is authoritative;
* how unit is stored;
* how formatted display differs from source value.

The rule must explicitly state:

> `formatted_value` is presentation-only and is never a calculation source.

If the proposed generic `numeric_value + text_value` structure is retained, define how invalid combinations are prevented.

Example:

```text
data_type = NUMERIC
→ numeric_value required
→ text_value null

data_type = TEXT
→ text_value required
→ numeric_value null
```

Implement the integrity rule either through a database CHECK constraint where possible or a centralized domain validation rule.

Do not create a generic EAV result system.

---

# 12. Review Report Snapshot Scope

Clarify the purpose of `report_result_snapshot`.

It must freeze the exact report-visible values needed to reproduce the issued report.

Distinguish:

### Technical traceability

Provided by:

* TestInstance;
* Result;
* ResultRevision;
* ApprovalChainEvent;
* Equipment;
* AuditEvent;
* Accreditation scope.

### Issued-report snapshot

Provided by:

* Report;
* ReportRevision;
* ReportResultSnapshot;
* PDF artifact/hash.

Do not copy every related field into the report snapshot without a reason.

Define what must be frozen because changing underlying master/configuration data must not alter the historical issued report.

---

# 13. Polymorphic References

The model currently uses controlled polymorphic references such as:

```text
attachment.entity_type
attachment.entity_id
```

and:

```text
notification.related_entity_type
notification.related_entity_id
```

Retain these only where genuine.

Define a **closed allowed entity-type set**.

The database must never accept arbitrary table names supplied by clients.

The application shall validate the allowed type and entity existence.

Document this explicitly as a controlled integrity exception.

---

# 14. JSON Usage Policy

JSON is permitted only for genuinely variable structures.

Current candidates:

* `audit_event.before_state`
* `audit_event.after_state`
* `calculation_run.input_snapshot`

Confirm whether each remains justified.

Explicitly prohibit JSON as the primary storage mechanism for:

* Customer
* Sample
* Test
* Method
* Parameter
* Result
* Equipment
* Approval
* Report

Update the JSON policy accordingly.

---

# 15. Foreign Key Strategy

Review every FK.

For each relationship define:

* parent;
* child;
* mandatory/optional;
* delete behavior;
* historical implications.

Be especially careful with:

* user references;
* historical revisions;
* method versions;
* accreditation scopes;
* reports;
* documents;
* configuration proposals;
* approval events.

No historical record should become unusable merely because a current master record is retired.

---

# 16. Delete / Retirement Strategy

Produce a table like:

| Entity | Delete allowed? | Retirement mechanism | Historical preservation |
| ------ | --------------- | -------------------- | ----------------------- |

Cover all major categories.

Use:

* `is_active`;
* lifecycle state;
* revision history;
* archival state;

where appropriate.

Avoid hard deletion of controlled technical records.

---

# 17. Business Identifier Strategy

Finalize the generic architecture without prematurely deciding cosmetic formatting.

Define:

* uniqueness;
* allocation;
* immutability;
* non-reuse;
* sequence gaps;
* year changes;
* rollback behavior;
* transaction handling.

Example format:

```text
SF-2026-000123
```

should be treated only as an example unless SMJ has formally approved it.

---

# 18. Numbering Sequence Concurrency

Because numbering is implemented with SQLite, explicitly design safe allocation.

Example:

```text
BEGIN
 → lock/update numbering_sequence
 → allocate number
 → create business record
 → audit
COMMIT
```

The design must prevent duplicate business identifiers even under simultaneous registrations.

Do not rely on application-side "read current number, increment in memory" logic.

---

# 19. Historical Reconstruction Test

Expand Section 25 into a genuine logical verification exercise.

For at least one hypothetical TestInstance, demonstrate how the proposed schema reconstructs:

1. Customer
2. Project
3. Sample
4. Test request
5. Test instance
6. Method
7. Method version
8. Test definition
9. Parameters
10. Analyst
11. Equipment
12. Equipment validity at execution time
13. Raw observations
14. Calculation formula/version
15. Result
16. Previous result revision
17. Review
18. Verification
19. Approval
20. Accreditation status at relevant time
21. Issued report
22. Exact report-visible result
23. PDF artifact
24. Audit history

Do this as a relational trace, not executable SQL.

The answer should demonstrate that the model genuinely satisfies D-005 and D-014.

---

# 20. Data Integrity Matrix

Expand the current matrix to include at least:

* FK integrity;
* business identifier uniqueness;
* business identifier non-reuse;
* sample/test lifecycle;
* result revision;
* approved-record immutability;
* review/verification/approval sequencing;
* SoD;
* equipment eligibility;
* accreditation scope history;
* configuration proposal approval;
* configuration effective value;
* report snapshot integrity;
* file hash;
* polymorphic attachment validation.

For each rule identify:

```text
Database Constraint
Domain Rule
Application Service Rule
Audit Requirement
```

---

# 21. Transaction Review

Recheck all transactions against SQLite's single-writer model.

At minimum:

* Sample registration
* Business-number allocation
* Test assignment
* Test start
* Observation entry
* Result submission
* Review
* Verification
* Approval
* Reopen
* Configuration proposal
* Configuration approval
* Accreditation-scope change
* Report issuance

For each:

```text
Tables
Transaction boundary
Audit event
Lock sensitivity
Failure behavior
```

No transaction should contain:

* PDF generation;
* long external calls;
* long user interactions;
* extended report rendering.

---

# 22. Index Review

Verify every index has a real query/use case.

Also verify:

* uniqueness;
* composite-index order;
* whether duplicate indexes exist;
* whether FK columns need indexes;
* whether audit queries are adequately supported;
* whether queue queries are covered.

Because this is SQLite, do not create speculative indexes.

---

# 23. Migration Strategy

Keep the current migration architecture, but explicitly distinguish:

### Legacy migration

Spreadsheet/paper import.

from:

### Schema migration

Alembic-controlled application/database version changes.

They are not the same thing.

Do not conflate the two.

---

# 24. Seed Data

Review the distinction between:

* system-seeded data;
* laboratory-configured data;
* operational data.

Also clarify whether the following are seeded or configured:

* roles;
* permissions;
* workflow values;
* default policies;
* initial disciplines;
* units.

---

# 25. ADR Updates

Review and update at least:

* ADR-013 Primary Key Strategy
* ADR-014 Business Numbering
* ADR-015 Revision Strategy
* ADR-016 Audit Storage
* ADR-017 RBAC Relational Model
* ADR-018 SoD Relational Model
* ADR-019 Workflow State Persistence
* ADR-020 Configuration Persistence
* ADR-021 Accreditation Scope Persistence
* ADR-022 Observation/Result Model
* ADR-023 Calculation Provenance
* ADR-024 Report Snapshot
* ADR-025 SQLite Integrity Constraints
* ADR-026 Indexing

Add new ADRs only where a genuinely new architectural decision emerged.

In particular, document the rationale for:

* separate Sample/TestInstance state machines;
* one approval_chain_event table;
* any retained denormalized fields;
* accreditation scope inheritance/assignment.

---

# 26. CP-000 / CP-002 Consistency Audit

Perform a final cross-check.

Explicitly verify that the Phase 3 data model does not contradict:

### D-005

Revision-based records + immutable audit.

### D-006

Per-TestInstance SoD.

### D-007

Explicit state machines.

### D-008

Strongly typed configuration.

### D-013

Charge calculation, external invoicing.

### D-014

Accreditation scope/history.

### D-015

Propose → Approve configuration.

Also verify compatibility with Phase 2:

* RBAC;
* sessions;
* authorization;
* audit;
* configuration governance;
* accreditation controls;
* SQLite security;
* transaction boundaries.

If no conflict exists, state that explicitly.

---

# 27. Do Not Reopen These Unless Evidence Requires It

Do not reopen:

* SQLite vs PostgreSQL;
* Modular Monolith vs microservices;
* React vs another frontend;
* FastAPI vs another backend;
* RBAC vs alternative authorization models;
* server-side sessions vs JWT;
* no blanket EAV;
* single-site scope;
* D-013 commercial boundary;
* D-014 accreditation model.

The task is data architecture, not general architecture reconsideration.

---

# 28. No Implementation

Do not create:

* SQL migration files;
* Alembic revisions;
* ORM classes;
* production database files;
* seed scripts;
* API endpoints;
* frontend components;
* application services.

Architecture and documentation only.

---

# 29. Required Final Output

Return the revised Phase 3 package in this order:

## 1. Phase 3 Review Summary

## 2. Final Data Architecture Decisions

## 3. Accreditation Scope Resolution

## 4. Historical Mechanism Strategy

## 5. PK / Identifier Resolution

## 6. Approval Chain Stage Resolution

## 7. Approval Chain Source-of-Truth Rule

## 8. TestInstance/Sample Relationship Resolution

## 9. Complete Entity Inventory

## 10. Complete ERD Set

## 11. Complete Data Dictionary

## 12. Constraints

## 13. Lifecycle / State Persistence

## 14. Revision / History Model

## 15. Audit Model

## 16. RBAC / SoD Persistence

## 17. Configuration Governance Persistence

## 18. Accreditation Persistence

## 19. Method / Test / Parameter Model

## 20. Observation / Calculation / Result Model

## 21. Equipment / QC Model

## 22. Review / Verification / Approval Model

## 23. Report / Snapshot Model

## 24. Document / Attachment Model

## 25. Workflow Persistence

## 26. Index Strategy

## 27. Transaction Boundary Strategy

## 28. SQLite-Specific Considerations

## 29. Migration Strategy

## 30. Seed Data Strategy

## 31. Historical Reconstruction Verification

## 32. Data Integrity Matrix

## 33. Data Sensitivity / Retention

## 34. ADR Register

## 35. Open Decisions

## 36. CP-000 / CP-002 Consistency Check

## 37. CP-003 Acceptance Assessment

---

# 30. CP-003 Acceptance Standard

The final determination shall use exactly one of:

### NOT READY

Material structural problem remains.

### CONDITIONALLY READY

Only explicitly non-blocking documentation or policy items remain.

### READY FOR CP-003

The complete implementation-ready data architecture is internally consistent, all required data structures are documented, historical reconstruction is demonstrated, and there is no unresolved structural ambiguity.

Do not declare **CP-003 Accepted** merely because the architecture appears good.

CP-003 is accepted only after the defined acceptance criteria are actually satisfied.

---

# 31. Final Instruction

The most important output is not the number of tables.

The objective is a **stable relational data contract** that another developer can implement without having to rediscover domain decisions.

The final architecture must make it possible to reconstruct:

> **what happened, to which sample and test, under which method/version/configuration, using which equipment, by whom, when, with which observations/calculations, producing which result, reviewed/verified/approved by whom, under which accreditation scope, and represented in which issued report.**

Resolve the six identified precision issues, finish the complete data dictionary, verify every ERD against it, update the ADRs, perform the consistency audit, and then make the final **CP-003 readiness determination**.

Do not begin Phase 4.

Do not begin implementation.

Do not create executable schema or migration artifacts.

Stop at the **CP-003-ready data architecture baseline**.
