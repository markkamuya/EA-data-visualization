# Data Analysis and Visualization of Learning Distractions and Participation

This Python script performs data cleaning, transformation, and visualization for analyzing survey data regarding student distractions and participation levels in online vs in-person learning environments. It utilizes **Pandas** for data manipulation, **Seaborn** and **Matplotlib** for visualizations, and **NumPy** for numerical operations. The analysis covers two main aspects: distractions and participation in different learning environments.

## Steps and Functionality

### Data Loading and Preprocessing

1. **Load Data**: The raw survey data is read from a CSV file using `pd.read_csv()`. 
   - File: `EA50 Scientific Proposal_ Science of Learning Data - Raw Data 1.csv`
   
2. **Column Cleanup**: All column names are stripped of leading/trailing spaces using `str.strip()`, ensuring clean and consistent column headers.

3. **Renaming Columns**: Relevant columns, particularly those related to distractions and participation in both online and in-person learning contexts, are renamed for clarity:
   - `Distraction_online`: Represents the distraction level in online learning.
   - `Distraction_inperson`: Represents the distraction level in in-person learning.
   - `Participation_online`: Represents student participation in online learning.
   - `Participation_inperson`: Represents student participation in in-person learning.

### Data Transformation

4. **Categorical to Numeric Mapping**: Categorical data (e.g., 'Strongly Agree', 'Disagree', etc.) is mapped to numerical values using a predefined mapping dictionary:
   ```python
   distraction_mapping = {
       'Strongly Disagree': 1,
       'Disagree': 2,
       'Neutral': 3,
       'Agree': 4,
       'Strongly Agree': 5
   }
   ```
   The `map()` function is applied to the `Distraction_online`, `Distraction_inperson`, `Participation_online`, and `Participation_inperson` columns to replace categorical values with numerical representations.

5. **Missing Data Handling**: Missing values are handled by filling with the median value of each respective column using `.fillna()`.

### Visualizations

#### 1. **Box Plot: Distraction Levels in Online vs In-Person Learning**

A **box plot** is generated to compare the distribution of distraction levels between online and in-person courses. This plot provides insights into the spread of responses and highlights the median and outliers.

- **Axes**:
  - X-axis: Mode of Learning (Online vs In-Person)
  - Y-axis: Distraction Level (1 = Strongly Disagree, 5 = Strongly Agree)
  
- **Box Plot Features**:
  - Box represents the interquartile range (IQR).
  - Whiskers extend to the most extreme data points within 1.5 times the IQR.
  - Outliers are displayed as individual points outside the whiskers.

#### 2. **Bar Plot: Average Participation Levels in Online vs In-Person Learning**

A **bar plot** visualizes the average participation levels in online and in-person courses. This provides a comparison of how students perceive their engagement in both environments.

- **Data Calculation**: The average participation levels are computed for both online and in-person courses by calculating the mean of the respective columns:
  ```python
  avg_participation = df[['Participation_online', 'Participation_inperson']].mean()
  ```
  
- **Bar Plot Customization**:
  - X-axis: Mode of Learning (Online vs In-Person)
  - Y-axis: Average Participation Level (scale: 1 to 5)
  - Gridlines and detailed captions are added for clarity.

### Visual Interpretation

- **Distraction Levels**: The box plot provides insights into how distractions are distributed across both learning modes, showing the variance, central tendency, and outliers.
  
- **Participation Levels**: The bar plot highlights the average participation across both modes of learning, providing a clear visual comparison. The caption in the plot provides an interpretation of possible reasons behind differences in participation levels.

### Code Snippets

- **Loading Data**:
  ```python
  df = pd.read_csv("EA50 Scientific Proposal_ Science of Learning Data - Raw Data 1.csv")
  ```

- **Cleaning Column Names**:
  ```python
  df.columns = df.columns.str.strip()
  ```

- **Mapping Categorical Values**:
  ```python
  df['Distraction_online'] = df['Distraction_online'].map(distraction_mapping)
  ```

- **Handling Missing Values**:
  ```python
  df['Distraction_online'] = df['Distraction_online'].fillna(df['Distraction_online'].median())
  ```

### Dependencies

- **pandas**: Data manipulation and cleaning.
- **seaborn**: Statistical data visualization.
- **matplotlib**: Plotting and customization of visualizations.
- **numpy**: Numerical calculations and handling.

## Execution

1. **Install Dependencies**:
   Ensure all required libraries are installed:
   ```bash
   pip install pandas seaborn matplotlib numpy
   ```

2. **Run the Script**:
   Execute the script in your Python environment:
   ```bash
   python script_name.py
   ```

3. **Visual Output**:
   The script will generate the following plots:
   - A **box plot** comparing distraction levels between online and in-person learning.
   - A **bar plot** comparing average participation levels between the two modes.

---

This `README.md` provides an extremely technical overview of the code and its functionality, with emphasis on the steps taken in data processing, transformations, and visual analysis. It also includes necessary installation steps and script execution instructions.
