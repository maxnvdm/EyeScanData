# Eye scan data processing

## File descriptions
### calculateBER.ipynb
This file processes the eye scan data output from the FPGA. Using the samples, errors, offsets, prescales and UT signs from the input data to calculate the BER at each pixel in the eye diagram.


An example input file is provided: prescale9defaultConfig.csv 


The associated output file is also provided: eyeDataprescale9defaultConfig.csv

### generateEyeDiagram.ipnyb
This file is used to plot the eye diagram from the processed eye scan data. 


Using the input file: eyeDataprescale9defaultConfig.csv


The following eye diagram is produced:


![eyeDiagramWithoutMask](https://user-images.githubusercontent.com/21842664/120776151-32ff0380-c524-11eb-825b-8e8ea38d5cec.png)


This file also has the ability to plot a mask over the eye diagram to determine if the eye diagram meets the given specifications (eye mask measurements).


An example of the eye diagram passing the provided mask measurements can be seen in the following image:


![eyeDiagramWithMaskPass](https://user-images.githubusercontent.com/21842664/120776171-37c3b780-c524-11eb-9e28-42c9a3e2b6b1.png)


An example of the eye diagram failing to meet the provided mask measurements is shown below:


![eyeDiagramWithMaskFail](https://user-images.githubusercontent.com/21842664/120776145-309ca980-c524-11eb-8e1f-6e0c3cdfdc5c.png)



The points used to describe the mask are illustrated in the following diagram:


![EyeDiagramMaskDefinition](https://user-images.githubusercontent.com/21842664/120774661-c6cfd000-c522-11eb-8f53-5b893f70335c.PNG)


### prescale9defaultConfig.csv
This is an example of the data output from the FPGA (before the BRAM readout/LabView interface was developed). The important aspects of the data are the samples (16bit hex), errors (16bit hex), vertical and horizontal offsets. The veritcal offset is labelled vertOut (16bit hex) and contains more than just the vertical offset, following the data structure: { 5'b Prescale, 2'b00, 1'b UTsign, 1'b OffsetSign, 7'b VertOffset }. The horizontal offset is labelled horzOut (16bit hex) and follows the data structure: { 5’b00000, 11'b HorizontalOffset } where the 11bit HorizontalOffset uses two's compliement to distinguish positive and negative offsets.

### eyeDataprescale9defaultConfig.csv
This is an example of the output from the calculateBER.ipynb file. It contains a table of the BER calculated for each horizontal and vertical offset.


