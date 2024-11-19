# NASAHackathonIMADE
UIUC i-MADE repo for NASA Hackathon 2024
High-Level Summary


**Provide a high-level summary of your project. What did you develop? How does it address the challenge? Why is it important?**

To address the challenge of detecting seismic events across the solar system, our team developed a solution combining advanced signal processing and machine learning. We first designed signal processing logic to parse seismic data, which involves converting raw data into the miniSEED format. From this, we extract key features such as velocities and timestamps for each data point.

Next, we applied a Short-Term Average to Long-Term Average (STA/LTA) ratio algorithm to detect potential seismic events, followed by a high-pass filter to reduce noise by removing low-frequency components. This refined data was then used to train a machine learning model capable of predicting the start times of seismic events.

Our trained model can now identify the onset of seismic events within a specified time interval, achieving an accuracy of x%. This approach combines precise signal extraction with predictive modeling, significantly enhancing our ability to detect and predict seismic activity in a complex extraterrestrial environment.


**Project Details
Provide additional details about your project. What exactly does it do? How does it work? What benefits does it have? What do you hope to achieve? What tools, coding languages, hardware, or software did you use to develop your project?**


**There are two parts to our project: Signal Processing and the Machine Learning Model. Our signal processing logic involves a series of steps:


Signal Processing:**

Convert raw data into mSEED file → pass file through a high pass filter to remove low frequency noise → generate sta/lta graph using sta/lta ratio algorithm → use previously calculated throttle values to predict start times.
To prepare our signal for the machine learning models, we carried out a series of signal processing techniques to increase the models’ accuracies. 
First, we converted the data from miniSEED format to a numpy.ndarray so that we can apply commonly used signal processing techniques to make the data more suitable for the ML models.
Next, we applied a novel signal processing technique, which we could not find a previous use of in our preliminary research. More specifically, we created a wavelet transformation function based on the lognormal distribution, which we found to best match the shape of seismic events in our training data. After applying this wavelet transformation function, we used the exaggerated values to created a threshold for a boolean mask of key data to include from the original seismic data, reducing a significant amount of noise, and thus improving the performance of both our algorithmic and machine learning seismic detection approaches.
After that, we passed the resulting, masked data through a high pass filter to filter out even more low frequency noise. 
From this point, we created graphs of the Short Term Average/Long Term Average (STA/LTA) ratio vs time, to be able to extenuate potential seismic events even more.
Following that, we applied a throttling detection algorithm to this preprocessed STA/LTA graph to predict potential start and end times based on the STA/LTA ratio.
Finally, we filtered each of these potential starts to make sure they met a specific threshold of width that is correspondent to average seismic events, by calculating the difference in time between each start and their corresponding ends. 
Using pure signal processing techniques gave us already an accuracy of 45%. We then also took this fed this processed data following the continuous wavelet transform and the high pass filter into our Machine Learning models.
Machine Learning:
We created two different types of models to apply our training data to in order to see which one yielded the best results. The regular LSTM model and the PhaseNet model. LSTMs are an RNN that is meant to capture long-term dependencies in sequential data. PhaseNet is a deep learning model meant specifically for seismic phase picking.


**Space Agency Data
Please list the resources used. You are welcome to use any open data in your project. However, to be eligible for a Global Award, you must use data or resources from NASA.

References
In addition to Space Agency Agency data, list any data, resources, and tools used in your project. Resources should include any code, text, and images (even if they are open source or freely available) that you used when creating your project. If you are using any copyrighted materials, make sure you have permission to use them.**


