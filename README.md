# 🎧 Spark — Sistema de Recomendação de Músicas

Recomendador de músicas em **PySpark** usando **PCA** (redução de dimensionalidade) e **K-Means** (clusterização).  
Dado o nome de uma música, o sistema encontra faixas **parecidas** pelos *audio features* (danceability, energy, tempo, etc.), exibe as **capas dos álbuns em mosaico** e retorna os **links do Spotify**.

> Feito para rodar em notebook (Jupyter/Colab) ou localmente com Spark.

---

## 🌟 Destaques

- 🔎 Busca robusta por música de referência  
- 🧠 Pipeline Spark: `VectorAssembler → StandardScaler → PCA → KMeans`  
- 📏 Similaridade via **distância euclidiana** no espaço PCA (priorizando o mesmo cluster)  
- 🖼️ Mosaico limpo das capas (sem eixos/grades) com **nome abaixo** da imagem  
- 🔗 Integração com **Spotify Web API** para capas e URLs

---

## 📦 Requisitos

- **Python 3.10+**
- **Apache Spark** (ou Google Colab com `pyspark`)
- Credenciais Spotify (crie um app em https://developer.spotify.com/dashboard)

Pacotes:
```bash
pip install pyspark spotipy scipy scikit-image matplotlib python-dotenv
```

## 🧠 Como o modelo funciona (visão rápida)
```
flowchart LR
    A[Dados de músicas<>id, artists, name, features] --> B[VectorAssembler<>features]
    B --> C[StandardScaler<>scaled_features]
    C --> D[PCA(k)<>pca_features]
    D --> E[KMeans(k)<>cluster_pca]
    E --> F[projection_kmeans<>id, artists_song, pca_features, cluster_pca]
    F --> G[Consulta música alvo]
    G --> H[Distância Euclidiana<>mesmo cluster]
    H --> I[Top-N similares<>capas + links Spotify]
```






