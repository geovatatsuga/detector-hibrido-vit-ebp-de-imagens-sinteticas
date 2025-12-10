# Detecção Híbrida de Imagens Sintéticas

### Vision Transformer (ViT) + Edge-Based Processing (EBP)

Leia no Medium : **

---

## 📌 Visão Geral

Este projeto implementa uma pipeline completa para detecção de imagens sintéticas geradas por modelos de difusão (Stable Diffusion 1.4).
A abordagem combina dois módulos complementares:

* **Vision Transformer (ViT)** fine-tunado para classificação binária
* **Edge-Based Processing (EBP)** para análise estrutural baseada em bordas


---

## 🎯 Objetivos do Projeto

* Treinar um **Vision Transformer** especializado em detectar imagens sintéticas
* Extrair padrões estruturais usando análise de bordas
* Construir um **modelo híbrido ViT + EBP**
* Avaliar e visualizar as diferenças entre imagens reais e sintéticas

---

## 🚀 Funcionalidades

### 1. Fine-tuning do Vision Transformer

* ViT pre treinado = `vit-base-patch16-224-in21k`
* Otimizações para GPU T4:

  * Mixed Precision (AMP)
  * Gradient Checkpointing
  * Gradient Accumulation
* O ViT pre treinado com o in21k foi finnetunned no dataset CIFAKE para conseguir classificar as imagens.

---

### 2. Edge-Based Processing (EBP)

O EBP analiza propriedades estruturais da imagem para identificar padrões artificiais.


1. Conversão para escala de cinza
2. Aplicação de Gaussian Blur 3×3
3. Extração de bordas com Canny
4. Construção do **Edge Difference Map (D)**
5. Cálcula =:

   * **Nedges**: quantidade de pixels de borda discrepantes
   * **Var(D)**: variância do mapa de diferenças
6. Cálculo do Structural Score (SI):

SI = N_edges / (Var(D) + ε)

Esse score é usado como critério adicional para distinguir imagens reais de sintéticas.

---

### 3. Valley Threshold

* As distribuições de scores SI de imagens reais e falsas são analisadas.
* Um limiar é determinado automaticamente como o ponto de menor densidade entre elas.
* Esse threshold é usado pelo EBP para reclassificar amostras onde o ViT errou.

---

### 4. Sistema Híbrido (ViT + EBP)

O processo final:

1. O ViT prediz REAL ou FAKE
2. Se o ViT acertar → mantemos
3. Se o ViT errar → o EBP recalcula a classe usando SI + threshold


---

## 📊 Resultados 

| Modelo                              | Accuracy   | Precision  | Recall     | F1-Score   |
| ----------------------------------- | ---------- | ---------- | ---------- | ---------- |
| **ViT ImgNet21k (Finetuned) + EBP** | **0.9943** | **0.9947** | **0.9939** | **0.9943** |
| ViT ImgNet21k (Finetuned)           | 0.9889     | 0.9903     | 0.9876     | 0.9889     |
| ViT ImgNet21k (Base) + EBP          | 0.8100     | 0.8095     | 0.8108     | 0.8102     |
| EBP Only                            | 0.5408     | 0.5291     | 0.7408     | 0.6173     |
| ViT ImgNet21k (Base Only)           | 0.4771     | 0.4717     | 0.3818     | 0.4220     |
---

## 🔧 Tecnologias Utilizadas

* Python
* PyTorch
* HuggingFace Transformers
* OpenCV
* NumPy
* Matplotlib / Seaborn
* Google Colab GPU (T4)

---

## 📂 Estrutura do Repositório

```
├── Dados/                    # Dataset CIFAKE ou preprocessado
├── Notebooks/               # Jupyter/Colab Notebooks com pipeline completa
├── Modelos/                  # Checkpoints do ViT e modelo híbrido
└── README.md
```

---

## 🧑‍💻 Autor

**Jeová Anderson**
Graduando em Ciência de Dados e Inteligência Artificial – UEPB

* GitHub: [https://github.com/geovatatsuga](https://github.com/geovatatsuga)
* E-mail: [jeova.herminio@gmail.com](mailto:jeova.herminio@gmail.com)
* LinkedIn: [https://linkedin.com/in/jeova-anderson](https://linkedin.com/in/jeova-anderson)
* Lattes: [https://lattes.cnpq.br/6417832925129744](https://lattes.cnpq.br/6417832925129744)
* Medium: [https://medium.com/@jeova.anderson](https://medium.com/@jeova.anderson)
