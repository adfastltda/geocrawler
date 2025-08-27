# AVISO
- vps gringa esta dando problemas, breve corrijo 

# GeoCrawler 

GeoCrawler é um scraper do Google Maps, permitindo extrair informações de estabelecimentos como nome, categoria, endereço, avaliações, website e telefone.  

---

## 🚀 Funcionalidades

- Busca por estabelecimentos no Google Maps com base em um termo de pesquisa (`query`).  
- Extrai dados de múltiplas páginas de resultados.  
- Retorna os dados no formato **JSON**.  
- Pronto para rodar em **Docker** ou **Docker Compose**.

---

## 🐳 Info do build

- Docker version 28.3.3, build 980b856

---

### ⚡ Como usar

### 1. Rodando direto com Docker

```bash
docker pull adfastltda/geocrawler:latest
docker run -p 5888:5888 adfastltda/geocrawler:latest
```
A API ficará disponível em: `http://localhost:5888`

### 2. Usando Docker Compose

Crie um arquivo `docker-compose.yml`:

```bash
services:
  geocrawler:
    image: adfastltda/geocrawler:latest
    container_name: geocrawler
    ports:
      - "5888:5888"
    restart: unless-stopped
```

Para iniciar:
```bash
docker-compose up -d
```
A API ficará disponível em: `http://localhost:5888`

### 3. Fazendo requisições

Você pode testar a API com `curl` ou `Postman`:
```bash
curl -X POST "http://localhost:5888/scrape" \
     -H "Content-Type: application/json" \
     -d '{"query": "padarias em São Paulo"}'
```
O retorno será um JSON com os dados extraídos:
`
[
    {
        "Name": "Padaria XYZ",
        "Category & Address": "Padaria · Rua Exemplo, 123",
        "Rating": "4.5",
        "Reviews": "120",
        "Website": "http://www.padariaxyz.com",
        "Detail Link": "https://www.google.com/maps/place/Padaria+XYZ",
        "Phone": "(11) 99999-9999"
    }
]
`

---
#### OBS: 

- O Google Maps limita a busca a 120 resultados por requisição;
- O processo leva, em média, 2 minutos para ser concluído;
- Não feche a conexão enquanto o processo de extração estiver em andamento, pois isso acarretará perda de dados.

---
##### ☕ Buy Me a Coffee

Se você gosta deste projeto e quer apoiar o desenvolvimento, pode contribuir com um café!  

**PIX:** `pix@adfastltda.com.br`
**PayPal:** [Doar](https://www.paypal.com/ncp/payment/TSLA567NR39LA) 

Toda ajuda e sugestoes é bem-vinda e motivadora!  

Obrigado pelo apoio! 🙏

