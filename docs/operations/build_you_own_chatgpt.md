## Ollama

Ollama is a tool used for running LLMs locally. It can be run very easily with just a docker container:

```
# Make a directory for ollama to download models to
mkdir ollama
docker run ollama/ollama:0.10.0-rc3 -p 11434:11434 -v ./ollama:/root/.ollama
```

For context, I am running the `llama3:8b` model on my M2 Mac Mini with 16GB of RAM.

## Open WebUI

[Open WebUI](https://github.com/open-webui/open-webui) is an open-source tool for providing a ChatGPT-like interface which can be used to point at your own locally-run LLMs. Meaning you can point it at your previously deployed ollama model, completing your completely on-premise ChatGPT.

The README for this repo is pretty useful, and provides a way that you can bundle the deployment of Open WebUI along with ollama, but I like to stick to running all my general web services on K8s. There is already a Helm chart built for running Open WebUI.

The chart actually comes with Ollama out of the box however, I will be running Open WebUI on a raspberry pi and point it to my externally running ollama instance.
