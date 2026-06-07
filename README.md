# 🛰️ OrbitalWatch Vision

Projeto desenvolvido para a disciplina **Applied Computer Vision**, dentro da **Global Solution 2026 - FIAP**.

O **OrbitalWatch Vision** é a etapa de Visão Computacional do projeto OrbitalWatch, voltado ao monitoramento ambiental com apoio de dados espaciais. Nesta entrega, o objetivo é classificar imagens de satélite entre áreas com indício de queimada e áreas sem indício de queimada.

---

## 📌 Problema

Identificar indícios de queimadas em imagens de satélite pode ser difícil porque as imagens variam em cor, textura, iluminação, fumaça e características do terreno.

Por isso, o problema foi definido como uma tarefa de classificação de imagens em duas classes:

- `wildfire`: imagem com indício de queimada;
- `no_wildfire`: imagem sem indício de queimada.

Essa classificação adiciona ao OrbitalWatch uma camada visual para apoiar o monitoramento ambiental em um contexto ligado à Indústria Espacial.

---

## 👥 Integrantes

| Nome | RM |
|---|---|
| Caíque Walter Silva | RM550693 |
| Guilherme Nobre Bernardo | RM98604 |
| Guilherme Monteiro Espim | RM99499 |
| João Paulo Fonseca Zamperlini | RM99279 |
| Matheus José de Lima Costa | RM551157 |

---

## 🛰️ Dataset

Foi utilizado um dataset de imagens de satélite relacionado à presença ou ausência de queimadas.

Para manter o projeto leve e compatível com o GitHub, foi usada uma amostra balanceada com:

- 500 imagens da classe `wildfire`;
- 500 imagens da classe `no_wildfire`;
- total de 1.000 imagens.

A estrutura esperada é:

```text
datasets/
├── wildfire/
└── no_wildfire/
```

A divisão dos dados é feita no próprio notebook:

- 70% para treino;
- 15% para validação;
- 15% para teste.

As imagens são carregadas com OpenCV, convertidas para RGB, redimensionadas para `128x128` pixels e normalizadas para a escala de 0 a 1.

---

## 🧠 Modelos treinados

Foram criadas e comparadas duas redes neurais convolucionais treinadas do zero, sem uso de modelos pré-treinados.

| Modelo | Descrição |
|---|---|
| CNN base | Arquitetura com duas camadas convolucionais, usada como referência inicial. |
| CNN maior | Arquitetura com uma camada convolucional adicional e camada densa maior. |

A diferença entre os modelos permite avaliar se uma rede com maior capacidade consegue aprender melhor os padrões visuais relacionados às queimadas.

---

## 📊 Resultados

Os modelos foram avaliados usando acurácia, loss, matriz de confusão e relatório de classificação.

Resultados obtidos no conjunto de teste:

| Modelo | Acurácia no teste |
|---|---|
| CNN base | 95,33% |
| CNN maior | 96,67% |

A **CNN maior** foi escolhida como melhor modelo, pois apresentou maior acurácia no conjunto de teste. O resultado ficou acima da referência mínima de **88%** definida na especificação do projeto.

---

## 🔎 Avaliação qualitativa

Além das métricas numéricas, o notebook apresenta exemplos de imagens do conjunto de teste com a classe real e a classe prevista.

Essa etapa permite observar visualmente os acertos e erros do modelo, complementando a análise feita pela matriz de confusão.

---

## 🚀 Demonstração funcional

A demonstração funcional é feita no próprio notebook, utilizando uma imagem externa chamada:

```text
imagem_teste.jpg
```

A imagem é carregada, redimensionada, normalizada e enviada ao melhor modelo treinado. O notebook retorna a classe prevista e as probabilidades para cada classe.

Também há uma aplicação simples em Streamlit para demonstrar o modelo com upload de imagem.

---

## 📁 Estrutura do projeto

```text
.
├── OrbitalWatch_CV.ipynb
├── modelos_cnn.py
├── requirements.txt
├── README.md
├── imagem_teste.jpg
└── datasets/
    ├── wildfire/
    └── no_wildfire/
```

---

## 📦 Instalação das dependências

Antes de executar o projeto, instale as bibliotecas necessárias usando o arquivo `requirements.txt`.

No terminal, dentro da pasta do projeto, execute:

```bash
pip install -r requirements.txt
```

Caso esteja usando mais de uma versão do Python no computador, pode usar:

```bash
python -m pip install -r requirements.txt
```

O arquivo `requirements.txt` deve conter:

```text
tensorflow
opencv-python
pandas
numpy
matplotlib
scikit-learn
streamlit
pillow
```

---

## ▶️ Como executar o notebook

Abra o arquivo:

```text
OrbitalWatch_CV_Comentado.ipynb
```

Execute as células em ordem.

O notebook realiza:

1. carregamento das imagens;
2. pré-processamento;
3. divisão em treino, validação e teste;
4. treinamento de duas CNNs;
5. comparação dos modelos;
6. matriz de confusão;
7. exemplos de acertos e erros;
8. demonstração com imagem nova;
9. salvamento do melhor modelo.

## ✅ Conclusão

O OrbitalWatch Vision implementa uma solução de Visão Computacional aplicada ao contexto da Indústria Espacial.

A solução classifica imagens de satélite entre `wildfire` e `no_wildfire`, treinando duas CNNs do zero e comparando seus resultados por métricas quantitativas e análise qualitativa.

A CNN mais complexo apresentou o melhor desempenho, com 97,33% de acurácia no conjunto de teste. Com isso, o projeto atende aos requisitos de classificação de imagens, preparação de dataset, treinamento supervisionado, comparação de arquiteturas, avaliação de modelos e demonstração funcional.

---

## 🔗 Links da entrega

- GitHub público: https://github.com/JoaoPauloFZ845/GS1-VisaoComputacional
- Vídeo de apresentação: https://youtu.be/A3OEoCJYwoY
