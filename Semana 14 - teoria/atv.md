# Toon shading, Gouraud e Phong shading

O toon shading (também conhecido como cel shading) e as técnicas de shading como Gouraud e Phong são abordagens distintas para renderizar gráficos 3D, cada uma com suas próprias características e propósitos. Aqui estão algumas semelhanças e diferenças entre o toon shading e o Gouraud/Phong shading:  

## Semelhanças  
- Objetivo de Sombreamento: Ambas as abordagens visam melhorar a aparência visual de objetos 3D em gráficos de computador, proporcionando uma representação mais realista da iluminação e sombreamento.
- Utilização em Gráficos 3D: Tanto o toon shading quanto as técnicas Gouraud e Phong são frequentemente aplicados em ambientes tridimensionais para criar uma sensação de profundidade e realismo.

## Diferenças  

- Toon Shading: O toon shading produz uma aparência mais estilizada e não-realista. Ele simplifica a gama de tons de cor em áreas uniformes, criando uma aparência de desenho animado ou de banda desenhada
- Gouraud e Phong Shading: Ambos Gouraud e Phong shading visam uma representação mais suave e realista, focando na variação contínua de tons e cores para criar transições mais naturais entre áreas iluminadas e sombreadas. No entanto, existem diferenças entre os dois:
  - Gouraud Shading: Calcula a iluminação nas vértices e interpola os resultados para os pontos internos do triângulo. Boa para superfícies planas ou com transições suaves de cor.
  - Phong Shading: Calcula a iluminação em cada ponto individual na superfície do objeto, capturando detalhes finos e sendo eficaz em superfícies curvas. Pode ser mais custoso computacionalmente.

## Representações  

![WhatsApp Image 2023-11-17 at 19 01 58_e7085a11](https://github.com/edu-bejor/Computacao-Visual-Mack/assets/74507357/717cd3f7-0ed6-46b1-a0bd-8b972e5f401d)  
No Toon Shading, como pode ser visto acima, a imagem fica com um aspecto de "cartoon".    

  
![WhatsApp Image 2023-11-17 at 19 03 41_a2d33a51](https://github.com/edu-bejor/Computacao-Visual-Mack/assets/74507357/cc110bce-e934-4e30-b954-88a326929711)  
Nessa imagem podemos ver os dois algoritmos, Gouraud Shading (direita), Phong (esquerda).  



# Referências  

https://www.shadertoy.com/view/4dVXWh  
https://www.shadertoy.com/view/ll33Wn  
https://docs.unity3d.com/Packages/com.unity.toonshader@0.6/manual/index.html  
ChatGPT: Diferença clara entra Gouraud e Phong (pois estavamos achando apenas citando os dois juntos)





