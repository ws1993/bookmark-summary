Title: DevOps Performance: InfluxDB and TimescaleDB vs. TDengine

URL Source: https://tdengine.com/devops-performance-comparison-influxdb-and-timescaledb-vs-tdengine/

Published Time: 2023-02-20T16:58:39-08:00

Markdown Content:
> _An in-depth look at the performance of key time-series databases_
> 
> 
> _For a quick overview, see [our infographic](https://content.tdengine.com/hubfs/Downloads/TSBS%20DevOps%20Performance%20Infographic.pdf) or watch a [video](https://tdengine.com/devops-performance-comparison-influxdb-and-timescaledb-vs-tdengine/#video)_

The sheer volume and complex nature of time-series data has given rise to the purpose-built [time series database](https://tdengine.com/what-is-a-time-series-database/) (TSDB). While performance is crucial for all databases, the scale and complexity of time-series data makes performance, precision, and scalability especially important.

The performance of your TSDB doesn’t just impact your ability to ingest, store, and analyze large amounts of data; it directly affects your [total cost of ownership](https://tdengine.com/reduce-tco/) (TCO). Better ingestion rates, query response times and compression ratios mean your system consumes fewer resources to process the same amount of data. To demonstrate TDengine’s [robust performance](https://tdengine.com/high-performance/), we evaluated the platform against two key players in this space: InfluxDB and TimescaleDB.

The findings clearly show that _TDengine offers significant advantages over both InfluxDB and TimescaleDB_ in terms of data ingestion, compression, and query performance. In addition, TDengine uses fewer server-side CPU resources than either competing time series DB to process identical datasets.

Objective Evaluation via the Time Series Benchmark Suite
--------------------------------------------------------

To ensure an even playing field, we used the open source Time Series Benchmark Suite (TSBS) framework and ran the tests on identical systems in AWS. TSBS is designed for objective database evaluations and generates datasets for a range of recommended ingestion and query scenarios. TSBS is used by other database providers, including VictoriaMetrics and Timescale, to perform evaluations similar to the one described here.

TSBS is an open and independent framework, meaning the test procedures and datasets generated aren’t designed to benefit any database platform, and allows anyone to conduct an objective evaluation.

This evaluation applied the TSBS DevOps dataset, which includes small and large-scale scenarios, each with ten metrics, ten tags, and a microsecond-precision timestamp. For detailed information, see the official [TSBS repository in GitHub](https://github.com/timescale/tsbs).

Performance Comparison
----------------------

### Ingestion Performance

Time series databases need to ingest massive amounts of data, and _TDengine achieves the fastest ingestion speeds across all TSBS scenarios_, ranging from 1.5 to 10.6 times the speed of the other products.

[![Image 1](https://eujqw4hwudm.exactdn.com/wp-content/uploads/22.093-01-ingestion.png?strip=all&lossy=1&sharp=1&ssl=1)](https://eujqw4hwudm.exactdn.com/wp-content/uploads/22.093-01-ingestion.png?strip=all&lossy=1&sharp=1&w=2560&ssl=1)

TDengine ingests data significantly faster than TimescaleDB or InfluxDB

### Resource Consumption

In addition, _TDengine uses less processing power than InfluxDB or TimescaleDB_ to ingest the datasets. At its peak, InfluxDB’s CPU usage exceeds 90% during the ingestion process, while TDengine remains under 15%. Although TimescaleDB used a similar amount of CPU resources to TDengine, it spent far more time to compress and order the data after writing it to the database.

[![Image 2](https://eujqw4hwudm.exactdn.com/wp-content/uploads/22.093-02-server-cpu.png?strip=all&lossy=1&sharp=1&ssl=1)](https://eujqw4hwudm.exactdn.com/wp-content/uploads/22.093-02-server-cpu.png?strip=all&lossy=1&sharp=1&w=2560&ssl=1)

TDengine has low CPU usage, while InfluxDB demands significant processing resources

### Query Performance

As performance can differ based on a number of factors, the TSBS framework covers a wide range of query types. _TDengine provided the fastest query response across all scenarios_, confirming that organizations dependent on real-time analytics are best served with this purpose-built platform.

[![Image 3](https://eujqw4hwudm.exactdn.com/wp-content/uploads/22.093-03-query-1.png?strip=all&lossy=1&sharp=1&ssl=1)](https://eujqw4hwudm.exactdn.com/wp-content/uploads/22.093-03-query-1.png?strip=all&lossy=1&sharp=1&w=2560&ssl=1)

For simpler queries, TDengine’s response time was 1.9 to 12.1 times faster than InfluxDB and TimescaleDB

More complex queries allowed TDengine to show off its processing power, reaching 24.3 times the performance of TimescaleDB and 34.3 times the performance of InfluxDB in the most challenging scenario: _double-groupby-all_. This demonstrates that TDengine is best prepared to handle the most performance-intensive queries without slowing down.

[![Image 4](https://eujqw4hwudm.exactdn.com/wp-content/uploads/22.093-04-query-2.png?strip=all&lossy=1&sharp=1&ssl=1)](https://eujqw4hwudm.exactdn.com/wp-content/uploads/22.093-04-query-2.png?strip=all&lossy=1&sharp=1&w=2560&ssl=1)

TDengine processes queries significantly faster than InfluxDB or TimescaleDB, especially for complex scenarios

The performance of TDengine in the other TSBS query categories was as follows:

*   Aggregates: Up to 6.9x faster than InfluxDB and 6.1x faster than TimescaleDB
*   Thresholds: Up to 15.1x faster than InfluxDB and 1.9x faster than TimescaleDB
*   Complex queries: Up to 21.1x faster than InfluxDB and 8.4x faster than TimescaleDB

[Download the full report](https://tdengine.com/downloads/devops-performance-comparison/) to see all of the query performance test data.

### Disk Storage

In smaller-scale scenarios, TDengine and InfluxDB took up a similar amount of disk space. When the datasets increased to one million or ten million devices, however, the benefits of TDengine’s storage design and architecture came into play; for large-scale datasets, _TDengine uses less than one-fourth the storage resources that InfluxDB requires_.

TimescaleDB on the other hand, had a significantly higher disk footprint across all scenarios. The clearest example was in the ten million device scenario, where _data processed by TimescaleDB occupied more than 26 times the disk space used by TDengine_.

[![Image 5](https://eujqw4hwudm.exactdn.com/wp-content/uploads/22.093-05-disk-usage.png?strip=all&lossy=1&sharp=1&ssl=1)](https://eujqw4hwudm.exactdn.com/wp-content/uploads/22.093-05-disk-usage.png?strip=all&lossy=1&sharp=1&w=2560&ssl=1)

When processing data from 10 million devices, TDengine consumes 26.9 times less disk space than TimescaleDB and 4.6 times less than InfluxDB

Conclusion
----------

_Across all key test metrics for ingestion, compression, and querying, TDengine clearly emerges as the highest-performing time series database_.

*   Ingestion: TDengine writes the test data between 1.5 to 6.7 times faster than TimescaleDB, and 3.0 to 10.6 times faster than InfluxDB, with significantly lower CPU overhead.
*   Compression: Due to its efficient data storage and compression features, TDengine consumes 26.9 times less disk space than TimescaleDB, and 4.5 times less than InfluxDB.
*   Queries: TDengine has the fastest query response time across all scenarios. For the most complex query type, TDengine responds 28.6 times faster than TimescaleDB and a whopping 37.0 times faster than InfluxDB.

### Purpose-Built Design

Unlike all-purpose databases like MySQL or PostgreSQL (which is used by TimescaleDB), TDengine was designed from the ground up to simplify and scale time series data management. The platform’s innovative storage engine makes full use of the unique [characteristics of time series data](https://tdengine.com/characteristics-of-time-series-data/), with novel concepts like a [single table for each data collection point](https://tdengine.com/tdengine-concepts-data-model/), which enables better ingestion, and data compression, and [supertables](https://tdengine.com/tdengine-concepts-supertable/), which speed up aggregation operations.

### Best in Class TSDB

The performance advantages shown by this evaluation indicate that TDengine excels at time-series data processing, especially with larger datasets and more complex queries. TDengine also requires fewer resources, significantly reducing the TCO of data operations. _These advantages, combined with its_[_comprehensive feature set_](https://tdengine.com/comprehensive-solution/)_and_[_ease of use_](https://tdengine.com/easy-to-use/)_, make TDengine the best option for growing enterprises to scale their data pipelines._

Video
-----

![Image 6: Time Series Database Performance Comparison Overview](https://i.ytimg.com/vi/_HYPJIGKEhE/hqdefault.jpg)

*   ![Image 7](https://eujqw4hwudm.exactdn.com/wp-content/uploads/29.03-05-cdiwadkar.jpg?strip=all&lossy=1&sharp=1&ssl=1) Chait Diwadkar

Chait Diwadkar previously worked as Director of Solutions Engineering at TDengine.
