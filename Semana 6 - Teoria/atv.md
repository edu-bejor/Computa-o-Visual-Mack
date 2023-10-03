Faça uma pesquisa sobre como é possível:

1. Realizar a limiarização de uma imagem usando Python e scikit-image.

   Limiarização é o método mais simples de segmentação de imagens e pode ser usado no processo de binarização. Consiste na escolha de um ponto T, que é usado como limiar de modo que para dada imagem I >= T, a nova imagem recebe valores branco, caso contrário recebe valores preto, ou vice e versa. Quando a constante T é aplicável a uma imagem inteira, o processo dado nesta equação é conhecido como limiarização global. Quando o valor de T muda ao longo da imagem, usamos o termo limiarização variável, ou adaptativa.  
   Exemplo de como realizar a limiarização de uma imagem:
  ```
import matplotlib.pyplot as plt
from skimage import io, color, filters

img = io.imread('img.png') 

gray_image = color.rgb2gray(img)

threshold_value = 0.5 

binary_image = gray_image > threshold_value

fig, axes = plt.subplots(1, 2, figsize=(10, 5))
ax = axes.ravel()

ax[0].imshow(gray_image, cmap=plt.cm.gray)
ax[0].set_title('Imagem Original')

ax[1].imshow(binary_image, cmap=plt.cm.gray)
ax[1].set_title('Imagem Binarizada')

for a in ax:
    a.axis('off')

plt.show()
```
2. Plotar o histograma de uma imagem tons de cinza usando Python, scikit-image e matplotlib.






Referências:
1. https://eb.ct.ufrn.br/wp-content/uploads/2019/03/Júlio-Moura.pdf;  
   ChatGpt: Me dê um exemplo de como realizar a limiarização de uma imagem usando Python e scikit-image.
2.
   
   
