<h1>Machine Learning Instrument</h1>

![We call it bambooz](Example.png)

<h2>Concept</h2>
This project was inspired by the approach to improvisation based experimental music known as “environmental improvisation” explored in depth in Chinese sound artist Li Jianhong’s (李剑鸿) work https://www.discogs.com/artist/583392-Li-Jianhong. Understood simply as a musical improvisation with and within a given environment we aimed to extend it to both artificial and natural environments and sites where these environments overlap and co-exist, such as the Guangzhou Campus of HKUST where unused plots of land meet the WLAN covering the entirety of the campus. Initially conceived as an exploration of found objects and shapes, this project gradually shifted focus towards the idea of “found environments” while retaining the improviser’s agency to express themselves sonically with and within the said environments. 

<h2>Contribution</h2>
We demonstrated the feasibility to use deep learning to convert analogue inputs of an instrument into a digital sound, and contribute a software architecture that took multiple input to power multiple outputs simultaneously, and sends input from esp32 or Microbit to p5js, via wire or wireless.  The software model is generic and can be applied to other projects which benefits from using multiple input to control multiple output (e.g., multiple axis).  You can run the code here https://editor.p5js.org/maestr001/sketches/623-W5b (tested on a microbit).  

<h1>Technical realization</h1>

<h2>Hardware</h2>
The design and functionality of the object were inspired by the forms and properties of traditional (bamboo stems and strips) and post-traditional materials (synthetic strings, plastic zip-ties) widely used in carpentry and construction in Mainland China and Hong Kong that do not require sophisticated tools to work with. The ability to heat-shape bamboo strips while retaining its natural flex “felt right” and paired well with the commercially available flex sensors and the straightness of bamboo reeds lent itself naturally to be re-imagined as a vertical axis connecting the aether of high frequency WLAN and the easily accessible properties of the ground (moisture level). The sensor data was collected with the use of generic ESP32 microcontroller, while it’s built in WLAN capacity was leveraged (and reinforced with an external antenna) to report the wireless signal strength and wirelessly transmit the sensor readings to the training algorithm over UDP.

<h2>Software</h2>
To turn movement, and the variables from the environment, into sound, we build a deep learning model which processed 3 input parameters (one for each sensor) and 3 output parameters (one for each sound signal).  The signals were read in as a string, parsed as an array which was passed into a simple, multilayer regression model with Tensorflow architecture.  We chose the regression model vs classification because we wanted the sound to be continuous (e.g., a slide on the violin) rather than discrete (e.g., a key on the piano). The software was developed using p5js, ml5js, and various packages from p5js such as p5serial and p5sound libraries.  

<br/>The architecture of can be found below: 

![Architecture](architecture.png)</p>

<h2>Limitations</h2>
Apart from the obvious technical difficulties of interfacing and integrating multiple layers some of the conceptual challenges (common to the NIME (New Interfaces for Musical Expression) and DMI (Digital Musical Instrument) domains) have become apparent during our work on the project. In such hybrid entity there is always a gap between the physical interface and the sounds it produces – the dissonance that doesn’t exist in most “traditional” instruments. This gap emphasizes the arbitrarily of parameter mapping and Machine Learning can be considered as a potent tool to overcome this gap. That said utilizing ML for these ends tends to create enough challenges of its own, for example it showed the inadequacy of the UI elements (sliders, buttons etc) usually used to train the model.

