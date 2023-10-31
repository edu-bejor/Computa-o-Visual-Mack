# O que é uma API gráfica? 
As APIs gráficas são uma variante dedicada especificamente à área de imagem e processamento gráfico 3D, fazendo todo o trabalho de comunicação entre os nossos jogos, drivers e a placa de vídeo em si.  

## Vulkan
A linguagem de shading do Vulkan é o SPIR-V, um conjunto de instruções de código de máquina de alto nível que pode ser compilado para vários formatos de GPU. O SPIR-V é um padrão aberto desenvolvido pela Khronos Group, a mesma organização que desenvolve o Vulkan. Ela está documentada no site https://registry.khronos.org/SPIR-V/.  

O pipeline da Vulkan é composto pelos seguintes estágios: 
- Vertex input: Este estágio é responsável por carregar os dados do modelo 3D para a GPU. Os dados do modelo 3D são armazenados em um buffer de vértices.
- Vertex shader: Este estágio é responsável por processar os dados dos vértices do modelo 3D. O vertex shader pode ser usado para transformar os vértices, aplicar transformações geométricas ou aplicar efeitos visuais.
- Tessellation: Este estágio é opcional e pode ser usado para dividir os vértices do modelo 3D em sub-vértices. A tessellation pode ser usada para criar superfícies mais suaves ou para gerar modelos 3D mais detalhados.
- Geometry shader: Este estágio é opcional e pode ser usado para gerar geometria adicional. O geometry shader pode ser usado para criar partículas, efeitos de iluminação ou outros efeitos visuais.
- Rasterization: Este estágio é responsável por rasterizar os vértices do modelo 3D em pixels. A rasterização é o processo de transformar os vértices em pixels que são exibidos na tela.
- Fragment shader: Este estágio é responsável por processar os pixels rasterizados. O fragment shader pode ser usado para aplicar efeitos visuais, como iluminação, sombras ou texturas.
- Color blending: Este estágio é responsável por misturar os pixels renderizados. A mistura de cores é usada para combinar os pixels renderizados de diferentes objetos ou de diferentes partes do mesmo objeto.
- Depth testing: Este estágio é responsável por testar se um pixel está na frente ou atrás de outro pixel. O teste de profundidade é usado para criar a ilusão de profundidade na imagem.
- Stencil testing: Este estágio é opcional e pode ser usado para aplicar efeitos visuais, como máscaras ou efeitos de iluminação.
- Output merger: Este estágio é responsável por combinar os resultados dos estágios anteriores e renderizar a imagem na tela.
  
