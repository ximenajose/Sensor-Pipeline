Basic Sensor Firmware + Software 

Rossi, a 3-channel photodiode sensor array, takes individual captures to roughly measure light. 
Each channel is covered in a bandpass filter, which allows only for a limited wavelength to be detected into the sensor. 

After calibration is completed by finding the noise floors and usable maximums for each diode, as well as normalizing the sensors to a common working range, we can generate useful information. 

By weighting and combining the three channels we can produce a single-colored pixel, as well as plot the curve of an illuminant. 

Considerations should include: 
  additive effect of transmissive reduction caused by the Wratten filters used and the IR-cut filter;
  time-based integrative measurement noise per capture;
  spectral responses of the sensors used;
  spectral distrubitions of the illuminants measured.
  
