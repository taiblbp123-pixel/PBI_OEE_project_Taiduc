# KPI Definitions

This document provides a simplified, business-friendly overview of key performance indicators (KPIs) used to evaluate production efficiency, time utilization, and machine reliability.

---

## 1. OEE Overall

| group       | business_question                          | kpi_name       | description                                 | formula                                     | notes    |
| ----------- | ------------------------------------------ | -------------- | ------------------------------------------- | ------------------------------------------- | -------- |
| OEE Overall | How effective is the production line?      | OEE %          | Overall equipment effectiveness             | Availability × Performance × Quality        | Core KPI |
|             | How much planned time is actually running? | Availability % | Ratio of runtime vs planned production time | Run Time / Planned Production Time          |          |
|             | Are we running at ideal speed?             | Performance %  | Speed efficiency vs ideal cycle time        | (Ideal Cycle Time × Total Count) / Run Time |          |
|             | How many good units are produced?          | Quality %      | Ratio of good units vs total produced       | Good Count / Total Count                    |          |

---

## 2. Time Usage

| group      | business_question                        | kpi_name             | description                              | formula                                                             | notes                  |
| ---------- | ---------------------------------------- | -------------------- | ---------------------------------------- | ------------------------------------------------------------------- | ---------------------- |
| Time Usage | Total time available?                    | Total Hours          | Total planned production time            | Sum of all time buckets                                             |                        |
|            | How much time is actually running?       | Run Time             | Time machine is operating                | Total Hours − Down Time                                             |                        |
|            | How much time is lost due to stops?      | Down Time            | Time machine is not running              | Sum of all downtime events                                          |                        |
|            | How much time is fully productive?       | Full Productive Time | Time producing good units at ideal speed | Total Hours − (Availability Loss + Performance Loss + Quality Loss) | Derived KPI            |
|            | How much time is lost due to downtime?   | Availability Loss    | Time lost due to breakdowns or stoppages | Planned Time − Run Time                                             | Links to Availability% |
|            | How much time is lost due to speed loss? | Performance Loss     | Time lost due to slow cycles             | Run Time − Ideal Run Time                                           | Links to Performance%  |
|            | How much time is lost due to defects?    | Quality Loss         | Time spent producing defective units     | Defect Count × Ideal Cycle Time                                     | Links to Quality%      |

---

## 3. Reliability

| group       | business_question            | kpi_name                               | description                     | formula                       | notes            |
| ----------- | ---------------------------- | -------------------------------------- | ------------------------------- | ----------------------------- | ---------------- |
| Reliability | How reliable is the machine? | MTBF<br><br>Mean Time Between Failures | Average time between failures   | Run Time / Number of Failures | Higher is better |
|             | How fast do we recover?      | MTTR<br><br>Mean Time To Repair        | Average repair time per failure | Downtime / Number of Failures | Lower is better  |



