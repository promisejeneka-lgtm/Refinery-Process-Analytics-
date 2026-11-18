# Data Cleaning Log

## Project
**Refinery Process Performance & Production Analytics**

## Dataset overview
- Dataset type: Synthetic refinery process dataset
- Initial dataset size: 2,166 records
- Coverage: 1 January 2026 to 31 March 2026 (90 days)
- Processing units: CDU-01, VDU-01, NHT-01
- Original fields: 14

## Initial data quality checks
The initial dataset was inspected for missing values and duplicate records.

Missing values identified in the initial dataset:
- `temperature_C`: 8
- `pressure_bar`: 8
- `energy_MWh`: 8

- Duplicate records: 6 exact duplicates (all fields identical): CDU-01 x1, VDU-01 x1, NHT-01 x4.

## Cleaning and preparation
Duplicate records were removed and missing values were reviewed before analysis. Duplicate removal was repeated in Power Query as a check, and column data types were set there (timestamp as date/time, numeric fields as numbers).

The original observation-level dataset is loaded into Power BI as `Refinery Data`.

A separate Power Query reference named `Product Yield Data` was created by unpivoting the four product-yield columns. This is a separate analytical table and should not be treated as the original observation-level cleaned dataset.

## Final dataset verification
| Check | Raw data | Cleaned data |
|---|---|---|
| Total records | 2,166 | 2,160 |
| Records per unit | CDU-01 721, VDU-01 721, NHT-01 724 | 720 each (90 days x 8 readings) |
| Duplicate records | 6 | 0 |
| Blank values | 24 (8 temperature, 8 pressure, 8 energy) | 24 (kept on purpose) |

Treatment applied:
- **Duplicates:** the 6 exact duplicate rows were removed, keeping the first copy.
- **Missing values:** the 24 blank values (about 1.1% of records, one blank per affected record) were left blank and not replaced with zeros or averages. Averages in Power BI ignore blanks, and each affected record still has valid throughput, downtime and yield values.
- **Other checks:** throughput is within about 5% of feed volume in every record, product-yield totals range from about 96.9% to 103.6%, and unit and shift categories are consistent. These were kept as recorded.

## Data source and limitations
This is a synthetic dataset created for educational and portfolio purposes. It does not represent actual refinery operating records, and its values are not validated industry benchmarks.
