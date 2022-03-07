

 <b><p style="text-align:center;">
    <font size ="12" color ="Black">
        Gangue Forecast in Flotation Concentrate in a Mine Mill process facility
    </font>
</b>

Mined ores are mostly mixtures of extractable minerals and nonvaluable material (gangue). Mineral processing (a.k.a. ore dressing, ore beneficiation) follows mining and prepares the ore for extraction of the valuable metal. A principal step in mineral processing is physical separation of the particles of valuable minerals from the gangue, to produce an enriched portion (concentrate) containing most of the valuable minerals, and a discard (tailing) containing predominantly the gangue.

A separation of minerals by exploiting difference of surface properties (hydrophobicity) is called flotation. The reverse cationic flotation is commonly used to separate iron from silica. By adjusting the 'chemistry' of the pulp by adding various chemical reagents, iron minerals remain in the water and create sediment with a high concentration of iron (valuable minerals). At the same time, silica particles (gangue) attach to air bubbles and float to the surface.

<p style="text-align:center;">
    <img width="400" alt="Reverse cationic flotation of iron ore" src="https://github.com/ginsaputra/gangue-forecast-in-flotation-concentrate/blob/main/reverse-cationic-flotation-iron-silica.png?raw=true">

Flotation concentrate is periodically sampled to determine its purity (i.e., *%valuable*, *%gangue*). Higher *%gangue* in the concentrate is undesirable as it indicates that most valuable minerals had gone into the tailing. Purity measurement is usually done in a lab and can take some time before process engineers can make any adjustments based on the results. A timely investigation of concentrate purity is, therefore, a fundamental aspect for the control and optimization of the flotation process.

This notebook explores the application of deep learning to forecast gangue (*%silica*) in the flotation concentrate. The forecast will help process engineers assess purity of flotation concentrate and take corrective actions in advance. More specifically, the goal is to tackle the following tasks:
- How many steps (hours) ahead can *%silica in concentrate* be forecasted?
- Is it possible to forecast *%silica in concentrate* without using the data of *%iron in concentrate*?
  
# Data Visual Summary
 
 # Correlation Heatmap - Gangue vs. Features
 
 <p style="text-align:center;">
    <img width="400" alt="Gangue Correlation Heatmap" src="https://github.com/patty-olanterns/mining_process_data/gangue-forecast-in-flotation-concentrate/blob/main/IronMiningProcessCorrelationHeatmap?raw=true">
  
 # Correlation Heatmap - Gangue vs. Features
 
 <p style="text-align:center;">
    <img width="400" alt="Gangue Correlation Heatmap" src="https://github.com/patty-olanterns/mining_process_data/gangue-forecast-in-flotation-concentrate/blob/main/MineralContentFeedAndConcentrate?raw=true">
  
# Training_History_Losses_Graph
 
 <p style="text-align:center;">
    <img width="400" alt="Training_History_Losses_Graph" src="https://github.com/patty-olanterns/mining_process_data/gangue-forecast-in-flotation-concentrate/blob/main/TrainingHistoryLossesGraph?raw=true">
  
# Silica_in_Concentrate_Actual_Values_and_Forecasts_LSTM
 
 <p style="text-align:center;">
    <img width="400" alt="Silica_in_Concentrate_Actual_Values_and_Forecasts_LSTM" src="https://github.com/patty-olanterns/mining_process_data/SilicaInConcentrateActualVSForecastLSTM?raw=true">
  
 # SilicaInConcentrateActualVSForecastRandomForest
 
 <p style="text-align:center;">
    <img width="400" alt="SilicaInConcentrateActualVSForecastRandomForest" src="https://github.com/patty-olanterns/mining_process_data/SilicaInConcentrateActualVSForecastRandomForest?raw=true">
 
 
 # Conclusion
A deep learning approach using LSTM was implemented to forecast gangue content in flotation concentrate. Excluding *%iron in concentrate* from the features, *%silica in concentrate* were forecasted one hour ahead and with error below 1 (based on RMSE, MAE). As the dataset owner stated in [this post](https://www.kaggle.com/rogerbellavista/randomforestregressor-mae-0-0922-rmse-0-2314#434654), MAE and RMSE of 1±0.2 is a satisfactory result. 
 
For this model an RMSE of 0.77 was achieved. While there is room for improvement, the forecasts are a method for process engineers to assess concentrate purity and take corrective actions in advance, especially when purity deviates from the acceptable values.

Finally, although LSTM implementation in this notebook has met the objectives, it will benefit from further exploration:
- Forecasting with smaller lag timesteps. For example, a 30-minute lag for the features/inputs.
- Analysis of feature importance in order to understand which parameters of the flotation process greatly affect *%silica in concentrate*. This ensures that the important parameters are adjusted accordingly.
