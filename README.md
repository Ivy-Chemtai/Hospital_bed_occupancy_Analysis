# Bed Occupancy Rate Calculation
This project analyzes hospital bed occupancy rates to measure healthcare resource utilization and patient flow efficiency. It demonstrates how data can be used to monitor hospital capacity, identify trends, and support decision-making for better healthcare management.

## Objectives
Calculate bed occupancy rates over a given time period.

Identify peak occupancy trends across departments or hospitals.

Visualize data for easy interpretation by healthcare administrators.

## Formula
Bed Occupancy Rate (BOR) measures the percentage of occupied hospital beds during a specific time frame.

*Bed Occupancy Rate (BOR)* = (Total Inpatient Bed Days Used / Total Available Bed Days) × 100
## Analysis
This section of the code performs data cleaning and calculates the Bed Occupancy Rate (BOR) for each healthcare facility using pandas.

Data Type Conversion:

*df["Average Monthly Patient Footfall"]* = pd.to_numeric(df["Average Monthly Patient Footfall"], errors="coerce")
*df["Number of Beds in facility type"]* = pd.to_numeric(df["Number of Beds in facility type"], errors="coerce")

These lines convert the columns “Average Monthly Patient Footfall” and “Number of Beds in facility type” to numeric data types.
The parameter errors="coerce" ensures that any non-numeric or missing values are converted to NaN, preventing calculation errors.
## Assumption:
It is assumed that “Average Monthly Patient Footfall” represents the number of beds occupied during the month.

This assumption simplifies the calculation of the Bed Occupancy Rate when detailed daily occupancy data is unavailable.

Bed Occupancy Rate Calculation:

*df['bed_occupancy_rate(%)'] *= (
    df["Average Monthly Patient Footfall"] /
    (df["Number of Beds in facility type"] * 30) * 100
)

The formula estimates the percentage of occupied beds within a month.
Each bed is considered available for 30 days.
The calculation divides the average monthly patient footfall (beds occupied) by the total available bed days (beds × 30) and multiplies by 100 to convert it into a percentage.
## Previewing Results:
df.head()
Displays the first five rows of the DataFrame to verify that the new column bed_occupancy_rate(%) has been created successfully.
<Figure size 1000x600 with 1 Axes><img width="998" height="590" alt="image" src="https://github.com/user-attachments/assets/82dc3b27-a236-41cf-8209-8fe2208e7ff7" />
    
## Insight

The chart shows significant variation in bed occupancy rates among maternity facilities in Pune. Late Matoshri Ramabai Ambedkar Maternity Home recorded the highest occupancy rate (around 1500%), indicating extreme overutilization relative to its available bed capacity. In contrast, facilities such as Dr. Dalvi, PMC Joint Project and Late Draupadabai Murlidhar Khedekar Maternity Home display much lower occupancy levels, suggesting possible underutilization or resource availability.

This imbalance highlights the need for better distribution of patients and resources across maternity centers to ensure more efficient service delivery and reduce pressure on overstretched facilities.
