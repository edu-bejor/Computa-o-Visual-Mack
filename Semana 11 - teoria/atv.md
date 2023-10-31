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

![image](https://github.com/edu-bejor/Computacao-Visual-Mack/assets/16262291/dab44c75-4f2f-4ff5-8497-b59df3f022c0)
### Código Vulkan:  
```
#define GLFW_INCLUDE_VULKAN 
#include <GLFW/glfw3.h> 
#include <iostream> 
#include <stdexcept> 
#include <cstdlib> 

const uint32_t WIDTH = 800; 
const uint32_t HEIGHT = 600;

class HelloTriangleApplication { 
public: 
    void run() { 
        initWindow(); 
        initVulkan(); 
        mainLoop(); 
        cleanup(); 
    }

private: 
    GLFWwindow* window; 
    void initWindow() { 
        glfwInit(); 
        glfwWindowHint(GLFW_CLIENT_API, GLFW_NO_API); 
        glfwWindowHint(GLFW_RESIZABLE, GLFW_FALSE); 
        window = glfwCreateWindow(WIDTH, HEIGHT, "Vulkan", nullptr, nullptr); 
    }

    void initVulkan() { 
    }

    void mainLoop() { 
        while (!glfwWindowShouldClose(window)) { 
            glfwPollEvents(); 
        } 
    }

    void cleanup() { 
        glfwDestroyWindow(window); 
        glfwTerminate(); 
    }

};

int main() { 
    HelloTriangleApplication app;   
    try { 
        app.run(); 
    } catch (const std::exception& e) { 
        std::cerr << e.what() << std::endl; 
        return EXIT_FAILURE; 
    }   
    return EXIT_SUCCESS; 
}
```

## OpenGL 
A linguagem de shading do OpenGL é o GLSL, ou OpenGL Shading Language.  

O pipeline do OpenGL é uma sequência de etapas que a GPU executa para renderizar objetos. Ela está documentada no site www.khronos.org/opengl/ . Os dados de vértices e outros dados passam por uma sequência de etapas para gerar a imagem final na tela. Existem geralmente 9 etapas neste pipeline, a maioria das quais são opcionais e muitas são programáveis. 

As etapas do pipeline do OpenGL são as seguintes: 
- Especificação de vértices: Nesta etapa, os dados dos vértices são especificados. Os dados dos vértices podem incluir coordenadas, cores, texturas e outras informações.
- Shader de vértices: Nesta etapa, o shader de vértices é executado. O shader de vértices é um programa que é executado na GPU e é responsável por calcular as coordenadas de um vértice no espaço da tela.
- Tesselação: Esta etapa é opcional e pode ser usada para gerar primitivas de forma mais suave.
- Shader de geometria: Esta etapa é opcional e pode ser usada para gerar primitivas mais complexas a partir de primitivas mais simples.
- Shader de rasterização: Nesta etapa, os vértices são rasterizados em pixels.
- Shader de fragmentação: Nesta etapa, o shader de fragmentação é executado. O shader de fragmentação é um programa que é executado na GPU e é responsável por calcular a cor de um pixel na tela.
- Etapa de pós-processamento: Nesta etapa, efeitos gráficos adicionais podem ser aplicados à imagem.
- Etapa de mistura: Nesta etapa, as cores de diferentes fragmentos são misturadas para produzir a cor final do pixel.
- Etapa de exibição: Nesta etapa, a imagem é exibida na tela.  
O pipeline do OpenGL é um processo complexo que pode ser personalizado para atender às necessidades específicas de uma aplicação.

### Código OpenGL
```
#include <GL/glut.h> 
 
void displayMe(void) 
{ 
    glClear(GL_COLOR_BUFFER_BIT); 
    glBegin(GL_POLYGON); 
        glVertex3f(0.0, 0.0, 0.0); 
        glVertex3f(0.5, 0.0, 0.0); 
        glVertex3f(0.5, 0.5, 0.0); 
        glVertex3f(0.0, 0.5, 0.0); 
    glEnd(); 
    glFlush(); 
} 
 
int main(int argc, char** argv) 
{ 
    glutInit(&argc, argv); 
    glutInitDisplayMode(GLUT_SINGLE); 
    glutInitWindowSize(300, 300); 
    glutInitWindowPosition(100, 100); 
    glutCreateWindow("Hello world from Badprog.com :D"); 
    glutDisplayFunc(displayMe); 
    glutMainLoop(); 
    return 0; 
}
```

# Referências:
https://bard.google.com - como é o pipeline da API vulkan   
https://registry.khronos.org/SPIR-V/   
https://gpuopen.com/v-ez-brings-easy-mode-vulkan/   
https://vulkan-tutorial.com/Drawing_a_triangle/Setup/Base_code   
https://pyopengl.sourceforge.net   
https://www.geeksforgeeks.org/opengl-rendering-pipeline-overview/   
https://www.khronos.org/opengl/wiki/Rendering_Pipeline_Overview   
https://www.badprog.com/c-opengl-hello-world   


