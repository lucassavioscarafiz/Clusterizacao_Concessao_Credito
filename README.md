# Clusterização de Clientes para Concessao Credito

## 1.0 OBJETIVO DO CASE 💻

👉 Temos um banco fictício que tem a intensão de conceder crédito para seus clientes, baseado nas informações que eles possuem sobre os mesmos.

👉 O objetivo do case é realizar a clusterização dos clientes, ou seja, o agrupamento dos clientes em grupos específicos que possam indicar para o banco se eles devem ou não conceder crédito à estas pessoas.

👉 O dataset em questão possui a variável target binária que indica como 0 - Clientes não arriscados e 1 - Clientes arriscados. O objetivo de realizar a clusterização é saber se o modelo é eficiente em realizar o MESMO agrupamento, ou se ele consegue encontrar outros grupos com diferentes características, que sejam importantes na avaliação do banco para saber se o cliente irá receber, ou não, o crédito.

👉 Utilizarei o algoritmo K-Means para testar se o modelo consegue segmentar os clientes em apenas 2 grupos, igual a variável target da base, e também testarei com valores diferentes de K para identificar possíveis outros grupos para segmentação da base dos clientes.

## 2.0 METODOLOGIA 🔧

👉 Inicialmente realizei a leitura do dataset que possui 1000 linhas e 21 colunas. O dataset apresenta todas as features com dados pessoais e econômicos dos clientes do banco, que serão úteis para a clusterização do público do banco.

👉 Realizei a limpeza e o tratamento dos dados verificando a existência de dados duplicados, nulos e criando novas features que simplicam informações a partir de outras features.

👉 Apliquei o processo de `Feature Engineering` e `Feature Scalling` para facilitar a leitura dos dados para o modelo, e também o `PCA` para reduzir os dados do dataset em 2 dimensões e 3 dimensões. Optei por seguir com os dados reduzidos para 3 dimensões como visto abaixo:

![image](https://user-images.githubusercontent.com/81670585/227036961-6ae563ac-4d9b-490b-baa7-ab1b2f5d5edc.png)

👉 Utilizei os algoritmos de Machine Learning de Clusterização: `K-Means` e `DBSCAN`, porém acabei optando por utilizar o `K-Means` pela facilidade de construção do modelo.

👉 Para encontrar o melhor valor de K, utilizei o método Elbow, resultando em K=4 (como pode ser visto na Figura abaixo). Também utilizei o K=2 para avaliar se o modelo `K-Means` iria clusterizar a base de dados da mesma forma que foi segmentada originalmente.

![image](https://user-images.githubusercontent.com/81670585/227037108-4e1b6082-c63a-4f97-81d7-ffbdd07acbef.png)


## 3.0 RESULTADOS 🤖

Os resultados estão resumidos nas Tabelas e Gráficos abaixo:

* ### 3.1) Modelo K-Means com k=2
![image](https://user-images.githubusercontent.com/81670585/227037227-db83cce7-ac5d-4fae-ad67-50442ddda353.png)
![image](https://user-images.githubusercontent.com/81670585/227037252-e89d6304-3f35-49c4-b90c-0e87ec3e54df.png)

* ### 3.2) Modelo K-Means com k=4

![image](https://user-images.githubusercontent.com/81670585/227037331-e15f8f71-67a3-4a6a-ab6d-24e72c6594e0.png)
![image](https://user-images.githubusercontent.com/81670585/227037352-4d8a0b61-fe28-4a50-b37f-83593b53ddc6.png)

* ### 3.3) Modelo DBSCAN (eps = 1.0, min_samples= 8)

![image](https://user-images.githubusercontent.com/81670585/227037469-ebca2a31-0f28-4565-8eef-4429f59a2199.png)
![image](https://user-images.githubusercontent.com/81670585/227037486-9d70de7f-d4ef-43bc-91ba-f2ba888a1e69.png)

## 4.0 CONCLUSÃO 🎉

👉 o modelo `K-Means` com k=2 separou os clientes da base de dados em 2 grupos de uma maneira bem similar à variável target original (Como pode ser visto na Tabela abaixo).

CLIENTES                  | Modelo K-Means (k=2)  | Target Base   |
|------------------------ |---------------------- |---------------|
Cliente Não Arriscado (0) |       681             |     700       |  
Cliente Arriscado (1)     |       319             |     300       | 

👉 O modelo construido utilizando o algoritmo `DBSCAN` também teve um agrupamento similar ao original do dataset, porém o mesmo encontrou 39 ruídos, ou seja, clientes que não foram classificados nem para o grupo 0 e nem para o grupo 1.

CLIENTES                  | Modelo DBSCAN         | Target Base   |
|------------------------ |---------------------- |---------------|
Cliente Não Arriscado (0) |       672             |     700       |  
Cliente Arriscado (1)     |       289             |     300       |
Ruído (-1)                |       39                              |

👉 O modelo `K-Means` com k=4 encontrou 4 clusters diferentes

👉 O grupo 0 é o que está presente em maioria, os grupos 1 e 2 possuem perfis similares em relação às variáveis analisadas anteriores, e o grupo 3 é ligeiramente menor que o 1 e o 2.

👉 O modelo K-Means com clusterização de 4 grupos não trouxe diferenças significativas e nem vantagens em separar os grupos de 4 maneiras diferentes.

👉 Com isso conclui-se que o método `K-Means`, quando utilizado o k=2, apresenta uma segmentação melhor para este tipo de dataset.

👉 Sempre que a clusterização é necessária, é necessário entendermos qual a melhor quantidade cluster a ser construída, e neste caso, como o objetivo é apenas identificar clientes arriscados ou não, 2 clusters foram suficientes para resolver o problema de negócio.

👉 Claro que para outro dataset diferente, e com features diferentes, poderiamos ter a situação em que uma clusterização, com mais de 2 grupos, poderia apresentar um resultado melhor.

👉 A clusterização é um método não supervisionado que traz uma solução de negócio e que não apresenta certo ou errado. Cada caso poderá apresentar um resultado que se adeque ou não ao problema, mas acima de tudo, o importante é que resolva o problema de negócio.

👉 Neste caso conseguimos provar que o modelo `K-MEANS` (k=2) conseguiria resolver o problema de segmentação dos clientes na base. Se este dataset fosse entregue sem a variável target, o modelo K-MEANS (k=2) se sairia muito bem, uma vez que a previsão foi bem similar à variável target original.



<h3 align="left">Contato:</h3>
<p align="left">
<a href="https://linkedin.com/in/lucassavioscarafiz" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="lucassavioscarafiz" height="30" width="40" /></a>
</p>

📫 **lucassavioscarafiz@gmail.com**

<h3 align="left">Linguagens e Ferramentas:</h3>
<p align="left"> <a href="https://cloud.google.com" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/google_cloud/google_cloud-icon.svg" alt="gcp" width="40" height="40"/> </a> <a href="https://www.mysql.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="mysql" width="40" height="40"/> </a> <a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg" alt="pandas" width="40" height="40"/> </a> <a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a> <a href="https://scikit-learn.org/" target="_blank" rel="noreferrer"> <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="scikit_learn" width="40" height="40"/> </a> <a href="https://seaborn.pydata.org/" target="_blank" rel="noreferrer"> <img src="https://seaborn.pydata.org/_images/logo-mark-lightbg.svg" alt="seaborn" width="40" height="40"/> </a> </p>


