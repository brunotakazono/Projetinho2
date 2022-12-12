# Análise de Algoritmos Projetinho2
   ## Desenvolvido por:
      Auriane do Carmo Barbosa          Matricula: 20202045050480
      Bruno Matsuyama Pereira Takazono  Matricula: 20202045050439


Neste projeto você vai comparar dois algoritmos para resolver problema que podem ser resolvidos com programação  dinâmica. Na comparação, você vai apresentar um gráfico no qual o eixo horizontal representa o tamanho da entrada e o eixo vertical representa otempo de execução.
Seu código deve escolher aleatoriamente tamanhos de entradas n adequados para a comparação. Alem disso, seu código deve criar aleatoriamente entradas para o problema.
Você deve comparar os algoritmos de forma justa, então você deve criar os tamanhos de entrada e as entradas para executar os algoritmos levando isso em consideração. Você pode usar como base o que foi feito no projeto da primeira etapa. Configurar os experimentos de comparação de forma adequada  é um dos elementos considerados na avaliação desta atividade.

## 1. Comparar os algoritmos Rod-Cut recursivo com memoização e o Rod-Cut iterativo.As implementações dos dois algoritmos devem ser capazes de mostrar o custo da solução  ótima e mostrar a solução ótima em si. 


O método de programação dinâmica funciona da seguinte maneira. Tendo observado que uma solução recursiva ingênua é ineficiente porque resolve os mesmos subproblemas repetidamente, fazemos com que cada subproblema seja resolvido apenas uma vez , salvando sua solução. Se precisarmos nos referir à solução desse subproblema novamente mais tarde, podemos apenas procurá-la, em vez de recalculá-la. A programação dinâmica, portanto, usa memória adicional para economizar tempo de computação; serve como um exemplo de troca de memória de tempo . A economia pode ser dramática: uma solução de tempo exponencial pode ser transformada em uma solução de tempo polinomial. Uma abordagem de programação dinâmica é executada em tempo polinomial quando o número de subproblemas distintos envolvidos é polinomial no tamanho da entrada e podemos resolver cada um desses subproblemas em tempo polinomial.
Geralmente, existem duas maneiras equivalentes de implementar uma abordagem de programação dinâmica. Ilustraremos ambos com nosso exemplo de corte de haste.
A primeira abordagem é de cima para baixo com memoização . (NOTA: MEMOIZATION != MEMORIZATION) Nesta abordagem, escrevemos o procedimento recursivamente de maneira natural, mas modificado para salvar o resultado de cada subproblema (geralmente em um array ou tabela hash). O procedimento agora primeiro verifica se já resolveu esse subproblema anteriormente. Nesse caso, ele retorna o valor salvo, economizando mais cálculos nesse nível; caso contrário, o procedimento calcula o valor da maneira usual. Dizemos que o procedimento recursivo foi memorizado ; ele “lembra” quais resultados calculou anteriormente.
A segunda abordagem é o método ascendente . Essa abordagem normalmente depende de alguma noção natural do “tamanho” de um subproblema, de modo que resolver qualquer subproblema específico depende apenas da solução de subproblemas “menores”. Classificamos os subproblemas por tamanho e os resolvemos em ordem de tamanho, do menor primeiro. Ao resolver um subproblema específico, já resolvemos todos os subproblemas menores dos quais sua solução depende e salvamos suas soluções. Resolvemos cada subproblema apenas uma vez e, quando o vemos pela primeira vez, já resolvemos todos os subproblemas de pré-requisito.
Essas duas abordagens produzem algoritmos com o mesmo tempo de execução assintótico , exceto em circunstâncias incomuns em que a abordagem top-down não recursa para examinar todos os subproblemas possíveis. A abordagem de baixo para cima geralmente tem fatores constantes muito melhores, pois tem menos sobrecarga para chamadas de procedimento. Aqui está o pseudocódigo para o procedimento CUT-ROD de cima para baixo, com memoização adicionada:
Aqui, o procedimento principal MEMOIZED-CUT-ROD inicializa uma nova matriz auxiliar r[0..n] com o valor -infinity, uma escolha conveniente para denotar "desconhecido". (Valores de receita conhecidos são sempre não negativos.) Em seguida, ele chama sua rotina auxiliar, MEMOIZED-CUT-ROD-AUX.
O procedimento MEMOIZED-CUT-ROD-AUX é apenas a versão memorizada de nosso procedimento anterior, CUT-ROD. Ele primeiro verifica se o valor desejado já é conhecido e, se for, o retorna. Caso contrário, calcule o valor desejado q da maneira usual, salve-o em r[n] e retorne-o.
A versão ascendente é ainda mais simples:
Ambos os algoritmos BOTTOM-UP-CUT-ROD e MEMOIZED-CUT-ROD levam tempo linear para resolver cada valor de n, então a complexidade de tempo total é θ(n²)
Se estivermos interessados ​​no conjunto de cortes para uma solução ótima, bem como na receita que ela gera, basta acompanhar a escolha feita para otimizar cada subproblema, podemos fazer isso adicionando um segundo array s, que rastreia o ótimo tamanho da primeira peça cortada em cada subproblema.
Problema: Modifique MEMOIZED-CUT-ROD para retornar não apenas o valor, mas também a solução real




