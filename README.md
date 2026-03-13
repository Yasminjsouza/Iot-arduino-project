# Iot-arduino-project

# Documentação – Fundamentos de Arduino, IoT e Prototipação

## Introdução

A aula abordou conceitos fundamentais de programação com Arduino, comunicação serial, uso de bibliotecas, prototipação eletrônica e configuração de dispositivos para Internet das Coisas (IoT). Também foram demonstradas ferramentas de simulação e produção de placas de circuito impresso (PCB), além da configuração de um Arduino como servidor web utilizando módulo Ethernet.

---

# Estrutura Básica de Programação no Arduino

Todo programa em Arduino possui duas funções principais:

## setup()

A função `setup()` executa apenas **uma vez** no início do programa.  
Ela é responsável por configurar o ambiente inicial, como:

- iniciar comunicação serial
- configurar pinos
- inicializar bibliotecas

## loop()

A função `loop()` executa **infinitamente após o setup()**.  
Ela contém o código que será repetido continuamente durante a execução do programa.

Antes da função `setup()` existe um espaço destinado à declaração de:

- bibliotecas
- variáveis globais
- funções reutilizáveis

Essa organização é comum em Arduino e em diversas linguagens de programação.

---

# Uso de Bibliotecas

Bibliotecas são conjuntos de códigos prontos que podem ser reutilizados para executar tarefas específicas.

Elas funcionam como um **repositório de soluções**, permitindo evitar a implementação manual de cálculos complexos.

Exemplo de uso comum:

- leitura de sensores
- cálculo de distância em sensor ultrassônico
- comunicação com módulos de rede

Bibliotecas geralmente são importadas no topo do código.

```cpp
#include <biblioteca.h>

```
---

# Comentários e Documentação do Código

A documentação dentro do código pode ser feita utilizando comentários estruturados.
 Exemplo:
```cpp
/**

  Programa: Fundamentos Arduino
  
  @author: Nome do autor
  
 */
```
 ---

# Comunicação Serial

A comunicação serial permite que o Arduino envie e receba dados através da porta USB conectada ao computador.

Os pinos utilizados são:

0 (RX) → recepção de dados

1 (TX) → transmissão de dados

Esses pinos ficam bloqueados durante a comunicação serial.

Grande parte dos erros em projetos Arduino ocorre por problemas de comunicação serial.

Exemplo de código:
```cpp
Serial.print("hello world");

```
Esse comando envia texto para o Serial Monitor.

A linguagem também é case sensitive, ou seja, diferencia letras maiúsculas e minúsculas.

Exemplo correto:
```cpp
Serial.print("Hello");
```
Exemplo incorreto:
```cp
serial.print("Hello");

```
---
# Fluxo de Desenvolvimento no Arduino

O fluxo básico de desenvolvimento segue as etapas:

##### 1.Escrever o código no Arduino IDE

##### 2.Salvar o sketch (sem espaços no nome)

##### 3.Clicar em Verify para compilar

##### 4.Conectar o Arduino ao computador

##### 5.Fazer Upload do código

##### 6.Abrir o Serial Monitor

##### 7.Verificar a saída do programa

Erros comuns:

* falta de ponto e vírgula

* chaves não fechadas

* erros de digitação

  ---
 # Simulação com TinkerCAD

O TinkerCAD pode ser usado para simular circuitos e testar programas de Arduino.

### Passos para utilizar código no simulador:

* Copiar o código

* Abrir o projeto no TinkerCAD

* Acessar a seção Código

* Selecionar modo Texto

* Apagar o código existente

* Colar o código copiado

* Iniciar a simulação

Após iniciar a simulação, é possível abrir o monitor serial para visualizar a saída do programa.

Alguns comportamentos podem diferir do hardware real.

---
# Ethernet Shield

O Ethernet Shield permite conectar o Arduino à rede.

### Ele utiliza os seguintes pinos do Arduino Uno:

* 4

* 10

* 11

* 12

* 13

Esses pinos ficam reservados para comunicação do módulo e não devem ser usados em outras funções.

Também é recomendado evitar os pinos 0 e 1 devido à comunicação serial.

Como o Arduino Uno possui recursos limitados, o uso da shield reduz a quantidade de pinos disponíveis.



---

# Cuidados com Hardware

Durante a montagem do circuito é necessário tomar alguns cuidados:

* desconectar o cabo USB antes de encaixar módulos

* evitar contato da placa com superfícies metálicas

* encaixar os pinos corretamente

Existem 7 kits reserva, portanto danos às placas devem ser evitados.

print 
---
# Prototipação e Produção de PCB

Foi apresentada a ferramenta Treadsim, utilizada para prototipação de circuitos e desenvolvimento de placas PCB.

####A ferramenta permite:

* simular circuitos

* documentar projetos

* gerar placas para produção

#### Processo de fabricação:

* aplicação de pasta de solda com stencil

* posicionamento dos componentes

* aquecimento da placa

* soldagem final

Componentes inferiores podem ser soldados manualmente para proteger os componentes superiores.

---

# TinkerCAD e Criação de Placas

O TinkerCAD possui dois modos principais:

 Modo Esquemático

#### Mostra as conexões entre componentes, como:

*resistores

*LEDs

*sensores

##Modo PCB

Permite gerar o layout da placa e exportar arquivos para fabricação.

#### A protoboard pode ser utilizada em diferentes tamanhos:

* half

* mini

---

# Configuração de Rede no Arduino

#### Para conexão com rede utilizando Ethernet é necessário configurar:

* endereço IP

* máscara de sub-rede

* gateway

* DNS

Exemplo de configuração:
```cpp
IP: 10.6.44.48
Máscara: 255.255.255.0
Gateway: 10.6.44.1
DNS: 10.6.47.90
  ```
Esses parâmetros são necessários para comunicação na rede.

---

# Arduino como Servidor Web

Utilizando a biblioteca Ethernet, o Arduino pode atuar como um servidor web.

Exemplo de criação de servidor:
```cpp
EthernetServer server(80);
```
A porta 80 é a porta padrão do protocolo HTTP.

Durante a execução do programa, o Arduino pode exibir o IP no Serial Monitor.

Isso permite acessar o servidor pelo navegador.
---
# Demonstração Prática

Foi realizada uma demonstração conectando o Arduino ao roteador da rede.

#### Após o envio do código:

* quatro LEDs indicaram comunicação TX/RX

* o IP foi exibido no Serial Monitor

Isso confirmou que o dispositivo estava conectado à rede.

---
# Organização da Atividade

A atividade prática foi organizada em 8 estações de trabalho.

Cada estação foi composta por grupos de 3 alunos.

Atividades do grupo:

conectar o Arduino ao roteador

enviar o código para a placa

verificar o IP no monitor serial

testar conectividade

Um grupo deveria apresentar o funcionamento detalhado do projeto.

---
# Conclusão

A aula apresentou conceitos essenciais para desenvolvimento com Arduino e IoT, incluindo:

* programação básica

* comunicação serial

* uso de bibliotecas

* prototipação eletrônica

* criação de placas PCB

* configuração de rede

* implementação de servidor web

Esses conhecimentos são fundamentais para projetos de sistemas embarcados e Internet das Coisas.





