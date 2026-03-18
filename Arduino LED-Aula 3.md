
# Arduino IoT Web Server – Controle de LED

##  Descrição

Este projeto demonstra a implementação de um **servidor web utilizando Arduino**, permitindo o controle de um LED através de uma interface web acessada pelo navegador.

O sistema utiliza **requisições HTTP** para enviar comandos ao Arduino, integrando conceitos de:

- IoT (Internet das Coisas)
- Programação em Arduino (C/C++)
- HTML + CSS
- Comunicação cliente-servidor

---

##  Conceito do Projeto

O Arduino funciona como um **servidor web**, enquanto o navegador atua como **cliente**.

Fluxo:

1. Usuário acessa o IP do Arduino
2. Navegador envia requisição HTTP
3. Arduino interpreta o comando
4. LED é ligado ou desligado

---

##  Hardware Utilizado

- Arduino Uno
- Ethernet Shield
- LED
- Resistor 220Ω
- Protoboard

---

##  Imagens do Projeto

### Código no Arduino IDE

![1000061545](https://github.com/user-attachments/assets/6f3213df-fe00-488c-9a7e-cc99c034ca54)

![1000061546](https://github.com/user-attachments/assets/a78c6cc1-f4a7-43c4-a212-f8522ad7ec2e)


![1000061547](https://github.com/user-attachments/assets/6985e64d-a783-4c71-be35-bbb5b0ee3a56)


---

##  Interface Web

A interface é gerada diretamente pelo Arduino e contém botões para controle do LED:

```html
<a href="/?led=on" class="on">ON</a>
<a href="/?led=off" class="off">OFF</a>

```
---

## Estilização (CSS)

a {
  text-decoration: none;
  font-weight: bold;
  padding: 12px;
  width: 100px;
  display: inline-block;
  color: #ffffff;
}

.on {
  background-color: #3498db;
}

.off {
  background-color: #e74c3c;
}


---

## Código Arduino

#include <SPI.h>
#include <Ethernet.h>

byte mac[6] = { 0x90, 0xA2, 0xDA, 0x2A, 0x31, 0xB2 };
EthernetServer server(80);

#define led 8

const char pagina[] PROGMEM = R"HTML(
<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Arduino WEB Server</title>

<style>
body {
  font-family: sans-serif;
  text-align: center;
}

a {
  text-decoration: none;
  font-weight: bold;
  padding: 12px;
  width: 100px;
  display: inline-block;
  color: #ffffff;
}

.on {
  background-color: #3498db;
}

.off {
  background-color: #e74c3c;
}
</style>
</head>

<body>

<h1>Arduino IoT</h1>
<p>Controle de dispositivos</p>

<a href="/?led=on" class="on">ON</a>
<a href="/?led=off" class="off">OFF</a>

</body>
</html>
)HTML";

void setup() {
  pinMode(led, OUTPUT);
  Serial.begin(9600);
  Ethernet.begin(mac);
  server.begin();

  Serial.println("Arduino IoT");
  Serial.print("IP: ");
  Serial.println(Ethernet.localIP());
}

void loop() {
  EthernetClient client = server.available();

  if (client) {
    String request = "";

    while (client.available()) {
      char c = client.read();
      request += c;
    }

    if (request.indexOf("GET /?led=on") >= 0) {
      digitalWrite(led, HIGH);
    }

    if (request.indexOf("GET /?led=off") >= 0) {
      digitalWrite(led, LOW);
    }

    client.println("HTTP/1.1 200 OK");
    client.println("Content-Type: text/html");
    client.println("Connection: close");
    client.println();

    client.print((__FlashStringHelper*)pagina);

    delay(1);
    client.stop();
  }
}


---

## Como Executar

1. Conectar o Arduino ao computador


2. Fazer upload do código


3. Abrar o Serial Monitor


4. Copiar o IP exibido


5. Acessar o IP no navegador (celular ou PC)




---

## Problemas Comuns

LED fraco → esquecer pinMode

Não conecta → erro na rede ou MAC

Página não abre → verificar IP

LED não responde → erro na lógica if



---

## Boas Práticas

Organizar código (Ctrl + T)

Remover comentários desnecessários

Usar nomes com #define

Testar cada alteração



---

## Conclusão

Este projeto demonstra como integrar hardware + web, permitindo controlar dispositivos físicos através de um navegador.

Base fundamental para desenvolvimento de sistemas IoT.


---

## Demonstração



https://github.com/user-attachments/assets/88aba2fa-4cc6-40b8-9eb1-196c1dd0fc4d



---

