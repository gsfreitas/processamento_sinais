# Processamento-de-Sinais

## Sobre o projeto

O projeto de processamento de sinais consiste na aplicação de filtros para determinar o número digitado em um smartphone através do áudio de cada botão. Além de determinar o número que foi digitado, um dos objetivos era eliminar os ruídos do áudio para captar somente as frequências de interesse.

![Sinal original](https://user-images.githubusercontent.com/83102320/134104379-a92d6d90-dde2-4d9d-871b-64d2d740a2a9.JPG)

O sinal original foi lido e armazenado em uma variável para facilitar toda a análise posteriormente. Na imagem acima é perceptível a dificuldade para diferenciar as frequências de interesse e do ruído presente no sinal.

![TF](https://user-images.githubusercontent.com/83102320/134104968-098f8c41-4de0-4e25-8a0a-eccebe502340.JPG)
![Magnitude](https://user-images.githubusercontent.com/83102320/134104977-721ac89c-91c3-4696-8034-af317d224564.JPG)

  Pela DTMF, a frequência máxima dos dígitos é 1500 Hz. Considerando o teorema de amostragem, a frequência mínima necessária para o registro sonoro é de 3000 Hz. No cálculo realizado para a amostra de áudio dada, o valor mínimo possível foi de 3150 Hz. Antes da realização da etapa de downsampling com o dado obtido, foi utilizado um filtro IIR anti-aliasing para remover frequências maiores que 1500 Hz e o resultado foi apresentado na Figura onde é apresentada a Magnitude, em conjunto com o gráfico do filtro em Dbs.
  Os filtros anti-aliasing foram usados para limpar frequências indesejadas de ruídos, sobrando apenas os dados que precisam ser analisados. O downsampling na prática deve ser utilizado para corrigir imperfeições do sinal, como o efeito “escada” na qual sua resolução não está boa o suficiente, ao analisar o gráfico com o espectro no domínio da frequência do sinal transformado, é notório que em torno dos picos há outos menores, o que atrapalha a análise, já que nem sempre os filtros anti-aliasing são totalmente eficientes na remoção, logo, é permitido o uso deste processo.

![Filtro IIR](https://user-images.githubusercontent.com/83102320/134105599-1b701728-1e91-4d1e-81e6-34615420ba9f.JPG)
![Sinal filtrado](https://user-images.githubusercontent.com/83102320/134105608-84424418-3b38-46c4-b73a-f4c9e029ca75.JPG)

O gráfico da TF, o áudio ainda apresenta frequências de até aproximadamente 8000 Hz. Porém, as frequências dos dígitos encontram-se entre 500Hz e 1500Hz. Foi utilizado um filtro FIR com janela Kaiser (beta igual a 12) e de um segundo filtro FIR com janela Hamming para remover as frequências menores que 600 e entre 1000 e 1100 Hz. Os filtros escolhidos foram evidenciados a seguir, assim como o sinal filtrado.

![Janelamento II](https://user-images.githubusercontent.com/83102320/134105967-c00358d9-4e81-4827-be71-4add6d31468d.JPG)
![Janelamento](https://user-images.githubusercontent.com/83102320/134105972-9b1a38b6-bd05-4b24-bbcc-ae8d4c72585c.JPG)

  O filtro Chebyshev foi utilizado por possuir melhor declive na banda de transição e eficiência na linearização da fase. Já a janela Kaiser foi usada por conseguir especificar os parâmetros do filtro e por ser ajustável o seu formato de acordo com o desvio desejado. Enquanto que a janela Hamming destacou-se por melhor detectar as frequências, reduzindo as oscilações na resposta em frequência.
  A Transformada de Fourier, a magnitude e o espectro de enrgia foram novamente calculados e mostrados abaixo.
  
![TF II](https://user-images.githubusercontent.com/83102320/134106380-8080dc73-8b4e-4cb2-950a-f948f716b7b6.JPG)
![Magnitude II](https://user-images.githubusercontent.com/83102320/134106408-34394d05-b3f0-4020-b974-94eeb615361f.JPG)
![Energia](https://user-images.githubusercontent.com/83102320/134106418-3ebf7899-890e-4422-8704-53c325f6e90b.JPG)

  Após todo o processo de filtragem mostrado anteriormente pudemos analisar e encontrar oito picos em instantes distintos. Esses picos mostram exatamente quais foram as teclas discadas, podendo relacionar diretamente ao tempo, onde há oito picos. A janela do tipo Hanning então foi aplicada no sinal filtrado para evitar cortes abruptos e fazer com que haja uma transição mais suave entre as frequências de rejeição e as bandas de passagem. Em seguida, para cada sinal amostrado foi feita a transformada de Fourier para analisá-los no domínio da frequência.
  
  ![FreqFinal](https://user-images.githubusercontent.com/83102320/134106669-135b7f38-0044-4475-96e8-ab7286b82ffe.JPG)
  
  Pela magnitude percebe-se então que o número digitado é zero. O processo se repete para todos os outros dígitos até formar o número discado em si.
  
## Bibliotecas
- numpy
- scipy
- matplotlib

## Autor
Gabriel Freitas

www.linkedin.com/in/gabrielsfreitas
