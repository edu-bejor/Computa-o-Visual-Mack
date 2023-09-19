## Uso do filtro 'blur' para esconder o rosto de pessoas no Google Street View.

O Google Street View é um serviço distribuído pela Google que permite que o usuário visualize ruas de vários locais do mundo através do escaneamento do ambiente através de fotos. Um carro da empresa com câmeras modificadas ao trafegar por um local, tira diversas fotos (8 para cada 'pedaço' da rua, além de uma com uma câmera do tipo fish-eye) que são combinadas de forma a representarem uma foto panorâmica.

Um dos problemas principais da tecnologia é a garantia da privacidade dos transeuntes, bem como informações confidenciais tais como as placas dos carros nas fotos. 
![image](https://github.com/edu-bejor/Computacao-Visual-Mack/assets/16262291/a6b58a6a-5af8-4754-a760-566858a76ad7)

Por isso, pesquisadores da empresa criaram um sistema que permite identificar e aplicar um filtro de blur nas faces das pessoas em cada foto. O paper "Large-scale Privacy Protection in Google Street View" mostra como o sistema de detecção de faces do Google Street View funciona. 

![image](https://github.com/edu-bejor/Computacao-Visual-Mack/assets/16262291/5d154fe9-3dcc-4857-8246-6acecf4834ab)

Usando dois detectores de face que capturam parâmetros e criam bounding boxes, uma rede neural convolucional (CNN) analisa essas boxes na imagem a qual retorna em seu output se tal caixa deve ser filtrada ou não. Ao filtrar, é utilizada uma métrica de quanto o filtro deve suavisar o rosto, a fim de não comprometer a qualidade da imagem (como explicado na seção 3.3, Face results, pelo nome de "hand-counted per-box recall").
A técnica então pode ser extendida para detecção de placas de carro, nomes de comércios, etc.  

O documento com os detalhes pode ser encontrado em: https://static.googleusercontent.com/media/research.google.com/pt-BR//archive/papers/cbprivacy_iccv09.pdf
