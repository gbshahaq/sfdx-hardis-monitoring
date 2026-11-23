<!-- This file is auto-generated. if you do not want it to be overwritten, set TRUE in the line below -->
<!-- DO_NOT_OVERWRITE_DOC=FALSE -->

# Handover_Item__c

## Schema

```mermaid
graph TD
Installation__c["Installation"]:::customObject
click Installation__c "../Installation__c/"
Handover_Item__c["Handover Item"]:::mainObject
click Handover_Item__c "../Handover_Item__c/"

Handover_Item__c -->|Installation__c| Installation__c

classDef object fill:#D6E9FF,stroke:#0070D2,stroke-width:3px,rx:12px,ry:12px,shadow:drop,color:#333;
classDef customObject fill:#FFF4C2,stroke:#CCAA00,stroke-width:3px,rx:12px,ry:12px,shadow:drop,color:#333;
classDef customObjectManaged fill:#FFD8B2,stroke:#CC5500,stroke-width:3px,rx:12px,ry:12px,shadow:drop,color:#333;
classDef mainObject fill:#FFB3B3,stroke:#A94442,stroke-width:4px,rx:14px,ry:14px,shadow:drop,color:#333,font-weight:bold;
linkStyle 0 stroke:#A6A6A6,stroke-width:2px;

```


<!-- Object description -->

## Fields

| Name | Label | Type | Description |
| :-------- | :---- | :--: | :---------- | 
| External_Id__c | External Id | Text | <!-- --> |
| Installation__c | Installation | Lookup | <!-- --> |
| Is_Done__c | Is Done | Checkbox | <!-- --> |
| Is_Template__c | Is Template | Checkbox | <!-- --> |
| Label__c | Label | Text | <!-- --> |
| Sequence__c | Sequence | Number | <!-- --> |


## Related Flows

| Object | Name | Type | Description | Status |
| :----  | :-------- | :--: | :---------- | :----- |
| Installation__c | [Installation_Close_Check](../flows/Installation_Close_Check.md) [🕒](../flows/Installation_Close_Check-history.md) | Record Before Save | An installation cannot be closed without an install date or incomplete handover items | Active |
























## Related Profiles

| Profile | User License |
| :----      | :--: | 
| [Admin](../profiles/Admin.md) | Salesforce |
| [Chatter Free User](../profiles/Chatter%20Free%20User.md) | Chatter Free |
| [Chatter Moderator User](../profiles/Chatter%20Moderator%20User.md) | Chatter Free |
| [ContractManager](../profiles/ContractManager.md) | Salesforce |
| [Cross Org Data Proxy User](../profiles/Cross%20Org%20Data%20Proxy%20User.md) | XOrg Proxy User |
| [Custom%3A Marketing Profile](../profiles/Custom%253A%20Marketing%20Profile.md) | Salesforce |
| [Custom%3A Sales Profile](../profiles/Custom%253A%20Sales%20Profile.md) | Salesforce |
| [Custom%3A Support Profile](../profiles/Custom%253A%20Support%20Profile.md) | Salesforce |
| [Customer Community Login User](../profiles/Customer%20Community%20Login%20User.md) | Customer Community Login |
| [Customer Community User](../profiles/Customer%20Community%20User.md) | Customer Community |
| [Helios Crew](../profiles/Helios%20Crew.md) | Salesforce |
| [MarketingProfile](../profiles/MarketingProfile.md) | Salesforce |
| [Partner Community Login User](../profiles/Partner%20Community%20Login%20User.md) | Partner Community Login |
| [Partner Community User](../profiles/Partner%20Community%20User.md) | Partner Community |
| [Read Only](../profiles/Read%20Only.md) | Salesforce |
| [SolutionManager](../profiles/SolutionManager.md) | Salesforce |
| [Standard](../profiles/Standard.md) | Salesforce |


## Related Permission Sets

| Permission Set | User License |
| :----      | :--: | 
| [Helios_Delivery_Manager](../permissionsets/Helios_Delivery_Manager.md) | None |


[![SFDX-Hardis is provided by Cloudity](https://raw.githubusercontent.com/hardisgroupcom/sfdx-hardis/refs/heads/main/docs/assets/images/cloudity-banner.png)](https://cloudity.com?ref=sfdxhardis)

_Documentation generated with [sfdx-hardis](https://sfdx-hardis.cloudity.com), by [Cloudity](https://www.cloudity.com/) & [friends](https://github.com/hardisgroupcom/sfdx-hardis/graphs/contributors)_
