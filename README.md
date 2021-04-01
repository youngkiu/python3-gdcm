python3-gdcm wrapper

I built the wrapper for python by building the latest gdcm source based on python docker.

### local build/installation instructions

```bash
apt-get update
apt install -y python-vtk6 libvtk6-dev cmake-curses-gui swig
mkdir gdcm && cd gdcm
git clone --branch release git://git.code.sf.net/p/gdcm/gdcm
mkdir build && cd build
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_C_FLAGS=-fPIC -DCMAKE_CXX_FLAGS=-fPIC -DGDCM_BUILD_SHARED_LIBS:BOOL=ON -DGDCM_WRAP_PYTHON=ON PYTHON_EXECUTABLE=/usr/local/bin/python3.8 PYTHON_INCLUDE_DIR=/usr/local/lib/python3.8/site-packages/ GDCM_BUILD_SHARED_LIBS=ON GDCM_USE_VTK=ON /gdcm/gdcm
cmake --build . --target install

cp /usr/local/lib/gdcm.py /usr/local/lib/python3.8/site-packages/.
cp /usr/local/lib/gdcmswig.py /usr/local/lib/python3.8/site-packages/.
cp /usr/local/lib/_gdcmswig.so /usr/local/lib/python3.8/site-packages/.
cp /usr/local/lib/libgdcm* /usr/local/lib/python3.8/site-packages/.
ldconfig
```
