# Arduino HTML

## Introdução

A aula abordou conceitos de **HTML, arquitetura cliente-servidor e Internet das Coisas (IoT)** utilizando Arduino como servidor web.

Foi demonstrado como criar uma interface HTML simples que pode ser acessada através de um navegador para controlar dispositivos conectados ao Arduino.

Também foram apresentados conceitos de desenvolvimento web, ferramentas como VS Code e boas práticas de organização de código.

---

# Objetivos da Aula

- Transformar o Arduino em um **servidor web**
- Criar uma **interface HTML** para controle de dispositivos IoT
- Testar conectividade utilizando **rede local**
- Compreender o modelo **cliente-servidor**
- Utilizar ferramentas de desenvolvimento web

---

# Upload e Teste do Servidor

Para executar o projeto é necessário realizar os seguintes passos:

1. Fazer upload do **sketch Arduino Web Server** para a placa.
2. Verificar se as **bibliotecas necessárias estão instaladas**.
3. Configurar corretamente o **MAC Address**.
4. Enviar o código para o Arduino.
5. Obter o **IP da placa** através do Serial Monitor.
6. Testar a conectividade utilizando **ping pelo celular** ou acessando o IP pelo navegador.

Antes de finalizar o código é recomendado:

- Remover comentários desnecessários
- Organizar o código
- Alinhar o código utilizando `Ctrl + T`

---

# Instalação do Live Server

Foi utilizada a extensão **Live Server** no Visual Studio Code para facilitar o desenvolvimento da interface HTML.

## Passos

1. Abrir o **Visual Studio Code**
2. Ir até a aba **Extensions**
3. Pesquisar por **Live Server**
4. Instalar a extensão
5. Executar o arquivo HTML utilizando **Open with Live Server**

Essa extensão permite visualizar alterações no navegador **em tempo real**.

---

# HTML e Origem da Web

O **HTML (HyperText Markup Language)** foi criado por **Tim Berners-Lee** no início da década de 1990.

Seu objetivo era facilitar o compartilhamento e a localização de documentos entre computadores conectados à internet.

O HTML funciona como o **esqueleto de uma página web**, definindo sua estrutura básica.

Exemplo de elementos HTML:

- `title` → título da página
- `h1` → título visível
- `p` → parágrafo
- `button` → botão

---

# Modelo Cliente-Servidor

A comunicação na web segue o modelo **cliente-servidor**.

## Funcionamento

1. O navegador envia uma **requisição**
2. O servidor processa a requisição
3. O servidor envia uma **resposta**

No contexto da aula:

- **Cliente:** navegador do celular ou computador
- **Servidor:** Arduino
- **Resposta:** página HTML enviada pelo Arduino

---

# Analogia Utilizada

Foi utilizada uma analogia para facilitar o entendimento:

- Cliente → pessoa que faz o pedido
- Garçom → servidor
- Pedido → requisição HTTP
- Prato servido → documento HTML

---

# Estrutura do Projeto

Foi criado um projeto com organização básica de arquivos.

iot-web-server/
│
├── index.html
├── arduino_web_server.ino
└── README.md


---

# Criação do index.html

O arquivo `index.html` foi criado no **VS Code**.

Atalho utilizado:

Esse atalho gera automaticamente a estrutura básica do HTML5.

Estrutura inicial:

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Controle IoT</title>
</head>

<body>

<h1>Controle Arduino IoT</h1>

</body>
</html>
```
---
CSS e Responsividade

O CSS é responsável pela estilização da página.

Comparação apresentada em aula:

HTML → esqueleto

CSS → aparência (cores, layout, estilo)

Devido às limitações de memória do Arduino, não é possível utilizar arquivos CSS externos.

A solução é utilizar CSS embutido no próprio HTML.

---
Limitações do Arduino

O Arduino possui limitações de hardware que impactam projetos web.

Principais limitações:

Memória de aproximadamente 32 KB

Não suporta arquivos grandes

Imagens geralmente não cabem na memória

Projetos maiores precisam de microSD

---
Configuração do Arduino Web Server

O Arduino pode funcionar como um servidor web utilizando a biblioteca Ethernet.

Etapas do código:

Importar bibliotecas

Definir MAC Address

Inicializar o servidor

Aguardar conexões

Receber requisições

Enviar documento HTML

Encerrar conexão

---
Cabeçalho HTTP

Para que o navegador interprete corretamente o documento enviado pelo Arduino, é necessário enviar um cabeçalho HTTP válido.

Exemplo:
HTTP/1.1 200 OK
Content-Type: text/html
Connection: close
Após o cabeçalho deve existir uma linha em branco antes do conteúdo HTML.
---
Estrutura do Código Arduino

O programa segue a estrutura padrão do Arduino:

setup() → inicializa o servidor

loop() → verifica conexões de clientes

No loop:

Detecta tentativa de conexão

Lê a requisição do cliente

Envia a página HTML

Encerra a conexão com:
```cpp
client.stop();
```
---
Leitura de Requisições

Comando utilizado para verificar se há dados disponíveis:
```
client.available()
```
Esse comando verifica se o cliente enviou alguma requisição.

Também foi apresentado o uso do operador ponto:
```
client.available()
```
O operador . permite acessar métodos e propriedades de um objeto.

---
Boas Práticas de Código

Algumas boas práticas foram destacadas durante a aula:

remover comentários desnecessários

organizar o código

manter indentação correta

utilizar Ctrl + T para alinhar o código

inserir delay(1) para estabilidade

salvar o código frequentemente

---
Teste de Conectividade

Após enviar o código para o Arduino:

Abrir o Serial Monitor

Verificar o IP atribuído

Abrir o navegador do celular

Digitar o IP do Arduino

Exemplo de IP:
```
10.26.44.56
```
Se tudo estiver configurado corretamente, a página HTML será exibida no navegador.
---
Conclusão

A aula demonstrou como integrar desenvolvimento web com sistemas embarcados, permitindo que dispositivos como Arduino funcionem como servidores web.

Foram abordados conceitos fundamentais de:

HTML

HTTP

arquitetura cliente-servidor

desenvolvimento IoT

comunicação em rede

Esse tipo de aplicação permite criar interfaces web simples para controle remoto de dispositivos eletrônicos.
