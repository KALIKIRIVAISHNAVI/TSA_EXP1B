# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 19-08-2025

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
# Importing required libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Read the dataset
df = pd.read_csv("/content/heart_rate.csv")

# Display first few rows
print("Dataset Preview:")
print(df.head())

# Select the 'T1' column as the heart rate data and reset the index to create a 'Time' column
df = df[['T1']].reset_index()
df.columns = ["Time", "Heart_Rate"]  # rename for clarity if needed
df["Time"] = pd.to_datetime(df["Time"])
df.set_index("Time", inplace=True)

# Original data plot
plt.figure(figsize=(10,5))
plt.plot(df["Heart_Rate"], label="Original Data")
plt.title("Original Heart Rate Data (Non-Stationary)")
plt.legend()
plt.show()
regular_diff = df["Heart_Rate"].diff().dropna()

plt.figure(figsize=(10,5))
plt.plot(regular_diff, label="Regular Differencing")
plt.title("Heart Rate Data After Regular Differencing")
plt.legend()
plt.show()

seasonal_diff = df["Heart_Rate"].diff(12).dropna()

plt.figure(figsize=(10,5))
plt.plot(seasonal_diff, label="Seasonal Adjustment (lag=12)")
plt.title("Heart Rate Data After Seasonal Adjustment")
plt.legend()
plt.show()

log_transform = np.log(df["Heart_Rate"])

plt.figure(figsize=(10,5))
plt.plot(log_transform, label="Log Transformation")
plt.title("Heart Rate Data After Log Transformation")
plt.legend()
plt.show()

# Final output
print("\nREGULAR DIFFERENCING:\n", regular_diff.head())
print("\nSEASONAL ADJUSTMENT:\n", seasonal_diff.head())
print("\nLOG TRANSFORMATION:\n", log_transform.head())

log_regular_diff = log_transform.diff().dropna()

plt.figure(figsize=(10,5))
plt.plot(log_regular_diff, label='Log Transformation and Regular Differencing')
plt.legend(loc='best')
plt.title('Log Transformation and Regular Differencing')
plt.xlabel('Time')
plt.ylabel('Diff(Log(Heart_Rate))')
plt.show()

# Calculate the seasonal difference of the log-transformed and regularly differenced data
log_regular_seasonal_diff = log_regular_diff.diff(12).dropna()

plt.figure(figsize=(10, 5))
plt.plot(log_regular_seasonal_diff, label='Log Transformation, Regular, and Seasonal Differencing')
plt.legend(loc='best')
plt.title('Heart Rate Data After Log Transformation, Regular, and Seasonal Differencing')
plt.xlabel('Time')
plt.ylabel('SDiff(RDiff(Log(Heart_Rate)))')
plt.show()

 plt.tight_layout()
 plt.show()
 df.plot(kind='line')
```

### OUTPUT:
ORIGINAL HEART RATE DATA (Non-Stationary):

<img width="818" height="424" alt="image" src="https://github.com/user-attachments/assets/d3ccdd15-85fa-43a9-9f1c-32b952f17040" />

REGULAR DIFFERENCING:

<img width="816" height="427" alt="image" src="https://github.com/user-attachments/assets/e82c8f04-cfd2-434a-90fd-46a23deaf39f" />

SEASONAL ADJUSTMENT:

<img width="792" height="424" alt="image" src="https://github.com/user-attachments/assets/df38ed2f-2c23-4ea0-aa99-5b479f769650" />

LOG TRANSFORMATION:

<img width="775" height="419" alt="image" src="https://github.com/user-attachments/assets/902239d6-a45b-4d65-a0d8-dcebed28c2b5" />

LOG TRANSFOMATION AND REGULAR DIFFERENCING:

<img width="864" height="442" alt="image" src="https://github.com/user-attachments/assets/4ee0a256-bfa0-48ce-be61-42a23b8e8d7a" />

HEART RATE DATA AFTER LOG TRANSFORMATION, REGULAR, AND SEASONAL DIFFERENCING:

<img width="816" height="435" alt="image" src="https://github.com/user-attachments/assets/10c6d6e8-c85a-4009-bad1-4f3e3ac300ca" />

<img width="544" height="456" alt="image" src="https://github.com/user-attachments/assets/8d53115e-ce6d-41aa-94e5-48968ea3750d" />


### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
