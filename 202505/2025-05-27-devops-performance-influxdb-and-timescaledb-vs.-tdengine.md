# DevOps Performance: InfluxDB and TimescaleDB vs. TDengine
- URL: https://tdengine.com/devops-performance-comparison-influxdb-and-timescaledb-vs-tdengine/
- Added At: 2025-05-27 02:13:02
- [Link To Text](2025-05-27-devops-performance-influxdb-and-timescaledb-vs.-tdengine_raw.md)

## TL;DR
TDengine在时间序列数据库测试中全面领先，数据摄取速度比InfluxDB快3-10倍，比TimescaleDB快1.5-6.7倍；查询性能最高快37倍；磁盘空间节省达26.9倍，显著降低资源消耗。

## Summary
1. **时间序列数据库概述**：
   - 时间序列数据（TSDB）因其数据量大和复杂性而需要专门的数据库。
   - 性能、精确性和可扩展性对TSDB尤为重要，直接影响总拥有成本（TCO）。

2. **测试目的**：
   - 通过对比测试展示TDengine在数据摄取、压缩和查询性能上的优势。
   - 测试对象包括InfluxDB和TimescaleDB。

3. **测试方法**：
   - 使用开源工具Time Series Benchmark Suite（TSBS）进行客观评估。
   - 测试在AWS的相同系统上运行，确保公平性。
   - 数据集包括DevOps场景，涵盖不同规模和复杂度的查询。

4. **性能对比**：
   - **数据摄取性能**：
     - TDengine在所有测试场景中表现最快，速度是其他产品的1.5到10.6倍。
   - **资源消耗**：
     - TDengine的CPU使用率显著低于InfluxDB（峰值低于15%，而InfluxDB超过90%）。
     - TimescaleDB在数据压缩和排序上耗时更长。
   - **查询性能**：
     - TDengine在所有查询类型中响应最快。
       - 简单查询：比InfluxDB快1.9到12.1倍，比TimescaleDB快1.9到12.1倍。
       - 复杂查询（如`double-groupby-all`）：比TimescaleDB快24.3倍，比InfluxDB快34.3倍。
     - 其他查询类别表现：
       - 聚合查询：比InfluxDB快6.9倍，比TimescaleDB快6.1倍。
       - 阈值查询：比InfluxDB快15.1倍，比TimescaleDB快1.9倍。
       - 复杂查询：比InfluxDB快21.1倍，比TimescaleDB快8.4倍。
   - **磁盘存储**：
     - 小规模场景：TDengine和InfluxDB占用空间相近。
     - 大规模场景（百万或千万设备）：
       - TDengine的存储需求不到InfluxDB的四分之一。
       - TimescaleDB的磁盘占用显著更高（千万设备场景中，TDengine比TimescaleDB节省26.9倍空间）。

5. **结论**：
   - TDengine在摄取、压缩和查询性能上全面领先。
     - 数据摄取：比TimescaleDB快1.5到6.7倍，比InfluxDB快3.0到10.6倍。
     - 压缩：比TimescaleDB节省26.9倍磁盘空间，比InfluxDB节省4.5倍。
     - 查询：复杂查询比TimescaleDB快28.6倍，比InfluxDB快37.0倍。
   - 设计优势：
     - 专为时间序列数据设计，采用单表存储和超级表（supertable）等创新技术。
   - 综合优势：
     - 高性能、低资源消耗、易用性，适合企业扩展数据管道。

6. **附加资源**：
   - 提供完整报告下载链接和视频概述。
   - 作者介绍：Chait Diwadkar（前TDengine解决方案工程总监）。
