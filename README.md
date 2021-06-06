# Workflows
#### 1. workflow
    A workflow is a sequence of steps or rules applied to a process from its initiation to completion.
    A workflow step is a state of an entity record.
    The process of moving an entity from one step to another is called a transition.
![image](https://user-images.githubusercontent.com/56823408/120911785-a0de3300-c6bc-11eb-910e-72fddaf686ec.png)
    
    Location:
        Resource/config/oro/workflows.yml (imports)
    Console Commands: 
        bin/console oro:workflow:definitions:load
        bin/console oro:debug:workflow:definitions `workflow_name`
    Tables:
        oro_workflow_definition
        oro_workflow_item
    Admin create workflow 
#### 2. Steps
    Represent state of a workflow
    Steps are ordered
    Steps know about possible transitions
    Workflow may have one start step
    Workflow may have one or more final steps
    Table:
        oro_workflow_step
    supplycore:
    yml: vendor\oro\crm\src\Oro\Bundle\SalesBundle\Resources\config\oro\workflows\opportunity_flow\steps.yml
#### 3. Attributes
    Represent data of workflow
    The attribute data is stored inside the WorkflowItem entity
    supplycore:
    yml: vendor\oro\crm\src\Oro\Bundle\SalesBundle\Resources\config\oro\workflows\opportunity_flow\attributes.yml
#### 4. Variables
![image](https://user-images.githubusercontent.com/56823408/120912689-f10cc380-c6c3-11eb-92db-949915fe6809.png)
![image](https://user-images.githubusercontent.com/56823408/120912666-adb25500-c6c3-11eb-841b-96bbdc20f6e7.png)

#### 5. Transitions
    Represent change of state
    Lead to one workflow step
    Workflow has one or more start transitions
    Might have a form with attribute fields
    Might have ACL restriction
    Might have assigned conditions
    Might have related actions
    supplycore: 
    yml: vendor\oro\crm\src\Oro\Bundle\SalesBundle\Resources\config\oro\workflows\opportunity_flow\transitions.yml
    
#### 6. Transition Definition
    Represent transition conditions and actions
    Pre-actions, pre-conditions(can be displayed)
    Actions, conditions(can be performed)
    Might be empty
    Several transitions might use the same transition definition
    supplycore: 
    yml: vendor\oro\crm\src\Oro\Bundle\SalesBundle\Resources\config\oro\workflows\opportunity_flow\transition_definitions.yml
    
#### 7. Actions
    functionality
    Might have parameters
    Might have conditions
    Custom actions: oro_action.action
    List of all actions: debug:container --tag="oro_action.action"
#### 8. Conditions
    check that returns
    Might have parameters
    Custom conditions: oro_action.condition
    List of all conditions: debug:container --tag="oro_action.condition"
#### 9. Opreations
    Provide possibility to assign any interaction with user
    Can be added to specific routes or datagrids
    Use actions and conditions
    example: oro CURD operations
    extends/for all entities/acl resource/frontend options/button options/actions/order/
![image](https://user-images.githubusercontent.com/56823408/120912923-e3583d80-c6c5-11eb-8693-1da55cfa34ef.png)
#### 10. Transition Triggers
    Transition Triggers are used to perform Transition by Event or by cron-definition. There are two types of triggers: Event Trigger and Cron Trigger.
    event triggers: 
        supplycore: 
        yml: vendor\oro\commerce-crm\src\Oro\Bridge\QuoteSales\Resources\config\oro\workflows\quote_flow\transitions.yml
    cron triggers:
        supplycore:
        yml: vendor\oro\platform\src\Oro\Bundle\WorkflowBundle\Tests\Functional\Command\DataFixtures\InvalidFilterExpression\workflows.yml
#### 11. Translation
    Location: Resources/translations/workfloes.<en>.yml
    Translation for steps, attributes and transitions
    Console Commands: 
        bin/console oro:workflow:translations:dump `workflow_name`



    
