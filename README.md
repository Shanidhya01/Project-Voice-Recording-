#Voice Recording Project 🎤
This Python script records audio using the sounddevice library and saves it in two different formats using scipy.io.wavfile and wavio.

How It Works
1. Import Required Libraries

import sounddevice as sd
from scipy.io.wavfile import write
import wavio as wv
sounddevice: Used for recording audio.
scipy.io.wavfile: Provides a function (write) to save NumPy arrays as WAV files.
wavio: Another library for handling WAV files, allowing control over sample width.

2. Set Recording Parameters

freq = 44100  # Sampling frequency (Hz)
duration = 10  # Duration of recording (seconds)
freq = 44100: Sets the sampling rate to 44.1 kHz, the standard for high-quality audio.
duration = 10: Specifies that the recording should last for 10 seconds.

3. Record the Audio

recording = sd.rec(int(duration * freq), samplerate=freq, channels=2)
sd.rec(): Starts recording audio.
int(duration * freq): Calculates the total number of samples.
samplerate=freq: Uses the defined sampling frequency (44.1 kHz).
channels=2: Records in stereo mode (two audio channels).

4. Wait for Recording to Finish

sd.wait()
Ensures that the recording process completes before proceeding.

5. Save the Recording using scipy.io.wavfile.write

write("recording0.wav", freq, recording)
Saves the recording as "recording0.wav".
Uses write(filename, samplerate, data), where:
"recording0.wav" is the output file name.
freq is the sampling rate.
recording is the recorded audio data.

6. Save the Recording using wavio.write
   
wv.write("recording1.wav", recording, freq, sampwidth=2)
Saves the recording as "recording1.wav".
wv.write(filename, data, rate, sampwidth):
"recording1.wav" is the output file name.
recording is the recorded NumPy array.
freq is the sampling rate.
sampwidth=2: Sets the sample width to 2 bytes (16-bit audio)

Key Differences Between write() and wavio.write()
✅ scipy.io.wavfile.write() saves in a default integer format.
✅ wavio.write() allows specifying sample width (bit depth), providing more flexibility.

Conclusion
This script records 10 seconds of stereo audio at 44.1 kHz and saves it in two different WAV file formats. 🚀

