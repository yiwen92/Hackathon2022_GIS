# RFC: <!-- Title --> WAY - TiDB GIS support

<!--
This is a template for TiDB's change proposal process, documented [here](./README.md).
-->
Team: Leonardo.TiDB (https://www.nationalgeographic.co.uk/history-and-civilisation/2020/05/leonardo-da-vinci-transformed-mapping-from-art-to-science)
- Leonardo da Vinci is a versatile talent in history, his research areas including painting, architecture, medicine, mechanics and even geography  cartography. In this WAY program, we would like to support spatial data in TiDB, make TiDB to support multi-model and become uniform data platform in future and show our respect to the genius.
- 历史上的莱昂纳多.达芬奇是一个全面发展的通才，他的涉猎领域包括绘画、建筑、医学、机械甚至地理地图学。在 WAY 这个项目里，我们希望开发 TiDB 使其支持空间信息数据，扩展 TiDB 在多模数据库上的能力和应用场景，期待未来 TiDB 成为一个更加通用、完整且统一的大数据平台，以此向这位天才致敬。


## 项目介绍 Program Intro

<!--
A short summary of the proposal:
- What is the issue that the proposal aims to solve?
- What needs to be done in this proposal?
- What is the impact of this proposal?
-->
WAY is a project to let TiDB support spatial data with a live demo. WAY is the short term of "Where Are You".

该项目旨在使 TiDB 支持 GIS ，即地理空间位置数据。该项目命名为 WAY， 是 Where Are You 的简称。

- Author(s): [@dveeden](https://github.com/dveeden), [@madwyn](https://github.com/madwyn), [@mjonss](https://github.com/mjonss), [@yiwen92](https://github.com/yiwen92) (in alphabetical order)
- Last updated: 2022-10-17 <!-- Date -->
- Discussion at: online meetings
- Project detail: https://github.com/orgs/Hackathon-2022-GIS/repositories
- RFC at:  https://github.com/yiwen92/Hackathon2022_GIS


## 背景&动机 Background&Motivation

<!--
An introduction of the necessary background and the problem being solved by the proposed change:
- The drawback of the current feature and the corresponding use case
- The expected outcome of this proposal.
-->

GIS data is widely used in many scenarios, including supply chain, on-line to off-line service, navigation service etc. In this project, we are going to support GIS data inside database to help TiDB expand more scenarios for business.

地理位置信息数据被广泛使用到许多场景中，包括供应链，O2O，导航等等。在该项目中，我们计划在 TiDB 数据库层支持位置信息数据，以拓展 TiDB 的应用场景，挖掘更多商业机会。

## 项目设计 Program Desgin

<!--
A precise statement of the proposed change:
- The new named concepts and a set of metrics to be collected in this proposal (if applicable)
- The overview of the design.
- How it works?
- What needs to be changed to implement this design?
- What may be positively influenced by the proposed change?
- What may be negatively impacted by the proposed change?
-->

Support GIS data type, support basic function, show a live demo with real-world scenario to validate it.

User scenario: shared bike
1. Input 1 location(positioning) point and other shared bike points, store in TiDB
2. Shown all these info in a city map
3. Find a shared bike nearby(within xx m)/ or find nearest one
4. Input destination to get a navigation map —— call map api
5. Show other usage of spatial data(forbidden area recognition)
6. *Explore Business Intelligence(business operation, nearby service recommendation) 
7. *Explore IOT extension solution(low battery warning, ring a bell, abnormal detection etc)

Basic functions:
1. Support spatial data type and SQL usage in TiDB
2. Basic functions like calculate distance in TiDB
3. Define interface to support frontend demo

Advanced features:
1. Integration with third party tool to do navigation
2. Business Intelligence（business operation for shared bike, nearby service recommendation）+ relational database filter
3. IOT extension(low battery warning, ring a bell, abnormal detection etc) + IOT realtime processing

Future proposal：
1. More functions, fully compatible with usages in MySQL
2. Support spatial index to accelarate search performance
3. More innovative scenarios adoption
4. TiDB serve as one-stop data solution with multi-model support(Document, spatial, time-series etc) to archieve more comprehensive usages

## Example scenarios

### A.shared bike

#### value:

provide a complete solution to the basic needs of shared bikes

#### case:

- query for nearby available bikes by single point
- check if current point is in specified polygon
- filter the points by specified filters like availability & health
- query vendor api to plan navigation for two points

#### requirement:
- data type
    - point
    - polygon
- functions
    - query for nearby points by point, with/without filter
    - check if point is in polygon

#### pages:

- index
    - map
    - show points
    - choose point to show navigation (can call phone navigator app, or do a embed one)
    - choose point to mark occupied (use websocket to show realtime update in other phones)
- return bike
    - map
    - show restricted area if user is in one of the restricted areas
    - show current point
    - alert if user is in restricted area

### B.rescue

#### value:

provide a complete solution to the basic needs of road rescue or any other kinds of rescue related to geographical locations  
may used in huge disaster, like let user report their locations, we can prompt the user to avoid the congestion by calculating the hotspot areas

#### case: 

- realtime update points
- query for nearby points by point
- include rescue costs for specified filter (car/bus/truck needs different kinds of rescue vehicle)(may need more effort)
- query vendor api to plan navigation for two points

#### requirement:

- data type
    - point
    - polygon
- functions
    - query for nearby points by point
    - check if point is in polygon

#### pages:

- index
    - map
    - show points (points are updated every second, needs websocket to show realtime update)
    - show the rescue vehicle and breakdown car in different styles
    - choose point to show navigation (can call phone navigator app, or do a embed one)
    - if one point is choosen, it should disappear in other phones (realtime update)
- hotspot
    - map
    - cover map with heatmap

#### SQL syntax
WIP

#### Visual simulator
!['./netherlands_map.png'](netherlands_map.png)

## Rationale

<!--
A discussion of alternate approaches and the trade-offs, advantages, and disadvantages of the specified approach:
- How other systems solve the same issue?
- What other designs have been considered and what are their disadvantages?
- What is the advantage of this design compared with other designs?
- What is the disadvantage of this design?
- What is the impact of not doing this?
-->
  1. https://db-engines.com/en/blog_post/88 - background about spatial db
  2. https://github.com/facebook/rocksdb/blob/main/docs/_posts/2015-07-17-spatial-indexing-in-rocksdb.markdown - Spatial indexing in RocksDB 
  3. https://geojson.org/ - geojson
  4. https://dev.mysql.com/blog-archive/mysql-workbench-6-2-spatial-data/  - mysql
  5. https://account.capitalbikeshare.com/map - source data
  6. https://developers.google.com/maps/documentation/directions/get-directions#maps_http_directions_brooklyn_queens_transit-go - third party api

## Compatibility and Migration Plan
None
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
Daniel, Mattias - Database Developer @ Nertherland

Elwyn - Frontend Developer

Yves - Product Manager

#### Architecture（WIP）

Frontend(elwyn) -> Middleware(mattias) -> Database(daniel)

Vue？          ->  https/json ~ sql    -> GeoJson, sp_functions

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

## Thanks to(in alphabetical order)
Shen Yongyuan,
[@sillydong](https://github.com/sillydong) 


