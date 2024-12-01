# Dio-Azure-AI

# TRADUTOR DE ARTIGOS TÉCNICOS COM AZURE AI

### Passo a passo para criar um tradutor de artigos técnicos com Azure AI

---

#### **1. Configurar os serviços no Azure**
1. **Criar uma conta no Azure**
   - Acesse [portal.azure.com](https://portal.azure.com).
   - Caso não tenha uma conta, crie uma.

2. **Provisionar o serviço Azure Translator**
   - No portal, procure por "Tradutor" e selecione o serviço.
   - Configure o grupo de recursos, nome do recurso e a região.
   - Após criado, copie a **chave de API** e o **endpoint**.

---

#### **2. Preparar o ambiente de desenvolvimento**
1. **Escolher a linguagem de programação**
   - Opte por Python, Node.js ou qualquer linguagem compatível.

2. **Instalar bibliotecas necessárias**
   - No Python, por exemplo:
     ```bash
     pip install requests azure-cognitiveservices-language-textanalytics
     ```

3. **Configurar variáveis de ambiente**
   - Salve a chave e o endpoint para evitar expor credenciais:
     ```bash
     export AZURE_TRANSLATOR_KEY="sua-chave"
     export AZURE_TRANSLATOR_ENDPOINT="seu-endpoint"
     ```

---

#### **3. Capturar o texto técnico**
1. **Extração de texto de documentos**
   - Use **IA do Azure para Informação de Documentos** para PDFs e Word.

2. **Extração de texto de sites**
   - Utilize um scraper como BeautifulSoup (Python).

---

#### **4. Enviar o texto ao Azure Translator**
1. **Configurar a API REST**
   - Endpoint típico:
     ```
     https://api.cognitive.microsofttranslator.com/translate?api-version=3.0&to=<idioma-destino>
     ```

2. **Exemplo de código em Python**
   ```python
   import requests

   key = "sua-chave"
   endpoint = "seu-endpoint"
   url = f"{endpoint}/translate?api-version=3.0&to=pt"

   headers = {
       "Ocp-Apim-Subscription-Key": key,
       "Content-Type": "application/json"
   }

   body = [{"text": "This is a technical article about machine learning."}]

   response = requests.post(url, headers=headers, json=body)
   translation = response.json()
   print(translation[0]['translations'][0]['text'])
   ```

---

#### **5. Personalizar a tradução (opcional)**
1. **Configurar o Custom Translator**
   - Acesse o recurso **Custom Translator** no portal Azure.
   - Carregue glosários técnicos e documentos bilíngues.

2. **Testar com novos termos técnicos**
   - Avalie como a tradução responde a termos específicos.

---

#### **6. Exibir o texto traduzido**
1. **Criar uma interface**
   - Use **Flask** ou **Django** (Python) para uma interface web simples.
   - Ou crie algo mais dinâmico com **React** e **Node.js**.

---

#### **7. Publicar e monitorar**
1. **Hospedar o aplicativo**
   - Use o **Azure App Service** ou **Azure Functions**.

2. **Configurar monitoramento**
   - Configure o **Azure Monitor** para verificar desempenho e problemas.

---

#### **8. Melhorar continuamente**
1. **Testar traduções**
   - Compare com traduções manuais de especialistas.

2. **Treinar o modelo**
   - Adicione novos dados e glosários específicos do setor.

---

### Resultado
Seguindo esses passos, você terá um tradutor eficiente e personalizável para artigos técnicos, utilizando os recursos do Azure AI!
