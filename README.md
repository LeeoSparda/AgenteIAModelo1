# AgenteIAModelo1
📘 README – Execução de Chat Local e API com Modelos Hugging Face

Este projeto contém um script completo (main.py) capaz de:

Instalar automaticamente todas as dependências necessárias

Detectar e configurar GPU com PyTorch CUDA 12.1

Carregar e executar um chat local com modelos Hugging Face

Alternativamente, executar um chat consumindo a API da Hugging Face

Suportar múltiplos modelos (texto, OCR, document-QA, visão, etc.) dependendo do pipeline ativado

Este manual explica tudo o que precisa ser feito antes de rodar a aplicação, incluindo instalação, configuração e execução.

🧩 1. Requisitos do Sistema
✔ Python

Python 3.9 ou superior

✔ Hardware (opcional, mas recomendado)

GPU NVIDIA com CUDA 12.1 para acelerar modelos modernos

Se não tiver GPU, o script funciona em CPU, apenas mais lento

✔ Sistemas compatíveis

Windows 10/11

Linux (altamente recomendado)

macOS (funciona apenas em CPU)

📁 2. Estrutura Recomendada do Projeto
/seu-projeto
│
├── main.py               → script principal (chat local + API)
└── README.md             → este manual

🧪 3. Criar Ambiente Virtual
Windows
python -m venv venv
venv\Scripts\activate

Linux / macOS
python3 -m venv venv
source venv/bin/activate

📦 4. Instalar Dependências (o script já instala sozinho)

O script instala automaticamente:

torch

transformers

accelerate

sentencepiece

requests

Mas, caso queira instalar manualmente:

pip install torch transformers accelerate sentencepiece requests

🔥 Instalar PyTorch com CUDA 12.1 (para RTX 4060, 4070 etc.)

Se quiser instalar manualmente:

pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121


O próprio script também realiza esta operação caso detecte erro no PyTorch.

🔑 5. Token Hugging Face

O script utiliza um token configurado diretamente:

get_token = "hf_xxxxxxxx"
os.environ["HF_TOKEN"] = get_token


Para utilizar seu próprio token:

Crie um token em:
https://huggingface.co/settings/tokens

Substitua a variável get_token.

🤖 6. Escolher o Modelo para Carregar

O script possui várias opções de modelos já configuradas.
Basta descomentar o modelo desejado.

Exemplos:

Modelo de texto (Phi-3-mini)
model_name = "microsoft/Phi-3-mini-4k-instruct"

OCR (Trocr)
model_name = "microsoft/trocr-base-stage1"

Document-QA (LayoutLMv3)
model_name = "microsoft/layoutlmv3-base"

Visão multimodal (SmolVLM)
model_name = "HuggingFaceM4/smolvlm-instruct"


Após escolher, o pipeline é configurado automaticamente.

💬 7. Chat Local – Modo Offline

Para iniciar o chat local:

python main.py


O script irá:

Instalar dependências

Detectar GPU

Baixar o modelo

Criar o pipeline

Abrir o chat no terminal

Uso

Digite mensagens:

Você: Olá!
Assistente: Olá! Como posso ajudar?


Para sair:

fim

🌐 8. Alternativa: Chat via API Hugging Face

Após o chat local, o script inicia o modo API, usando:

https://api-inference.huggingface.co/models/microsoft/Phi-3-mini-4k-instruct

Como funciona

O script envia requisições para a API oficial da HF:

response = requests.post(API_URL, headers=headers, json=payload)


E exibe a resposta no terminal.

Uso
Você: Explique o que é machine learning
Assistente: ...


Para sair:

fim

⚠️ 9. Possíveis Problemas e Soluções
❌ GPU não detectada

Verifique drivers NVIDIA

Verifique versão CUDA

Tente reinstalar PyTorch com CUDA 12.1

❌ “CUDA error: ...”

Instalar PyTorch compatível com sua GPU:

pip install torch --index-url https://download.pytorch.org/whl/cu121

❌ Token inválido

Certifique-se de que:

O token é do tipo read

Está ativo

Está corretamente configurado no script

❌ Modelo muito grande para GPU

Escolha modelos menores:

microsoft/Phi-3-mini-4k-instruct

Qwen/Qwen2.5-0.5B

google/gemma-2b

📄 10. Licença

Recomenda-se utilizar MIT License, mas pode ajustar conforme necessidade.
