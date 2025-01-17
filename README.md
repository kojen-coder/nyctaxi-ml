<h1>🚕 NYC Taxi Demand Forecasting</h1>

<p>This project predicts <strong>daily ride demands</strong> for NYC's Yellow Taxi service using historical trip data from the Taxi & Limousine Commission. By forecasting daily demand, the project empowers taxi operators to optimize resources, improve customer satisfaction, and reduce operational inefficiencies.</p>

<h2>🌟 Project Overview</h2>

<h3>Dataset</h3>
<p>The dataset is sourced from NYC's Taxi & Limousine Commission and includes:</p>
<ul>
  <li><strong>Trip Start and End Times</strong>: Date and time of pickup and dropoff.</li>
  <li><strong>Passenger Counts</strong>: Number of passengers per trip.</li>
  <li><strong>Trip Distance</strong>: Measured in miles.</li>
  <li><strong>Fares and Payment Details</strong>: Includes total fare, payment type, and tips.</li>
  <li><strong>Pickup and Dropoff Locations</strong>: Latitude and longitude coordinates.</li>
</ul>

<h3>Tech Stack</h3>
<ul>
  <li><strong>Programming:</strong> Python (Data Curation & Modeling)</li>
  <li><strong>Libraries:</strong> Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Plotly, CausalML</li>
</ul>

<h3>My Role</h3>
<p>As a <strong>Data Scientist</strong>, I led:</p>
<ul>
  <li><strong>Exploratory Data Analysis (EDA):</strong> Uncovered demand trends, seasonal patterns, and external influences.</li>
  <li><strong>Feature Engineering:</strong> Created meaningful predictors, such as lagged demand, weather, and holiday indicators.</li>
  <li><strong>Machine Learning Models:</strong> Developed and evaluated baseline and advanced forecasting techniques.</li>
  <li><strong>Causal Analysis:</strong> Assessed the impact of external factors (e.g., holidays and weather) on demand to provide actionable business recommendations.</li>
</ul>

<h2>🔧 Data Preparation and Feature Engineering</h2>

<h3>Data Cleaning</h3>
<ul>
  <li>Removed outliers, such as trips with unrealistic durations or distances.</li>
  <li>Interpolated missing values and aggregated trip data by day to calculate <strong>daily ride demand</strong>.</li>
</ul>

<h3>Feature Engineering</h3>
<p>To enhance model performance, I added the following features, supported by data observations and assumptions:</p>
<ul>
  <li><strong>Lagged Demand:</strong>
    <ul>
      <li>Observations: Daily demand often correlates with recent trends.</li>
      <li>Expectation: Captures sequential dependencies (e.g., yesterday’s demand influences today).</li>
    </ul>
  </li>
  <li><strong>Rolling Averages:</strong>
    <ul>
      <li>Observations: Daily fluctuations can create noise in predictions.</li>
      <li>Expectation: Smooths short-term variations to highlight broader patterns.</li>
    </ul>
  </li>
  <li><strong>Weather:</strong>
    <ul>
      <li>Observations: Precipitation negatively impacts ride demand, as shown in EDA.</li>
      <li>Expectation: Models weather-related variability, such as demand drops during rainy days.</li>
    </ul>
  </li>
  <li><strong>Holidays:</strong>
    <ul>
      <li>Observations: Certain holidays (e.g., New Year’s Eve) significantly increase demand, while others reduce it.</li>
      <li>Expectation: Differentiates holiday demand patterns from regular days.</li>
    </ul>
  </li>
</ul>

<h2>🔍 Exploratory Data Analysis (EDA)</h2>

<h3>Key Findings</h3>
<ul>
  <li><strong>Temporal Trends:</strong> Weekday demand peaks on Mondays and Fridays, with reduced demand on weekends. Summer months exhibit higher ride demand, reflecting tourism trends.</li>
  <li><strong>External Factors:</strong> Precipitation correlates with a ~10–15% drop in ride demand. Holidays like New Year’s Eve result in significant spikes, while minor holidays see reduced demand.</li>
</ul>

<h2>⚙️ Models and Techniques</h2>

<h3>Baseline Models</h3>
<ul>
  <li><strong>Linear Regression:</strong> Captures basic linear relationships but struggled with non-linear trends.</li>
  <ul>
    <li><strong>Results:</strong> MAE: 11,872 | RMSE: 16,605</li>
  </ul>
  <li><strong>Ridge and Lasso Regression:</strong> Added regularization to reduce overfitting but lacked flexibility to model complex interactions.</li>
</ul>

<h3>Advanced Models</h3>
<ul>
  <li><strong>Random Forest Regressor:</strong> I incorporated new features as below: 
    <ul>
      <li><strong>Lagged Demand:</strong> Helps capture sequential dependencies (e.g., yesterday’s demand influences today).</li>
      <li><strong>Rolling Averages:</strong> Smooths short-term fluctuations.</li>
      <li><strong>Weather:</strong> Captures weather-related variability, such as reduced demand during rainy days.</li>
      <li><strong>Holidays:</strong> Differentiates demand spikes on major holidays and drops on minor holidays.</li>
    </ul>
  </li>
</ul>

<h3>Model Performance</h3>
<table>
  <thead>
    <tr>
      <th>Model</th>
      <th>MAE</th>
      <th>RMSE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Linear Regression</td>
      <td>11,872.12</td>
      <td>16,604.86</td>
    </tr>
    <tr>
      <td>Ridge Regression</td>
      <td>12,029.43</td>
      <td>16,853.22</td>
    </tr>
    <tr>
      <td>Lasso Regression</td>
      <td>12,095.11</td>
      <td>16,920.45</td>
    </tr>
    <tr>
      <td><strong>Random Forest Regressor</strong></td>
      <td><strong>10,528.17</strong></td>
      <td><strong>14,504.20</strong></td>
    </tr>
  </tbody>
</table>

<strong>Best Model: </strong> Random Forest Regressor
<ul>
  <li><strong>Why?:</strong> Outperformed baseline models by effectively capturing non-linear relationships and interactions between features.</li>
  <li><strong>Business Implications: </strong> Provides reliable daily demand predictions, enabling taxi operators to allocate resources more effectively and improve service reliability.</li>
</ul>
<h2>📊 Results and Visualizations</h2>

<h3>Observations and Business Insights</h3>
<h4>From a Business Standpoint:</h4>
<ul>
  <li>Results align with expectations: weekdays show higher demand, and external factors like weather and holidays significantly influence ride counts.</li>
  <li>Random Forest’s accuracy ensures actionable insights for daily decision-making.</li>
</ul>

<h4>Key Insights:</h4>
<ul>
  <li>External predictors like precipitation highlight opportunities for targeted promotions during low-demand periods.</li>
  <li>Holidays and weekdays with high demand can guide fleet optimization strategies.</li>
</ul>

<h2>📈 Causal ML: Impact Analysis</h2>

<h3>Why Causal Analysis?</h3>
<p>While forecasting demand helps optimize resources, causal analysis provides deeper insights into <strong>why</strong> demand fluctuates. This enables businesses to implement targeted interventions and plan better.</p>

<h3>Techniques</h3>
<ul>
  <li><strong>LRSRegressor:</strong> Linear regression-based causal analysis.</li>
  <li><strong>XGBTRegressor:</strong> Captures complex, non-linear treatment effects.</li>
</ul>

<h3>Results and Observations</h3>
<h4>Holiday Effects:</h4>
<ul>
  <li>Major holidays (e.g., New Year’s Eve) increased demand by ~25,000 trips.</li>
  <li>Minor holidays reduced demand by ~10%.</li>
  <li><strong>Reason:</strong> Celebratory holidays drive more travel, while others like Thanksgiving reduce non-essential trips.</li>
</ul>

<h4>Weather Impact:</h4>
<ul>
  <li>Rainy days reduced demand by an average of ~12%.</li>
  <li><strong>Reason:</strong> Bad weather discourages outdoor activities and reduces the need for taxi travel.</li>
</ul>

<h2>🧩 Business Recommendations</h2>
<ul>
  <li><strong>Targeted Promotions:</strong> Offer discounts or special deals during low-demand holidays to encourage travel.</li>
  <li><strong>Fleet Optimization:</strong> Deploy additional cabs during high-demand holidays and rainy weekdays.</li>
</ul>

<p>Feel free to explore the repository for detailed notebooks, visualizations, and code implementation. 🎉</p>
