# 查询性能： TDengine 最高达到了 InfluxDB 的 37 倍、 TimescaleDB 的 28.6 倍 - 涛思数据TDengine - 博客园
- URL: https://www.cnblogs.com/taosdata/p/17199193.html
- Added At: 2025-05-27 02:14:02
- [Link To Text](2025-05-27-查询性能：-tdengine-最高达到了-influxdb-的-37-倍、-timescaledb-的-28.6-倍---涛思数据tdengine---博客园_raw.md)

## TL;DR
TSBS时序数据库性能测试显示，TDengine在4000设备和100设备两种场景下，查询性能全面优于InfluxDB和TimescaleDB，最高达37倍和28.6倍，且资源开销更低。实际案例中，TDengine处理数十亿行数据查询仅需0.1秒左右。

## Summary
1. **测试背景**：
   - 基于TSBS时序数据库性能基准测试，对比TDengine、InfluxDB和TimescaleDB的查询性能。
   - 测试数据集：
     - 场景一：100设备 × 10指标（4天数据）
     - 场景二：4000设备 × 10指标

2. **测试配置**：
   - TimescaleDB：设置为8个Chunk（推荐配置）
   - InfluxDB：开启TSI(time series index)
   - TDengine：默认6个虚拟节点(vnodes)，其他参数保持默认
   - 单查询运行5000次取平均值，并发客户端Workers数量为8

3. **4000设备测试结果**：
   - **Simple Rollups查询**：
     - TDengine在所有类型查询响应时间上均优于InfluxDB和TimescaleDB
   - **Aggregates查询**：
     - cpu-max-all-8查询性能是InfluxDB的7倍，TimescaleDB的6倍
   - **Double rollups查询**：
     - double-groupby-5和double-groupby-all查询性能是TimescaleDB的24倍
     - double-groupby-5查询是InfluxDB的26倍，double-groupby-all是其34倍
   - **Thresholds查询**：
     - high-cpu-all查询性能是InfluxDB的15倍，TimescaleDB的1.23倍
   - **Complex queries查询**：
     - lastpoint查询性能是TimescaleDB的5倍，InfluxDB的21倍
     - groupby-orderby-limit查询性能是TimescaleDB的8倍，InfluxDB的15倍

4. **资源开销对比**：
   - **CPU开销**：
     - TDengine整体CPU占用约80%，完成查询时间仅为其他数据库的1/20
     - 整体CPU计算时间消耗是InfluxDB的1/10
   - **内存状况**：
     - TDengine内存维持相对平稳
     - TimescaleDB内存呈现增加后恢复状态
   - **网络带宽**：
     - TDengine网络带宽开销最高（因最短时间完成查询）

5. **100设备测试结果**：
   - TDengine在所有15个查询中均优于其他数据库
   - 最高性能达到：
     - TimescaleDB的28.6倍
     - InfluxDB的37倍

6. **实际应用案例**：
   - 广东省环境科学研究院项目：
     - 76亿行超级表的分组TOP查询仅0.2秒
     - 返回2,968行数据仅0.06秒
     - 返回5,280行数据仅0.1秒

7. **总结**：
   - 在两种场景的15个查询类型中，TDengine平均响应时间全面优于其他数据库
   - 相对于InfluxDB：
     - 场景一性能是其1.9-37倍
     - 场景二性能是其1.8-34.2倍
   - 相对于TimescaleDB：
     - 场景一性能是其1.1-28.6倍
     - 场景二性能是其1.2-24.6倍
