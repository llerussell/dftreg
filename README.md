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


# define a directory of single page tiffs
data_path = '/define/your/path/here/'

# get all tiff files in directory
file_list = sorted(glob.glob(input_path + '*.tif'))

# read tiff files into array
array = tifffile.imread(file_list[0], multifile=True)

# register
dx, dy, registered_array = dftreg.register(array, save_name='test')
```
