# Dynamic Test Analysis

A Python-based data analysis and visualization tool for comparing dynamic test results across multiple weight conditions. This project analyzes voltage, current, and speed measurements from test runs to identify performance patterns and variations.

## Overview

This project processes test data from four different weight conditions (900, 1200, 1500, and 2000) and creates interactive visualizations to compare metrics over time. The analysis helps identify how different loads affect electrical and mechanical performance during dynamic testing.

## Features

- **Data Loading**: Automatically reads all CSV files from the test directory
- **Data Merging**: Aligns measurements from different test runs by time
- **Interpolation**: Handles missing data points by interpolating between known values
- **Interactive Visualizations**: Creates responsive Plotly charts for easy exploration
- **Multiple Metrics**: Analyzes voltage, current, and speed (mph) data
- **Comparison Plots**: Side-by-side comparisons of metrics across all test conditions

## Project Structure

```
Dynamic_testing2/
├── analysis.ipynb              # Main Jupyter notebook with all analysis
├── 900.csv                     # Test data for 900 weight condition
├── 1200.csv                    # Test data for 1200 weight condition
├── 1500.csv                    # Test data for 1500 weight condition
├── 2000.csv                    # Test data for 2000 weight condition
├── voltage_vs_time_plot.png    # Matplotlib voltage comparison plot
├── current_vs_time_plot.png    # Plotly current comparison plot
├── requirements.txt            # Python dependencies
└── README.md                   # This file
```

## Requirements

- Python 3.11+
- pandas
- matplotlib
- plotly
- nbformat
- ipython

## Installation

1. Clone the repository:
```bash
git clone https://github.com/scottsun2026/Dynamic_testing2.git
cd Dynamic_testing2
```

2. Create and activate a virtual environment:
```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
```

3. Install required packages:
```bash
pip install -r requirements.txt
```

## Usage

### Running the Analysis

Open the Jupyter notebook and run all cells:

```bash
jupyter notebook analysis.ipynb
```

Or use VS Code with the Jupyter extension:
- Open `analysis.ipynb` in VS Code
- Select the "dynamic_testing" kernel
- Run cells in sequence (Cells 1 → 28)

### Key Analysis Steps

1. **Data Loading** (Cell 2): Loads all CSV files from the directory
2. **Data Preparation** (Cells 3-5): Creates DataFrames and merges data by time
3. **Voltage Analysis** (Cells 8-13): Visualizes voltage variations across test conditions
4. **Current Analysis** (Cells 14-20): Analyzes current measurements
5. **Speed Analysis** (Cells 21-28): Shows speed (mph) comparisons

## Visualizations

The notebook generates interactive Plotly charts that allow you to:
- Hover over data points to see exact values
- Zoom in/out for detailed inspection
- Pan across the time axis
- Toggle traces on/off in the legend
- Download plots as PNG files

### Chart Types

- **Line Plots**: Time-series data with distinct colors for each test condition
- **Responsive Design**: Charts adapt to different screen sizes
- **Custom Tick Intervals**: X-axis shows 50-second intervals for clarity

### Interactive Charts (Live)

View the interactive Plotly charts hosted on GitHub Pages:

- [Current vs Time Analysis](https://scottsun2026.github.io/dynamic_testing2/docs/current_vs_time_chart.html)
- [Voltage vs Time Analysis](https://scottsun2026.github.io/dynamic_testing2/docs/voltage_vs_time_chart.html)
- [Speed (MPH) vs Time Analysis](https://scottsun2026.github.io/dynamic_testing2/docs/mph_vs_time_chart.html)


## Data Format

CSV files should contain at least these columns:
- `Time sec`: Timestamp in seconds
- `Volt`: Voltage measurements
- `Current` (or similar): Current measurements
- Other relevant metrics (speed, rpm, etc.)

## Output Files

- **voltage_vs_time_plot.png**: Static matplotlib plot comparing voltage across all test conditions
- **current_vs_time_plot.png**: Interactive Plotly chart comparing current draw across all test conditions
- **Interactive Charts**: Plotly visualizations displayed inline in the notebook for voltage, current, speed (mph), and temperature data

### Example Outputs

The analysis generates comparison plots comparing voltage across all test conditions (900, 1200, 1500, 2000 lb).

## View Full Analysis

Run the notebook locally or view it online:

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/scottsun2026/Dynamic_testing2/main?filepath=analysis.ipynb)

*Click the badge above to run the analysis interactively online with Binder (no installation required)*

## Key Functions

- **Data Merging**: Uses `pd.merge()` with outer joins to align data from different files
- **Interpolation**: Linear interpolation fills gaps in misaligned time series
- **Plotting**: Plotly `go.Scatter()` traces for interactive visualization

## Customization

### Change Tick Intervals
Modify the x-axis tick spacing in plotting cells:
```python
xaxis=dict(dtick=50)  # Change 50 to your desired interval
```

### Add More Metrics
To analyze additional columns, duplicate a plotting cell and change the column name:
```python
voltage_vs_time = df_2000[['Time sec', 'new_column_name']].copy()
```

### Adjust Colors
Modify the colors list in plotting cells:
```python
colors = ['blue', 'green', 'orange', 'red']  # Add or change colors
```

## Troubleshooting

### Plot not displaying?
1. Restart the Jupyter kernel (Ctrl+Shift+P → Restart Kernel)
2. Ensure all packages are installed: `pip install -r requirements.txt`

### Import errors?
```bash
pip install nbformat ipython
```

### Virtual environment not activating?
```bash
source .venv/bin/activate  # macOS/Linux
.venv\Scripts\activate     # Windows
```

---

**Last Updated**: May 7, 2026
