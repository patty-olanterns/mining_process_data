

 <b><p style="text-align:center;">
    <font size ="24" color ="Black">
        Gangue Forecast in Flotation Concentrate in a Mine Mill process facility
    </font>
</b>

Mined ores are mostly mixtures of extractable minerals and nonvaluable material (gangue). Mineral processing (a.k.a. ore dressing, ore beneficiation) follows mining and prepares the ore for extraction of the valuable metal. A principal step in mineral processing is physical separation of the particles of valuable minerals from the gangue, to produce an enriched portion (concentrate) containing most of the valuable minerals, and a discard (tailing) containing predominantly the gangue.

A separation of minerals by exploiting difference of surface properties (hydrophobicity) is called flotation. The reverse cationic flotation is commonly used to separate iron from silica. By adjusting the 'chemistry' of the pulp by adding various chemical reagents, iron minerals remain in the water and create sediment with a high concentration of iron (valuable minerals). At the same time, silica particles (gangue) attach to air bubbles and float to the surface.

<p style="text-align:center;">
    <img width="400" alt="Reverse cationic flotation of iron ore" src="https://github.com/ginsaputra/gangue-forecast-in-flotation-concentrate/blob/main/reverse-cationic-flotation-iron-silica.png?raw=true">

Flotation concentrate is periodically sampled to determine its purity (i.e., *%valuable*, *%gangue*). Higher *%gangue* in the concentrate is undesirable as it indicates that most valuable minerals had gone into the tailings. Purity measurement is usually done in a lab and can take some time before process engineers can make any adjustments based on the results. A timely investigation of concentrate purity is, therefore, a fundamental aspect for the control and optimization of the flotation process.

This notebook explores the application of deep learning to forecast gangue (*%silica*) in the flotation concentrate. The forecast will help process engineers assess purity of flotation concentrate and take corrective actions in advance. More specifically, the goal is to tackle the following tasks:
- How many steps (hours) ahead can *%silica in concentrate* be forecasted?
- Is it possible to forecast *%silica in concentrate* without using the data of *%iron in concentrate*?
  
# Data Visual Summary
 
 # Correlation Heatmap - Gangue (CONC_SILICA) vs. Features
 
  The following chart displays the correlation between training variables and
  the target variable CONC_SILICA (% Silica Concentrate). This correlation plot is BEFORE CONC_IRON is dropped
  as a training feature.
 
 <p style="text-align:center;">
    <img width="400" alt="Gangue Correlation Heatmap" src="https://github.com/patty-olanterns/mining_process_data/blob/main/IronMiningProcessCorrelationHeatmap.png?raw=true">
  
 # Mineral Content - Feed And Concentrate
  
  This chart displays the percentage (%) of mineral content(Iron and Silica) at a specific time
  interval. IRON_FEED AND SILICA_FEED refers to the raw product entering the process plant. CONC_IRON and CONC_SILICA
  are the percentage (%) of Iron and Silica (Gangue) in the Flotation Concentrate.
  
 <p style="text-align:center;">
    <img width="400" alt="Mineral Content Feed And Flotation Concentrate" src="https://github.com/patty-olanterns/mining_process_data/blob/main/MineralContentFeedAndConcentrate.png?raw=true">
  
# Training_History_Losses_Graph
  
  The following chart is a breakdown of the LSTM Model and the training losses (MAE - Mean Absolute Error) for 
  training and validation data.
  
  The model runs 100 times (epochs) and the lowest loss number is the epoch where
  the model is fitted and performing at its best!
  
 <p style="text-align:center;">
    <img width="400" alt="Training_History_Losses_Graph" src="https://github.com/patty-olanterns/mining_process_data/blob/main/TrainingHistoryLossesGraph.png?raw=true">
  
 # SilicaInConcentrateActualVSForecastRandomForest
 
 <p style="text-align:center;">
    <img width="400" alt="SilicaInConcentrateActualVSForecastRandomForest" src="https://github.com/patty-olanterns/mining_process_data/blob/main/SilicaInConcentrateActualVSForecastRandomForest.png?raw=true">
  
 # Silica_in_Concentrate_Actual_Values_and_Forecasts_LSTM
  
  For the LSTM method (Long Short Term Memory), a RMSE of 0.708 was achieved.  This is lower
  than the result achieved for a RandomForestRegressor model (0.77), and is the better model of
  the two!
  
 <p style="text-align:center;">
    <img width="400" alt="Silica_in_Concentrate_Actual_Values_and_Forecasts_LSTM" src="https://github.com/patty-olanterns/mining_process_data/blob/main/SilicaInConcentrateActualVSForecastLSTM.png?raw=true">
 
 
# Conclusion
A deep learning approach using RF (Random Forest Regressor) and LSTM (Long Short Term Memory) was implemented to forecast gangue content in flotation concentrate. Excluding *%iron in concentrate* from the features, *%silica in concentrate* were forecasted one hour ahead and with error below 1 (based on RMSE, MAE). As the dataset owner stated in [this post](https://www.kaggle.com/rogerbellavista/randomforestregressor-mae-0-0922-rmse-0-2314#434654), MAE and RMSE of 1±0.2 is a satisfactory result.

A **RMSE of 0.72** was achieved using the LSTM model. It performed better than the Random Forest model which had 
a **RMSE of 0.77.**

In general, the lower the value of the RMSE the better. Recall that the RMSE is a metric that tells us the average distance between the predicted values from the model and the actual values in the dataset. The lower the RMSE, the better a given model is able to “fit” a dataset.[https://www.statology.org/how-to-interpret-rmse/]

Although LSTM implementation in this notebook has met the objectives, it will benefit from further exploration:
- Forecasting with smaller lag timesteps. For example, a 30-minute lag for the features/inputs.
