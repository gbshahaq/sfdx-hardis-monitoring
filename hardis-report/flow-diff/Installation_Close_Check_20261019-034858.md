# Installation Close Check

## Flow Diagram [(_View History_)](Installation_Close_Check-history.md)

```mermaid
%% If you read this, your Markdown visualizer does not handle MermaidJS syntax.
%% - If you are in VS Code, install extension `Markdown Preview Mermaid Support` at https://marketplace.visualstudio.com/items?itemName=bierner.markdown-mermaid
%% - If you are using sfdx-hardis, try to define env variable `MERMAID_MODES=cli,docker` ,then run again the command to regenerate markdown with SVG images.
%% - If you are within a Zensical site, define the mermaid custom fence in `mkdocs.yml` as described in https://zensical.org/docs/
%% - As a last resort, you can copy-paste this MermaidJS code into https://mermaid.live/ to see the flow diagram

flowchart TB
START(["START<br/><b>AutoLaunched Flow</b></br>Type: <b>Record Before Save</b>"]):::startClass
click START "#general-information" "1424613916"

Handover_item_incomplete("🚫 <em></em><br/>Handover item incomplete"):::customErrors
click Handover_item_incomplete "#handover_item_incomplete" "1127674392"

Install_Date_Missing("🚫 <em></em><br/>Install Date Missing"):::customErrors
click Install_Date_Missing "#install_date_missing" "426048938"

Are_related_handover_items_incomplete{"🔀 <em></em><br/>Are related handover items incomplete?"}:::decisions
click Are_related_handover_items_incomplete "#are_related_handover_items_incomplete" "2119811928"

No_Install_Date{"🔀 <em></em><br/>No Install Date"}:::decisions
click No_Install_Date "#no_install_date" "1511554579"

Check_Handover_Items[("🔍 <em></em><br/>Check Handover Items")]:::recordLookups
click Check_Handover_Items "#check_handover_items" "2789252844"

Handover_item_incomplete --> END_Handover_item_incomplete
Install_Date_Missing --> END_Install_Date_Missing
Are_related_handover_items_incomplete --> |"Yes"| Handover_item_incomplete
Are_related_handover_items_incomplete --> |"No"| END_Are_related_handover_items_incomplete
No_Install_Date --> |"Date missing"| Install_Date_Missing
No_Install_Date --> |"Install date set"| Check_Handover_Items
Check_Handover_Items --> Are_related_handover_items_incomplete
START -->  No_Install_Date
END_Handover_item_incomplete(( END )):::endClass
END_Install_Date_Missing(( END )):::endClass
END_Are_related_handover_items_incomplete(( END )):::endClass


classDef actionCalls fill:#D4E4FC,color:black,text-decoration:none,max-height:100px
classDef assignments fill:#FBEED7,color:black,text-decoration:none,max-height:100px
classDef collectionProcessors fill:#F0E3FA,color:black,text-decoration:none,max-height:100px
classDef customErrors fill:#FFE9E9,color:black,text-decoration:none,max-height:100px
classDef decisions fill:#FDEAF6,color:black,text-decoration:none,max-height:100px
classDef loops fill:#FDEAF6,color:black,text-decoration:none,max-height:100px
classDef recordCreates fill:#FFF8C9,color:black,text-decoration:none,max-height:100px
classDef recordDeletes fill:#FFF8C9,color:black,text-decoration:none,max-height:100px
classDef recordLookups fill:#EDEAFF,color:black,text-decoration:none,max-height:100px
classDef recordRollbacks fill:#FFF8C9,color:black,text-decoration:none,max-height:100px
classDef recordUpdates fill:#FFF8C9,color:black,text-decoration:none,max-height:100px
classDef screens fill:#DFF6FF,color:black,text-decoration:none,max-height:100px
classDef subflows fill:#D4E4FC,color:black,text-decoration:none,max-height:100px
classDef startClass fill:#D9F2E6,color:black,text-decoration:none,max-height:100px
classDef endClass fill:#F9BABA,color:black,text-decoration:none,max-height:100px
classDef transforms fill:#FDEAF6,color:black,text-decoration:none,max-height:100px


```

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