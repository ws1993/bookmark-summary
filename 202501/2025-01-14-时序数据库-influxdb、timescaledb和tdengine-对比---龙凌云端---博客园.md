# 时序数据库 InfluxDB、TimeScaleDB和TDengine 对比 - 龙凌云端 - 博客园
- URL: https://www.cnblogs.com/miracle-luna/p/17973749
- Added At: 2025-01-14 05:42:13
- [Link To Text](2025-01-14-时序数据库-influxdb、timescaledb和tdengine-对比---龙凌云端---博客园_raw.md)

## TL;DR
本文介绍了三种主流时序数据库：InfluxDB、TimeScaleDB和TDengine，分别从开源性、开发语言、数据模型、查询语言、性能、存储引擎、数据压缩、生态系统等方面进行了详细对比。InfluxDB适用于实时监控和物联网，TimeScaleDB适合处理关系型数据的场景，TDengine则在大数据和物联网领域表现优异。选择时序数据库时需根据具体需求进行权衡。

## Summary
1. **时序数据库简介**：
   - **InfluxDB**：
     - 由InfluxData开发，专注于时间序列数据处理和分析。
     - 开源时间序列数据库，适用于实时监控和物联网应用。
     - 提供企业版、云服务、数据可视化和监控工具。
   - **TimeScaleDB**：
     - 由TimeScale开发，建立在PostgreSQL之上。
     - 结合关系型数据库和时间序列功能，支持SQL查询。
   - **TDengine**：
     - 由中国的TD Tech开发，专注于大数据和物联网领域。
     - 高性能时间序列数据库，适用于大规模数据处理。

2. **官网信息**：
   - **InfluxDB**：
     - 官网地址：[https://www.influxdata.com/](https://www.influxdata.com/)
     - 官网文档：[https://docs.influxdata.com/](https://docs.influxdata.com/)
   - **TimeScaleDB**：
     - 官网地址：[https://www.timescale.com/](https://www.timescale.com/)
     - 官网文档：[https://docs.timescale.com/](https://docs.timescale.com/)
   - **TDengine**：
     - 官网地址：[https://tdengine.com/](https://tdengine.com/)
     - 官网文档：[https://docs.tdengine.com/](https://docs.tdengine.com/)

3. **时序数据库对比**：
   - **开源性**：
     - InfluxDB、TimeScaleDB和TDengine均为开源数据库。
   - **开源许可**：
     - InfluxDB采用MIT许可证。
     - TimeScaleDB采用Apache许可证。
     - TDengine采用GNU Affero General Public License v3.0。
   - **开发语言**：
     - InfluxDB使用Go语言。
     - TimeScaleDB和TDengine使用C语言。
   - **数据模型**：
     - InfluxDB使用测量、标签和字段的形式组织数据。
     - TimeScaleDB支持关系型数据和时序数据。
     - TDengine引入超级表概念，支持多层次时序数据组织。
   - **查询语言**：
     - InfluxDB使用InfluxQL。
     - TimeScaleDB支持SQL。
     - TDengine使用Taos Query Language (TDengine SQL)。
   - **水平扩展性**：
     - InfluxDB通过Influx Enterprise支持水平扩展。
     - TimeScaleDB通过PostgreSQL的水平扩展实现。
     - TDengine支持通过添加节点来增加存储和计算能力。
   - **存储引擎**：
     - InfluxDB使用TSM引擎。
     - TimeScaleDB使用PostgreSQL的表分区和复制机制。
     - TDengine使用自研的分层存储引擎。
   - **性能**：
     - InfluxDB以高写入性能和低延迟为特点。
     - TimeScaleDB在大规模数据上表现良好。
     - TDengine适用于高并发写入和查询。
   - **数据压缩和存储**：
     - InfluxDB支持自动压缩和过期策略。
     - TimeScaleDB利用表分区和复制管理数据。
     - TDengine使用多层次数据压缩算法。
   - **数据保留策略**：
     - InfluxDB通过保留策略定义数据保存时间。
     - TimeScaleDB支持通过表分区和时间戳进行数据保留。
     - TDengine具有数据保留和压缩策略。
   - **生态系统和集成**：
     - InfluxDB具有丰富的生态系统和第三方工具集成。
     - TimeScaleDB可利用PostgreSQL的生态系统和工具。
     - TDengine提供自己的生态系统和工具。
   - **社区支持**：
     - InfluxDB拥有活跃的社区。
     - TimeScaleDB受到PostgreSQL社区的支持。
     - TDengine在中国有一定的用户基础。
   - **适用场景**：
     - InfluxDB适用于实时监控和物联网。
     - TimeScaleDB适合金融和物流等需要处理关系型数据的应用。
     - TDengine适用于物联网、工业领域和大数据应用。
   - **时序数据库排名**：
     - InfluxDB稳居第1名。
     - TimeScaleDB第5名。
     - TDengine第8名，相比去年上升2名。

4. **总结**：
   - 在选择时序数据库时，需考虑数据量、写入频率、查询模式、集成需求和可扩展性。
   - 每个数据库都有其优势，适合特定的应用场景。
