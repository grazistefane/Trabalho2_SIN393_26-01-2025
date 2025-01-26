# Projeto de Classificação de Imagens com Redes Neurais Convolucionais

Este projeto foi desenvolvido com o objetivo de realizar a classificação de imagens utilizando redes neurais convolucionais pré-treinadas, como VGG16 e ResNet18. O dataset utilizado contém imagens de ressonâncias magnéticas cerebrais e foi adaptado para este trabalho.

## Implementação Inicial e Problemas Enfrentados

Inicialmente, foi implementado um código mais completo com configurações de hiperparâmetros e estratégias avançadas, como grid search para otimização e validação cruzada. No entanto, esse código enfrentou dois problemas principais ao ser executado no Google Colab:

1. **Problemas de Memória:** O uso de um tamanho de batch maior gerou um consumo elevado de memória, resultando em falhas durante a execução.
2. **Tempo de GPU:** Após a redução do tamanho do batch para solucionar o problema de memória, o tempo de GPU disponível no Colab foi excedido antes da conclusão da execução.

Devido a essas limitações, foi necessário simplificar o código para garantir a viabilidade de execução dentro do ambiente de desenvolvimento disponível. A versão final utilizada no projeto mantém a funcionalidade essencial para a classificação, mas sem a implementação de hiperparâmetros otimizados via grid search ou validação cruzada.

---

## Pré Requisitos

- Dataset Utilizado: https://www.kaggle.com/datasets/rm1000/brain-tumor-mri-scans?select=glioma
- Python 3.8 ou superior
- Bibliotecas: `torch`, `torchvision`, `numpy`, `sklearn`, `matplotlib`, `seaborn`, `Pillow`

## Execução do Projeto

1. Monte o Google Drive no Colab para acessar o dataset:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```

2. Defina o caminho para o dataset:
   ```python
   dataset_path = '/content/drive/MyDrive/trabalho_visao/BrainTumor_MRI_Scans'
   ```

3. Execute o script simplificado para realizar a classificação de imagens.

## Estrutura do Código

### 1. **Importação de Bibliotecas**
O código utiliza bibliotecas amplamente conhecidas, como:
- `PyTorch` e `torchvision`: Construção, treinamento e avaliação de modelos de aprendizado profundo.
- `scikit-learn`: Métricas e ferramentas de avaliação.
- `Matplotlib` e `Seaborn`: Visualização de resultados.
- `PIL`: Manipulação de imagens.
- `Google Colab Drive`: Integração para acessar datasets armazenados no Google Drive.

### 2. **Transformações de Imagem**
As imagens do dataset são redimensionadas e transformadas para se adequar aos modelos pré-treinados. As transformações incluem:
- Redimensionamento para 224x224.
- Flip horizontal e rotação aleatória para aumentar a robustez do modelo.
- Normalização com valores padrão do ImageNet.

### 3. **Carregamento do Dataset**
O dataset é carregado a partir do caminho especificado na variável `dataset_path`, com as classes organizadas em subpastas. As amostras de cada classe são exibidas graficamente para verificação.

### 4. **Divisão do Dataset**
Os dados são divididos em:
- Treinamento (70%)
- Validação (15%)
- Teste (15%)
Os splits são feitos de forma aleatória com uma semente fixa para reprodutibilidade.

### 5. **Modelos Utilizados**
Os modelos VGG16 e ResNet18 são carregados com pesos pré-treinados no ImageNet, e suas últimas camadas são ajustadas para corresponder ao número de classes do dataset.

### 6. **Treinamento**
Cada modelo é treinado usando:
- Função de perda: CrossEntropyLoss.
- Otimizador: Adam com taxa de aprendizado de 0.001.
O treinamento utiliza validação cruzada com 5 folds para avaliar a consistência do desempenho.

### 7. **Avaliação**
As etapas de avaliação incluem:
- **Matriz de Confusão**: Visualização gráfica das predições.
- **Relatório de Classificação**: Métricas como precisão, recall e F1-score.
- **Validação Cruzada**: Resultados para cada fold do treinamento.

---

## Resultados
O script exibe:
- Matrizes de confusão para cada fold.
- Métricas detalhadas de desempenho para cada modelo.
- Comparação do desempenho entre modelos.
---

## Como Usar

1. Configure o caminho do dataset:
   Altere a variável `dataset_path` para o caminho do dataset de ressonância magnética.
   O dataset deve estar estruturado com subpastas representando as classes.

2. Execute o script:
   ```bash
   python script.py
   ```

3. Visualize os resultados:
   Os gráficos e relatórios são exibidos diretamente no terminal ou notebook.

---

## Notas
- O treinamento foi acelerado ao usar uma GPU, que foi fornecida pelo Google Colab.
- Certifique-se de que as classes no dataset estejam equilibradas para melhores resultados.
- O número de epochs foi adaptado e o tamanho do batch também, conforme o tamanho do dataset.

## Integrantes do projeto:
- João Matheus Rosano Rocha - 6031. email: joao.rosano@ufv.br
- Grazielle Stefane Cruz - 7021. email: grazielle.cruz@ufv.br


---
