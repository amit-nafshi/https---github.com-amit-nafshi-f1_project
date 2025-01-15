# **F1 Tire Strategy Prediction Project**

## **Project Overview**
This project aims to develop a machine learning-based system that predicts the optimal tire strategy for Formula 1 races. The predictions consider various factors such as track type, weather conditions, driver performance, and historical race data. The system outputs detailed tire strategy recommendations, along with visualizations to help understand the reasoning behind the predictions.

---

## **Goals**
1. **Accurate Tire Strategy Predictions**: Predict the optimal number of laps for each tire compound during a race.
2. **Incorporate Real-World Variations**: Adjust for factors like safety cars, yellow flags, and pit stop delays.
3. **Data-Driven Insights**: Use historical data to improve strategy recommendations.
4. **Visualization**: Create clear visual outputs to represent the tire strategies for better understanding and analysis.

---

## **Key Assumptions**
- **Pirelli Compounds**: Due to different tire compounds used throughout F1 history, this project will solely focus on the most recent Pirelli compounds, which were first introduced in 2022.
- **Consistency in Metrics**: The model uses data from 2022–2024 for consistency in tire degradation and performance metrics.

---

## **Key Features**
- **Race Input Function**:
  - Dynamically fetches data for a race using the FastF1 API.
  - Combines fetched data with manually classified track information.
  - Includes track type, aerodynamic requirements, power sensitivity, weather, and more.
  
- **Driver and Tire Metrics**:
  - **Tire Degradation Rate**: Calculated as the drop in lap performance over a stint.
  - **Average Lap Time by Compound**: Helps assess compound-specific performance.
  - **Driver-Specific Performance**:
    - **Aggressive Drivers**: Higher tire wear, faster lap times.
    - **Conservative Drivers**: Lower tire wear, more consistent performance.

- **Event-Specific Adjustments**:
  - **Safety Car or Virtual Safety Car**: Adjusts average stint length and lap times.
  - **Yellow Flags**: Impacts lap times during affected stints.
  - **Pit Stop Delays**: Includes factors such as pit crew performance or pit lane congestion.

- **Machine Learning Integration**:
  - Predicts tire strategies using historical data as input.
  - Tests multiple algorithms, such as Random Forest and XGBoost.

- **Comprehensive Visualizations**:
  - Outputs graphs and tables to explain predictions.
  - Illustrates lap-by-lap or stint-by-stint breakdowns for clarity.

---

## **Data Sources**
1. **FastF1 API**:
   - Provides session data for each race, including lap times, weather, and tire usage.
   - Fetches live or historical data dynamically.
   
2. **Manually Defined Track Classifications**:
   - Adds static data such as track type, aerodynamic requirements, and power sensitivity.
   - Enables the model to consider unique characteristics of each track.

---

## **Variables Used**
### **Race Input Data**
- **Track Type**: Permanent Circuit, Street Circuit, or Hybrid Circuit.
- **Length Classification**: Short, Medium, or Long track.
- **Aerodynamic Requirement**: High, Medium, or Low aerodynamic dependency.
- **Power Sensitivity**: High, Medium, or Low engine power influence.
- **Weather Data**:
  - **Air Temperature**: Ambient temperature during the race.
  - **Track Temperature**: Surface temperature of the track.
  - **Rainfall**: Probability of rain during the race.
- **Total Laps**: Number of laps in the race.

### **Lap-Level Data**
- **Tire Compound**: The type of tire used (Soft, Medium, Hard).
- **Lap Time**: Time taken to complete each lap.
- **Driver**: Abbreviation of the driver's name.
- **Lap Number**: Race progression.
- **Event Flags**: Safety Car, Virtual Safety Car, or Yellow Flag impacts.

### **Stint-Level Data**
- **Stint Length**: Number of laps completed on a single tire compound.
- **Average Lap Time**: Mean lap time within a stint.
- **Tire Degradation Rate**: Change in lap times over a stint (e.g., seconds per lap degradation).

### **Driver-Specific Metrics**
- **Aggressiveness**: Derived from tire wear rate and lap time consistency.
- **Conservativeness**: Derived from low tire wear and stable lap times.

---

## **Key Functions**
### **1. Track Classification**
Manually defined dictionary mapping each race to:
- Track Type
- Length Classification
- Aerodynamic Requirement
- Power Sensitivity

### **2. Race Input Function (`fetch_race_input`)**
Fetches and combines:
- Track classifications.
- Weather data (air and track temperatures, rainfall).
- Total race laps.

### **3. Driver and Tire Performance Metrics**
- Calculate average lap times, tire degradation rates, and stint lengths.
- Aggregate driver-specific performance metrics.

### **4. Event-Specific Adjustments**
- Modify lap times and stint lengths based on:
  - Safety Car or Virtual Safety Car periods.
  - Yellow Flag occurrences.
  - Pit stop delays.

### **5. Machine Learning Model**
- **Features**:
  - Lap times, stint lengths, tire compounds, track classifications, weather conditions, and event-specific metrics.
- **Target Variable**:
  - Predicted stint length (number of laps per tire compound).
- **Algorithms**:
  - Random Forest, XGBoost, or other regression models.

### **6. Visualization**
- Tire stint predictions shown in bar graphs or line plots.
- Residual analysis to evaluate model performance.

---

## **Expected Outputs**
1. **Tire Strategy Predictions**:
   - Predicted stint lengths for each tire compound.
   - Recommended tire strategy for the race.
   
2. **Visualizations**:
   - Graphs showing tire usage over the race.
   - Predicted vs actual stint performance comparison.

3. **Performance Metrics**:
   - Mean Squared Error (MSE)
   - R² Score (Coefficient of Determination)

---

## **Workflow**
1. **Setup and Initialization**:
   - Install and configure the FastF1 API.
   - Create a caching mechanism for efficient data fetching.

2. **Input Data Collection**:
   - Fetch race input variables (track and weather data).
   - Retrieve lap-level and stint-level data.

3. **Feature Engineering**:
   - Combine fetched and manual data into a feature matrix.
   - Calculate tire degradation rates, driver performance metrics, and event-specific adjustments.

4. **Model Training**:
   - Split the data into training and testing sets.
   - Train and test multiple algorithms to find the best fit.

5. **Prediction and Visualization**:
   - Predict tire strategies for future races.
   - Visualize the predictions for clarity and analysis.

---

## **Future Improvements**
- **Expand Features**: Add variables like pit stop timing, fuel load effects, or tire heating/cooling rates.
- **Improve Algorithm**: Experiment with neural networks or ensemble methods for better predictions.
- **Integrate Live Data**: Use live race data for real-time strategy predictions.

---

## **Conclusion**
This project combines historical data, track-specific characteristics, driver performance metrics, and advanced machine learning algorithms to predict optimal tire strategies for Formula 1 races. By leveraging the FastF1 API and visualizing the results, the system aims to provide actionable insights for race strategy optimization.