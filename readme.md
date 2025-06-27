# Agile Story Management Framework
## Team Reference Guide

**Version:** 1.0  
**Date:** June 2025  
**Purpose:** Comprehensive guide for improved sprint completion, fair accountability, and effective research management

---

## Executive Summary

This framework addresses three critical challenges in our agile delivery:
1. **Low sprint completion rates** due to oversized stories
2. **Unfair performance metrics** caused by external dependencies
3. **Misrepresented research effort** that doesn't reflect actual work complexity

Our new approach separates different types of work, applies appropriate sizing rules, and creates fair accountability while maintaining visibility and predictability.

---

## Core Principles

### 1. Story Sizing Philosophy
- **Maximum story size:** 5 story points
- **Sprint capacity per person:** 7-8 story points typically represents a full sprint effort
- **Sprint duration:** 2 weeks (10 working days)
- **Relative sizing:** Story points represent complexity and effort, not specific time commitments

### 2. Work Type Separation
- **Development Stories:** Traditional feature work with clear deliverables
- **Research/Spike Stories:** Investigation and learning activities
- **External Dependency Stories:** Work requiring client/external team input

### 3. Fair Accountability
- Developer metrics only reflect work within their control
- External dependencies tracked separately
- Research value measured through knowledge outcomes, not velocity

---

## Story Sizing Rules

### Mandatory Story Breakdown
**Rule:** Any story estimated at more than 5 story points MUST be broken down into smaller stories.

**Rationale:**
- Improves sprint completion consistency
- Reduces estimation uncertainty
- Enables better progress tracking
- Allows partial completion if blockers arise

### Story Point Guidelines
| Story Points | Complexity | Examples for Spring Boot Application |
|--------------|------------|--------------------------------------|
| 1 | Simple | Bug fix, configuration change, simple unit test |
| 2 | Straightforward | Add REST endpoint, basic service method, integration test setup |
| 3 | Moderate | Complex API endpoint with validation, service layer integration, database query optimization |
| 5 | Complex | Multi-service integration, authentication implementation, comprehensive test suite for feature |

**Note:** No stories should exceed 5 points. Stories requiring more effort must be decomposed.

### Sprint Capacity Planning
- **Individual capacity:** 7-8 story points maximum per 2-week sprint
- **Work type allocation:**
  - **Development stories:** 60-80% of capacity
  - **Research/spikes:** 10-20% of capacity  
  - **External dependency work:** 10-20% of capacity
- **Total sprint commitment:** Sum of all story types within capacity limits

---

## Development Stories with External Dependencies

### Problem Statement
Traditional stories that require external review often get unfairly counted against developer performance when delays occur outside their control.

### Solution: Three-Story Pattern

#### Story A - Development Complete (5 points typical)
- **Owner:** Primary developer
- **Definition of Done:** Code complete, unit tests pass, ready for external review
- **Moves to "Done":** When client confirms it's review-ready
- **Success Criteria:** Development work finished according to requirements

#### Story B - External Review (1 point)
- **Owner:** Client team/external reviewer
- **Definition of Done:** Review completed, feedback provided
- **Duration:** Tracked but not counted against dev team velocity
- **Purpose:** Visibility into external dependency time

#### Story C - Review Remediation (2 points typical)
- **Owner:** Primary developer
- **Triggered:** Only if review identifies issues requiring changes
- **Scope:** Specific to review feedback items
- **Definition of Done:** All review comments addressed

### Example Implementation
**Original Story:** "Implement user notification service" (10 points)

**Decomposed Approach:**
- **NOTIF-123A:** "Implement notification REST API - Development Complete" (5 points)
- **NOTIF-123B:** "Notification service - Client Review" (1 point - assigned to client)
- **NOTIF-123C:** "Notification service - Address Review Feedback" (2 points - created if needed)

---

## Research and Spike Stories

### Research Story Characteristics
- High uncertainty requiring investigation
- New technology evaluation
- Proof of concept development
- Architectural decision research

### Research Story Framework

#### Spike Stories (Time-boxed WITH Story Points)
**Purpose:** Investigate unknown areas to enable informed decisions

**Sizing:** Based on effort/complexity like development stories, but capped at timebox
**Tracking:** Separate "Research Velocity" from "Development Velocity"

**Template:**
```
Title: SPIKE - [Research Question]
Story Points: [1-5 points based on effort/complexity]
Timebox: [1-5 days maximum - hard stop regardless of points]
Questions to Answer:
- [Specific question 1]
- [Specific question 2]

Acceptance Criteria:
- Research findings documented
- Recommendation provided
- Follow-up stories created
- Knowledge shared with team
```

**Example:**
```
Title: SPIKE - Evaluate Spring Boot to AWS Lambda migration feasibility
Story Points: 5 points
Timebox: 3 days (hard stop)
Questions to Answer:
- Can our current Spring Boot application run on AWS Lambda?
- What are cold start performance implications?
- What changes are needed for ECS to Lambda migration?

Deliverables:
- Technical feasibility report
- Performance benchmark comparison (ECS vs Lambda)
- Migration effort estimate and timeline
- Architecture Decision Record (ADR)
```

**Research Story Sizing Guidelines:**
- **1-2 points:** Simple investigation, proof of concept, documentation research
- **3 points:** Moderate complexity research, small prototype development
- **5 points:** Complex investigation, comprehensive prototyping, architecture analysis

#### Implementation Stories (After Research Complete)
Once spike is complete, create properly estimated development stories:
- **LAMBDA-001:** "Refactor Spring Boot app for Lambda compatibility" (5 points)
- **LAMBDA-002:** "Create Lambda deployment pipeline with SAM" (3 points)
- **LAMBDA-003:** "Implement Lambda-specific logging and monitoring" (2 points)
- **LAMBDA-004:** "Update integration tests for serverless architecture" (4 points)

### Research Documentation Requirements
All research stories must produce:
1. **Architecture Decision Record (ADR)** - Structured decision documentation
2. **Technical findings summary** - What was learned
3. **Follow-up story creation** - Next steps identified
4. **Knowledge sharing session** - Team presentation of findings

---

## Implementation Guidelines

### Sprint Planning Process

#### 1. Capacity Allocation
- Calculate total team capacity (7-8 points per person)
- Reserve 10-20% for research/spikes
- Allocate remaining capacity to development stories

#### 2. Story Review Checklist
Before adding to sprint:
- [ ] Story is 5 points or less
- [ ] Dependencies identified and tracked
- [ ] Definition of Done is clear
- [ ] External review requirements separated

#### 3. Backlog Refinement
- Break down any stories over 5 points
- Identify research needs and create spikes
- Separate external dependencies into review stories
- Ensure all stories have clear acceptance criteria

### Daily Standup Adjustments
**Traditional Focus:** What did you do, what will you do, blockers

**Enhanced Focus:**
- Progress on committed stories
- External dependencies waiting time
- Research findings and next steps
- Blocker escalation status

### Sprint Review Updates
**Demonstrate:**
- Completed development stories with working software
- Research findings, decisions made, and follow-up stories created
- External dependency resolution progress
- Knowledge gained and documented

**Sprint Completion Reporting:**
```
Sprint X Results:
Total Story Points Completed: 32/35 (91%)

Breakdown:
- Development Work: 24 points (75%)
- Research/Spikes: 6 points (19%) 
- External Remediation: 2 points (6%)

Key Outcomes:
- 4 features delivered to production
- Lambda migration feasibility confirmed
- 2 external dependency blockers resolved
```

---

## Metrics and Tracking

### Development Velocity
- **Track:** Development stories completed by the team
- **Exclude:** External review time from cycle time calculations
- **Goal:** Consistent velocity based on development work

### Research Velocity
- **Track:** Research/spike stories completed with story points
- **Measure:** Knowledge outcomes achieved per points invested
- **Goal:** Valuable research findings that inform development decisions

### Combined Sprint Output
- **Total Story Points:** Development + Research + External Remediation
- **Breakdown Visibility:** Show stakeholders the mix of work types
- **Capacity Planning:** Allocate 60-80% development, 10-20% research, 10-20% external work

### External Dependency Metrics
- **Review Cycle Time:** Average time for external review completion
- **Escalation Rate:** Percentage of dependencies requiring escalation
- **Impact Tracking:** Sprint goals affected by external delays

### Success Indicators
- **Sprint Completion Rate:** Target 85%+ of committed story points
- **Story Rollover Reduction:** Fewer incomplete stories carrying to next sprint
- **Team Confidence:** Improved estimation accuracy over time

---

## Common Scenarios and Solutions

### Scenario 1: Large Feature Implementation
**Challenge:** Feature requires 15 story points of work

**Solution:**
```
Epic: User Authentication System for Spring Boot App

Stories:
- AUTH-001: Implement login REST endpoint with JWT (3 points)
- AUTH-002: Create user registration service layer (5 points)
- AUTH-003: Add password reset functionality (3 points)
- AUTH-004: Implement JWT token validation filter (4 points)
- AUTH-005: Add comprehensive security testing suite (5 points)
```

### Scenario 2: POC for New Technology
**Challenge:** Need to evaluate Spring Boot to AWS Lambda migration

**Solution:**
```
Phase 1 - Research:
- SPIKE-001: Spring Boot Lambda compatibility analysis (3 points, 2 days max)
- SPIKE-002: Performance comparison ECS vs Lambda (5 points, 3 days max)

Phase 2 - Implementation (if approved):
- LAMBDA-001: Refactor Spring Boot for Lambda runtime (5 points)
- LAMBDA-002: Create SAM deployment templates (3 points)
- LAMBDA-003: Implement Lambda-specific health checks (2 points)
```

### Scenario 3: External Review Required
**Challenge:** Security compliance review needed for authentication feature

**Solution:**
```
- AUTH-001A: Implement JWT authentication - Dev Complete (5 points)
- AUTH-001B: JWT authentication security review (1 point - assigned to security team)
- AUTH-001C: Address security review findings (2 points - if needed)
```

---

## Communication Guidelines

### With Stakeholders
- **Highlight:** Improved predictability through better sizing
- **Explain:** External dependencies now visible and tracked
- **Emphasize:** Research investment leads to better implementation

### With Leadership
- **Report:** Separate metrics for development vs. research vs. external dependencies
- **Demonstrate:** How new approach improves delivery consistency
- **Request:** Support for research time allocation

### With Client Teams
- **Collaborate:** On external dependency story definitions
- **Communicate:** Expected timelines for external review work
- **Escalate:** When external dependencies impact sprint goals

---

## Implementation Timeline

### Week 1-2: Foundation Setup
- Train team on new story patterns
- Create story templates in Jira
- Establish new Definition of Done criteria

### Week 3-4: First Sprint Trial
- Apply new sizing rules to current backlog
- Practice three-story pattern for external dependencies
- Create first research spikes

### Week 5-6: Process Refinement
- Gather team feedback on new approach
- Adjust templates based on learnings
- Establish metrics tracking

### Week 7-8: Full Implementation
- Apply framework to all new work
- Communicate changes to stakeholders
- Begin tracking success metrics

---

## Success Criteria

### Short-term (1-2 sprints)
- 90% of stories are 5 points or less
- External dependencies clearly identified and tracked
- Research activities time-boxed and documented

### Medium-term (3-6 sprints)
- Sprint completion rate above 85%
- Reduced story rollover between sprints
- Improved estimation accuracy

### Long-term (6+ sprints)
- Consistent team velocity
- Stakeholder confidence in delivery predictability
- Valuable research outcomes feeding into product decisions

---

## Troubleshooting Guide

### "We can't break this story down further"
- Challenge the Definition of Done - can it be simplified?
- Look for vertical slices rather than horizontal layers
- Consider separating UI from backend work
- Create spike to better understand the work

### "Research is taking longer than expected"
- Time-box strictly - stop at deadline regardless of findings
- Document what was learned within the timebox
- Create additional spike if more research needed
- Reassess if the research question was too broad

### "External dependencies are still blocking us"
- Escalate through proper channels immediately
- Document impact on sprint goals
- Communicate delays to stakeholders proactively
- Have backup work ready for blocked developers

---

## References and Resources

### Templates
- [Story Template - Development]
- [Story Template - Research/Spike]
- [Story Template - External Review]
- [Architecture Decision Record Template]

### Tools
- Jira configuration for new story types
- Sprint planning estimation worksheets
- Velocity tracking dashboards

### Training Materials
- Story decomposition workshop
- Research methodology training
- Estimation techniques refresher

---

**Document Maintainer:** GMR 
**Last Updated:** [Date]  
**Next Review:** [Date + 3 months]

*This is a living document. Please provide feedback and suggestions for improvement*
