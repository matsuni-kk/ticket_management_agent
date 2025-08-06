---
name: 90_task_management
description: SlackTicket Task Management
---

# Task Management

create_daily_task:
  template: |
    # Daily Tasks - {{env.NOW:date:YYYY-MM-DD}}
    
    ## ticket_management Domain Tasks
    
    ### High Priority
    - [ ] 
    
    ### Medium Priority
    - [ ] 
    
    ### Low Priority
    - [ ] 
    
    ### Notes
    - Created: {{env.NOW:datetime:YYYY-MM-DD HH:mm:ss}}
    - Domain: ticket_management
