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

   Histograma é um gráfico que avalia o brilho de uma imagem representando a frequência de cada tom como um valor em um gráfico de barras. O eixo horizontal começa com uma cor preta pura no lado esquerdo do histograma, passa por sombreados, tons médios e realces, até chegar ao branco mais brilhoso no lado direito. O eixo vertical representa a frequência ou a intensidade de cada tom, com picos de alta frequência e vales nos níveis inferiores

   Implementação:
   ```
   import matplotlib.pyplot as plt
   from skimage import io, color
   
   gray_image = io.imread('img.png', as_gray=True)
   
   hist, bins = plt.histogram(gray_image, bins=256, range=(0, 1)) # Neste exemplo, estamos usando 256 bins para representar o histograma, e a faixa está definida como (0, 1) porque a imagem em tons de cinza é normalmente representada em um intervalo de 0 a 1.
   
   plt.figure(figsize=(8, 5))
   plt.plot(bins[:-1], hist, lw=2)
   plt.title('Histograma da Imagem em Tons de Cinza')
   plt.xlabel('Valor de Intensidade de Pixel')
   plt.ylabel('Frequência')
   plt.xlim(0, 1)
   plt.grid()
   plt.show()

   ```

3. Plotar o histograma de uma imagem colorida (um histograma por canal de cor) usando Python, scikit-image e matplotlib.

   Implementação:
   ```
   import matplotlib.pyplot as plt
   from skimage import io, color
   
   
   img = io.imread('img.jpg')
   
   # Divida a imagem em canais de cor RGB
   red_channel = img[:, :, 0]
   green_channel = img[:, :, 1]
   blue_channel = img[:, :, 2]
   
   # Calcule os histogramas para cada canal de cor
   hist_red, bins_red = plt.histogram(red_channel, bins=256, range=(0, 256))
   hist_green, bins_green = plt.histogram(green_channel, bins=256, range=(0, 256))
   hist_blue, bins_blue = plt.histogram(blue_channel, bins=256, range=(0, 256))
   
   # Plote os histogramas separadamente
   plt.figure(figsize=(12, 6))
   
   plt.subplot(131)
   plt.plot(bins_red[:-1], hist_red, color='red')
   plt.title('Histograma do Canal Vermelho')
   plt.xlabel('Valor de Intensidade de Pixel')
   plt.ylabel('Frequência')
   
   plt.subplot(132)
   plt.plot(bins_green[:-1], hist_green, color='green')
   plt.title('Histograma do Canal Verde')
   plt.xlabel('Valor de Intensidade de Pixel')
   plt.ylabel('Frequência')
   
   plt.subplot(133)
   plt.plot(bins_blue[:-1], hist_blue, color='blue')
   plt.title('Histograma do Canal Azul')
   plt.xlabel('Valor de Intensidade de Pixel')
   plt.ylabel('Frequência')
   
   plt.tight_layout()
   plt.show()

   ```

4. Equalizar o histograma de uma imagem usando Python e scikit-image.
   
   A equalização de histograma é muito utilizada em processamento digital de imagens (PDI), onde é possível ajustar os níveis de cinza de uma imagem automaticamente, garantindo um brilho e contraste balanceados de forma rápida e fácil. A equalização de histograma é uma técnica de transformação de intensidade que tem por objetivo balancear os níveis de cinza em uma imagem de forma automática, sem precisar de parâmetros e configurações adicionais. Dessa forma, imagens com um nível de brilho desbalanceados, ou seja, claras ou escuras demais atingem uma distribuição normalizada, o que garante um melhor contraste e visualização dos detalhes presentes na cena.
   
   Implementação:
   ```
   import numpy as np
   import matplotlib.pyplot as plt 
   from skimage import data
   from PIL import Image
   import math
   
   image = data.coffee()
   plt.imshow(image, cmap='gray')
      
   def convert_to_gray(image, luma=False):
   if luma:
       params = [0.299, 0.589, 0.114]
   else:
       params = [0.2125, 0.7154, 0.0721]    
   gray_image = np.ceil(np.dot(image[...,:3], params))
   
   # Saturando os valores em 255
   gray_image[gray_image > 255] = 255
   
   return gray_image
   
   def instantiate_histogram():    
       hist_array= []
       
       for i in range(0,256):
           hist_array.append(str(i))
           hist_array.append(0)
       
       hist_dct = {hist_array[i]: hist_array[i + 1] for i in range(0, len(hist_array), 2)} 
       
       return hist_dct
   histogram = instantiate_histogram()
   
   def count_intensity_values(hist, img):
       for row in img:
           for column in row:
               hist[str(int(column))] = hist[str(int(column))] + 1
        
       return hist
   histogram = count_intensity_values(histogram, image)
   
   def plot_hist(hist, hist2=''):
       if hist2 != '':
           figure, axarr = plt.subplots(1,2, figsize=(20, 10))
           axarr[0].bar(hist.keys(), hist.values())
           axarr[1].bar(hist2.keys(), hist2.values())
       else:
           plt.bar(hist.keys(), hist.values())
           plt.xlabel("Níveis intensidade")
           ax = plt.gca()
           ax.axes.xaxis.set_ticks([])
           plt.grid(True)
           plt.show()
   ```

5. Detectar (concluir) que uma foto está subexposta ou que está superexposta, analisando o histograma.
   
   Uma imagem subexposta é o tipo de fotografia que pode ser considerada muito escura, já a superexposição é exatamente o oposto do termo definido anteriormente. Uma imagem que é mais brilhante do que deveria ser pode ser considerada com excesso de exposição. Quando muita luz é permitida durante a exposição, o resultado é uma fotografia muito clara. Levando isso em consideração,
   
   Subexposição:
   
- Histograma Deslocado para a Esquerda: Se o histograma da imagem estiver deslocado para a esquerda, isso pode indicar subexposição.
  ![image](https://github.com/edu-bejor/Computacao-Visual-Mack/assets/74507357/99467eb6-7418-422f-a2f5-c5e4867ae69e)


   Superexposição:

- Histograma Deslocado para a Direita: Se o histograma da imagem estiver deslocado para a direita, isso pode indicar superexposição. 
   ![image](https://github.com/edu-bejor/Computacao-Visual-Mack/assets/74507357/2f942848-1a8c-43bb-832e-70d959b85957)

6. Detectar (concluir) se uma imagem está com baixo contraste ou alto contraste, analisando o histograma.

   Uma imagem de baixo contraste retém os detalhes, embora tenda a não ter dimensão e parecer suave, ja uma imagem de alto contraste perde detalhes, especialmente em áreas com tons graduados, e pode parecer um rascunho ou estar posterizada. 

   Alto Contraste:
   
   Histograma: Em uma imagem de alto contraste, o histograma tende a ser mais concentrado em um ou mais picos.
   ![image](https://github.com/edu-bejor/Computacao-Visual-Mack/assets/74507357/ed55f8ef-b9f3-4296-9254-18d9a3118f5d)

   Baixo Contraste:
   
   Histograma: Em uma imagem de baixo contraste, o histograma tende a ser espalhado pelo intervalo de valores de intensidade.
   ![image](https://github.com/edu-bejor/Computacao-Visual-Mack/assets/74507357/eeb57fa2-3d55-4f48-b3b7-37f3078d35ae)


Referências:
1. https://eb.ct.ufrn.br/wp-content/uploads/2019/03/Júlio-Moura.pdf;  
   ChatGpt: Me dê um exemplo de como realizar a limiarização de uma imagem usando Python e scikit-image.

2. https://www.adobe.com/br/creativecloud/photography/discover/how-to-read-a-histogram.html#:~:text=Histograma%20é%20um%20gráfico%20que,mais%20brilhoso%20no%20lado%20direito;  
   ChatGpt: Me dê um exemplo de como plotar o histograma de uma imagem tons de cinza usando Python, scikit-image e matplotlib.

3. ChatGpt: Agora me dê um exemplo de como plotar o histograma de uma imagem colorida (um histograma por canal de cor) usando Python, scikit-image e matplotlib.
   
4. https://medium.com/data-hackers/equalização-de-histograma-em-python-378830368d60

5. https://fotodicasbrasil.com.br/subexposicao-e-superexposicao-um-guia-para-iniciantes/;
   PDF do professor: https://graduacao.mackenzie.br/mod/resource/view.php?id=875301

6. https://helpx.adobe.com/br/lightroom-classic/lightroom-key-concepts/contrast.html#:~:text=Uma%20imagem%20de%20baixo%20contraste,dimensões%2C%20e%20tem%20aspecto%20nítido;
   PDF do professor: https://graduacao.mackenzie.br/mod/resource/view.php?id=875301
