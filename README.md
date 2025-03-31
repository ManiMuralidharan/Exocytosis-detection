# Exocytosis-detection
Exocytosis detection from Excel intensity values 
This MATLAB code creates a Graphical User Interface (GUI) for annotating and selecting specific ranges of data from vesicle and FRET (Förster Resonance Energy Transfer) traces stored in an Excel file. Here's a breakdown of what it does and how to use it:

Purpose:

The GUI allows users to:

Load Excel Data: Import time-series data from an Excel file.
Navigate Through Data Pairs: Display and navigate through vesicle and FRET trace pairs stored as columns in the Excel file.
Select Data Ranges: Interactively select a range of data points on the vesicle trace.
Save Selected Data: Save the selected data range, including time, vesicle intensity, and FRET ratio, to a .mat file.
Visualize Data: Plot the vesicle and FRET traces and highlight the selected data range.
How to Use:

Run the Code:

Copy and paste the code into a new MATLAB script file (.m file).
Run the script. This will open the GUI window.
Load Excel Data:

Click the "Load Excel" button.
Select the Excel file containing your data. The Excel file should have the following structure:
The first column contains time points.
Subsequent columns contain vesicle and FRET ratio pairs (vesicle, ratio, vesicle, ratio, etc.).
Navigate Through Data Pairs:

Click the "Next Pair" button to display the next vesicle and FRET ratio pair.
The current pair number is displayed in the plot title.
Select Data Range:

Click the "Select Range" button.
The plot title will change to "Select START and END points on vesicle trace".
Click on the plot to select the start and end points of the desired range on the vesicle trace.
The selected range will be highlighted on the plot with markers.
The number of selected points and the mean FRET ratio within the selected range will be displayed in the corresponding text boxes.
The plot title will change to display the selected time range.
Save Selected Data:

Click the "Save Selection" button.
Choose a filename and location to save the selected data as a .mat file.
The saved .mat file will contain a structure named selection with the following fields:
filename: The name of the Excel file.
pairIndex: The index of the selected pair.
timeRange: The start and end times of the selected range.
timePoints: The time points within the selected range.
vesicleValues: The vesicle intensity values within the selected range.
ratioValues: The FRET ratio values within the selected range.
meanRatio: The mean FRET ratio within the selected range.
Code Explanation:

vesicleTraceGUI function:

Creates the main GUI figure and UI controls (buttons, text boxes, axes).
Defines callback functions for each button.
Stores shared data in the data structure.
loadExcel callback:

Prompts the user to select an Excel file.
Reads the data from the Excel file using readtable.
Stores the data in the data.table field.
Initializes the pairIndex to 1 and displays the first pair.
nextPair callback:

Increments the pairIndex to display the next pair.
Removes the selectedRange field if it exists.
Calls showCurrentPair to update the plot.
showCurrentPair function:

Extracts the time, vesicle, and FRET ratio data for the current pair.
Plots the vesicle and FRET traces on the axes.
Highlights the selected range (if any) with markers.
Updates the text boxes with the number of selected points and the mean FRET ratio.
Sets the plot title and labels.
selectRange callback:

Prompts the user to select the start and end points of the range using ginput.
Finds the indices of the closest time points to the selected start and end times.
Stores the selected range data in the data.selectedRange field.
Calls showCurrentPair to update the plot.
saveSelection callback:

Prompts the user to choose a filename and location to save the selected data.
Creates a selection structure containing the selected data.
Saves the selection structure to a .mat file.
Displays a message box confirming the save operation.
This GUI simplifies the process of manually selecting and annotating data ranges from vesicle and FRET traces, making it easier to analyze and extract relevant information from your experiments
