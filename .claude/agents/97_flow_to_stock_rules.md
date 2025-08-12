---
name: 97_flow_to_stock_rules
description: SlackTicket Flow to Stock Rules
---

# Flow to Stock Movement

flow_to_stock_process:
  steps:
    - validate_document
    - add_version_info
    - move_to_stock
    - archive_previous
  
  template: |
    ---
    file_type: "stock_document"
    stage: "finalization"
    version: "v1.0"
    generated_at: "{{env.NOW:datetime:YYYY-MM-DD HH:mm:ss}}"
    domain: "ticket_management"
    agent: "TicketManagement"
    ---
    # Document Finalization - {{env.NOW:date:YYYY-MM-DD}}
    
    ## Document Information
    - Domain: ticket_management
    - Version: v1.0
    - Finalized: {{env.NOW:datetime:YYYY-MM-DD HH:mm:ss}}
