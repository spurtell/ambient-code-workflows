# ACM JIRA Issue Creation Guide

Project: **Red Hat Advanced Cluster Management** (key: `ACM`, id: `10625`)
Cloud ID: `issues.redhat.com`

## Issue Type Reference

| Type | ID | Hierarchy | Fields |
|------|:--:|:---------:|:------:|
| Feature | 10142 | 2 | 77 |
| Epic | 10000 | 1 | 82 |
| Story | 10009 | 0 | 77 |
| Bug | 10016 | 0 | 80 |
| Task | 10014 | 0 | 71 |
| Spike | 10104 | 0 | 57 |

## Required Fields (all types)

| Field | Key | Type |
|-------|-----|------|
| Summary | `summary` | string |
| Project | `project` | `{"key": "ACM"}` |
| Issue Type | `issuetype` | `{"id": "<type_id>"}` |
| Reporter | `reporter` | `{"id": "<account_id>"}` |

## Field Availability Matrix

**Legend:** `*` = available on that type

### Universal Fields (all 6 types)

| Field | Key | Type |
|-------|-----|------|
| Assignee | `assignee` | user |
| Attachment | `attachment` | array[attachment] |
| Components | `components` | array[component] — see [allowed-values](acm-jira-allowed-values.md#components) |
| Team | `customfield_10001` | team |
| Epic Link | `customfield_10014` | any |
| Start date | `customfield_10015` | date |
| Parent Link | `customfield_10018` | any |
| Sprint | `customfield_10020` | array[json] |
| Flagged | `customfield_10021` | array[option] — `Impediment` (10019) |
| Target start | `customfield_10022` | date |
| Target end | `customfield_10023` | date |
| Story Points | `customfield_10028` | number |
| Activity Type | `customfield_10464` | option — see below |
| Contributors | `customfield_10466` | array[user] |
| QA Contact | `customfield_10470` | user |
| Doc Contact | `customfield_10473` | user |
| Contributing Groups | `customfield_10479` | array[group] |
| Need Info From | `customfield_10482` | array[user] |
| Blocked Reason | `customfield_10483` | string |
| Ready | `customfield_10484` | option — `True` (10471), `False` (10472) |
| Blocked | `customfield_10517` | option — `True` (10852), `False` (10853) |
| Sync Failure Flag | `customfield_10656` | array[string] |
| Acceptance Criteria | `customfield_10718` | string |
| Release Note Text | `customfield_10783` | string |
| Release Note Type | `customfield_10785` | option — see below |
| Severity | `customfield_10840` | option — see below |
| Target Version | `customfield_10855` | array[version] — see [allowed-values](acm-jira-allowed-values.md#versions) |
| Products | `customfield_10868` | array[option] — see [allowed-values](acm-jira-allowed-values.md#products) |
| Git Pull Request | `customfield_10875` | string |
| Bugzilla Bug | `customfield_10877` | string |
| Original story points | `customfield_10977` | number |
| Description | `description` | string |
| Due date | `duedate` | date |
| Environment | `environment` | string |
| Fix versions | `fixVersions` | array[version] — same values as Target Version |
| Labels | `labels` | array[string] |
| Parent | `parent` | issuelink |
| Priority | `priority` | priority — see below |
| Security Level | `security` | securitylevel — see below |
| Time tracking | `timetracking` | timetracking |
| Affects versions | `versions` | array[version] — same values as Target Version |
| Intelligence Requested | `rh-cf-single-select__0cc12138-8ccf-4171-86c8-ce3cf458d3e6` | string |
| SDLC stage when should've been found | `rh-cf-single-select__b18b5653-6431-4450-b556-f54b4af003ab` | string |
| Market | `rh-cf-multi-select__69443e64-0907-42fd-a259-4fafcdf6a0f6` | string |
| Portfolio Solutions | `rh-cf-multi-select__9632b58d-c5e6-4af8-933b-c142dc5c2408` | string |
| Test Link | `rh-cf-multi-url__af83e671-1563-475b-91f9-1902b48f28f2` | string |
| SFDC Cases Counter/Links/Open | (sfdc plugin keys) | string |
| Red Hat Privacy Banner | (plugin key) | string |

### Conditional Fields

| Field | Key | Type | F | E | S | B | T | Sp |
|-------|-----|------|:-:|:-:|:-:|:-:|:-:|:--:|
| ACKs Check | `customfield_10487` | array[option] | * | * | * | * | * | |
| Architect | `customfield_10467` | user | * | * | * | | * | |
| BZ Internal Whiteboard | `customfield_10527` | string | | * | * | * | * | * |
| Color Status | `customfield_10712` | option | * | * | * | | * | |
| Customer Impact | `customfield_10689` | array[option] | | | * | * | * | |
| Designer | `customfield_10499` | user | * | * | | * | * | |
| Documentation Type | `customfield_10659` | array[option] | | * | * | * | * | * |
| Epic Name | `customfield_10011` | string | | * | | | | |
| Escape Impact | `rh-cf-single-select__ed146d2b...` | string | | | | * | | |
| Escape Reason | `rh-cf-single-select__14248eef...` | string | | | | * | | |
| Corrective Measures | `rh-cf-multi-select__f88e7979...` | string | | | | * | | |
| Git Commit | `customfield_10583` | string | * | * | * | * | * | |
| GitHub Issue | `customfield_10747` | string | * | * | * | * | * | |
| Latest Status Summary | `customfield_10778` | string | | * | * | * | * | |
| Manager | `customfield_10677` | user | * | * | * | | * | |
| OpenShift Planning Ack | `customfield_10761` | array[option] | | * | | | | |
| Organization Sponsor | `customfield_10558` | option | * | * | * | | | |
| Product Manager | `customfield_10469` | user | * | * | | * | | |
| Product Ops Eng Contact | `customfield_10666` | user | * | * | | | | |
| Product Sponsor | `customfield_10612` | option | * | * | | | | |
| PX fields (6 fields) | `rh-cf-*` | string | * | * | * | * | | |
| Regression | `customfield_10623` | option | | | * | * | * | * |
| Release Blocker | `customfield_10847` | option | * | * | * | * | * | |
| Release Commit Exception | `customfield_10849` | option | * | * | * | * | * | |
| Release Note Status | `customfield_10807` | option | * | * | * | * | * | |
| Release Type | `customfield_10851` | option | * | * | | | | |
| RH Private Keywords | `rh-cf-multi-select__0585ba67...` | string | | | | * | | |
| Size | `customfield_10795` | option | * | * | | | | |
| Special Handling | `customfield_10670` | array[option] | | | | * | | |
| Steps to Reproduce | `customfield_10821` | string | | | | * | | |
| Technical Lead | `customfield_10675` | user | * | * | * | | * | |
| Test Coverage | `customfield_10638` | array[option] | | | * | * | * | * |

## Allowed Values — Small Option Fields

### Priority
| Value | ID |
|-------|:--:|
| Blocker | 10000 |
| Critical | 10001 |
| Major | 10002 |
| Normal | 10003 |
| Minor | 10004 |
| Undefined | 10005 |

### Severity
| Value | ID |
|-------|:--:|
| Critical | 19917 |
| Important | 19918 |
| Moderate | 19919 |
| Low | 19920 |
| Informational | 19921 |

### Activity Type
| Value | ID |
|-------|:--:|
| Associate Wellness & Development | 10604 |
| Future Sustainability | 10606 |
| Incidents & Support | 10607 |
| Quality / Stability / Reliability | 10608 |
| Security & Compliance | 10609 |
| Product / Portfolio Work | 10610 |

### Release Note Type
| Value | ID |
|-------|:--:|
| Bug Fix | 12492 |
| CVE - Common Vulnerabilities and Exposures | 12493 |
| Deprecated Functionality | 12494 |
| Developer Preview | 12495 |
| Enhancement | 12497 |
| Feature | 12498 |
| Known Issue | 12500 |
| Rebase | 12501 |
| Removed Functionality | 12505 |
| Technology Preview | 12506 |
| Unspecified Release Note Type - Unknown | 12507 |
| Release Note Not Required | 12510 |

### Release Note Status
| Value | ID |
|-------|:--:|
| Done | 12528 |
| In Progress | 12529 |
| Proposed | 12533 |
| Rejected | 12534 |
| Upstream Only | 12536 |

### Size (Feature, Epic only)
| Value | ID |
|-------|:--:|
| XL | 19206 |
| L | 19207 |
| M | 19208 |
| S | 19209 |
| XS | 19210 |

### Release Type (Feature, Epic only)
| Value | ID |
|-------|:--:|
| GA | 19299 |
| Tech Preview | 19300 |
| Conditional Tech Preview | 19301 |
| Dev Preview | 19302 |

### Color Status
| Value | ID |
|-------|:--:|
| Not Selected | 11102 |
| Green | 11103 |
| Yellow | 11104 |
| Red | 11105 |

### Release Blocker / Release Commit Exception
| Value | ID (Blocker) | ID (Exception) |
|-------|:--:|:--:|
| Approved | 16772 | 16058 |
| Proposed | 16773 | 16059 |
| Rejected | 16774 | 16060 |

### Security Level
| Value | ID | Description |
|-------|:--:|-------------|
| Embargoed Security Issue | 10038 | Product Security only |
| Red Hat Employee | 10034 | Employees and contractors |
| Red Hat Engineering Authorized | 10036 | Approved for product dev info |
| Red Hat Partner | 10039 | Partner confidential |
| Restricted | 10035 | Project admins + involved users |
| Team | 10037 | Project roles + involved users |

### ACKs Check
eng-lead (10920), devel-ack (10921), qa-ack (10922), pm-ack (10923), cee-ack (10924), ux-ack (10925), doc-ack (10926)

### OpenShift Planning Ack (Epic only)
qe-ack (14494), doc-ack (14495), px-ack (14496)

### Regression (Story, Bug, Task, Spike)
No (16061), Yes (16062)

### Test Coverage (Story, Bug, Task, Spike)
\+ (15875), - (15876), ? (15877)

### Customer Impact (Story, Bug, Task)
Customer Escalated (16324), Customer Facing (16325), QE Confirmed (16326), Customer Reported (16327)

### Documentation Type (Epic, Story, Bug, Task, Spike)
Administer (19275), API (19276), Deploy (19277), Develop (19278), Install (19279), Instructions (19280), Migrate (19281), Monitor (19282), Network (19283), Optimize (19284), Provision (19285), Plan (19286), Quickstarts (19287), Release Notes (19288), Security (19289), Storage (19290), Troubleshoot (19291)

### Organization Sponsor (Feature, Epic, Story)
Developer Tools (14503), Kubernetes-native Infrastructure (14504), Management (14505), Middleware (14506), OpenShift Add-ons (14507), OpenStack (14508), RHEV (14509), Service Delivery (14510), Storage (14511)

### Product Sponsor (Feature, Epic)
ARO (16741), Automation (16742), CNV (16743), Edge (16744), Integration (16745), IPv6 (16746), ISC (16747), Metal Management (16748), OCM (16749), OCS (16750), ODO (16751), On Prem Operations (16752), OSD (16753), OVN-Kubernetes (16754), Pipelines (16755), Quay (16756), RHMI (16757), ROSA (16758), Runtimes (16759), Serverless (16760), Service Mesh (16761), Telco 5G Core (16762), Telco 5G RAN (16763), Telco Partners (16764)

### Special Handling (Bug only)
compliance-priority (19864), contract-priority (19865), KEV (active exploit case) (19866), Major Incident (19867), Minor Incident (19868), security-select (19869), support-exception (19870)

## Workflow: Recommended Fields by Type

### Feature
**Always ask:** Summary, Description, Components, Target Version, Priority
**Recommended:** Parent (Outcome/Initiative), Acceptance Criteria, Release Type, Size, Activity Type, Product Manager, Architect
**Optional:** Labels, Target start/end, Contributors, Doc Contact, QA Contact

### Epic
**Always ask:** Summary, Description, Components, Target Version, Priority, Epic Name
**Recommended:** Parent Link (Feature), Acceptance Criteria, Activity Type, Architect, Technical Lead
**Optional:** Labels, Target start/end, Story Points, OpenShift Planning Ack, Documentation Type

### Story
**Always ask:** Summary, Description, Components, Target Version, Priority
**Recommended:** Parent (Epic), Acceptance Criteria, Story Points, Activity Type
**Optional:** Labels, Assignee, Sprint, Documentation Type, Regression, Test Coverage

### Bug
**Always ask:** Summary, Description, Components, Target Version, Priority, Severity
**Recommended:** Steps to Reproduce, Acceptance Criteria, Assignee, Regression
**Optional:** Labels, Sprint, Release Blocker, Customer Impact, Special Handling, Environment, Affects versions

### Task
**Always ask:** Summary, Description, Components, Priority
**Recommended:** Assignee, Story Points, Activity Type
**Optional:** Labels, Sprint, Target Version, Parent (Epic)

### Spike
**Always ask:** Summary, Description, Components, Priority
**Recommended:** Assignee, Story Points, Acceptance Criteria
**Optional:** Labels, Sprint, Target Version, Parent (Epic)
