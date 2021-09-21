# Processamento-de-Sinais

## Sobre o projeto

O projeto de processamento de sinais consiste na aplicação de filtros para determinar o número digitado em um smartphone através do áudio de cada botão. Além de determinar o número que foi digitado, um dos objetivos era eliminar os ruídos do áudio para captar somente as frequências de interesse.

![Sinal original](https://user-images.githubusercontent.com/83102320/134104379-a92d6d90-dde2-4d9d-871b-64d2d740a2a9.JPG)

O sinal original foi lido e armazenado em uma variável para facilitar toda a análise posteriormente. Na imagem acima é perceptível a dificuldade para diferenciar as frequências de interesse e do ruído presente no sinal.

![TF](https://user-images.githubusercontent.com/83102320/134104968-098f8c41-4de0-4e25-8a0a-eccebe502340.JPG)
![Magnitude](https://user-images.githubusercontent.com/83102320/134104977-721ac89c-91c3-4696-8034-af317d224564.JPG)

  Pela DTMF, a frequência máxima dos dígitos é 1500 Hz. Considerando o teorema de amostragem, a frequência mínima necessária para o registro sonoro é de 3000 Hz. No cálculo realizado para a amostra de áudio dada, o valor mínimo possível foi de 3150 Hz. Antes da realização da etapa de downsampling com o dado obtido, foi utilizado um filtro IIR anti-aliasing para remover frequências maiores que 1500 Hz e o resultado foi apresentado na Figura onde é apresentada a Magnitude, em conjunto com o gráfico do filtro em Dbs.
  Os filtros anti-aliasing foram usados para limpar frequências indesejadas de ruídos, sobrando apenas os dados que precisam ser analisados. O downsampling na prática deve ser utilizado para corrigir imperfeições do sinal, como o efeito “escada” na qual sua resolução não está boa o suficiente, ao analisar o gráfico com o espectro no domínio da frequência do sinal transformado, é notório que em torno dos picos há outos menores, o que atrapalha a análise, já que nem sempre os filtros anti-aliasing são totalmente eficientes na remoção, logo, é permitido o uso deste processo.
