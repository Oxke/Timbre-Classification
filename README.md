# Timbre classification problem
The goal of this project is to classify different musical instruments based on
their timbre.

## Dataset
The dataset used is the [Philarmonia sound samples
dataset](http://www.philharmonia.co.uk/resources/sound_samples/). The dataset
contains 13535 samples of 19 different orchestra instruments. Each instruments
has samples that differ in pitch, dynamics and playing technique.

## Preprocessing
The dataset is preprocessed by extracting the Mel-frequency spectrogram of each
sample in 129 different frequency bands and 9 time frames. The spectrogram is
then flattened to a 1D array of 1161 features.

## Model
Different models are trained on the dataset to classify the instruments. The
best performing model is a Perceptron as a One-vs-One classifier, with PCA to
reduce dimensions and oversampling to balance the classes. The model achieves an
accuracy of 0.80 on the test set.

## Results
![Confusion matrix](https://github.com/user-attachments/assets/f92aae9c-6395-4b5f-880a-60ccd36ddc21)

The confusion matrix shows that the most difficult instruments to recognize are the
ones with the least samples in the dataset. This probem could be solved by
extending the dataset and trying to manage the class imbalance in other ways
then just using balanced accuracy as the metric for the loss functions. Another
possibility is to change the way the data is represented: at the cost of a much
higher resources usage, we could have a more detailed spectrogram, for example
by using a longer bit of audio, in order to analyse more then 0.2 seconds for
each recordings, and have more detail in the frequencies, instead of binning it
to just 129 ranges. However, this would hugely impact the computational cost.

It must be noted that many of the instruments are very similar in timbre, and
having different techniques of playing the same instrument could make the task
even harder. For example, violin pizzicato and violin arco are very different
and could be easily misclassified as different instruments, while violin
pizzicato and viola pizzicato are very similar and could be easily misclassified
as the same instrument.

Finally. It could be the case that analysing and storing the audio files in
different ways might give better results (ex. performing some kind of cleaning
from noise and adding a low and high frequency cut in order to limit our
knowledge to the useful data)
