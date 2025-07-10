# Monitoramento de Inclinação com Sensor MPU6050 

Projeto em MicroPython para leitura e exibição em tempo real dos dados de aceleração, giroscópio e ângulos de inclinação (roll e pitch) do sensor MPU6050, com visualização no display OLED 128x64.

## Componentes

- Raspberry Pi Pico (MicroPython)
- Sensor MPU6050 (I2C)
- Display OLED SSD1306 (SoftI2C)

## Conexões

| Função MPU6050 | GPIO Pico |  
|---------------|----------|  
| SDA           | GP2      |  
| SCL           | GP3      |  

| Função OLED    | GPIO Pico |  
|---------------|-----------|  
| SDA           | GP14      |  
| SCL           | GP15      |  

## Funcionamento

- Inicializa e configura MPU6050 e OLED via I2C.
- Lê acelerômetro e giroscópio a cada 0,2s.
- Calcula roll e pitch com suavização para estabilidade.
- Mostra dados formatados no OLED:  
  - Roll e Pitch em graus  
  - Aceleração (X,Y,Z) em g  
  - Giroscópio (X,Y,Z) em °/s  
- Em caso de erro na leitura, exibe mensagem e reinicializa o sensor.

## Saída Exemplo no OLED

R: -12.4 deg
P: 18.7 deg
A: 0.01,-0.02,0.98
G: 0.25,0.10,-0.05
