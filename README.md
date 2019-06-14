# Purewater_SpecBuilder_acs
Creates single absorption (a) and attenuation (c) spectra for Wet Labs ac-s meter pure-water calibration measurements as performed in the laboratory, typically directly preceding or following a field deployment. 

Program Description:
WET Labs ac-s meter (ac-s) measures spectral absorption and attenuation in the visible range (~400-750 nm) at 80+ spectral channels within natural water bodies. To ensure the highest level of instrument precision and data quality, ac-s should be calibrated on a regular basis in a laboratory setting. This is typically performed by running deionized water through ac-s flow chambers while the instrument is collecting measurements. When processing field data, these pure-water measurements are subtracted from a and c spectra in order to correct for directional instrument-related noise. 

Before laboratory-measured pure-water data can be subtracted however, it must first be averaged into single a and c spectra. During laboratory calibrations, ac-s is typically permitted to collect data for several minutes as deionized water continuously flows through its chambers. These measurements can flutuate widely, especially in the start of the calibration period, yielding extreme a and c values that are not representative of pure-water a/c as measured by the ac-s. Therefore, before averaging laboratory-collected pure-water absorption and attenuation data into single a and c spectra, investigators need select a portion of the time series that is unlikely to be contaminated and thus likely representative of actual pure-water optical properties as measured by ac-s. Purewater_SpecBuilder_acs accomplshes this by allowing users to visualize laboratory-collected ac data and interactively select the timeseries region to subset and average into single pure-water spectra.

Inputs: 
File_name.dat - laboratory-measured pure-water a or c data as sampled by ac-s 

Outputs:
File_name.mat - contains a single averaged pure-water a or c spectrum with corresponding wavelengths and average water temperature
File_name_gateSAMPLE.jpg - displays a/c "time series" with user-selected min/max indices
File_name_spectrum.jpg - displays a/c spectrum along with averaged temperature at each wavelength (temperature will be a horizontal straight line if user does not change min/max indices (see below).

Directions for use:
1. User run Purewater_SpecBuilder_acs using matlab command window or editor. The script is designed to process absorption and attenuation data (DAT files) separately. Upon initiation user is prompted to enter "a" or "c" into the command window to specify whether he/she is analyzing absorption or attenuation respectively.
2. User selects a ac-s pure-water DAT file when requested to do so. Confirm or reject selection with "y" or "n".
3. A time series plot displaying pure-water a or c (depending on previous selection) of the first ac-s channel (lowest wavelength). Y-axis represents a/c (m^-1), x-axis depicts "time" as numerical indices (DemoFig1.jpeg).
4. Select the region of the a/c time series for which to average by entering the minimum and maximum indices of "time series" as prompted by the command window. This should be a region with stability (e.g. negligible fluctuation) in a/c. Purewater_SpecBuilder_acs will average a/c values found between min/max indices. 
5. As user makes his/her selection, positions of selected indices will appear on the plot as vertical lines. This allows user to visualize selection to ensure he/she did not make a selection error. User is prompted to confirm or reject selections on command window using "y" or "n" keys. If user selects "n", he/she will be prompted to re-select min/max indices.
6. Upon confirmation of min/max selection, Purewater_SpecBuilder_acs will display a/c time series of the second ac-s channel (second lowest wavelength), along with user's previously-selected min/max time series indices. User is prompted to re-confirm previously-selected indices. If user is satisfied with previous selection, he/she enters "y" into the command window and will be directed to the next channel. If user is unsatisfied, he/she enters "n" as is prompted to re-select min/max time series indices. These newly-selected min-max indices will not apply to previous ac-s channels, only the ones that have not yet been evaluated.
7. Purewater_SpecBuilder_acs prompts user to repeat step 6 for all ac-s channels. Upon completion, the script will calculate average of user-selected time series regions.
