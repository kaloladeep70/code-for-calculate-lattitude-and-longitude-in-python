# code-for-calculate-lattitude-and-longitude-in-python
 f= []  
     
ds = gdal.Open(r'D:\deep_ongoing\dtiff.tif')

# GDAL affine transform parameters, According to gdal documentation xoff/yoff are image left corner, a/e are pixel wight/height and b/d is rotation and is zero if image is north up. 
xoff, a, b, yoff, d, e = ds.GetGeoTransform()

def pixel2coord(x, y):
 """Returns global coordinates from pixel x, y coords"""
 xp = a * x + b * y + xoff
 yp = d * x + e * y + yoff
 return(xp, yp)

# get columns and rows of your image from gdalinfo
rows = 1404
colms = 1717

if __name__ == "__main__":
 for row in  range(0,rows):
  for col in  range(0,colms): 
      f.append (pixel2coord(col,row))
  
