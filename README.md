# Cross-View Fusion Dataset



## Synthetic datasets 

Synthetic datasets are composed of over-view image set taken by UAV and street-view video and LiDAR data taken by UGV (Unmanned Ground Vehicle). The data acquisition environment is based on Unreal Engine 4, and the UAV, UGV and various sensors are controlled by Airsim simulation. For the over-view image set, the GNSS information is stored as well as the color image. For street-view scene, the camera and LiDAR are loaded in front of the UGV to capture the environmental information in real time and record the information through the recording function of ROS.



## Real World Datasets 

For the real world dataset: the DJI Mavic 2 Pro UAV is used to cruise the urban area at a certain image repetition rate, take photos at regular intervals, record the GNSS position information when taking photos, and generate an over-view image set. The flight altitude is about 65 meters. For the collection of street-view environment on the ground side, we use RealSense D435 camera, Livox Avia LiDAR and GNSS receiver, which are connected to Jetson Xavier NX for data collection.



##  Explain  

For the over-view image set, the GNSS information is stored in the EXIF partition of the picture. You can use python `py3exiv2` package to get it.

There is a example:

```python
import pyexiv2
import fractions

template = pyexiv2.ImageMetadata('[image].png')
template.read()
print(template['Exif.GPSInfo.GPSAltitudeRef'].value)
print(template['Exif.GPSInfo.GPSAltitude'].value)
print(template['Exif.GPSInfo.GPSLatitudeRef'].value)
print(template['Exif.GPSInfo.GPSLatitude'].value)
print(template['Exif.GPSInfo.GPSLongitudeRef'].value)
print(template['Exif.GPSInfo.GPSLongitude'].value)
```

 For the street-view information, we use `rosbag`  to store it.  For the simulation dataset, we use `zstdmt` to compress it. You can use `zstdmt -d` to decompression.

### Download

download link：https://pan.baidu.com/s/1Qx3cpg-HyQ8f8JTlHsy00g 
extraction code：p63s 

