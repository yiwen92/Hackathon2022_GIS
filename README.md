# Hackathon2022_GIS
Support GIS for TiDB
<!--
This is a template for TiDB's change proposal process, documented [here](./README.md).
-->

# RFC: <!-- Title --> GIS - GIS support For TiDB

- Author(s): [@dveeden](https://github.com/dveeden), [@madwyn](https://github.com/madwyn), [@mjonss](https://github.com/mjonss), [@yiwen92](https://github.com/yiwen92) (in alphabetical order)
- Last updated: 2022-10-06 <!-- Date -->
- Discussion at: online meeting
- Project at: https://github.com/yiwen92/Hackathon2022_GIS

## 项目介绍

<!--
A short summary of the proposal:
- What is the issue that the proposal aims to solve?
- What needs to be done in this proposal?
- What is the impact of this proposal?
-->

XXX is a project to let TiDB support GIS data with a live demo.
该项目旨在使 TiDB 支持 GIS 数据。

## 背景&动机

<!--
An introduction of the necessary background and the problem being solved by the proposed change:
- The drawback of the current feature and the corresponding use case
- The expected outcome of this proposal.
-->

GIS data is widely used in many scenarios, including supply chain, on-line service, navigation service etc, we are going to support GIS data inside TiDB to help service more scenarios.

## 项目设计

<!--
A precise statement of the proposed change:
- The new named concepts and a set of metrics to be collected in this proposal (if applicable)
- The overview of the design.
- How it works?
- What needs to be changed to implement this design?
- What may be positively influenced by the proposed change?
- What may be negatively impacted by the proposed change?
-->

Support GIS data type, support basic function, show a live demo to validate it.

Main functions:

Future proposal：

### Example

#### SQL 语句

#### json type


#### 对应的可视化渲染结果（效果模拟图）

!['./GIS-demo.png'](GIS-demo.png)

## Rationale

<!--
A discussion of alternate approaches and the trade-offs, advantages, and disadvantages of the specified approach:
- How other systems solve the same issue?
- What other designs have been considered and what are their disadvantages?
- What is the advantage of this design compared with other designs?
- What is the disadvantage of this design?
- What is the impact of not doing this?
-->


## Compatibility and Migration Plan

<!--
A discussion of the change with regard to the compatibility issues:
- Does this proposal make TiDB not compatible with the old versions?
- Does this proposal make TiDB not compatible with TiDB tools?
    + [BR](https://github.com/pingcap/br)
    + [DM](https://github.com/pingcap/dm)
    + [Dumpling](https://github.com/pingcap/dumpling)
    + [TiCDC](https://github.com/pingcap/ticdc)
    + [TiDB Binlog](https://github.com/pingcap/tidb-binlog)
    + [TiDB Lightning](https://github.com/pingcap/tidb-lightning)
- If the existing behavior will be changed, how will we phase out the older behavior?
- Does this proposal make TiDB more compatible with MySQL?
- What is the impact(if any) on the data migration:
    + from MySQL to TiDB
    + from TiDB to MySQL
    + from old TiDB cluster to new TiDB cluster
-->


## Implementation

<!--
A detailed description for each step in the implementation:
- Does any former steps block this step?
- Who will do it?
- When to do it?
- How long it takes to accomplish it?
-->




1st meeting note: Setup team, Sync-up idea

Task:
Preparation & investigation
RFC draft
Repo setup

2nd meeting note：framework discussion, responsibility division

Task:
Frontend work & Backend work
RFC commit & Org setup
Presenting initial


## Testing Plan

<!--
A brief description on how the implementation will be tested. Both integration test and unit test should consider the following things:
- How to ensure that the implementation works as expected?
- How will we know nothing broke?
-->
Demo

## Open issues (if applicable)

<!--
A discussion of issues relating to this proposal for which the author does not know the solution. This section may be omitted if there are none.
-->
None
