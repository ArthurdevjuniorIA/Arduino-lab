<div align="center">

# ⚡ Arduino Engineering Lab

### Roteiro progressivo de sistemas embarcados, prototipagem de circuitos e protocolos de comunicação

[![C++](https://img.shields.io/badge/Linguagem-C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)](https://isocpp.org/)
[![Arduino](https://img.shields.io/badge/Hardware-Arduino-00979D?style=for-the-badge&logo=arduino&logoColor=white)](https://www.arduino.cc/)
[![PlatformIO](https://img.shields.io/badge/PlatformIO-Compatível-F5822A?style=for-the-badge&logo=platformio&logoColor=white)](https://platformio.org/)
[![License: GPL v3](https://img.shields.io/badge/Licença-GPLv3-blue?style=for-the-badge)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-bem--vindos-brightgreen?style=for-the-badge)](#-como-contribuir)

[Visão geral](#-visão-geral) •
[Roadmap](#-roadmap-de-aprendizado) •
[Hardware](#-hardware-necessário) •
[Como usar](#-como-compilar-e-gravar) •
[Contribuir](#-como-contribuir)

</div>

---

## 📑 Sumário

- [Visão geral](#-visão-geral)
- [Estrutura do repositório](#-estrutura-do-repositório)
- [Roadmap de aprendizado](#-roadmap-de-aprendizado)
- [Hardware necessário](#-hardware-necessário)
- [Ambiente de desenvolvimento](#-ambiente-de-desenvolvimento)
- [Como compilar e gravar](#-como-compilar-e-gravar)
- [Bibliotecas utilizadas](#-bibliotecas-utilizadas)
- [Padrão dos projetos](#-padrão-dos-projetos)
- [Boas práticas e segurança](#-boas-práticas-e-segurança)
- [Solução de problemas](#-solução-de-problemas)
- [Como contribuir](#-como-contribuir)
- [Licença](#-licença)

---

## 📌 Visão geral

**Arduino Engineering Lab** é um repositório de aprendizado prático que documenta uma jornada completa em sistemas embarcados: das saídas digitais mais simples até sistemas integrados e autônomos.

Cada projeto contém:

- 💻 **Código-fonte** (`.ino`) comentado e funcional
- 🔌 **Esquema de ligação** (circuito) em imagem
- 🧾 **Lista de componentes** (BOM)
- 📖 **README próprio** com objetivo, conceitos, pinagem e passo a passo

**Você vai aprender:**

| Área | Conceitos |
|------|-----------|
| Entrada/Saída digital | GPIO, `digitalWrite`, `digitalRead`, pull-up/pull-down, debounce |
| Sinais analógicos | ADC, `analogRead`, mapeamento de valores, filtragem |
| Controle de potência | PWM, drivers de motor, ponte H, isolamento de carga |
| Comunicação | UART, I2C (SDA/SCL), parsing de comandos |
| Interfaces | Displays LCD, telemetria em tempo real |
| Arquitetura de firmware | Máquinas de estado, temporização sem `delay()`, integração de módulos |

---

## 📂 Estrutura do repositório

```text
arduino-projects/
├── .gitignore
├── LICENSE
├── README.md
├── 01-fundamentals/
│   ├── blink-led/
│   │   ├── blink-led.ino
│   │   ├── circuit.png
│   │   └── README.md
│   └── interactive-traffic-light/
├── 02-inputs-and-sensors/
│   ├── dht11-temperature-humidity/
│   └── hc-sr04-ultrasonic-distance/
├── 03-actuators-and-motors/
│   ├── servo-motor-control/
│   └── dc-motor-l298n-driver/
├── 04-displays-and-interfaces/
│   └── i2c-lcd-thermometer/
├── 05-serial-communication/
│   └── serial-terminal-led-control/
└── 06-integrated-projects/
    ├── mini-weather-station/
    └── intruder-alarm-system/
```

---

## 🛠️ Roadmap de aprendizado

Siga a ordem numérica: cada módulo reaproveita conceitos do anterior.

| # | Módulo | Nível | Foco principal |
|---|--------|:-----:|----------------|
| 01 | [Fundamentos](./01-fundamentals) | 🟢 Iniciante | GPIO, temporização, botões |
| 02 | [Entradas e sensores](./02-inputs-and-sensors) | 🟢 Iniciante | Sensores digitais/analógicos, ADC |
| 03 | [Atuadores e motores](./03-actuators-and-motors) | 🟡 Intermediário | PWM, servo, ponte H |
| 04 | [Displays e interfaces](./04-displays-and-interfaces) | 🟡 Intermediário | LCD, barramento I2C |
| 05 | [Comunicação serial](./05-serial-communication) | 🟡 Intermediário | UART, parsing de comandos |
| 06 | [Projetos integrados](./06-integrated-projects) | 🔴 Avançado | Sistemas completos e autônomos |

### 1️⃣ `01-fundamentals` — E/S digital básica

**Foco:** controle de pinos GPIO, escrita digital (`digitalWrite`), leitura digital (`digitalRead`), temporização (`delay`) e resistores de pull-up internos/externos.

| Projeto | Descrição |
|---------|-----------|
| `blink-led` | Pisca um LED: o "Hello World" do embarcado |
| `interactive-traffic-light` | Semáforo com botão de pedestre |

### 2️⃣ `02-inputs-and-sensors` — Aquisição de dados físicos

**Foco:** interface com sensores digitais e analógicos, amostragem (`analogRead`), conversão ADC e uso de bibliotecas externas.

| Projeto | Descrição |
|---------|-----------|
| `dht11-temperature-humidity` | Leitura de temperatura e umidade |
| `hc-sr04-ultrasonic-distance` | Medição de distância com alerta sonoro |

### 3️⃣ `03-actuators-and-motors` — Movimento e potência

**Foco:** modulação por largura de pulso (PWM) via `analogWrite`, posicionamento de servos e acionamento de motores DC de alta corrente com ponte H (L298N).

| Projeto | Descrição |
|---------|-----------|
| `servo-motor-control` | Servo SG90 controlado por potenciômetro |
| `dc-motor-l298n-driver` | Controle de direção e velocidade de motor DC |

### 4️⃣ `04-displays-and-interfaces` — Interfaces homem-máquina

**Foco:** visualização de telemetria, biblioteca `LiquidCrystal` e redução de pinos com o barramento I2C (SDA/SCL).

| Projeto | Descrição |
|---------|-----------|
| `i2c-lcd-thermometer` | Termômetro digital em LCD 16x2 em tempo real |

### 5️⃣ `05-serial-communication` — Elo hardware-software

**Foco:** protocolo UART, configuração de baud rate (`Serial.begin`), leitura não bloqueante (`Serial.available`) e interpretação de comandos em texto enviados pelo computador.

| Projeto | Descrição |
|---------|-----------|
| `serial-terminal-led-control` | Terminal CLI interativo para controlar periféricos |

### 6️⃣ `06-integrated-projects` — Sistemas embarcados completos

**Foco:** combinar sensores, atuadores, displays e lógica de controle condicional em aplicações autônomas.

| Projeto | Descrição |
|---------|-----------|
| `mini-weather-station` | Estação meteorológica com ventoinha de resfriamento adaptativa |
| `intruder-alarm-system` | Alarme de segurança acionado por distância |

---

## ⚙️ Hardware necessário

### Placas compatíveis

| Placa | Compatibilidade | Observação |
|-------|:---------------:|------------|
| Arduino Uno | ✅ | Placa de referência dos projetos |
| Arduino Nano | ✅ | Mesmo MCU (ATmega328P), formato compacto |
| Arduino Mega 2560 | ✅ | Mais pinos e memória; pinos I2C/PWM diferentes |

> ⚠️ Em placas diferentes do Uno, confira a pinagem (principalmente I2C e PWM) antes de ligar.

### Lista de componentes

<details>
<summary><b>🔧 Básicos</b></summary>

- LEDs (vermelho, amarelo, verde)
- Resistores: 220 Ω (LEDs) e 10 kΩ (pull-down/pull-up)
- Push-buttons
- Potenciômetros (10 kΩ)
- Protoboard e jumpers (macho-macho e macho-fêmea)

</details>

<details>
<summary><b>📡 Sensores</b></summary>

- DHT11 (temperatura e umidade)
- HC-SR04 (distância ultrassônica)

</details>

<details>
<summary><b>⚙️ Atuadores e saídas</b></summary>

- Servo SG90
- Motor DC + driver ponte H L298N
- Buzzer ativo e passivo
- Display LCD 16x2 com módulo I2C

</details>

<details>
<summary><b>🔋 Alimentação</b></summary>

- Cabo USB (A/B ou Mini/Micro, conforme a placa)
- Fonte externa ou pack de pilhas para motores (recomendado)

</details>

---

## 💻 Ambiente de desenvolvimento

Escolha uma das opções:

| Opção | Indicada para | Link |
|-------|---------------|------|
| **Arduino IDE 2.x** | Iniciantes | [arduino.cc/en/software](https://www.arduino.cc/en/software) |
| **VS Code + PlatformIO** | Quem busca fluxo profissional, gerenciamento de dependências e versionamento | [platformio.org](https://platformio.org/) |

Clone o repositório:

```bash
git clone https://github.com/your-username/arduino-projects.git
cd arduino-projects
```

---

## 🚀 Como compilar e gravar

### Arduino IDE

1. Abra o arquivo `.ino` do projeto desejado (ex.: `01-fundamentals/blink-led/blink-led.ino`).
2. Conecte a placa via USB.
3. Selecione a placa em **Ferramentas → Placa**.
4. Selecione a porta (COM/TTY) em **Ferramentas → Porta**.
5. Clique em **Verificar** (compila) e depois em **Carregar** (grava o firmware).
6. Se o projeto usa serial, abra o **Monitor Serial** (`Ctrl+Shift+M`) e ajuste o baud rate conforme o README do projeto.

### PlatformIO (opcional)

```ini
; platformio.ini (exemplo para Arduino Uno)
[env:uno]
platform = atmelavr
board = uno
framework = arduino
monitor_speed = 9600
lib_deps =
    adafruit/DHT sensor library
    marcoschwartz/LiquidCrystal_I2C
```

```bash
pio run                  # compilar
pio run -t upload        # gravar
pio device monitor       # monitor serial
```

> 🐧 **Linux:** se a porta der "permission denied", adicione seu usuário ao grupo `dialout`: `sudo usermod -aG dialout $USER` e faça logout/login.

---

## 📚 Bibliotecas utilizadas

Instale pelo **Gerenciador de Bibliotecas** (`Ferramentas → Gerenciar Bibliotecas`):

| Biblioteca | Usada em | Observação |
|------------|----------|------------|
| `DHT sensor library` (Adafruit) | DHT11 | Requer também `Adafruit Unified Sensor` |
| `Servo` | Servo motor | Já inclusa na IDE |
| `LiquidCrystal` | LCD paralelo | Já inclusa na IDE |
| `LiquidCrystal I2C` | LCD com módulo I2C | Verifique o endereço (`0x27` ou `0x3F`) |
| `Wire` | I2C | Já inclusa na IDE |

---

## 🧩 Padrão dos projetos

Todo projeto segue a mesma estrutura, facilitando a leitura e a contribuição:

```text
nome-do-projeto/
├── nome-do-projeto.ino   # código-fonte
├── circuit.png           # esquema de ligação
└── README.md             # documentação do projeto
```

O `README.md` de cada projeto deve conter:

1. **Objetivo** — o que o projeto faz
2. **Conceitos abordados** — o que se aprende
3. **Componentes** — lista de materiais
4. **Tabela de pinagem** — conexão de cada pino
5. **Diagrama do circuito**
6. **Como funciona** — explicação da lógica
7. **Saída esperada** — comportamento ou saída serial
8. **Desafios extras** — ideias de evolução

**Exemplo de tabela de pinagem:**

| Componente | Pino do Arduino | Observação |
|------------|:---------------:|------------|
| LED | D13 | Com resistor de 220 Ω em série |
| Botão | D2 | `INPUT_PULLUP` |
| Sensor DHT11 (DATA) | D4 | Pull-up de 10 kΩ, se o módulo não tiver |

**Convenções de código:**

- Nomes de pinos como constantes (`const uint8_t LED_PIN = 13;`)
- Comentários explicando o *porquê*, não apenas o *o quê*
- Evitar `delay()` em projetos que exigem multitarefa (usar `millis()`)
- Um bloco de cabeçalho no topo de cada `.ino` com título, autor e descrição

---

## 🛡️ Boas práticas e segurança

- 🔌 **Desligue a alimentação** antes de alterar a montagem.
- 💡 **Sempre use resistor** em série com LEDs (220 Ω é um bom ponto de partida).
- ⚡ Cada pino do Arduino fornece no máximo **~20 mA** (limite absoluto 40 mA). Para cargas maiores, use transistor, relé ou driver.
- 🔋 **Não alimente motores pelo pino 5V** do Arduino: use fonte externa e una os **GNDs** (GND comum).
- 🔁 Para botões, prefira `INPUT_PULLUP` e trate o *debounce*.
- 📏 Confira a tensão de cada módulo (3,3 V vs 5 V) antes de conectar.
- 🧪 Teste os componentes isoladamente antes de integrá-los.

---

## 🩺 Solução de problemas

| Problema | Causa provável | Solução |
|----------|----------------|---------|
| Porta COM não aparece | Cabo só de carga ou driver ausente | Use cabo de dados; instale driver CH340/FTDI se necessário |
| Erro `avrdude: stk500_recv()` | Placa/porta errada | Revise **Ferramentas → Placa/Porta** |
| LCD I2C liga, mas sem texto | Contraste ou endereço incorreto | Ajuste o trimpot do módulo; rode um *I2C scanner* |
| DHT11 retorna `NaN` | Fiação ou pull-up ausente | Confira VCC/GND/DATA e o resistor de 10 kΩ |
| Servo treme ou reinicia a placa | Alimentação insuficiente | Use fonte externa e GND comum |
| Texto estranho no Monitor Serial | Baud rate diferente | Iguale o valor do `Serial.begin()` ao do monitor |

---

## 🤝 Como contribuir

Contribuições são muito bem-vindas! 🎉

1. Faça um **fork** do repositório.
2. Crie uma branch: `git checkout -b feature/nome-do-projeto`
3. Siga o [padrão dos projetos](#-padrão-dos-projetos).
4. Faça o commit: `git commit -m "feat: adiciona projeto X"`
5. Envie: `git push origin feature/nome-do-projeto`
6. Abra um **Pull Request** descrevendo o que foi feito.

**Padrão de commits sugerido:** `feat:` (novo projeto), `fix:` (correção), `docs:` (documentação), `refactor:` (reorganização de código).

Encontrou um bug ou tem uma ideia? Abra uma [issue](../../issues).

---

## ✅ Progresso do roadmap

- [ ] 01 — Fundamentos
- [ ] 02 — Entradas e sensores
- [ ] 03 — Atuadores e motores
- [ ] 04 — Displays e interfaces
- [ ] 05 — Comunicação serial
- [ ] 06 — Projetos integrados

---

## 📜 Licença

Este projeto está licenciado sob a **GNU General Public License v3.0**. Consulte o arquivo [LICENSE](LICENSE) para mais detalhes.

---

<div align="center">

Feito com ☕ e muitos jumpers por **[seu-nome](https://github.com/your-username)**

⭐ Se este repositório te ajudou, deixe uma estrela!

</div>
