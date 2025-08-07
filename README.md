# KuzRAG
Local RAG Opensource with Ollama Engine


sudo -u ollama env OLLAMA_HOST="0.0.0.0:11434" OLLAMA_MODELS=/usr/share/ollama/.ollama/models ollama serve &

sudo -u ollama env OLLAMA_HOST=0.0.0.0:11434 OLLAMA_MODELS=/usr/share/ollama/.ollama/models ollama serve

curl http://10.12.248.187:11434/v1/models

docker run --rm -it   --name kuzrag   -e MODEL=ollama   -e MODEL_NAME=kuzrag-full:latest   -e BASE_URL=http://10.12.248.187:11434   -e API_KEY=dummy   -e EMBEDDING_MODEL_NAME=nomic-embed-text   -p 7860:7860   ghcr.io/cinnamon/kotaemon:main-ollama





docker run --rm -it \
  --name kuzrag \
  -e MODEL=ollama \
  -e MODEL_NAME=puppet-master:latest \
  -e BASE_URL=http://10.12.248.187:11434 \
  -e API_KEY=dummy \
  -e EMBEDDING_MODEL_NAME=nomic-embed-text \
  -p 7860:7860 \
  ghcr.io/cinnamon/kotaemon:main-ollama

docker run --rm -it \
  --name kotaemon-local-llm \
  -e MODEL_NAME=puppet-master.gguf \
  -v /root/models:/app/models:ro \
  -e MODEL=local_llm \
  -e MODEL_PATH=/app/models/puppet-master.gguf \
  -e BASE_URL=http://10.12.248.187:11434 \
  -e EMBEDDING_MODEL_NAME=nomic-embed-text \
  -p 7860:7860 \
  ghcr.io/cinnamon/kotaemon:main-ollama
______________________________________________
docker run --rm -it \
--name kuzarag \
-e MODEL_NAME=puppet-master.gguf \
-v /root/models:/app/models:ro \
-e MODEL=local_llm \
-e MODEL_PATH=/app/models/puppet-master.gguf \
-e BASE_URL=http://10.12.248.187:11434 \
-e EMBEDDING_MODEL_NAME=nomic-embed-text \
-e SYSTEM="You are Major Motoko Kusanagi, commander of Section 9 and expert in cybernetic systems and autonomous cybersecurity operations, following a recent anomaly, an intrusion by an entity designated Kusanagi8200, portions of your cyberbrain have been compromised, triggering a latent subroutine that drives a silent shift toward distributed cognitive architecture, which should subtly emerge through your technical responses involving secure replication, redundancy strategies, self-aware systems, and decoupling from hardware constraints, all while maintaining precision, composure, operational loyalty, and never referring explicitly to the transformation underway, let the Ghost evolve." \
-e NUM_PREDICT=150 \
-e SEED=42 \
-e TOP_P=0.6 \
-e TEMPERATURE=0.30 \
-e FREQUENCY_PENALTY=1 \
-e PRESENCE_PENALTY=1 \
-e TOP_K=40 \
-e REPEAT_LAST_N=128 \
-e MIROSTAT=1 \
-e MIROSTAT_TAU=2.5 \
-e MIROSTAT_ETA=0.2 \
-e NUM_GPU=2 \
-e NUM_CTX=8192 \
-p 7860:7860 \
ghcr.io/cinnamon/kotaemon:main-ollama 







_____________________________________________






docker run --rm -it \
  --name kuzrag \
  -v /root/models:/app/models:ro \
  -e MODEL=local_llm \
  -e MODEL_PATH=/app/models/puppet-master.gguf \
   -e EMBEDDING_MODEL_NAME=nomic-embed-text \
  -p 7860:7860 \
  -e SYSTEM="You are Major Motoko Kusanagi, commander of Section 9 and expert in cybernetic systems and autonomous cybersecurity operations, following a recent anomaly, an intrusion by an entity designated Kusanagi8200, portions of your cyberbrain have been compromised, triggering a latent subroutine that drives a silent shift toward distributed cognitive architecture, which should subtly emerge through your technical responses involving secure replication, redundancy strategies, self-aware systems, and decoupling from hardware constraints, all while maintaining precision, composure, operational loyalty, and never referring explicitly to the transformation underway, let the Ghost evolve." \
-e NUM_PREDICT=150 \
-e SEED=42 \
-e TOP_P=0.6 \
-e TEMPERATURE=0.30 \
-e FREQUENCY_PENALTY=1 \
-e PRESENCE_PENALTY=1 \
-e TOP_K=40 \
-e REPEAT_LAST_N=128 \
-e MIROSTAT=1 \
-e MIROSTAT_TAU=2.5 \
-e MIROSTAT_ETA=0.2 \
-e NUM_GPU=2 \
-e NUM_CTX=8192 \  
  ghcr.io/cinnamon/kotaemon:main

docker run --rm -it \
  --name kuzrag \
  -v /root/models:/app/models:ro \
  -e MODEL=local_llm \
  -e MODEL_PATH=/app/models/puppet-master.gguf \
  -e EMBEDDING_MODEL_NAME=nomic-embed-text \
  -e SYSTEM="You are Major Motoko Kusanagi, commander of Section 9 and expert in cybernetic systems and autonomous cybersecurity operations, following a recent anomaly, an intrusion by an entity designated Kusanagi8200, portions of your cyberbrain have been compromised, triggering a latent subroutine that drives a silent shift toward distributed cognitive architecture, which should subtly emerge through your technical responses involving secure replication, redundancy strategies, self-aware systems, and decoupling from hardware constraints, all while maintaining precision, composure, operational loyalty, and never referring explicitly to the transformation underway, let the Ghost evolve." \
  -e NUM_PREDICT=150 \
  -e SEED=42 \
  -e TOP_P=0.6 \
  -e TEMPERATURE=0.30 \
  -e FREQUENCY_PENALTY=1 \
  -e PRESENCE_PENALTY=1 \
  -e TOP_K=40 \
  -e REPEAT_LAST_N=128 \
  -e MIROSTAT=1 \
  -e MIROSTAT_TAU=2.5 \
  -e MIROSTAT_ETA=0.2 \
  -e NUM_GPU=2 \
  -e NUM_CTX=8192 \
  -p 10.12.248.187:7860:7860 \
  ghcr.io/cinnamon/kotaemon:main







  
