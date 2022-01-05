# Varshini-T-IP-Lab
# Develop a program to perform linear transformation on a image.
import cv2

image = cv2.imread('yeontan.jpg')

height, width = image.shape[:2]

center = (width/2, height/2)

rotate_matrix = cv2.getRotationMatrix2D(center=center, angle=45, scale=1)

rotated_image = cv2.warpAffine(src=image, M=rotate_matrix, dsize=(width, height))

cv2.imshow('Original image', image)![148201346-cc96e108-c021-4fc1-ad38-02035fa21762](https://user-images.githubusercontent.com/95745335/148201464-9330fe3f-bdd0-4a87-8734-d5995c895a6f.png)

cv2.imshow('Rotated image', rotated_image)

cv2.waitKey(0)

cv2.imwrite('rotated_image.jpg', rotated_image)

# OUTPUT :
![image](https://user-images.githubusercontent.com/95745335/148201346-cc96e108-c021-4fc1-ad38-02035fa21762.png)
![image](https://user-images.githubusercontent.com/95745335/148201428-03888741-313c-4523-b912-8c519fc6c992.png)

