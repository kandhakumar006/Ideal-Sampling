## AIM
To demonstrate ideal sampling of a continuous signal using Scilab, ensuring accurate signal reconstruction while avoiding aliasing

## COMPONENTS REQUIRED:
python IDE with Numpy and Scipy

## PROGRAM:
```
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import resample
fs = 100
t = np.arange(0, 1, 1/fs) 
f = 5
signal = np.sin(2 * np.pi * f * t)
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal')
plt.title('Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
t_sampled = np.arange(0, 1, 1/fs)
signal_sampled = np.sin(2 * np.pi * f * t_sampled)
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal', alpha=0.7)
plt.stem(t_sampled, signal_sampled, linefmt='r-', markerfmt='ro', basefmt='r-', label='Sampled Signal (fs = 100 Hz)')
plt.title('Sampling of Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
reconstructed_signal = resample(signal_sampled, len(t))
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal', alpha=0.7)
plt.plot(t, reconstructed_signal, 'r--', label='Reconstructed Signal (fs = 100 Hz)')
plt.title('Reconstruction of Sampled Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()
```
## OUTPUT WAVEFORMS:
![Image 2025-03-28 at 10 29 34_aff5ddb4](https://github.com/user-attachments/assets/5d50173b-b94e-4d1c-afd1-348770aa1a10)
![Image 2025-03-28 at 10 29 56_99f3e976](https://github.com/user-attachments/assets/e2713889-62f2-44ec-a724-af8f6bbccbf8)
![Image 2025-03-28 at 10 29 57_3fbf2cfd](https://github.com/user-attachments/assets/fd7038cb-4f4c-4ef0-aa4c-bfe028558ff2)


## RESULT:
Ideal sampling captures a continuous signal at perfect intervals, ensuring accurate reconstruction if sampled at twice the highest frequency (Nyquist rate). It’s a key concept in digital signal processing and telecommunications. Practical systems approximate ideal sampling with some limitations.
