# AI-Driven Customer Support Automation System

**Team Project – SAW AI-TEAM 40 | Week 2 Deliverable**

---

## Team Members
- Atiatunnasir Oni-Bashir  
- Funmi Ayowole  
- Farai Audrey  
- Rachel Atienza  
- Nwachukwu Chukwukwe  
- Saransh Maurya  
- Hafiza  

---

## Project Overview
This project implements an **AI-driven customer support workflow** to handle event-related inquiries automatically. The system:  
- Interprets messages from customers  
- Classifies intent using an LLM  
- Retrieves relevant knowledge from a vector database  
- Drafts responses intelligently  
- Escalates uncertain or high-risk cases to human agents  
- Logs all interactions for analytics and QA  

**Goal:** Reduce manual triage, ensure faster responses, and improve scalability of customer support.

---

## Workflow Architecture

**Trigger:** Customer message via WhatsApp or form submission  
**Process:**  

1. **Chat Trigger:** n8n receives incoming messages.  
2. **Intent Classification:** Text is analyzed using Gemini to determine if inquiry is event-related.  
   - If not event-related → auto-response: “I can only answer event-related questions.”  
   - If event-related → routed to QA node.  
3. **Knowledge Retrieval (RAG):**  
   - Pinecone vector search + Supabase structured DB used to fetch relevant info.  
   - Gemini drafts the response based on retrieved context.  
4. **Confidence Assessment:**  
   - Responses classified as *confident* or *not confident*.  
   - Not confident → escalated to agents via Gmail.  
   - Confident → response sent to customer, awaiting approval.  
5. **Approval Node:**  
   - Approved → logged in Google Sheet / Airtable.  
   - Not approved → sent back to agent for review via Gmail.  
6. **Outcome Logging:** Track all responses, confidence scores, escalation paths, and metrics.

**Visual Workflow Wireframe:**  
## AI-Driven Customer Support Workflow

```text
[Customer Message] (WhatsApp / Form)
          │
          ▼
   [Text Classifier] -- Is it event-related?
          │
   ┌──────┴──────┐
   │             │
 [No]           [Yes]
   │             │
Respond:       [QA Node]
"I can only       │
answer event"     ▼
             [Knowledge Retriever]
          (Pinecone + Supabase)
                   │
                   ▼
              [Gemini LLM]
         (Classification + Draft)
                   │
                   ▼
         [Confidence Assessment]
        /                     \
  Not Confident             Confident
       │                        │
Escalate via Gmail/Slack  Respond → Await Approval
                               │
                    ┌──────────┴───────────┐
                 Approved               Not Approved
                   │                        │
             Log in Sheet / Airtable   Escalate via Gmail 

---

## Tool Stack & Justification

| Component | Tool | Purpose |
|-----------|------|---------|
| Orchestration | n8n | Node-based automation for multi-step workflows and branching logic |
| AI Reasoning & Drafting | Gemini | Classifies inquiries, drafts responses, and generates context-aware answers |
| Knowledge Retrieval | Pinecone + Supabase | RAG: Pinecone handles vector search; Supabase stores structured metadata |
| Triggers | WhatsApp / Form submissions | Real-time, structured input sources |
| Human Handoff | Slack / Gmail | Escalation and context delivery for uncertain cases |
| Logging | Airtable / Google Sheets | Structured logging, metrics, and analytics dashboards |
| Workflow Design | draw.io | Clear visual representation of automation logic and decision paths |

---

## AI Integration Points

1. **Intent Detection:** Determines event relevance of customer queries.  
2. **Response Drafting:** Generates human-like replies grounded in retrieved knowledge.  
3. **Confidence Scoring:** Mimics human judgment to decide auto-response vs. escalation.  
4. **Human Handoff Assistance:** Prepares draft replies and context for agents.  

**Impact:**  
- Reduces manual workload  
- Ensures faster, consistent responses  
- Scalable for high-volume inquiries  
- Human-in-the-loop ensures quality and reliability  

---

## Tool Comparison Highlights

- **n8n vs Zapier vs Make:** Chosen for flexibility, branching logic, and self-hosting capabilities.  
- **Gemini vs GPT-4o vs Claude 3.5:** Chosen for deep integration with Google Cloud, large context window, and multi-modal support.  
- **Pinecone/Supabase vs traditional DBs:** Vector search + structured DB supports semantic RAG better than keyword-only or vanilla DBs.  
- **Airtable vs Google Sheets:** Airtable for structured case management; Google Sheets for reporting and dashboards.  

---

## Notes
- This project focuses on **workflow design and conceptual AI integration** — no production code included.  
- The workflow shows **end-to-end automation from chat intake to AI reasoning to human escalation**.  
- Visual diagrams, workflow documentation, and tool justification are included to demonstrate technical depth and implementation planning.  

---
