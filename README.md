# DISPLAY-IPS

Os códigos ST7789 e ST7335 foram desenvolvidos utilizando outras libs disponíveis online em:
https://github.com/afiskon/stm32-st7735 e https://github.com/Floyd-Fish/ST7789-STM32.

Eles foram adaptados para serem executados na placa STM32F103C8, também conhecida como BluePill,
sendo utilizado o STMCube IDE como plataforma principal, junto ao recurso MX.

Para utilizar os códigos, vários passos devem ser seguidos. Preste atenção:

1-Faça o download da pasta com os arquivos .c e .h que serão utilizados
2-Crie um projeto normalmente no STMCube IDE
3-Na configuração do MX, você pode configurar os leds e botões da placa:
  3.1 LEDs: PB3 a PB6
  3.2 Botões: PA9 a PA12
4-Ainda na configuração do MX, é necessário configurar os GPIOs dos pinos de controle do display
  RES=RESET: configurar o pino PB1 como GPIO_OUTPUT. Você deve dar um nome (LABEL) para esse pino. 
              Para isso, clique com o botão direito e use a opção "Enter User Label". Você deve configurar
              conforme o modelo de display ST7789_RS ou ST7735_RS
  DC: configurar o pino PB0 como GPIO_OUTPUT. Você deve dar um nome (LABEL) para esse pino. 
              Para isso, clique com o botão direito e use a opção "Enter User Label". Você deve configurar
              conforme o modelo de display ST7789_DC ou ST7735_DC
  CS: configurar o pino PA4 como GPIO_OUTPUT. Você deve dar um nome (LABEL) para esse pino. 
              Para isso, clique com o botão direito e use a opção "Enter User Label". Você deve configurar
              conforme o modelo de display ST7789_CS ou ST7735_CS
5-Ainda na configuração do MX, é necessário configurar a SPI1 para comunicar com o display. Para isso, vá
      em Connectivity e selecione SPI1. Configure da seguinte forma:
      5.1  Mode: Full-Duplex Master
      5.2  Hardware NSS Signal: Disable
      5.3  Parameter Settings:
            Basic: Motorola, 8 bits, MSB first
            Clock Parameters: Prescaler = 4, Clock Polarity (CPOL) = High, Clock Phase (CPHA) = 1 Edge
            Advanced Parameters: CRC Calculation = Disabled, NSS Signal Type = Software
6-Salve a configuração.
