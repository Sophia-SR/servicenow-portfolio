# ServiceNow Daily Labs Configuration Package

## What This Is

A comprehensive ServiceNow configuration package containing workflows, business rules, custom tables, and service catalog components developed during daily lab exercises. The focus was on building practical automation for incident management and asset recovery processes.

This isn't just random lab work—everything here addresses real operational scenarios you'd encounter in production ServiceNow environments.

## What I Built

I developed end-to-end automation covering incident workflows, asset management, and knowledge systems. The approach prioritized practical functionality over academic exercises.

## Technical Implementation

### Workflow Automation
Built three core flows that handle the incident lifecycle:
- **Incident Urgency Response**: Automatically routes emails based on incident priority levels
- **Auto-Reply System**: Provides immediate acknowledgment for new incident submissions  
- **Resolution Notifications**: Closes the loop with caller notifications when incidents resolve

### Custom Data Models
Created the **Asset Recovery Request** table extending the Task framework. This handles laptop return workflows with proper state management and field validation.

**Key Fields:**
- Laptop Serial Number (validated, digits only)
- Return Condition (Like New, Damaged, Missing Parts)  
- Customer Priority classification

### Business Logic & Validation
**Business Rules:**
- Auto-populated descriptions using employee data
- Reminder generation for pending laptop returns

**UI Policies & Scripts:**
- Real-time serial number validation (digits only)
- Dynamic field requirements based on asset type selection
- Role-based submission controls for dxc_employee users

### Access Controls & Security
Implemented proper data policies and ACL restrictions:
- Enforced mandatory fields on Asset Recovery Requests
- Restricted Import Set access to data_manager_admin role only
- Created granular knowledge base access controls

### Service Catalog Integration
**iPhone 16 Catalog Item:**
- Color selection with pricing logic
- Storage tier options
- Dynamic cost calculation

**Broken Monitor Record Producer:**
- Auto-generates incidents with proper categorization
- Collects summary, details, and urgency upfront

### Knowledge Management System
Built complete knowledge base infrastructure:
- DXC Tech IT Support KB with proper access controls
- Knowledge Authors role and group management
- Separate read/contribute permissions (DXC_KB_Read_Access, DXC_KB_Contribute_Access)

### Data Integration
Developed transform maps for:
- Asset Recovery Request imports (handles clean and dirty data)
- User data batch uploads with coalesce logic for duplicate prevention

## Update Set Contents

The `ServiceNow_Daily_Labs_Update_Set.xml` contains:

**Flows & Notifications** (3 components)  
**Custom Fields** (3 components)  
**Business Rules** (2 components)  
**UI Policies & Client Scripts** (3 components)  
**Data Policies & ACLs** (2 components)  
**Tables & Modules** (3 components)  
**Transform Maps** (2 component sets)  
**Dashboards & Reports** (2 components)  
**Knowledge Management** (5 components)  
**Service Catalog** (2 components)

## What Can't Go in the Update Set

Some configurations require manual setup and screenshots for documentation:

### Import Operations
Import sets and their execution can't be packaged. I've documented:
- Asset recovery data imports (clean and problematic datasets)
- User batch uploads with duplicate handling
- Coalesce testing results

**Screenshots needed:** `import_results_clean.png`, `import_results_errors.png`, `user_upload_duplicates.png`

### Security & System Settings  
System properties and security configurations don't transfer via update sets:
- Session timeout (set to 60 minutes)
- Device encryption requirements
- Security Center best practices updates
- Default credential policies

**Screenshots needed:** `session_timeout_config.png`, `security_settings.png`, `encryption_policy.png`

### User Assignments
Role and group memberships are instance-specific:
- Knowledge Authors group assignments  
- Individual user role grants
- Group-to-role mappings

**Screenshots needed:** `user_group_assignments.png`, `role_assignments.png`

## Deployment Process

1. **Import the Update Set**
   - Navigate to System Update Sets > Retrieved Update Sets
   - Load `ServiceNow_Daily_Labs_Update_Set.xml`
   - Preview for conflicts, then commit

2. **Manual Configuration**
   - Configure session timeout in System Properties
   - Set up security policies per screenshot documentation
   - Assign users to appropriate groups and roles
   - Execute import sets for test data

3. **Validation**
   - Test incident urgency flow with P1 incidents
   - Verify laptop serial number validation works
   - Confirm Asset Recovery Request submission restrictions
   - Check knowledge base access controls

## Results & Impact

This configuration package demonstrates:
- Complete workflow automation from creation to resolution
- Proper data validation and business rule enforcement  
- Role-based security with appropriate access controls
- Integration between incident management and asset recovery
- Scalable knowledge management infrastructure

The components work together as a cohesive system rather than isolated lab exercises.

## Learning Outcomes

Building this expanded my ServiceNow skills significantly:
- Flow Designer for complex workflow orchestration
- Custom table design with proper field validation
- Transform map development for data integration
- ACL and data policy configuration
- Service catalog item development with dynamic logic

The key insight was understanding how ServiceNow components integrate—business rules, UI policies, and flows need to work together, not just function in isolation.

## AI Enhancement Potential

The current setup handles basic automation, but there's opportunity for intelligent routing and decision-making. An AI layer could analyze incident patterns, predict asset return issues, and optimize knowledge article recommendations based on user behavior and case resolution data.

That's not just "AI for AI's sake"—it's about making the automation smarter based on actual usage patterns and outcomes.

---

**Project**: ServiceNow Daily Labs Configuration  
**Completion**: [Date]  
**Technologies**: ServiceNow Flow Designer, Custom Tables, Transform Maps, Service Catalog  
**Package**: Complete XML update set with documentation
