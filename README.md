# dftreg
python module for image sequence registration

#### dependencies
* numpy
* scipy
* pyfftw (optional)
* skimage (for tifffile, optional)

#### install
```
cd ~
git clone https://github.com/llerussell/dftreg.git
cd dftreg
python setup.py build
sudo python setup.py install
cd ~
```

#### example usage
```ruby
import dftreg
import glob
from skimage.external import tifffile
import numpy as np


# define a directory of single page tiffs
data_path = '/define/your/path/here/'

# get all tiff files in directory
file_list = sorted(glob.glob(input_path + '*.tif'))
num_frames = len(file_list)

# read first file to get dimensions and datatype
first_file = tifffile.imread(file_list[0], multifile=False)
im_dim = first_file.shape
im_dtype = first_file.dtype

# make array
raw_frames = np.zeros([num_frames, im_dim[0], im_dim[1]], dtype=im_dtype)

# read frames into array
for i, frame in enumerate(file_list):
    raw_frames[i] = tifffile.imread(frame, multifile=False)

# register
dy, dx, registered_array = dftreg.register(raw_frames, save_name='test')
```
