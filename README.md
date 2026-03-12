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
Fluxo de Desenvolvimento no Arduino

O fluxo básico de desenvolvimento segue as etapas:

1.Escrever o código no Arduino IDE

2.Salvar o sketch (sem espaços no nome)

3.Clicar em Verify para compilar

Conectar o Arduino ao computador

Fazer Upload do código

Abrir o Serial Monitor

Verificar a saída do programa

Erros comuns:

falta de ponto e vírgula

chaves não fechadas

erros de digitação
