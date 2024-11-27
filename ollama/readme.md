# Ollama

## Install ollama
```
curl -fsSL https://ollama.com/install.sh | sh
```

## Download models
Text models
```
ollama pull llama3.2
ollama pull llama3.2:3b
ollama pull llama3.2:1b

ollama pull qwen2.5
ollama pull qwen2.5:1.5b
ollama pull qwen2.5:3b
ollama pull qwen2.5:0.5b

ollama pull mistral-nemo
ollama pull mistral

ollama pull smollm
ollama pull smollm:360m
ollama pull smollm:135m

ollama pull gemma2
ollama pull gemma2:2b
ollama pull gemma2:27b

ollama pull command-r
```

Vison models
```
ollama pull llama3.2-vision
ollama pull llama3.2-vision:90b

ollama pull llava
ollama pull llava:13b
ollama pull llava:34b

ollama pull llava-llama3

ollama pull moondream

ollama pull llava-phi3

ollama pull minicpm-v
```

Coding models
```
ollama pull codellama
ollama pull codellama:13b
ollama pull codellama:34b
ollama pull codellama:70b

ollama pull qwen2.5-coder:3b
ollama pull qwen2.5-coder:7b
ollama pull qwen2.5-coder:32b

ollama pull deepseek-coder-v2

ollama pull dolphin-mixtral:8x7b

ollama run starcoder2
ollama run starcoder2:7b
ollama run starcoder2:15b
```

Embedding models
```
ollama pull nomic-embed-text

ollama pull mxbai-embed-large

ollama pull snowflake-arctic-embed:335m
ollama pull snowflake-arctic-embed:137m
ollama pull snowflake-arctic-embed:110m
ollama pull snowflake-arctic-embed:33m
ollama pull snowflake-arctic-embed:22m
```

Command to pull all models
```
ollama pull llama3.2 && ollama pull llama3.2:3b && ollama pull llama3.2:1b && ollama pull qwen2.5 && ollama pull qwen2.5:1.5b && ollama pull qwen2.5:3b && ollama pull qwen2.5:0.5b && ollama pull mistral-nemo && ollama pull mistral && ollama pull smollm && ollama pull smollm:360m && ollama pull smollm:135m && ollama pull gemma2 && ollama pull gemma2:2b && ollama pull gemma2:27b && ollama pull command-r && ollama pull llama3.2-vision && ollama pull llama3.2-vision:90b && ollama pull llava && ollama pull llava:13b && ollama pull llava:34b && ollama pull llava-llama3 && ollama pull moondream && ollama pull llava-phi3 && ollama pull minicpm-v && ollama pull codellama && ollama pull codellama:13b && ollama pull codellama:34b && ollama pull codellama:70b && ollama pull qwen2.5-coder:3b && ollama pull qwen2.5-coder:7b && ollama pull qwen2.5-coder:32b && ollama pull deepseek-coder-v2 && ollama pull dolphin-mixtral:8x7b && ollama run starcoder2 && ollama run starcoder2:7b && ollama run starcoder2:15b && ollama pull nomic-embed-text && ollama pull mxbai-embed-large && ollama pull snowflake-arctic-embed:335m && ollama pull snowflake-arctic-embed:137m && ollama pull snowflake-arctic-embed:110m && ollama pull snowflake-arctic-embed:33m && ollama pull snowflake-arctic-embed:22m
```
