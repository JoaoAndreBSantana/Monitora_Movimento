# Monitoramento de Inclinação com Sensor MPU6050 

Este projeto implementa um sistema embarcado utilizando o sensor **MPU6050** para monitorar movimentos e inclinação em tempo real, com exibição dos dados em um display **OLED SSD1306 128x64**. A leitura é realizada via protocolo I2C e processada com um filtro de suavização para garantir estabilidade visual e precisão nas medições.

---

## Objetivo

Desenvolver uma ferramenta compacta e confiável para **medir ângulos de inclinação (roll e pitch)**, além de monitorar aceleração e rotação em três eixos. Ideal para aplicações em:
- Robótica
- Estabilização de plataformas
- Sistemas de navegação
- Projetos educacionais de controle inercial

---

## Componentes Utilizados

| Componente        | Descrição                                        |
|-------------------|--------------------------------------------------|
| Raspberry Pi Pico | Microcontrolador principal |
| MPU6050           | Sensor IMU com acelerômetro + giroscópio   |
| Display OLED      | Tela SSD1306 128x64    |

---

## 🔌 Mapeamento de Pinos

### Conexão do MPU6050

| Função | GPIO (Pico) |
|--------|-------------|
| SDA    | GP2         |
| SCL    | GP3         |

### Conexão do Display OLED

| Função | GPIO (Pico) |
|--------|-------------|
| SDA    | GP14        |
| SCL    | GP15        |

---

## Funcionamento do Sistema

1. **Inicialização**  
   O código configura o MPU6050, ativa o sensor e define suas escalas de medição. Também inicializa o barramento SoftI2C do OLED.

2. **Leitura de Dados**  
   A cada 0.2 segundos:
   - Lê os valores brutos do acelerômetro e giroscópio.
   - Converte os dados para:
     - Aceleração (g)
     - Velocidade angular (°/s)

3. **Cálculo de Inclinação**  
   Os ângulos **Roll** e **Pitch** são calculados com base nos dados do acelerômetro, utilizando fórmulas trigonométricas padrão (atan2).

4. **Filtro de Suavização**  
   Um filtro exponencial é aplicado aos ângulos para reduzir oscilações e melhorar a leitura visual no display.

5.  **Tratamento de Erros**  
- Em caso de falha de leitura, o sistema informa no display e tenta reconfigurar o sensor automaticamente.

---

##  Resultado Esperado

Com o sistema em funcionamento, você terá:

- Um monitor de inclinação responsivo, estável e em tempo real.
- Visualização simultânea dos eixos do acelerômetro e giroscópio.
- Detecção precisa de movimentos angulares, útil para vários contextos técnicos e acadêmicos.

---



