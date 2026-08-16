Basic Photometer Firmware + Software 

The device, a photodiode array of 3-channels, takes captures to roughly measure light. 
Each channel is covered in a Kodak Wratten filter, which allows only for a limited wavelength to be detected into the sensor. 

After calibration is completed by finding the noise floors and usable maximums for each diode, the sensors are normalized to a common working range.

By weighting and combining the contribution of these three channels we can produce a single-colored pixel, which would ideally plot a similar graph to the Spectral Distribution curve of the known illuminant being used to test it. 

Considerations should include: 
  additive effect of transmissive reduction caused by the Wratten filters used and IR-cut filter;
  time-based integrative measurement variation per capture;
  spectral responses of the sensors used;
  spectral transmissiveness of the filters used;
  spectral distrubitions of the illuminants measured.

The firmware maps out each photodiode to individual ADC pins which receive the incoming voltages and process those into digital numbers on a 16-bit scale. A button function is defined to capture when the voltage from that pin changes states, and only captures once for 0.02 seconds.
The firmware can have dark floor values set manually, as well gains per channel if needed. 
Dark floors are established as the readings captured during "near absolute dark conditions" which account for sensor noise. To normalize the system, each channel's raw contribution gets the dark floor reading subtracted from it to yield a usable range. Then, values are clamped at the maximum of 65535 per diode. The firmware then prints and plots the raw values as well as the normalized values. 

The display code receives the raw and corrected RGB photometer values sent by the device firmware over USB serial. A thread "listens" for new captures so that the connection with the Pico does not interrupt the live display. Several conversions occur:
1) Each corrected sensor value is brought from 16-bit (from 0–65,535) to an 8-bit range (from 0–255) and interpreted as an R, G, or B contribution to produce a single color pixel.
2) These same RGB values are combined using weighted red, green, and blue contributions, currently based on an NTSC scale of 0.30 R, 0.59 G, and 0.11 B, to produce a grayscale value.
Finally, the program displays the most recent captures of raw readings, corrected readings, 8-bit display values, RGB pixel, and grayscale pixel.

Considerations should include:
  scaling 16-bit (corrected) sensor values to 8-bit display;
  RGB weighting used for grayscale;  
  clipping or loss of precision during conversion; 
  RGB pixel represents sensor contributions, not precise measured color.

The device and systems are intended as educational tools to better understand the underlying systems used for cameras and telescopes, and which components and programs those  require to function. As such, the student acknowledges that the instrument does not yet yield metrologically or colorimetrically precise data, despite being an invaluable project as an introduction into detector optics and image science. 


  
