# Análise Avançada de Imagens e Texto com IA na AWS (Amazon Textract) 🚀

Repositório criado para o desafio de projeto da **Refatorando com IA da DIO (Digital Innovation One)**, focado em explorar o potencial do Amazon Textract para extração inteligente de dados utilizando a linguagem Python.

## 📋 Descrição do Projeto
Este projeto demonstra como utilizar o **Amazon Textract**, um serviço de aprendizado de máquina da AWS que vai muito além de um OCR tradicional. Através do SDK oficial da AWS para Python (`boto3`), conseguimos programar uma aplicação capaz de identificar, ler e extrair textos de documentos digitalizados sem configurações manuais.

## 🛠️ Tecnologias Utilizadas
* **Python 3** (Linguagem de programação)
* **Boto3** (SDK oficial da AWS para Python)
* **Amazon Textract API** (Serviço de IA)
* **Git & GitHub** (Para controle de versão e portfólio)

## 🐍 Implementação do Código em Python

Abaixo está o script estruturado para carregar um documento local e enviar para a API do Amazon Textract realizar a extração do texto:

```python
import boto3

def extrair_texto_documento(caminho_imagem):
    # Inicializa o cliente do Textract usando as credenciais da AWS configuradas
    textract_client = boto3.client('textract', region_name='us-east-1')

    # Abre o arquivo de imagem do documento local em modo binário
    with open(caminho_imagem, 'rb') as documento:
        bytes_imagem = documento.read()

    try:
        # Chama a API do Amazon Textract para detectar o texto
        response = textract_client.detect_document_text(
            Document={
                'Bytes': bytes_imagem
            }
        )

        print("\n--- Texto Extraído com Sucesso pelo Textract ---")
        # Varre os blocos detectados pela Inteligência Artificial
        for block in response['Blocks']:
            if block['BlockType'] == 'LINE':
                print(block['Text'])
                
    except Exception as e:
        print(f"Erro ao processar o documento: {e}")

# Execução do script passando o arquivo de exemplo
if __name__ == "__main__":
    # Substitua pelo caminho do seu documento (ex: nota_fiscal.png, contrato.jpg)
    caminho_do_arquivo = "documento_exemplo.jpg"
    extrair_texto_documento(caminho_do_arquivo)
```

## 🧠 Insights e Aprendizados
1. **Automação com Python:** O uso do `boto3` permite integrar a IA da AWS em qualquer sistema local ou API em poucas linhas de código.
2. **Diferença de Blocos:** O Textract separa o resultado em blocos estruturados (`PAGE`, `LINE`, `WORD`), permitindo que o desenvolvedor filtre exatamente o nível de detalhe que precisa.
3. **Casos de Uso Reais:** Automatizar a leitura de milhares de notas fiscais, relatórios médicos ou contratos em lotes, gerando economia de tempo no ambiente corporativo.

## 📸 Demonstração do Serviço na AWS

Abaixo estão os registros do Amazon Textract analisando os documentos:

### 1. Extração de Texto Puro (Raw Text)
O serviço mapeia e digitaliza cada linha de texto com precisão cirúrgica.
![Extração de Texto Puro](https://githubusercontent.com)

### 2. Reconhecimento de Tabelas e Formulários (Key-Value Pairs)
A IA identifica a estrutura de tabelas complexas, separando os dados por colunas e linhas automaticamente.
![Mapeamento de Tabelas](https://githubusercontent.com)

---
⭐ Desenvolvido por um Embaixador DIO! Compartilhando conhecimento de Monteiro-PB para o mundo.
