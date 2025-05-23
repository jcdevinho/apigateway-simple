🛡️ API Gateway em Go com Descoberta de Serviço via Nacos
Este projeto é uma implementação de um API Gateway minimalista em Go com proxy reverso dinâmico e descoberta de serviços usando Nacos, ideal para arquiteturas de microserviços.

🚀 Visão Geral
Este gateway:

Roteia chamadas para serviços via path (/server-a/*)

Resolve IP e porta automaticamente usando o Nacos

Funciona como proxy reverso

Separa autenticação/roteamento da lógica dos microserviços

Exemplo:
GET /server-a/user/list → resolvido para uma instância real registrada no Nacos com nome server-a.

🧱 Tecnologias
Go 1.20+

Nacos SDK Go v2

httprouter

📦 Instalação
1. Suba o Nacos Server
docker run -d -p 8848:8848 --name nacos nacos/nacos-server

2. Clone o projeto
git clone https://github.com/seu-usuario/gateway-nacos-go.git
cd gateway-nacos-go

3. Instale as dependências
go mod tidy

4. Rode o gateway
go run main.go

🧪 Exemplo de Uso

🔌 Registro de serviço no Nacos
Um microserviço chamado server-a deve estar registrado no Nacos, por exemplo:

ServiceName: server-a

Group: DEFAULT_GROUP

🔄 Requisição HTTP

GET http://localhost:8080/server-a/user/list

O gateway resolve dinamicamente uma instância saudável registrada como server-a.

Encaminha a requisição para http://<ip>:<port>/user/list.

Retorna a resposta ao cliente.

📂 Estrutura do Projeto

gateway-nacos-go/

├── main.go        
├── go.mod         
├── logs/          
├── cache/     
