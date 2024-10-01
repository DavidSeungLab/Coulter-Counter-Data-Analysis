Purpose:
The script fits distributions to bimodal or unimodal size distribution curves to allow estimation of starch granule size.

Formatting of individual data files:
An example of how data should be formatted for input is provided - 'Data_template.csv'. This is the format of CSV files produced by the Multisizer 4e Coulter counter (Beckman Coulter). Briefly: Data should be organised in a csv file with a .csv filename - if not the script won't recognise it. The starting diameter of first bin should be placed in cell B56, with the corresponding differential volume (%) placed in the adjacent cell (C56). The maximum size of the final bin should be placed directly underneath the final row of data in column B. Lines 1-52 contained info from the coulter counter and these can be left empty as they are skipped by the script.


Organisation of data:
In your folder, all csv files should be placed in a subfolder called 'data_inputs'. Within the main folder you also need a subfolder called 'output'. The fitting and batch running scripts should also be placed within the main folder. The running script should be placed in an easy to access location, not necessarily the folder containing the data.

Running the script:
The scripts should be run using a Jupyter notebook. The running script is the only script which needs to be accessed and opened. Once opened, change the working directory to the folder containing your data (without data_inputs). The script can now be ran. The scripts contains optional parameters which can be altered:
	
	x_value_to_plot_to = default 50 - this is maximum value plotted on the x axis, for the 70 um aperture 50 is 	enough, but should be increased if a larger aperture is used so that the data are not truncated

	display_initial_parameter_graphs = default 'FALSE', options are 'TRUE' or 'FALSE', if true then plots of the 	initial parameters will be saved, these can be useful if the fits are bad and you want to alter the initial 	parameters before rerunning the fitting

	it also allows the initial parameters of the initial parameters to be edited individually

To alter any of the optional parameters remove the # from the front of the line and change the value as appropriate

Outputs:
The scripts produce multiple outputs to allow efficient data analysis of data. 
Firstly, it generates a series of pdf files containing graphs of the fittings for each of the samples. In these graphs, the data and fitted curves have been divided by the sum of the raw volume (%), which is a simple stretch and results in no changes to the overall fitting or calculated parameters (Figure 1c). This brings the y-axis more in line with the scale from the raw output of the Coulter counter and previous literature. 
Secondly, it produces Excel spreadsheets: ‘Starch_parameters_from_fittings’ which gives the mean and variance of granule size for all optimised fittings, and for the bimodal script gives A- and B- granule contents (Table 1); ‘Mathematical_values_to_reproduce_fittings’ contains all fitting parameters from the optimised fitting, along with uncertainties for each fitting parameter, to allow users to re-plot the mathematical curves if required (Table 2). 
Finally, the script produces a plot of S and total uncertainty values for all models for all samples. This assists the user in selecting the best overall model for curve fitting within their dataset, as the model that produces the lowest values for most samples can be easily visualised.
Error catching is incorporated to produce lists of samples where the script completely failed to produce fittings (“Samples_where_the_script_failed.xlsx”) suggesting an issue with the format of the input data, or where the fitting could not be sufficiently optimised (“Samples_which_fitted_successfully_and_samples_which_failed”) suggesting that none of the models provide an optimal fit for the data.
