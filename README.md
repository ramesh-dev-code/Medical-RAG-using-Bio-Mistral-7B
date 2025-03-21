# Build a Medical RAG App using BioMistral, Qdrant, and Llama.cpp
This is a RAG implementation using Open Source stack. BioMistral 7B has been used to build this app along with PubMedBert as an embedding model, Qdrant as a self hosted Vector DB, and Langchain &amp; Llama CPP as an orchestration frameworks.

## Description & Key Features:
- Build a cutting-edge Medical Retrieval Augmented Generation (RAG) Application using a suite of powerful technologies tailored for the medical domain.
- BioMistral 7B, a new large language model specifically designed for medical applications, offering unparalleled accuracy and insight into complex medical queries.
- Qdrant, a self-hosted vector database that we run inside a Docker container. This robust tool serves as the backbone for managing and retrieving high-dimensional data vectors, such as those generated by our medical language model.
- To enhance our model's understanding of medical texts, I utilize PubMed BERT embeddings, an embeddings model specifically crafted for the medical domain.
- This ensures our application can grasp the nuances of medical literature and queries, providing more precise and relevant answers.
- A crucial component of our setup is Llama.cpp, a library that enables the inference of large language models on CPU machines. This quantized model approach allows for efficient and cost-effective deployment without compromising on performance.
- For orchestrating our application components, I introduce LangChain, an orchestration framework that seamlessly integrates our tools and services, ensuring smooth operation and scalability.
- On the backend, I leverage FastAPI, a modern, fast (high-performance) web framework for building APIs with Python 3.7+. FastAPI provides the speed and ease of use needed to create a responsive and efficient backend for our medical RAG application.
- Finally, for the web UI, I employ Bootstrap 5.3, the latest version of the world’s most popular front-end open-source toolkit. This enables us to create a sleek, intuitive, and mobile-responsive user interface that makes our medical RAG application accessible and easy to use.
- We set up the environment to integrate these technologies into a cohesive and functional medical RAG application.

  
 ## Implementation Expert Guide:
[Demo ▶️](https://www.youtube.com/watch?v=A_m3tCqdts4)

## Implementation on Intel AI PC    
### Disclaimer   
This demo is intended only for the purpose of exploring new LLM use cases at the edge and not recommended for production-grade medical chatbot    

### Device Under Test   
Processor: Intel® Core™ Ultra 7 165H      
OS: Windows 11 Pro 23H2   
RAM: 64GB   
Python 3.11.9   

### Prerequisite   
Install [Microsoft Visual C++](https://code.visualstudio.com/docs/cpp/config-msvc) compiler toolset required for installing llama-cpp-python       

### Steps   
1. Clone this repository
2. Create a Python virtual environment and install the dependencies   
   ```
   python -m venv biomistral_rag   
   biomistral_rag\Scripts\activate   
   python -m pip install pip --upgrade  
   cd Medical-RAG-using-Bio-Mistral-7B-main
   pip install -r requirements.txt   
   pip install qdrant-client --upgrade   
   ```
3. Download the INT4 version of [BioMistral-7B](https://huggingface.co/MaziyarPanahi/BioMistral-7B-GGUF/blob/main/BioMistral-7B.Q4_K_M.gguf) model in GGUF format 
4. Download the embedding model
   ```
   git lfs install
   git clone https://huggingface.co/NeuML/pubmedbert-base-embeddings
   ```
5. Install [Docker Desktop for Windows](https://docs.docker.com/desktop/setup/install/windows-install/) with optional proxy settings    
6. Create the Qdrant container
   ```
   docker pull qdrant/qdrant
   docker run -p 6333:6333 -v .\qdrant_db\:/qdrant/storage qdrant/qdrant
   ```
   ![image](https://github.com/user-attachments/assets/36b17d09-2f61-4645-a336-3458627da6be)   
   Access the Dashboard using http://localhost:6333/dashboard    
7. Create embeddings for the new documents in data
   ```
   python ingest.py
   ```   
   Check the new Collection on the Qdrant Dashboard   
   ![image](https://github.com/user-attachments/assets/13740e55-4e12-4d0f-8267-695d5edeec0a)     
8. Run the application
   ```
   uvicorn app:app   
   ```
   ![image](https://github.com/user-attachments/assets/5ec90875-be78-4bc9-9acf-09859235e313)    
#### Sample Outputs
![image](https://github.com/user-attachments/assets/94282267-ebf0-46eb-b587-996e886e6cb7)   
![image](https://github.com/user-attachments/assets/37aa70b3-1b6d-49b3-a050-d6d5aef882ee)   

 ---
## ©️ License 🪪 

Distributed under the MIT License. See `LICENSE` for more information.

---

#### **If you like this LLM Project do drop ⭐ to this repo**
#### Follow me on [![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gurpreetkaurjethra/) &nbsp; [![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/GURPREETKAURJETHRA/)

---
