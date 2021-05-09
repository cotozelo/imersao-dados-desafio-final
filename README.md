
# Desafio Final Imersão Dados

Este gitbhub, é um projeto que tem como objetivo estudar Ciência de Dados. E foi idealizado durante o Curso de Imersão Dados aplicado pela <a href="https://www.alura.com.br/">Alura</a>, a partir de uma competição realizanda no Kaggle.

## O Kaggle

Esse projeto foi inspirado em uma competição do <a href="https://www.kaggle.com/c/lish-moa">kaggle</a>, onde que tem os dados disponiblizados pelo <a href="https://lish.harvard.edu/">Laboratory Innovation Science at Harvad</a>. 

A competição do <a href="https://www.kaggle.com/c/lish-moa">kaggle</a> tem como objetivo principal, melhorar o algoritmo que classifica os medicamento com base em sua ativação biológica, ou seja, identifcar quais "drogas" ativam quais mecanismos de ação (MoA).
 
Neste nosso projeto, seguiremos a mesma linha de da competição e tentaremos propor algum algoritmo que consiga melhora essa predição. 

### Os Dados

Um conjunto de dados exclusivo que combina a expressão gênica e os dados de viabilidade celular. Os dados são baseados em uma nova tecnologia que mede simultaneamente (nas mesmas amostras) as respostas das células humanas aos medicamentos em um pool de 100 tipos de células diferentes (resolvendo assim o problema de identificação ex-ante, quais tipos de células são mais adequados para um determinado medicamento). Além disso, contém às anotações do MoA para mais de 5.000 medicamentos neste conjunto de dados.

### Validação

Com base nas anotações de MoA, a precisão das soluções será avaliada no valor médio da função de perda logarítmica aplicada a cada par de anotação de droga-MoA.

## O Curso de Imersão de Dados

### Sobre os Dados

Usaremos os dados como foram disponibilizados pela Alura durante o curo se Imersão de Dados. Os dados se encontram na pasta _Dados_, e estão dividido em dois arquivos: 
* _dados_experimentos.zip_, contém as informações dos experimentos, são elas: id, tratamento, tempo, dose, droga, expreção genica e tipos de células
* _dados_resultados.csv_, contém a relção de entre os experementos e os MoA's. 

### Sobre as Aulas

Durante as aulas foram realizandos vários estudos nessos dados disponibilizados, esse estudos estão disponíveis no arquivo "Aulas.ipynb" dentro da pasta "Notebooks".

## O Desafio Final do Curso

Como desafio final do curso foi proposto que fizessemos um estudo dos dados disponibilizados, onde tentariamos seguir a linha do que a competição pede. O código dos estudos estão disponiveis no arquivo _primeira_analise.ipynb_ na pasta _Notebooks_.

### o Estudo
 
No notebook _primeira_analise.ipynb_ encontrasse detalhadamente os estudos efetuados. 
Aqui iremos somente apresenta a analise final do estudo.

#### Analise final

Após todo tratamento dos dados, construimos dois modelos de classifica: baseline (dummy) e regressão logistica. Afim de classificar quais experimentos tiveram ativação de alguma mecanismos de ação (MoA). Para baseline foi escolhido um método dummy, ou seja, o método escolhe a classe de maior frequencia e opta por atrituir a todas as ocorrência essa classe de maior frequencia. 

Como resultados constatamos que o metódo baseline obteve 60% e a regressão logistica 62%, o que acreditamos ser um resultado muito ruim, vista a proximidade entre o baseline e a regressão logistica.

Então propomos uma segunda abortagem, classificar segundo uma ação expecifica. Selecionamos a ação "inhibitor" que tem a maior quantidade de ocorrência e mais MoA's relacionados. Os resultados melhoraram, o baseline obteve 66% e a regressão logistica 75%, que é uma melhora significativa nos resultados. O que nos inclina a dizer que classificar os experimentos em somente em duas classes "existe moa ativo" e "não existe moa ativo", não é uma boa abordagem. Talvez essa abordagem não seja boa em virtude das caracteristicas que cada MoA tem em relação às experessões genéticas e tipos celulares.

Extendendo um pouco, propomos um segundo modelo, classificar segundo a ação "antiarrhythmic", esta é um ação com somete um MoA relacionado e contém somente 6 ocorrências. Os resultados foram: baseline 99.9% e regressão logistica 99.9%. Esse pode parecer um resultado bom, mas na realidade não é, isso por que como evidenciado no baseline, se o classificador selecionar para todas ocorrência a classe "não ativado" a precissão encontrada é 99.9%. Mas na realidade não consegui classificar visto que não encontrou o experimento com MoA ativo. Assim podemos dizer que para MoA's com poucas ocorrência a dificuldade de classificação é ainda maior.

####Trabalhos futuros

Como sugestão para trabalhos futuros, propomos:
 * Usar outros classificadores mais complexos.
 * Para MoA's com poucas ocorrência, tentar usar metodos de agrupamento, afim de agrupar MoA's semelhantes aumentando assim as ocorrências.
