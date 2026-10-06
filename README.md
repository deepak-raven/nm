# Auto Ticket Classification using Flow Designer
## ServiceNow Administrator Track – End-to-End Phasewise Project Documentation
**Team ID:** `SWTID-2026-7735`  
**Submission Date:** October 2026  
**Track:** ServiceNow Administrator – Practical Implementation Deliverable  

---

### Project Overview
The **Auto Ticket Classification using Flow Designer** project provides an automated, no-code triage and notification solution built natively on the **ServiceNow** platform. 

In school and campus IT environments, IT helpdesks receive dozens of incoming support requests daily from students and faculty for issues such as Wi-Fi disruptions, classroom projector failures, locked/forgotten passwords, and slow computer performance. Traditionally, IT staff manually open and classify each record before assigning it to a technician, causing administrative bottlenecks and delayed classroom support.

This project completely automates ticket intake:
1. **Custom Data Model**: Records are captured in a custom table `Incident WorkFlow` (`u_incident_workflow`) with Auto-Numbering enabled (`Prefix: INC, Number: 500, Digits: 5` -> `INC00509`, `INC00511`, `INC00512`).
2. **Dependent Choices**: `Category` and `Subcategory` choice lists enforce dictionary dependencies:
   - `Wi-Fi` -> `Network`
   - `Projector` -> `Hardware`
   - `Forgot Password` -> `Access`
   - `Slow Computer` -> `Performance`
3. **Flow Designer Automation**: Trigger evaluates newly created tickets where `Category is empty`, parses keywords in `Short Description`, and updates the record with the correct Category and Subcategory.
4. **Instant Caller Notification**: An automated `Send Email` action immediately emails the caller with ticket details and confirmation.
5. **Update Set Packaging**: All configuration elements are tracked in `Project Update Set` and exported to XML (`sys_remote_update_set_a7b40de6fc590ceaad36c.xml`, 182 KB).

---

### Complete Phasewise File Structure (with Embedded Diagrams & Screenshots)

```
Auto Ticket Classification using Flow Designer/
├── 1. Ideation Phase/
│   ├── Brainstorming- Idea Generation- Prioritizaation Template.docx (.pdf)
│   ├── Define Problem Statements Template.docx (.pdf)
│   └── Empathy Map Canvas.docx (.pdf)
│
├── 2. Requirement Analysis/
│   ├── Customer Journey Map.docx (.pdf)
│   ├── Customer Journey Map - Example.pdf
│   ├── Data Flow Diagrams and User Stories.docx (.pdf)
│   ├── Solution Requirements.docx (.pdf)
│   └── Technology Stack - Template.docx (.pdf)
│
├── 3. Project Design Phase/
│   ├── Problem - Solution Fit Template/
│   │   └── Problem - Solution Fit Template v1.docx (.pdf)
│   ├── Proposed Solution/
│   │   └── Proposed Solution Template.docx (.pdf)
│   └── Solution Architecture/
│       └── Solution Architecture.docx (.pdf)
│
├── 4. Project Planning Phase/
│   ├── Planning logic.docx (.pdf)
│   └── Project Planning Template.docx (.pdf)
│
├── 5. Project Development Phase/
│   ├── Performance Testing/
│   │   ├── ServiceNow Performance and Functional Testing.docx (.pdf)
│   │   └── User Acceptance Testing FSD.docx (.pdf)
│   └── User Acceptance Testing/
│       └── UAT Report Template.docx (.pdf)
│
└── 6. Project Documentation/
    ├── FSD Documentation Format.docx (.pdf)
    └── Final Report - Auto Ticket Classification using Flow Designer.docx (.pdf)
```

---

### Embedded Diagrams & Screenshot Index

| Document | Embedded Visual Assets | Source |
| :--- | :--- | :--- |
| **Brainstorming Template** | • Brainstorming Creative Ideation Canvas<br>• Idea Listing & Post-it Clustering Map<br>• Value vs. Complexity Prioritization Grid | Extracted from Phasewise Template |
| **Define Problem Statements** | • 5W1H Customer Problem Statement Framework Canvas | Extracted from Phasewise Template |
| **Empathy Map Canvas** | • Empathy Map Canvas Layout (Says, Does, Thinks, Feels)<br>• Persona Journey & Sentiment Reference Model | Extracted from Phasewise Template |
| **Customer Journey Map** | • Multi-Stage Customer Journey Map Architecture | Extracted from Phasewise Template |
| **Data Flow Diagrams** | • Level 0 Context & Level 1 Functional Data Flow Diagram | Extracted from Phasewise Template |
| **Technology Stack** | • ServiceNow Enterprise Tiered Technology Architecture Diagram | Extracted from Phasewise Template |
| **Solution Architecture** | • Multi-Tier Architecture Diagram (Presentation, Logic, Data, Notification) | Extracted from Phasewise Template |
| **User Acceptance Testing (UAT)** | • UAT Test 1 Execution Screenshot (`INC00511` Wi-Fi Auto-Classification)<br>• UAT Test 2 Execution Screenshot (`INC00512` Projector Auto-Classification)<br>• System Logs Outbound Email Dispatch Verification Screenshot | Extracted from Project Guide PDF |
| **FSD Documentation Format** | • **32 Step-by-Step Screenshots**:<br>  - Update Set creation & 'Make Current'<br>  - Custom table creation & Auto Number controls<br>  - Form Designer & Choice field lists<br>  - Dictionary Dependency configuration<br>  - Dynamic Subcategory filtering verification<br>  - Flow Designer trigger setup<br>  - If/Else-If condition logic (Wi-Fi, Projector, Password, Slow Computer)<br>  - Send Email action with data pills<br>  - Test Scenario 1 & 2 execution verification (`INC00511`, `INC00512`)<br>  - Email logs & preview mail dialog<br>  - Update Set completion & Export to XML download history | Extracted from Project Guide PDF |
| **Final Project Report** | • All 11 formal report chapters with diagrams and execution evidence screenshots | Extracted from Curriculum Guidelines & Guide |

---

### Key ServiceNow Technical Implementation Summary

1. **Update Set**: `Project Update Set` in Global scope, marked Current during development and exported to XML (`sys_remote_update_set_a7b40de6fc590ceaad36c.xml`) upon completion.
2. **Custom Table**: `Incident WorkFlow` (`u_incident_workflow`) with Auto Number enabled (`Prefix: INC, Number: 500, Digits: 5`).
3. **Dictionary Dependency**: Configured on `u_subcategory` dictionary entry pointing to `category`:
   - `network` -> `Wi-Fi`
   - `hardware` -> `Projector`
   - `access` -> `Forgot password`
   - `performance` -> `Slow computer`
4. **Flow Designer Automation**: Flow titled `Auto Classify School IT Tickets` triggered on `Record Created` when `Category is empty`:
   - Checks `Short Description` for keywords (`Wi-Fi`, `Projector`, `Password`, `Slow Computer`).
   - Updates `Category` and `Subcategory`.
   - Sends automated email confirmation to `Caller -> Email`.
5. **Testing Verification**: Tested with actual scenarios (`INC00511`, `INC00512`) and verified in `System Logs > Emails`.
