# Pocratsky2023_signalScript
Custom-written script for signal analysis of monosynaptic reflexes (CED Signal). Associated with Pocratsky et al 2023, Science Translational Medicine.

I. SCRIPT INFO
- This script quantifies and formats (for figures) the in vitro monosynaptic reflex. 


II. ANALYSIS INFO
- This script is written for quantifying the following parameters for in vitro
monosynaptic reflex using XYdataPlot relative to baseline threshold activity. You will first format the data and use static and active cursors to define
the ROI for analysis and measure the baseline activity preceding stimulus. Thereafter, you will calculate the parameters listed above relative to the
baseline threshold activity. Data will be shown in XY plots for export.


Button functions on Toolbar: 
 1. Open: 
    End user will select file to analyse (must be a CED Signal .cfs data file)

 2. Set-up: 
    2a. Optional: define channel title(s)
    2b. Select channel to measure
    2c. Define stimulus onset (unit = seconds)
    2d. Prompt: prior to proceeding with analysis (standard waveform and/or complex waveform functions)
                end-user must tag any frames that should be excluded from analysis
 
 3. Standard waveform: select this option if the reflex is "textbook" and there is little noise
    This script primarily uses dynamic cursors to calculate cursor positioning and waveform measurement
    End user will have two options: Full Analysis or Select Outcome(s) of Interest
    
   - 3a. Option-1: Run Full Analysis - the following outcome parameters will be calculated automatically
        - (i) latency to onset, 
        - (ii) latency to and amplitude of peak, 
        - (iii) area (positive response),
        - (iv) RMS (positive response), 
        - (v) minimum, 
        - (vi) positive response duration, 
        - (vii) triphasic response duration 
   - 3b. Option-2: Select Outcome(s) of Interest - end user will select the from the above list which parameter(s)
                  the script will measure
   - 3c. After selecting the analysis strategy, end user will be prompted to define threshold crossing strategy to
        measure signal above baseline 
        - Option-1: Use BL+2SD denotes baseline + 2 standard deviations, preferred for noisy signal
        - Option-2: Use BL(+/-)2SD denotes baseline + 2 standard deviations for rising threshold crossing and 
                                         baseline - 2 standard deviations for falling threshold crossing
   - 3d. After confirming threshold crossing strategy, end user will be prompted to accept or revise cursor 
        placements for all frames, all sweeps
   - 3e. Final output will be XY trendplot, to be exported in raw (.xy) and .txt format for subsequent offline analysis  

 4. Complex waveform: select this option if reflex shows altered, complex waveform and/or noise contamination
    This script uses a combination of static and dynamic cursors to measure more complex waveforms and/or signal
    that is contaminated with noise. *Static* cursors will be placed around evoked response - irrespective of "on-off" - 
    to calculate the latency to peak (from stim onset) and amplitude of peak (within ROI).
    End user will be prompted with three options for "Select outcome measure(s)":
    - 4a. Option-1: True peak evoked response
        This option will return the following measurements for the *largest* spike observed in a multipeaked response:
        - (i) latency to onset, 
        - (ii) latency to and amplitude of peak, 
        - (iii) duration (positive response), 
        - (iv) area (positive response)
    - 4b. Option-2: First evoked response (multipeaked)
        This option will return the following measurements for the *first* spike observed in a multipeaked response:
        - (i) latency to and amplitude of first response
        Nb: this script is error prone, cursor placement requires careful oversight by end-user!
    - 4c. Option-3: Total evoked activity
        This option will return the following measurements for *broadened* reflexes that show prolonged onset-offset duration:
        - (i) duration and 
        - (ii) area
    After selecting analysis strategy, end user will be prompted to repeat steps described above (3c-3e)

 5. Format: prepare sweeps for figure export
    - 5a. End user must define the top (y-max), bottom (y-min), left (x-min), and right (x-max) in seconds
    - 5b. Output will be two plots: left plot = overdrawn frames (gray), right plot (red) = averaged waveform
    - 5c. As of 2022-04-30, the average waveform function is broken. X-max value input value is not being recognised.
   
 6. Clean-up: restores dataview, removing formatting applied for figure export

 7. Quit: closes script toolbar

 Summary of measurement details:
 1. Latency to onset : time to first rising threshold crossing
 2. Latency to peak : time to and amplitude of peak evoked response* (see revision below)
 3. Peak response : amplitude of peak positive evoked response
 4. Area (under the curve for positive response component of triphasic wave)
 5. RMS (under the curve for positive response component of triphasic wave)
 6. Response duration (for positive component of triphasic wave)
 7. Peak-to-peak response (for full triphasic wave)
 8. Minimum response : time to and amplitude of max negative evoked response
 9. Triphasic duration : total response duration from onset to return threshold crossing
   

III. FORMATTING INFO
 - The data will be formatted as follows:
 1. User-defined scaling for x- and y-axes
 2. Overlay all sweeps collected (traces = gray)
 3. Average waveform will be calculated and scaled identical to raw data (trace = red)
 4. Data views will be scaled equally for post hoc overlay in figure editing software
