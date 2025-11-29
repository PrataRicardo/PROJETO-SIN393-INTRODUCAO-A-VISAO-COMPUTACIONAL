# PROJETO-SIN393-INTRODUCAO-A-VISAO-COMPUTACIONAL
Classificação de animais com MobileNetV2 utilizando Transfer Learning no dataset Animals-10. Projeto focado em experimentação científica e otimização sob restrições computacionais.

# Classificação de Animais com MobileNetV2 — Transfer Learning em Ambiente com Recursos Limitados

Este repositório apresenta um estudo aplicado de classificação de imagens utilizando a arquitetura **MobileNetV2** como extratora de características, combinada com **Transfer Learning** e técnicas de pré-processamento otimizadas para ambientes computacionalmente restritos. O projeto faz parte das atividades da disciplina *Introdução à Visão Computacional (SIN393)* da Universidade Federal de Viçosa – Campus Rio Paranaíba.

---

## Objetivos do Projeto

- Avaliar a eficiência da MobileNetV2 para classificação de imagens do dataset **Animals-10**.
- Analisar o comportamento do modelo em um **ambiente com restrições computacionais**, especificamente o Google Colab Free Tier.
- Investigar o impacto do número de épocas e do tamanho do batch no desempenho.
- Explorar limitações reais de memória e processamento e ajustar o pipeline para manter estabilidade.
- Produzir um conjunto de resultados visuais:  
  - curvas de loss e accuracy  
  - matriz de confusão  
  - relatório de classificação  
- Fornecer uma análise crítica dos limites do modelo e possíveis caminhos para trabalhos futuros.

---

## Metodologia Resumida

O pipeline foi projetado para funcionar sem sobrecarregar a memória RAM, usando:

- **ImageDataGenerator** apenas como ferramenta de streaming, não de Data Augmentation.
- **Batch size pequeno (16)** para evitar encerramento do kernel.
- **MobileNetV2 congelada (feature extraction)**.
- Treinamentos em **5 e 10 épocas** para analisar convergência e saturação.
- Salvamento automático do melhor modelo via callbacks.

Com isso, o modelo alcançou **acurácia de validação > 96% logo nas primeiras épocas**, mesmo em ambiente limitado.

---

## Tecnologias e Ferramentas Utilizadas

- **Python 3.10+**
- **TensorFlow / Keras**
- **NumPy**
- **Matplotlib & Seaborn**
- **Scikit-learn**
- **Google Colab (GPU T4)**
- **MobileNetV2 pré-treinada na ImageNet**

---

## Resultados Obtidos

### Curvas de treinamento  
- Rápida convergência acima de **96% de accuracy** já na primeira época.
- Saturação observada após poucas épocas.
- Aumentos esporádicos na loss de validação, típicos de pipelines sem cache e com streaming.

### Matriz de Confusão  
Mostra que a rede é consistente entre as classes, ainda que algumas apresentem maior variação devido à diversidade do Animals-10.

### Relatório de Classificação  
Inclui:  
- precisão  
- recall  
- f1-score  
- suporte por classe  

Comportamento equilibrado entre categorias, reforçando a qualidade da MobileNetV2 como extratora de características.

---

## Trabalhos Futuros

Aplicar fine-tuning parcial nas camadas superiores da MobileNetV2.

Implementar data augmentation controlado para aumentar a robustez.

Comparar desempenho com arquiteturas modernas como EfficientNet-B0, NASNet-Mobile e ResNet50.

Testar quantização e exportação para TensorFlow Lite visando uso em dispositivos embarcados.

Criar API de inferência com FastAPI e demo web interativa.

---
## Apresentação
Link: https://youtu.be/Tk5p4OYrATY

## Autor
Ricardo Prata
Universidade Federal de Viçosa – CRP
Discente de Sistemas de Informação
Email: ricardo.j.filho@ufv.br
Orientação: Prof. João Fernando Mari
