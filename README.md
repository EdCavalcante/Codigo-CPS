# 🌡️ Rede IoT com ESP-NOW — Monitoramento Ambiental Distribuído

> Projeto desenvolvido para a disciplina de **Sistemas Ciberfísicos Colaborativos**  
> **Universidade de Fortaleza (UNIFOR)** — Centro de Ciências Tecnológicas  
> Curso de Ciência da Computação — 2025

---

## 📋 Sobre o Projeto

Implementação de uma rede de Sistemas Ciberfísicos distribuídos utilizando microcontroladores **ESP32** e o protocolo de comunicação sem fio **ESP-NOW**. Cada nó da rede coleta dados de temperatura e umidade via sensor **DHT11** e os transmite em formato **JSON** para os demais nós, formando uma rede descentralizada com controle de looping e retransmissão inteligente.

---

## ⚙️ Funcionalidades

- Comunicação sem fio ponto a ponto via ESP-NOW (sem roteador)
- Coleta de temperatura e umidade com sensor DHT11
- Transmissão de dados em formato JSON com ID, contador, temperatura e umidade
- Controle de mensagens duplicadas para evitar looping na rede
- LED indicador de transmissão
- Suporte a múltiplos nós simultâneos

---

## 🛠️ Tecnologias e Componentes

| Item | Descrição |
|------|-----------|
| ESP32 | Microcontrolador principal com suporte ao ESP-NOW |
| DHT11 | Sensor de temperatura e umidade |
| ESP-NOW | Protocolo de comunicação sem fio ponto a ponto |
| Arduino IDE | Ambiente de desenvolvimento do firmware |
| `esp_now.h` | Biblioteca do protocolo ESP-NOW |
| `DHT.h` | Biblioteca do sensor DHT11 |

---

## 📁 Estrutura do Repositório

```
/
├── no_sensor/
│   └── no_sensor.ino        # Código do nó sensor (coleta e envia dados)
├── no_roteador/
│   └── no_roteador.ino      # Código do nó roteador (retransmite mensagens)
├── gateway/
│   ├── gateway_espnow.ino   # ESP32 que recebe via ESP-NOW e envia via Serial
│   └── gateway_mqtt.ino     # ESP32 que recebe via Serial e publica via MQTT
└── README.md
```

---

## 🚀 Como Usar

### Pré-requisitos

- Arduino IDE instalada
- Suporte ao ESP32 configurado na Arduino IDE
- Bibliotecas instaladas:
  - `esp_now.h` (inclusa no pacote ESP32)
  - `DHT sensor library` (instalar via Library Manager)

### Passos

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/seu-repositorio.git
   ```

2. Abra o arquivo `.ino` correspondente ao tipo de nó que deseja configurar.

3. Altere o **ID do nó** no código conforme o formato da turma:
   ```cpp
   String nodeID = "10-1"; // Substitua pelo ID do seu nó
   ```

4. Adicione os **MAC addresses** dos peers no código de cada nó.

5. Faça o upload para o ESP32 via Arduino IDE.

---

## 📦 Formato da Mensagem JSON

```json
{
  "id": "10-1",
  "contador": 42,
  "temperatura": 27.5,
  "umidade": 65.0
}
```

---

## ✅ Resultados

- Comunicação estável entre múltiplos nós via ESP-NOW
- Controle de looping implementado com sucesso
- Validação com adição de novo nó sem reconfiguração da rede
- Integração com AdafruitIO (MQTT) não concluída nesta versão

---

## 🔮 Melhorias Futuras

- Integração com AdafruitIO via MQTT para visualização em nuvem
- Implementação de criptografia nas mensagens ESP-NOW
- Migração para ESP-Mesh para redes maiores
- Adição de novos sensores (luminosidade, qualidade do ar)

---

## 👥 Equipe

Desenvolvido por estudantes do curso de Ciência da Computação — UNIFOR, 2025.

---

## 📄 Licença

Este projeto foi desenvolvido para fins acadêmicos.
