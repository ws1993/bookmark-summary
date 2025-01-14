Title: 时序数据库 InfluxDB、TimeScaleDB和TDengine 对比

URL Source: https://www.cnblogs.com/miracle-luna/p/17973749

Published Time: 2024-01-19T00:53:00.0000000+08:00

Markdown Content:
### 时序数据库 InfluxDB、TimeScaleDB和TDengine 对比

* * *

### 一、时序数据库简介

#### 1、InfluxDB

InfluxDB 是由 **InfluxData** 开发的。InfluxData 是一家专注于时间序列数据处理和分析的技术公司，他们致力于提供高性能、可扩展的时间序列数据库和相关工具。InfluxDB 是他们的核心产品，是一款开源的时间序列数据库，广泛应用于实时监控、物联网和指标数据存储等领域。InfluxData 公司提供了全面的解决方案，包括 InfluxDB 的企业版、云服务、数据可视化和监控工具，以帮助用户更好地管理和分析时间序列数据。  
InfluxDB 是一个开源的时间序列数据库，专注于实时监控和物联网应用。它具有灵活的数据模型和高性能的存储与查询能力，适用于需要处理大量实时数据的场景。

**1）官网地址**  
[https://www.influxdata.com/](https://www.influxdata.com/)

![Image 32](https://img2024.cnblogs.com/blog/1148440/202401/1148440-20240120230735650-1297045267.png)

**2）官网文档**  
[https://docs.influxdata.com/](https://docs.influxdata.com/)

![Image 33](https://img2024.cnblogs.com/blog/1148440/202401/1148440-20240120230845927-1969668248.png)

#### 2、TimescaleDB

TimeScaleDB 是由 **TimeScale** 开发的。TimeScale是一家专注于时间序列数据处理的技术公司，他们致力于提供高性能、可扩展的时间序列数据库解决方案。TimeScaleDB是他们的核心产品，建立在PostgreSQL之上，为用户提供了强大的时间序列数据存储和查询能力。TimeScale公司的目标是为各行业的用户提供可靠、高效的时间序列数据管理和分析工具。  
TimeScaleDB是建立在PostgreSQL之上的开源时间序列数据库，结合了关系型数据库和时间序列功能。它支持SQL查询和高级功能，适用于需要同时满足时间序列和关系型需求的应用。

**1）官网地址**  
[https://www.timescale.com/](https://www.timescale.com/)

![Image 34](https://img2024.cnblogs.com/blog/1148440/202401/1148440-20240120231059132-60828369.png)

**2）官网文档**  
[https://docs.timescale.com/](https://docs.timescale.com/)

![Image 35](https://img2024.cnblogs.com/blog/1148440/202401/1148440-20240120231018580-1161318346.png)

#### 3、TDengine

TDengine（原名为TaosData）是由中国的TD Tech（天地伟业）开发的。TD Tech 是一家专注于大数据和物联网领域的技术公司，致力于提供高性能的数据存储和分析解决方案。  
TDengine 是一款高性能的时间序列数据库，专为实时处理大规模时间序列数据而设计。它具有高速数据摄入和实时分析的能力，适用于需要处理大规模数据的应用，如物联网、金融和工业领域。

**1）官网地址**  
[https://tdengine.com/](https://tdengine.com/)

![Image 36](https://img2024.cnblogs.com/blog/1148440/202401/1148440-20240120231153533-1592230866.png)

**2）官网文档**  
[https://docs.tdengine.com/](https://docs.tdengine.com/)

![Image 37](https://img2024.cnblogs.com/blog/1148440/202401/1148440-20240120231223234-930584849.png)

### 二、时序数据库对比

InfluxDB、TimeScaleDB和TDengine都是时序数据库，它们在处理时间序列数据方面有一些共同点，但也存在一些区别。  
以下是它们在多个维度上的比较：

#### 1、开源性

1）InfluxDB：是一个开源的时间序列数据库。  
2）TimeScaleDB：是一个开源的时间序列数据库，建立在PostgreSQL之上。  
3）TDengine：是一个开源的时序数据库。

#### 2、开源许可

1）InfluxDB：采用MIT许可证。  
2）TimeScaleDB：采用Apache许可证。  
3）TDengine：采用GNU Affero General Public License v3.0。

#### 3、开发语言

1）InfluxDB：使用Go语言编写。  
2）TimeScaleDB：使用C语言编写。  
3）TDengine：使用C语言编写。

#### 4、数据模型

1）InfluxDB：使用类似于SQL的查询语言，支持tag和field的概念，数据以测量(measurement)、标签(tags)和字段(fields)的形式组织。  
2）TimeScaleDB：支持SQL，具有与PostgreSQL类似的数据模型，能够处理关系型数据和时序数据。  
3）TDengine：使用类似于SQL的查询语言，引入了超级表(super table)的概念，支持多层次的时序数据组织。

#### 5、查询语言

1）InfluxDB：使用InfluxQL查询语言，支持聚合、降采样等时间序列特定的功能。  
2）TimeScaleDB：支持SQL查询，具备丰富的关系型数据库功能，如JOIN和窗口函数。  
3）TDengine：使用Taos Query Language (TDengine SQL)进行查询，支持类SQL语法和时间序列特定的功能。

#### 6、水平扩展性

1）InfluxDB：通过Influx Enterprise支持水平扩展。  
2）TimeScaleDB：可以通过PostgreSQL的水平扩展来实现。  
3）TDengine：支持水平扩展，可以通过添加节点来增加存储和计算能力。

#### 7、存储引擎

1）InfluxDB：使用TSM（Time Structured Merge）引擎。  
2）TimeScaleDB：建立在PostgreSQL之上，使用表分区和复制机制来提高查询性能。  
3）TDengine：使用自研的分层存储引擎，支持数据的快速写入和检索。

#### 8、性能

1）InfluxDB：以高写入性能和低延迟为特点。  
2）TimeScaleDB：利用PostgreSQL的强大性能，并在大规模数据上表现良好。  
3）TDengine：被设计为高性能时序数据库，特别适用于高并发写入和查询。

#### 9、数据压缩和存储

1）InfluxDB：支持数据的自动压缩和过期策略。  
2）TimeScaleDB：利用PostgreSQL的表分区和复制来管理数据。  
3）TDengine：使用了多层次的数据压缩算法，以最小化存储占用。

#### 10、数据保留策略

1）InfluxDB：通过保留策略定义数据的保存时间。  
2）TimeScaleDB：支持通过表分区和时间戳进行数据保留。  
3）TDengine：具有数据保留和数据压缩策略。

#### 11、生态系统和集成

1）InfluxDB：具有丰富的生态系统和第三方工具集成，如Grafana、Telegraf等。  
2）TimeScaleDB：作为PostgreSQL的扩展，可以利用PostgreSQL的生态系统和工具。  
3）TDengine：提供了自己的生态系统和工具，支持与其他系统的数据集成。

#### 12、社区支持

1）InfluxDB：拥有活跃的社区，广泛应用于监控和度量等领域。  
2）TimeScaleDB：社区较大，受到PostgreSQL社区的支持。  
3）TDengine：相对较新，但在物联网和工业领域有一些应用，在中国有一定的用户基础。

#### 13、适用场景

1）InfluxDB：主要用于实时监控、物联网和传感器数据处理。  
2）TimeScaleDB：适合需要同时处理时间序列和关系型数据的应用，如金融和物流。  
3）TDengine：专注于高速数据摄入和实时分析，适用于物联网、工业领域和大数据应用。

#### 14、时序数据库排名

1）InfluxDB：目前稳居**第1名**，Score：27.56。  
2）TimeScaleDB：目前第5名，Score：5.24。  
3）TDengine：目前第8名，相比去年1月份上升了2名，Score：3.43。

![Image 38](https://img2024.cnblogs.com/blog/1148440/202401/1148440-20240120230639792-1724688418.png)

在选择这些数据库时，需要考虑具体要求，例如数据量、写入频率、查询模式、集成需求、可扩展性。

每个数据库都有其优势，并且可能更适合特定的场景。
