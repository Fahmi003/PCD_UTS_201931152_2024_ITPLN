#soal nomor 2

import cv2
import numpy as np
import matplotlib.pyplot as plt
def detect_color(image, lower_red, upper_red, lower_blue, upper_blue):
    # Konversi citra ke ruang warna HSV
    hsv_image = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)
    
    # Buat mask untuk warna merah dan biru
    mask_red = cv2.inRange(hsv_image, lower_red, upper_red)
    mask_blue = cv2.inRange(hsv_image, lower_blue, upper_blue)
    mask_green = cv2.inRange(hsv_image, lower_green, upper_green)
    
    # Gabungkan mask biru dan mask merah
    mask_combined = cv2.bitwise_or(mask_red, mask_blue, mask_green)
    
    # Aplikasikan mask ke citra asli
    result = cv2.bitwise_and(image, image, mask=mask_combined)
    
    return result
image = cv2.imread('nama.jpg')
lower_red = np.array([136, 87, 111])
upper_red = np.array([180, 255, 255])
lower_green = np.array([40, 50, 50])
upper_green = np.array([90, 255, 255])
lower_blue = np.array([100, 50, 50])
upper_blue = np.array([140, 255, 255])
a = detect_color(image, lower_red, upper_red, lower_blue, upper_blue)
plt.figure(figsize=(12, 8))

plt.subplot(231)
plt.imshow(blue_gray, cmap='gray')
plt.title('Blue Image')

plt.subplot(232)
plt.imshow(a, cmap='gray')
plt.title('Blue Red Image')


plt.tight_layout()
plt.show()
