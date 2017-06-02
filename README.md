# axes_sequence
Allows for making a single matplotlib-figure with multiple frames/axes in it. These axes can be navigated with keyboard-arrows. Made for Python (pyplot from matplotlib).

![alt text][screen1]![alt text][screen2]  ![alt text][screen3]    

Above shows three examples of a frame in an AxesSequence. The frame-numbering at the top-right corner can be toggled.

### Quick run

The main-block at the bottom of the script will create an AxesSequence of eight frames for showing how 
everything works.

### How to use it
You create an axes-sequence and query it for new axes. The queries can be used either by iterating over the AxesSequence
or by calling `next()` on it for a single new frame. These two methods can be used interchangeably.
```python
import numpy as np
from axes_sequence import AxesSequence

# Make axes-sequence
axes = AxesSequence()

# Add a couple of plots
for i, frame in zip(range(3), axes):
    x = np.linspace(0, 10, 100)
    frame.plot(x, np.sin(i * x))
    frame.set_title('Line {}'.format(i + 1))
    
# Add a single plot
frame = next(axes)
frame.plot([1, 4, 2, 3], [1, 2, 3, 4])
frame.set_title("Lonely plot")
```

### Navigation
You can navigate through the frames with the keyboard arrow-keys. `Home`- and `End`-buttons navigate to first and last 
frame respectively. `Delete` toggles the frame-numbering.  


[screen1]: https://github.com/North-Guard/axes_sequence/screenshots/screen1.PNG "First frame."
[screen2]: https://github.com/North-Guard/axes_sequence/screenshots/screen2.PNG "Seventh frame."
[screen3]: https://github.com/North-Guard/axes_sequence/screenshots/screen3.PNG "Eighth frame."