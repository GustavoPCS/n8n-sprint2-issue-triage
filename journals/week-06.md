# Week 06 – Build Journal

**Course:** CS 590 Low Code No Code for Rapid Prototyping  
**Student:** Gustavo Pereira Corsi da Silva  
**Week:** 06  
**Date Range:** 09/28 – 10/02  
**Activity:** In-Class Activity Week 06

## 1. Weekly Focus and Goals
- Complete the Week 06 in-class activity.
- Build and successfully execute an n8n workflow.

## 2. Completed Work and Evidence
I completed the in-class activity by building a Tech Signal News Aggregator in n8n. The workflow retrieves RSS articles, filters relevant AI-related content, and stores the results. This helped me become familiar with n8n's nodes and workflow execution.

**Evidence:** [Add workflow screenshot or export](images/week06-workflow.png)

## 3. Work in Progress and Next Step
I started working on Sprint 2 for Week 07. My next step is to continue building and testing the GitHub issue-triage workflow.

## 4. What You Learned
This week, I learned how n8n connects different nodes to automate data processing. Filtering and limiting results were important to avoid storing unnecessary articles. The prototype dimension I tested most directly was **process**, since I focused on how information moves through the workflow.

**Extensibility Observation:** n8n makes it relatively easy to expand a workflow by adding nodes for new data sources, filters, or actions without rebuilding the entire automation. However, adding more nodes can make the workflow harder to manage and troubleshoot.

One remaining question is whether the filtering rules would remain effective when the workflow runs automatically over a longer period.

## 5. Challenge and Diagnosis
One challenge was that some RSS articles passed through the filters even though they were not very relevant. I inspected the incoming RSS fields and adjusted the Filter node conditions. Next, I would test stricter filtering rules across multiple executions to improve accuracy.

## 6. Response Plan
Next week, I plan to continue Sprint 2, improve my understanding of n8n, and focus on building reliable workflows that handle incoming data correctly without creating unnecessary or duplicate records.
