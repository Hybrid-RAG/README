# Hybrid RAG Dashboard para Legislacion Aduanera

Este proyecto del curso de **IA Generativa** de la maestria en Ciencia de Datos de la UNI, implementa un sistema Hybrid RAG sobre legislacion aduanera SUNAT.

Nuestra solucion esta separada en dos repositorios locales:

- `rag_pipeline/`: backend, indexacion, retrieval, reranker, grounding y evaluacion
- `rag_dashboard/`: dashboard Gradio para consulta interactiva y comparacion de corridas

## Objetivos

- Sistema RAG robusto
- Retrieval híbrido
- Minimizar alucinaciones
- Evaluación con métricas

## Arquitectura

![Arquitectura ejecutiva](architecture/project_architecture_executive.svg)

## Que cubre el proyecto

- dataset externo real del dominio
- chunking con overlap
- FAISS HNSW
- retrieval hibrido `BM25 + FAISS`
- reranker cross-encoder
- citation per sentence
- grounding score y hallucination guard
- evaluacion `BLEU / ROUGE + grounding`
- dashboard interactivo con `Ask` y `Evaluation`

## Estructura del workspace

- `rag_pipeline/`
  - construccion del corpus, indexacion, backend RAG y evaluacion
- `rag_dashboard/`
  - interfaz Gradio conectada localmente al backend

## Ejecucion rapida

### 1. Instalar el dashboard y el backend local

Desde `rag_dashboard/`:

```bash
python -m venv venv
venv\Scripts\activate
pip install --upgrade pip setuptools wheel
pip install -r requirements.txt
pip install -e ../rag_pipeline
```

### 2. Configurar credenciales

Crear `rag_pipeline/.env` con al menos:

```env
HF_TOKEN=tu_token_de_hugging_face
```

### 3. Ejecutar el dashboard

Desde `rag_dashboard/`:

```bash
python app.py
```

## Demo

Este README deja preparada la seccion de demo.

Opciones recomendadas:

1. insertar un GIF corto del flujo `Ask`
2. agregar una captura del dashboard con enlace a un video
3. enlazar un video externo si el archivo es muy pesado

Contenido del demo:

- pregunta en `Ask`
- respuesta con evidencias y citas
- inspeccion de `Estado`, `Evidencias`, `Citas` y `Debug`
- comparacion en `Evaluation`

## Repos principales

### Backend

- [hybrid-rag-pipeline/README.md](https://github.com/Hybrid-RAG/hybrid-rag-pipeline/blob/main/README.md)
- [hybrid-rag-pipeline/TRADEOFFS.md](https://github.com/Hybrid-RAG/hybrid-rag-pipeline/blob/main/TRADEOFFS.md)

### Dashboard

- [hybrid-rag-dashboard/README.md](https://github.com/Hybrid-RAG/hybrid-rag-dashboard/blob/main/README.md)

## Flujo funcional del sistema

1. Ingesta y descarga del corpus legal SUNAT
2. Parsing por pagina y chunking con overlap
3. Construccion de embeddings e indices `FAISS HNSW + BM25`
4. Retrieval hibrido
5. Reranker cross-encoder
6. Generacion con LLM
7. Citation per sentence
8. Grounding y guard
9. Visualizacion en `Ask`
10. Comparacion e historial en `Evaluation`

## Integrantes

- Amalia Anahi Anto Alzamora
- Jaime Canchari Gutierrez
- Leticia Verano Custodio
