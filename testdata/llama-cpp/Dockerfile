FROM ghcr.io/ggerganov/llama.cpp:server--b1-8f1d81a

RUN mkdir /models
RUN curl -L https://huggingface.co/Qwen/Qwen2-0.5B-Instruct-GGUF/resolve/main/qwen2-0_5b-instruct-q4_k_m.gguf?download=true \
  -o /models/qwen2-0_5b-instruct-q4_k_m.gguf