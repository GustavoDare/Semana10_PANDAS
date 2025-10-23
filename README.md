# Classificação de Imagens com CNN – Fashion MNIST

## Descrição do Projeto
Este projeto tem como objetivo comparar o desempenho de duas arquiteturas de Redes Neurais Convolucionais (CNNs) aplicadas à classificação de imagens do dataset Fashion-MNIST.
O conjunto de dados contém 70.000 imagens em tons de cinza (28×28 pixels), divididas entre 10 classes de roupas e acessórios (como camisetas, calçados e bolsas).
Foi utilizado o dataset do kaggle "Fashion MNIST", retirado do link: https://www.kaggle.com/datasets/zalando-research/fashionmnist

## Etapas do Projeto

### Carregamento dos dados:
Os arquivos fashion-mnist_train.csv e fashion-mnist_test.csv foram lidos via Pandas.
A primeira coluna representa o rótulo da classe, e as demais contêm os 784 pixels da imagem.

### Pré-processamento:
Normalização dos valores de pixels para o intervalo [0, 1];
Redimensionamento das imagens para (28, 28, 1);
Separação entre treino, validação e teste.

### Modelos testados:
#### Modelo 1 – CNN Simples
- 2 camadas convolucionais (32 e 64 filtros)
- 2 camadas de pooling
- 1 camada densa com 128 neurônios
- Função de ativação ReLU, saída Softmax
- Otimizador Adam
- Acurácia de teste: 90.75%

#### Modelo 2 – CNN Profunda com Dropout
- 3 camadas convolucionais (32, 64 e 128 filtros)
- Dropout após cada bloco convolucional (0.25)
- Camada densa com 256 neurônios e Dropout (0.5)
- Otimizador Adam
- Acurácia de teste: 92.74%

### Treinamento:
Ambos os modelos foram treinados por 10 épocas com batch size = 128, usando 10% dos dados para validação.

### Resultados
Modelo	Estrutura	Épocas	Acurácia (teste)
- CNN Simples	2 conv + 1 densa	10	0.9075
- CNN Profunda	3 conv + dropout	10	0.9274
A CNN mais profunda apresentou melhor desempenho geral, evidenciando que o aumento da profundidade e o uso de dropout ajudaram a reduzir o overfitting e a melhorar a capacidade de generalização.

### Visualização dos Treinamentos
CNN Simples
<Figure size 1200x500 with 2 Axes><img width="1010" height="472" alt="image" src="https://github.com/user-attachments/assets/28e3cb31-5248-432a-bec5-5132b973767d" />

CNN Profunda
<Figure size 1200x500 with 2 Axes><img width="1010" height="471" alt="image" src="https://github.com/user-attachments/assets/493595bd-574a-4cc1-860e-c3632996c468" />


### Conclusão
O experimento confirma que CNNs são altamente eficazes para classificação de imagens.
Mesmo um modelo relativamente simples já alcança mais de 90% de acurácia, enquanto uma rede mais profunda e regularizada pode ultrapassar 92%.
