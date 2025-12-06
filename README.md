
🧠 Detecção de Imagens Sintéticas com Vision Transformer (ViT) + Edge-Based Processing (EBP)

Este projeto implementa uma pipeline completa de detecção de imagens sintéticas geradas por modelos de difusão (Stable Diffusion) utilizando duas abordagens complementares:

- Fine-tuning de um Vision Transformer (ViT-Base-Patch16-224-In21k)
- Módulo estrutural Edge-Based Processing (EBP) para análise de bordas e texturas artificiais

O objetivo é avaliar a capacidade do ViT e do EBP em discriminar imagens reais e geradas por IA, exclusivamente dentro do escopo do dataset CIFAKE, que contém imagens sintéticas produzidas por Stable Diffusion e fotografias reais.

O foco central do projeto é atingir alta precisão estatística nas métricas tradicionais (Accuracy, Precision, Recall, F1-score) por meio de fine-tuning cuidadoso, otimizações para GPU T4, e métodos híbridos de pós-processamento.

**Autor**

- **Nome:** Jeová Anderson
- **GitHub:** `geovatatsuga`
- **Resumo:** Graduando em Ciência de Dados e IA
- **Instituição:** UEPB (Universidade Estadual da Paraíba)
- **Localização:** João Pessoa, Paraíba, Brasil
- **E-mail:** `jeova.herminio@gmail.com`
- **LinkedIn:** `in/jeova-anderson`
- **Lattes:** https://lattes.cnpq.br/6417832925129744
- **Medium:** https://medium.com/@jeova.anderson

**Repositório**

Nome local do repositório: `detector-hibrido-vit-ebp-de-imagens-sinteticas`

Para criar o repositório no GitHub e enviar (push) este código, siga as instruções na seção "Publicar no GitHub" abaixo.

**Publicar no GitHub (com `gh` — GitHub CLI)**

1. Autentique o `gh` (caso ainda não tenha):

```powershell
gh auth login
```

2. Crie o repositório remoto a partir da pasta do projeto:

```powershell
cd "c:\Users\jeova\detector-hibrido-vit-ebp-de-imagens-sinteticas"
git init
git add .
git commit -m "Initial commit"
gh repo create geovatatsuga/detector-hibrido-vit-ebp-de-imagens-sinteticas --public --source=. --remote=origin --push
```

Isso criará o repositório no GitHub sob a sua conta (`geovatatsuga`), adicionará o remoto `origin` e enviará o código.

Se preferir criar o repositório manualmente via interface web, crie-o com o mesmo nome e depois execute:

```powershell
git remote add origin https://github.com/geovatatsuga/detector-hibrido-vit-ebp-de-imagens-sinteticas.git
git branch -M main
git push -u origin main
```

Se quiser, eu posso preparar também um `.gitignore` e uma licença (por exemplo, `MIT`). Diga qual licença prefere.
