## 淮海经济区
不是给xueyong的版本
```python
#  框选地理范围
roi = ee.Geometry.Polygon(
        [[[114.69, 32.99],
          [119.91, 32.99],
          [119.91, 36.31],
          [114.69, 36.31]]])
roiGeo = ee.Geometry(roi).toGeoJSONString()

# 插值到统一的范围
ds_i = ds.interp(longitude=np.array(range(520))*0.01 + 114.705,latitude=np.array(range(330))*0.01 + 33.005)
ds_i.to_netcdf(filePath/f'{feature}.nc')
```


## 徐州
```python
netCDF_xr_i = netCDF_xr.interp(longitude=np.array(range(480))*0.005 + 116.3025,latitude=np.array(range(280))*0.005 + 33.6025)
```

## 江苏
```python
#  框选地理范围
roi = ee.Geometry.Polygon(
        [[[116.0, 30.4],
          [122.3, 30.4],
          [122.3, 35.4],
          [116.0, 35.4]]])
roiGeo = ee.Geometry(roi).toGeoJSONString()

# 插值到统一的范围
ds_i = ds.interp(longitude=np.array(range(575))*0.01 + 116.305,\
                 latitude=np.array(range(450))*0.01 + 30.655)
ds_i.to_netcdf(filePath/'0.01.nc')

ds_i = ds.interp(longitude=np.array(range(25))*0.25 + 116.2,\
          latitude=np.array(range(20))*0.25 + 30.63)
ds_i.to_netcdf(filePath/'0.25.nc')
```

## 宁东（规划）
实际上这个范围偏大
```python
#  框选地理范围
roi = ee.Geometry.Polygon(
        [[[106.1, 37],
          [107, 37],
          [107, 38.8],
          [106.1, 38.8]]])
roiGeo = ee.Geometry(roi).toGeoJSONString()

# 插值到统一的范围
ds_i = ds.interp(longitude=np.array(range(450))*0.002 + 106.1,\
                 latitude=np.array(range(850))*0.002 + 37.1)
ds_i.to_netcdf(filePath/(feature+'.nc'))
```
绘图时一般只取
```python
lonlim=(106.1, 106.9),latlim=(37.89,38.67),
lonlines=plot.arange(106.1, 106.9, 0.2), #lonlines=90,
latlines=plot.arange(37, 39, 0.2),
```
