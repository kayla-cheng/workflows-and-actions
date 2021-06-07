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
    How to creat simple workflow in Admin Console?
    node: entity/entity_attribute/start_step/applications/attributes/steps/transitions/transition_definitions
#### 2. Steps
    Represent state of a workflow
    Steps are ordered
    Steps know about possible transitions
    Workflow may have one start step
    Workflow may have one or more final steps
    node: order/allowed_transitions/is_final
    Table:
        oro_workflow_step
    supplycore: src\SupplyCore\Bundle\RFPBundle\Resources\config\oro\workflows.yml
    yml: vendor\oro\crm\src\Oro\Bundle\SalesBundle\Resources\config\oro\workflows\opportunity_flow\steps.yml
#### 3. Attributes
    Represent data of workflow
    The attribute data is stored inside the WorkflowItem entity
    node: type/options/label/property_path
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
    node: step_to/transition_definition/is_start/is_hidden/acl_resource/frontend_options/form_options/transition_definition/triggers
    supplycore: src\SupplyCore\Bundle\RFPBundle\Resources\config\oro\workflows\sc_request\start.yml
    yml: vendor\oro\crm\src\Oro\Bundle\SalesBundle\Resources\config\oro\workflows\opportunity_flow\transitions.yml
    
#### 6. Transition Definition
    Represent transition conditions and actions
    Pre-actions, pre-conditions(can be displayed)
    Actions, conditions(can be performed)
    Might be empty
    Several transitions might use the same transition definition
    node: preactions/preconditions/conditions/actions
    supplycore: src\SupplyCore\Bundle\RFPBundle\Resources\config\oro\workflows\sc_request\ready_for_review.yml
    yml: vendor\oro\crm\src\Oro\Bundle\SalesBundle\Resources\config\oro\workflows\opportunity_flow\transition_definitions.yml
    
#### 7. Transition Triggers
    Transition Triggers are used to perform Transition by Event or by cron-definition. There are two types of triggers: Event Trigger and Cron Trigger.
    event triggers: 
        supplycore: 
        yml: vendor\oro\commerce-crm\src\Oro\Bridge\QuoteSales\Resources\config\oro\workflows\quote_flow\transitions.yml
    cron triggers:
        supplycore:
        yml: vendor\oro\platform\src\Oro\Bundle\WorkflowBundle\Tests\Functional\Command\DataFixtures\InvalidFilterExpression\workflows.yml
        
#### 8. Translation
    Location: Resources/translations/workfloes.<en>.yml
    Translation for steps, attributes and transitions
    Console Commands: 
        bin/console oro:workflow:translations:dump `workflow_name`
        
#### 9. Actions
    functionality
    Might have parameters
    Might have conditions
    Custom actions: oro_action.action
    List of all actions: debug:container --tag="oro_action.action"
    Action groups: 
        node: parameters/conditions/actions
        run: @run_action_group
![image](https://user-images.githubusercontent.com/56823408/120953769-51613b00-c780-11eb-9858-ae297099b354.png)
#### 10. Conditions
    check that returns
    Might have parameters
    Custom conditions: oro_action.condition
    List of all conditions: debug:container --tag="oro_action.condition"
#### 11. Opreations
    Provide possibility to assign any interaction with user
    Can be added to specific routes or datagrids
    Use actions and conditions
    example: oro CURD operations
    extends/enabled/entities/for_all_entities/exclude_entities/routes/datagrids/for_all_datagrids/exclude_datagrids/order/acl_resource/frontend_options/preactions/preconditions
    attributes/datagrid_options/form_options/form_init/conditions/actions/button_options
![image](https://user-images.githubusercontent.com/56823408/120912923-e3583d80-c6c5-11eb-8693-1da55cfa34ef.png)




    
