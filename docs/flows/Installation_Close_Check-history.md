# Installation_Close_Check history

<!-- This page has been generated to be viewed with Zensical, you can not view it just as markdown . Activate content tabs following the doc at https://zensical.org/docs/ -->

=== "Oct 18, 2026 (Initial)"

    _Oct 18, 2026, by gbshahaq in commit chore(monitoring): org state on 2026-10-18 13:10 for monitoring_d700000009o68eae_dev_ed [skip ci]_

    
    ## Flow Diagram [(_View History_)](Installation_Close_Check-history.md)
    
    ![diagram](./Installation_Close_Check-history-1.svg)
    
    <!-- Flow description -->
    
    ## General Information
    
    |<!-- -->|<!-- -->|
    |:---|:---|
    |Object|Installation__c|
    |Process Type|Auto Launched Flow|
    |Trigger Type|Record Before Save|
    |Record Trigger Type|Update|
    |Label|Installation Close Check|
    |Status|Active|
    |Does Require Record Changed To Meet Criteria|✅|
    |Description|An installation cannot be closed without an install date or incomplete handover items|
    |Environments|Default|
    |Interview Label|Installation Close Check {!$Flow.CurrentDateTime}|
    |BuilderType (PM)|LightningFlowBuilder|
    |CanvasMode (PM)|AUTO_LAYOUT_CANVAS|
    |Connector|[No_Install_Date](#no_install_date)|
    |Next Node|[No_Install_Date](#no_install_date)|
    
    
    #### Filters (logic: **and**)
    
    |Filter Id|Field|Operator|Value|
    |:-- |:-- |:--:|:--: |
    |1|Status__c|Equal To|Completed|
    
    
    ## Flow Nodes Details
    
    ### Handover_item_incomplete
    
    |<!-- -->|<!-- -->|
    |:---|:---|
    |Type|Custom Error|
    |Label|Handover item incomplete|
    |Description|error message|
    |Custom Error Messages|errorMessage: >-<br/>&nbsp;&nbsp;One or more handover items are incomplete. Please check before marking install<br/>&nbsp;&nbsp;as closed<br/>isFieldError: false<br/>|
    
    
    ### Install_Date_Missing
    
    |<!-- -->|<!-- -->|
    |:---|:---|
    |Type|Custom Error|
    |Label|Install Date Missing|
    |Description|Refuses to close an installation that was never given an install date.|
    |Custom Error Messages|errorMessage: Set the install date before closing this installation.<br/>isFieldError: false<br/>|
    
    
    ### Are_related_handover_items_incomplete
    
    |<!-- -->|<!-- -->|
    |:---|:---|
    |Type|Decision|
    |Label|Are related handover items incomplete?|
    |Default Connector Label|No|
    
    
    #### Rule Yes (Yes)
    
    |<!-- -->|<!-- -->|
    |:---|:---|
    |Connector|[Handover_item_incomplete](#handover_item_incomplete)|
    |Condition Logic|and|
    
    
    
    
    |Condition Id|Left Value Reference|Operator|Right Value|
    |:-- |:-- |:--:|:--: |
    |1|[Check_Handover_Items](#check_handover_items)|Is Null|False|
    
    
    
    
    ### No_Install_Date
    
    |<!-- -->|<!-- -->|
    |:---|:---|
    |Type|Decision|
    |Label|No Install Date|
    |Description|Was the installation ever given an install date?|
    |Default Connector|[Check_Handover_Items](#check_handover_items)|
    |Default Connector Label|Install date set|
    
    
    #### Rule Date_Missing (Date missing)
    
    |<!-- -->|<!-- -->|
    |:---|:---|
    |Connector|[Install_Date_Missing](#install_date_missing)|
    |Condition Logic|and|
    
    
    
    
    |Condition Id|Left Value Reference|Operator|Right Value|
    |:-- |:-- |:--:|:--: |
    |1|$Record.Install_Date__c|Is Null|True|
    
    
    
    
    ### Check_Handover_Items
    
    |<!-- -->|<!-- -->|
    |:---|:---|
    |Type|Record Lookup|
    |Object|Handover_Item__c|
    |Label|Check Handover Items|
    |Assign Null Values If No Records Found|⬜|
    |Get First Record Only|✅|
    |Queried Fields|Id|
    |Store Output Automatically|✅|
    |Connector|[Are_related_handover_items_incomplete](#are_related_handover_items_incomplete)|
    
    
    #### Filters (logic: **and**)
    
    |Filter Id|Field|Operator|Value|
    |:-- |:-- |:--:|:--: |
    |1|Installation__c|Equal To|$Record.Name|
    |2|Is_Done__c|Equal To|⬜|
    
    
    
    
    
    
    
    
    ___
    
    _Documentation generated from branch monitoring_d700000009o68eae_dev_ed by [sfdx-hardis](https://sfdx-hardis.cloudity.com), featuring [salesforce-flow-visualiser](https://github.com/toddhalfpenny/salesforce-flow-visualiser)_

