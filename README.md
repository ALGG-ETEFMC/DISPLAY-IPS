# DISPLAY-IPS

Os códigos ST7789 e ST7335 foram desenvolvidos utilizando outras libs disponíveis online em:
https://github.com/afiskon/stm32-st7735 e https://github.com/Floyd-Fish/ST7789-STM32.

Eles foram adaptados para serem executados na placa STM32F103C8, também conhecida como BluePill,
sendo utilizado o STMCube IDE como plataforma principal, junto ao recurso MX.

Para utilizar os códigos, vários passos devem ser seguidos. Preste atenção!

<h2>Configurando a IDE</h2>
<ul>
<li>Faça o download da pasta com os arquivos .c e .h que serão utilizados</li>
<li>Crie um projeto normalmente no STMCube IDE</li>
<li>Na configuração do MX, você pode configurar os leds e botões da placa:
  <ul><li>LEDs: PB3 a PB6</li>
  <li>Botões: PA9 a PA12</li></li></ul>
<li>Ainda na configuração do MX, é necessário configurar os GPIOs dos pinos de controle do display
  <ul><li>RES=RESET: configurar o pino PB1 como GPIO_OUTPUT. Você deve dar um nome (LABEL) para esse pino. 
              Para isso, clique com o botão direito e use a opção "Enter User Label". Você deve configurar
              conforme o modelo de display ST7789_RST ou ST7735_RES </li>
  <li>DC: configurar o pino PB0 como GPIO_OUTPUT. Você deve dar um nome (LABEL) para esse pino. 
              Para isso, clique com o botão direito e use a opção "Enter User Label". Você deve configurar
              conforme o modelo de display ST7789_DC ou ST7735_DC</li>
  <li>CS: configurar o pino PA4 como GPIO_OUTPUT. Você deve dar um nome (LABEL) para esse pino. 
              Para isso, clique com o botão direito e use a opção "Enter User Label". Você deve configurar
              conforme o modelo de display ST7789_CS ou ST7735_CS</li></ul></li>
<li>Ainda na configuração do MX, é necessário configurar a SPI1 para comunicar com o display. Para isso, vá
      em Connectivity e selecione SPI1. Configure da seguinte forma:
      <ul><li>Mode: Full-Duplex Master</li>
      <li>Hardware NSS Signal: Disable</li>
      <li>Parameter Settings:
            <ul>
            <li>Basic: Motorola, 8 bits, MSB first</li>
            <li>Clock Parameters: Prescaler = 4, Clock Polarity (CPOL) = High, Clock Phase (CPHA) = 1 Edge</li>
            <li>Advanced Parameters: CRC Calculation = Disabled, NSS Signal Type = Software</li></ul>
            </li></ul></li>
<li>Salve a configuração.</li>
<li>No janela Project Explorer, selecione a pasta Core\Src. Clique com o botão direito e escolha a opção New => Folder. Escolha o nome conforme o modelo do display ST7789 ou ST7735 e clique em Finish</li>
<li>Selecione a pasta que acabou de criar (ST7789 ou ST7735), clique com o botão direito e escolha a opção IMPORT</li>
<li>No menu de seleção, escolha File System e clique em Next. Após, clique em Browse e vá até a pasta que contém os arquivo que você fez o donwload desse repositório e confirme clicando em Open. Na sequência, marque todos os arquivos e clique em Finish</li>
<li>Após esses passos, você poderá ver os arquivos na pasta. Por fim, você precisa incluir esses arquivos no Path para que o Build ocorra corretamente. Para isso, selecione a pasta que acabou de adicionar, clique com o botão direito e escolha a opção Add and Remove Include Path.</li>
<li>Pronto! Agora o projeto está configurado para usar as funcionalidades do display. .</li>
</ul>
<h2> Utilizando os recursos do display</h2>
No arquivo main.c você deverá fazer duas alterações importantes: incluir os arquivos .h da biblioteca e inicializar o display.
<ul>
<li>Para incluir os arquivos.h, localize no main.c a tag "USER CODE BEGIN INCLUDES". Na tag, inclua o código
  #include "st7789.h"
</li>
<li>Para inicializar o display, localize no main.c a tag "USER CODE BEGIN 2". Na tag, inclua a chamada da função
 ST7789_Init();
</li>
Pronto! Se quiser testar o display, você pode chamar a função  ST7789_Test(); dentro do loop principal do código. 
Faça um build e verifique erros. Se encontrar, revise esse passo-a-passo. Depois, só iniciar o debug e acompanhar a execução do código, preferencialmente, passo-a-passo.
</ul>
