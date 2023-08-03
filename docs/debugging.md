# Debugging Queries

There are a number of issues that can crop up when running BigQuery. They can be roughly grouped into
a few categories:

* Insufficient Slots
* Inefficient Query Constructs
* Data Problems


## Insufficient Slots

The query execution will request slots depending on how well it can parallelise its work.
Bigquery will allocate slots to the query using several considerations:

* The slots available under the reservation for the project
* Idle slots available from other reservations
* Other queries running at the same time
* Autoscaling settings


In general, BigQuery tries to be fair and will allocate slots to the jobs in equal manner (subject to reservations). 
This allocation is dynamic, i.e. if slots become available as a query ends, the slots are redistributed within seconds.

### How to detect insufficient Slots

There are several places to determine this:

1. In the Tree display, stages may be highlighted in RED and the stage detail may have an entry
called `performance` with the value being `Slot Contention`
2. Stage(s) `wait (ms)` average value shoots up, with waiting times being a series portion of the overall job duuration
3. In the Progress Tab, **Estimated Slot Usage Graph** maxes out for long periods
4. Same place, **Estimated Runnable Units Graph** maxes out for long periods

## Inefficient Query constructs

There are many types of query constructs that can result in slow performance.

In the Gantt Tab, you will be able to see stages that dominate the total execution time. 

The [GCP BigQuery Documentation](https://cloud.google.com/bigquery/docs/best-practices-performance-compute) contains a number of suggestions

In addition to these, look for COUNT and QUANTILE calls that can be slow if the data has high cardinality. 

In this case use the [Approximate Aggregate Functions](https://cloud.google.com/bigquery/docs/reference/standard-sql/functions-and-operators#approximate_aggregate_functions)

## Data Problems
A common data problem is where the data categories are uneven, i.e. 100 categories represent 1% of the total of data and one category represents the remaidner.
When doing counts or aggregation of groupings, such a condition will result in one work unit taking a much longer time than the rest.

Looking at stage details, the `compute (ms)` entry will show a a max value that is substantially larger than the average value.



